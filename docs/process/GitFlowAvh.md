# Git Flow & Git Flow AVH 

## Qu'est-ce que Git Flow ?

Git Flow est une méthodologie de gestion de branches pour Git, conçue pour faciliter le développement collaboratif et la livraison continue. Elle structure le cycle de vie du code source autour de plusieurs types de branches, chacune ayant un rôle précis.

## Les Branches Principales

- **main** : Contient le code de production stable.
- **develop** : Intègre les fonctionnalités terminées, en attente de mise en production.

## Les Branches de Support

- **feature/** : Pour le développement de nouvelles fonctionnalités.  
  Exemple : `feature/ajout-paiement-carte`
- **release/** : Préparation d'une nouvelle version de production.  
  Exemple : `release/1.2.0`
- **hotfix/** : Corrections urgentes sur la production.  
  Exemple : `hotfix/correction-bug-paiement`

## Cycle de Vie Typique

1. **Développement d'une fonctionnalité**
   - Créer une branche à partir de `develop` :  
     `git checkout develop`  
     `git checkout -b feature/ma-fonctionnalite`
   - Développer, puis fusionner dans `develop` à la fin :  
     `git checkout develop`  
     `git merge feature/ma-fonctionnalite`

2. **Préparation d'une release**
   - Créer une branche à partir de `develop` :  
     `git checkout develop`  
     `git checkout -b release/1.0.0`
   - Effectuer les derniers correctifs, puis fusionner dans `main` et `develop` :  
     `git checkout main`  
     `git merge release/1.0.0`  
     `git checkout develop`  
     `git merge release/1.0.0`

3. **Correction urgente (hotfix)**
   - Créer une branche à partir de `main` :  
     `git checkout main`  
     `git checkout -b hotfix/bug-critique`
   - Corriger, puis fusionner dans `main` et `develop` :  
     `git checkout main`  
     `git merge hotfix/bug-critique`  
     `git checkout develop`  
     `git merge hotfix/bug-critique`


## Qu'est-ce que Git Flow AVH ?

Git Flow AVH est une version améliorée de l’outil git-flow original, compatible avec les dernières versions de Git et intégrant de nombreuses corrections et fonctionnalités supplémentaires. Il facilite la gestion des branches et des versions dans un projet Git, en suivant une méthodologie structurée.

1. **Origine**
-	git flow : Outil original créé par Vincent Driessen pour appliquer le workflow Git Flow.
-	git flow AVH : Fork maintenu par Peter van der Does (AVH), avec de nombreuses améliorations et corrections.
2. **Compatibilité et maintenance**
-	git flow : Plus maintenu activement, peut poser des problèmes avec les versions récentes de Git.
-	git flow AVH : Maintenu, compatible avec les dernières versions de Git, disponible sur la plupart des gestionnaires de paquets (brew, apt, choco…).
3. Fonctionnalités supplémentaires
-	**git flow AVH ajoute** :
-	Branches bugfix/ : gestion native des corrections de bugs sur develop/support.
-	Branches support/ : maintenance de versions anciennes en parallèle.
-	Options avancées : gestion des tags, hooks personnalisés, intégration continue facilitée.
-	Plus de commandes et d’options : ex : git flow bugfix start, git flow support start, etc.
-	Meilleure gestion des conflits et des merges.
  
## Installation

Git flow n'etant plus maintenu c'est c'est git flow avh qui se trouve par défaut dans la plus part des installation récente de git (c'est le cas de git pour windows)

# Outillage
## Initialisation

Dans le dossier de votre projet :
```sh
git flow init
```
Suivez les instructions pour définir les noms des branches principales et de support.

## Commandes principales

Git flow et Git flow Avh apportent à git des nouvelles commandes pour automatiser les process et n'avoir qu'une seule commande a chaque étape
### Une fonctionnalité :

```sh
git flow feature start nom-fonctionnalite
git flow feature finish nom-fonctionnalite
```
### Une release :
```sh
git flow release start 1.2.0
git flow release finish 1.2.0
```
### un hotfix :
```sh
git flow hotfix start correction-critique
git flow hotfix finish correction-critique
```


## Bonnes pratiques

- Utilisez des noms explicites pour vos branches.
- Fusionnez régulièrement pour limiter les conflits.
- Utilisez les Pull Requests pour la revue de code.
- Documentez les releases et hotfixes dans vos messages de commit.

## Ressources

- [Documentation officielle Git Flow AVH](https://github.com/petervanderdoes/gitflow-avh)
- [Cheat Sheet Git Flow (EN)](https://danielkummer.github.io/git-flow-cheatsheet/)
