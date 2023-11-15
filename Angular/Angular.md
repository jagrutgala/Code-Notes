# Angular

Angular is an application-design framework and development platform for creating efficient and sophisticated single-page apps.

## Prerequisite

- Html, CSS, Javascript
- Classes, Functions, Modules
- Typescript, dependency injection, decorators

> Note
> If not familiar with Typescript, see typescript crash course [here](Typescript.md)

## Getting Started

With Node installed, to install a and create a angular project, use the following command -

```
$ npm install -g @angular/cli

$ npm init -y

$ ng new <project-name>
```

Now you have a project with angular installed. Use the following command to run the project on `localhost`.

```
$ ng serve -o
```

## Directory Structure

An Angular project's folder structure can change based on the project's size and complexity, but it often follows a consistent pattern. An Angular project's basic folder structure consists of the following main folders:

- `node_modules` -> This folder is created when you run npm install, and it contains all of the project's dependencies.

- `src` -> This is the main folder for the application's source code.

- `.angular-cli.json` -> This file contains configurations for the Angular CLI.

- `package.json` -> This file contains the project's dependencies, scripts, and other metadata.

- `tsconfig.json` -> This file contains the TypeScript compiler configurations for the application.

- `angular.json` -> This file contains the angular project configurations for the application.

- `.gitignore` -> This file contains the configuration for git, which files to ignore.

- `.editorconfig` -> This file contains the configuration for editor and code format.

- `src/app` -> This folder contains the actual code for the application, including the components, services, pipes, and other code.

- `src/app/components` -> This folder contains all the components of the application.

- `src/app/services` -> This folder contains all the services of the application.

- `src/app/models` -> This folder contains all the data models of the application.

- `src/assets` -> This folder contains all the assets of the application such as images, fonts and etc.

- `src/environments` -> This folder contains the environment-specific settings of the application such as api endpoint etc.

- `src/styles` -> This folder contains all the global css and scss files of the application.

# Next Steps
[<-- Typescript](Typescript.md#typescript) | [Bootstrap -->](Bootstrap.md#angular-bootstrap)

- [Bootstrap](Bootstrap.md#angular-bootstrap)
- [Components](Component.md#angular-components)
- [Modules](Modules.md#angular-modules)
- [CLI](Angular-CLI.md#angular-cli)
