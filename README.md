# Biblio 📖

Logiciel de gestion de bibliothèque en ligne de commande : il enregistre les livres, les emprunts et les retours d'une association, pour ses bénévoles.

## Sommaire

- [Prérequis](#prérequis)
- [Installation](#installation)
- [Utilisation](#utilisation)
- [Tests](#tests)
- [Structure du projet](#structure-du-projet)
- [Contribuer](#contribuer)
- [Auteurs](#auteurs)

## Prérequis

- **Python 3** (développé sous Python 3.14.7)
- **Git**

> **Quelle commande Python utiliser ?**
>
> | Système | Commande |
> |---|---|
> | Windows | `python`, ou `py` si `python` ne marche pas |
> | macOS / Linux | `python3` |
>
> Dans la suite, les exemples utilisent `python`. Remplacez-le par `python3` ou `py` selon votre système.

## Installation

1. Cloner le dépôt, soit avec GitHub Desktop (*File > Clone repository > onglet URL*), soit avec Git en ligne de commande :

   ```
   git clone https://github.com/GADEL-01/biblio-tp
   ```

2. Ouvrir le dossier du dépôt dans une invite de commandes ou un terminal.
   Avec GitHub Desktop : *Repository > Open in Command Prompt*.

3. Créer la base de démonstration (**à faire une fois, avant tout le reste**) :

   ```
   python biblio.py init
   ```

   Résultat attendu :

   ```
   Base initialisee : 6 livres, 3 membres.
   ```

## Utilisation

Toutes les commandes se lancent depuis la racine du dépôt, après avoir fait `python biblio.py init` (voir [Installation](#installation)).

### Lister les livres

```
python biblio.py livres
```

Résultat attendu :

```
[1] L'Etranger (Albert Camus) : disponible
[2] Dune (Frank Herbert) : emprunte
[3] Le Petit Prince (Antoine de Saint-Exupery) : disponible
[4] Fondation (Isaac Asimov) : disponible
[5] Les Miserables (Victor Hugo) : disponible
[6] Neuromancien (William Gibson) : disponible
```

### Chercher un livre

```
python biblio.py chercher "Dune"
```

Résultat attendu :

```
[2] Dune (Frank Herbert)
```

### Emprunter un livre

```
python biblio.py emprunter <id_livre> <id_membre>
```

Exemple :

```
python biblio.py emprunter 3 1
```

Résultat attendu :

```
Emprunt enregistre : livre 3, membre 1.
```

### Rendre un livre

```
python biblio.py rendre <id_livre>
```

Exemple :

```
python biblio.py rendre 3
```

Résultat attendu :

```
Retour enregistre pour le livre 3.
```

### Lister les retards

Affiche les livres empruntés depuis plus de 14 jours et non rendus.

```
python biblio.py retards
```

Résultat attendu :

```
Dune, emprunte par Alice Martin : 254 jours de retard
```

Le nombre de jours dépend de la date du jour : il sera différent chez vous.

## Tests

```
python -m unittest discover -s tests -t .
```

Résultat attendu :

```
Ran 4 tests in 0.1s

OK
```

La durée affichée peut varier d'une machine à l'autre.

## Structure du projet

```
biblio-tp/
├── biblio.py            # programme principal
├── README.md            # ce fichier
├── CONTRIBUTING.md      # règles de contribution
├── docs/
│   ├── adr/             # décisions techniques (ADR)
│   └── circulation.md   # circulation de l'information dans l'équipe
├── tests/
│   └── test_biblio.py   # tests automatisés
└── .github/
    ├── ISSUE_TEMPLATE/  # modèles d'issues
    └── workflows/       # intégration continue
```

## Contribuer

Les règles complètes sont dans [CONTRIBUTING.md](CONTRIBUTING.md). En résumé :

1. **Issue** : une issue par problème, avec un titre qui dit ce qui se passe et où. Utiliser le bon modèle et le bon label (`bug`, `enhancement`, `question`, `securite`, `documentation`).
2. **Branche** : jamais de push direct sur `main`. Nommer la branche `fix/<n°-issue>-mots-cles` pour une correction, `feat/<n°-issue>-mots-cles` pour une évolution, `docs/<n°-issue>-mots-cles` pour la documentation.
3. **Pull request** : décrire le contexte (avec `Closes #n`), les changements, l'impact et comment tester. Lancer les tests avant de l'ouvrir, et vérifier que la base est bien le dépôt du groupe, branche `main`.
4. **Review** : au moins un autre membre relit la PR. L'auteur ne valide jamais seul son propre changement ; le mainteneur décide du merge.

## Auteurs

- Anthony Nagul ([@Nixus-security](https://github.com/Nixus-security))
- Gauthier
- Clement