0004 — Convention de nommage des branches
Date : 2026-10-05
Statut : proposé
Contexte
Le dépôt est partagé entre plusieurs contributeurs qui travaillent sur des corrections et des évolutions en parallèle. Sans convention, les noms de branches deviennent ambigus (fix, test, ma-branche, etc.), ce qui rend difficile de savoir à quoi correspond chaque branche dans la liste et dans les pull requests.

Le module impose qu'aucun push direct ne soit fait sur main à partir de la séance 2 : chaque changement passe par une branche dédiée et une PR relue.

Décision
Les branches suivent le format :

<type>/<numéro-issue>-<description-courte>
Types
Type	Usage
fix	Correction d'un bug lié à une issue
feat	Nouvelle fonctionnalité ou évolution
docs	Documentation uniquement (README, ADR, circulation.md)
refactor	Réécriture sans changement de comportement visible
Règles
La description est en kebab-case, en français, sans accent ni espace.
Le numéro d'issue est obligatoire pour fix et feat ; facultatif pour docs.
La branche est supprimée après le merge de la PR.
Exemples
fix/1-chercher-apostrophe
fix/2-retards-livres-rendus
fix/3-double-emprunt
fix/4-membre-inexistant
feat/5-afficher-emprunteur-dans-livres
docs/readme-initial
docs/adr-0002-sqlite
Justification
Un nom de branche structuré permet à n'importe quel membre de l'équipe de comprendre immédiatement l'objet d'une branche sans ouvrir la PR, et de retrouver l'issue associée en un clic.

Le lien fix/<numéro> complète la traçabilité déjà assurée par Closes #n dans la description de la PR.

Conséquences
Positives :

La liste des branches en cours reflète la liste des tâches en cours.
La PR hérite naturellement d'un titre clair si on reprend le nom de la branche.
Le mainteneur peut identifier les branches orphelines (sans PR associée).
Négatives / limites :

Ajoute une contrainte à mémoriser pour chaque nouveau contributeur.
Ne s'applique pas aux branches feature/ déjà présentes dans le dépôt template (celles-ci sont réservées aux PR de Sam en S2 et ne doivent pas être modifiées).