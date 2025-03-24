# monorepo-bootstrap

Ce repo vise à résumer comment démarrer avec un monorepo Nx, un backend utilisant NestJs et un frontend en Angular.

## Prérequis

Un minimum d'outils est nécessaire:
- NodeJs (https://nodejs.org/)
- Optionnel: 
  ```shell
  npm i -g nx
  ```

## le monorepo Nx

Créez un nouveau workspace Nx avec Angular et NestJS.

```shell
npx create-nx-workspace@latest monorepo
```
Suivez les instructions à l'écran. Ici nous allons choisir `Angular` quand l'outil demande la stack à utiliser.

## NestJs

Commencez par ajouter le plugin nx:

```shell
nx add @nx/nest
```

Puis ajoutez votre application backend:

```shell
nx generate @nx/nest:app apps/backend --frontendProject frontend
```

> citez l'application `frontend` avec le nom donné à l'étape précédente 

> `--frontendProject frontend` permet de créer le proxy dans le projet frontend pour lier le serveur backend de développement

## Lancement en parallèle

```shell
nx run-many --target=serve --projects=backend,frontend --parallel
```
