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
Suivez les instructions à l'écran. Ici nous allons choisir `None` quand l'outil demande la stack à utiliser, pour avoir le choix par la suite du front et du back.

## Angular

Commencez par ajouter le plugin nx:

```shell
nx add @nx/angular
```

Puis ajoutez votre application frontend:

```shell
nx generate @nx/angular:app apps/frontend
```

> en cas d'erreur de type
>>  NX   The "@nx/angular:application" generator doesn't yet support the existing TypeScript setup
>> 
>>  We're working hard to support the existing TypeScript setup with the "@nx/angular:application" generator. We'll soon release a new version of Nx with support for it.
> 
> voici une résolution possible https://github.com/nrwl/nx/issues/28322#issuecomment-2627757718

## NestJs

Commencez par ajouter le plugin nx:

```shell
nx add @nx/nest
```

Puis ajoutez votre application backend:

```shell
nx generate @nx/nest:app apps/backend --frontendProject frontend
```

> `--frontendProject frontend` permet de créer le proxy dans le projet frontend pour lier le serveur backend de développement
