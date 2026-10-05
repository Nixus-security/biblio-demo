0003 — Requêtes SQL paramétrées obligatoires
Date : 2026-10-05
Statut : proposé
Contexte
Le bug signalé dans l'issue #1 révèle que la fonction search_books construit sa requête SQL par concaténation de chaînes :

query = "SELECT id, title, author FROM books WHERE title LIKE '%" + text + "%'"
cur.execute(query)
Si text contient une apostrophe (ex. : l'étranger), la syntaxe SQL est cassée et le programme plante avec une OperationalError.

Ce pattern expose également l'application à une injection SQL : un utilisateur malveillant pourrait passer une valeur comme ' OR '1'='1 pour extraire ou corrompre toutes les données.

Toutes les autres fonctions utilisent correctement des requêtes paramétrées (?), sauf search_books.

Décision
Toute requête SQL qui intègre une valeur externe (saisie utilisateur, paramètre de fonction) doit utiliser des requêtes paramétrées avec des espaces réservés ?.

La concaténation de chaînes pour construire une requête SQL est interdite.

La correction appliquée à search_books :

# Avant (interdit)
query = "SELECT id, title, author FROM books WHERE title LIKE '%" + text + "%'"
cur.execute(query)

# Après (correct)
cur.execute(
    "SELECT id, title, author FROM books WHERE title LIKE ?",
    ("%" + text + "%",)
)
Justification
Les requêtes paramétrées délèguent l'échappement des valeurs au pilote SQLite, qui garantit qu'aucune valeur ne peut modifier la structure de la requête, quel que soit son contenu.

C'est la pratique standard en Python (PEP 249) et la seule défense fiable contre l'injection SQL.

Conséquences
Positives :

Le crash avec les apostrophes est corrigé (l'étranger fonctionne).
L'injection SQL est impossible dans les fonctions qui respectent cette règle.
La règle est simple à vérifier en relecture : toute requête avec + ou % dans la chaîne SQL doit être refusée.
Négatives / limites :

Les requêtes paramétrées ne s'appliquent qu'aux valeurs, pas aux noms de tables ou de colonnes. Si un nom de colonne devait être dynamique, une liste blanche explicite serait nécessaire.
Cette décision ne couvre pas les autres vecteurs d'injection éventuels (ex. : noms de fichiers, variables d'environnement).