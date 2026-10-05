Biblio 📖
Logiciel de gestion de bibliothèque.

Sommaire
Prérequis
Installation
Utilisation
Tests
Structure du projet
Contribuer
Auteurs
Prérequis
Python3 (développé sous Python v3.14.7)
Git
Installation
Cloner le dépôt soit avec GitHub Desktop soit avec Git CLI
git clone https://github.com/GADEL-01/biblio-tp
Ouvrir le dossier du repository dans une invite de commande/terminal.

Créer la base de démonstration (à faire une fois, avant le reste)

python biblio.py init
Résultat attendu :

Base initialisee : 6 livres, 3 membres.
Sous macOS ou Linux : python3. Sous Windows, si python ne marche pas : py.

Utilisation
Toutes les commandes se lancent depuis la racine du dépôt, après avoir fait python biblio.py init (voir Installation). Sous macOS ou Linux : python3. Sous Windows, si python ne marche pas : py.

Lister les livres
python biblio.py livres
Résultat attendu :

[1] L'Etranger (Albert Camus) : disponible
[2] Dune (Frank Herbert) : emprunte
[3] Le Petit Prince (Antoine de Saint-Exupery) : disponible
[4] Fondation (Isaac Asimov) : disponible
[5] Les Miserables (Victor Hugo) : disponible
[6] Neuromancien (William Gibson) : disponible
Chercher un livre
python biblio.py chercher "Dune"
Résultat attendu :

[2] Dune (Frank Herbert)
Emprunter un livre
python biblio.py emprunter <id_livre> <id_membre>
Exemple :

python biblio.py emprunter 3 1
Résultat attendu :

Emprunt enregistre : livre 3, membre 1.
Rendre un livre
python biblio.py rendre <id_livre>
Exemple :

python biblio.py rendre 3
Résultat attendu :

Retour enregistre pour le livre 3.
Lister les retards
python biblio.py retards
Résultat attendu (liste les livres empruntés depuis plus de 14 jours et non rendus) :

Dune, emprunte par Alice Martin : 254 jours de retard
Tests
python -m unittest discover -s tests -t .
Résultat attendu :

Ran 4 tests in 0.1s

OK
Sous macOS ou Linux : python3. Sous Windows, si python ne marche pas : py.

Structure du projet
biblio-tp/
├── biblio.py               # programme principal
├── README.md               # ce fichier
├── CONTRIBUTING.md         # règles de contribution
├── docs/
│   ├── adr/                # décisions techniques (ADR)
│   └── circulation.md
├── tests/
│   └── test_biblio.py      # tests automatisés
└── .github/
    ├── ISSUE_TEMPLATE/     # modèles d'issues
    └── workflows/          # intégration continue
Contribuer
Merci de vous référer au fichier CONTRIBUTING.md

Auteurs


AnthonyN Nagul 

Gauthier 

Clement 