0002 — SQLite plutôt qu'un fichier JSON ou un serveur PostgreSQL
Date : 2026-10-05
Statut : proposé
Contexte
Biblio doit stocker de façon persistante trois types de données liées entre elles : les livres, les membres et les prêts. Trois options ont été envisagées :

Fichier JSON — simple, lisible, sans dépendance.
SQLite — base relationnelle embarquée, incluse dans la bibliothèque standard Python (sqlite3).
Serveur PostgreSQL — base relationnelle client-serveur, nécessite une installation séparée.
Le projet est un outil associatif de petite taille, sans accès distant ni utilisateurs simultanés.

Décision
Nous utilisons SQLite via le module sqlite3 de la bibliothèque standard Python.

Justification
Critère	JSON	SQLite	PostgreSQL
Dépendances externes	Aucune	Aucune	Serveur à installer
Relations entre données	Manuelles	Natives (clés étrangères)	Natives
Requêtes filtrées	Boucles Python	SQL	SQL
Portabilité	Fichier texte	Fichier .db unique	Nécessite un serveur
Adapté à la taille du projet	Oui (si peu de données)	Oui	Surdimensionné
SQLite permet d'exprimer les relations entre livres, membres et prêts nativement en SQL, sans aucune dépendance externe, et fonctionne avec un simple fichier biblio.db déplaçable.

Conséquences
Positives :

Aucune installation préalable au-delà de Python 3.8+.
Les requêtes SQL permettent des filtrages précis (ex. : prêts actifs, retards).
Le fichier biblio.db peut être supprimé et recréé avec python biblio.py init.
Négatives / limites :

SQLite ne supporte pas les accès concurrents en écriture : inadapté si plusieurs bénévoles utilisent l'outil simultanément sur un serveur partagé.
En cas de montée en charge, une migration vers PostgreSQL serait nécessaire.
Le fichier biblio.db ne doit pas être versionné (ajouté dans .gitignore).