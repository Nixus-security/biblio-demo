Circulation de l'information : groupe Anthony , Gauthier et clement 
À compléter par le groupe en séance 1. Chaque section est rédigée et poussée par un membre différent.

1. Rôles
Rédigé par : @pseudo

Qui produit les issues, qui relit les pull requests, qui décide du merge.

2. Où circule chaque information
Rédigé par : @pseudo

Information	Qui la produit	Qui la valide	Où elle est stockée	Durée de vie
Code source	Auteur de la PR	Relecteur + Mainteneur	Git (commits)	Permanente
Bug signalé	Toute personne qui constate	Mainteneur (labels, tri)	GitHub Issues	Jusqu'à résolution
Décision technique	Auteur de l'ADR (via PR)	Relecteur + Mainteneur	docs/ (ADR)	Tant que la décision est valable
Documentation d'installation	Auteur (via PR)	Relecteur + Mainteneur	README.md	Toute la vie du projet
Question rapide entre membres	N'importe qui	—	Discord / chat	Quelques heures
Compte rendu de réunion	—	—	Discord (éphémère)	Non conservé
3. Règles de l'équipe
Rédigé par : @NightFoxIsCool

Titres d'issue
Format : <commande> <symptôme> (<type d'erreur>)
Exemples : chercher plante avec une apostrophe (OperationalError), retards liste les livres déjà rendus
Pas de majuscule inutile, pas de point final, pas de "bug" dans le titre (le label suffit)
Labels utilisés
Label	Usage
bug	Le logiciel ne fait pas ce qu'il devrait faire
enhancement	Évolution souhaitée, rien n'est cassé
question	Comportement incertain, à qualifier
securite	Faille de sécurité (SQL injection, etc.)
documentation	Tâche de doc sans changement de code
Tri et assignation
Le mainteneur trie les nouvelles issues (labels, assignation)
Une issue = un seul problème
L'auteur d'un changement ne le valide jamais seul
Aucun push direct sur main à partir de la séance 2 : tout passe par une PR relue
Nommage des branches
fix/<numéro-issue>-<description-courte> pour les corrections de bug
feat/<numéro-issue>-<description-courte> pour les évolutions
docs/<description-courte> pour la documentation