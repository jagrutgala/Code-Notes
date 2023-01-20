# Angular Modules

In Angular, a module is a way to organize different parts of our application. A module is a collection of components, directives, pipes, and services.

An Angular application is made up of one or more modules. The root module, also known as the `app module`, is the entry point of the application and is responsible for bootstrapping the application.

Other modules in the application are typically used to organize functionality and to share functionality among different parts of the application.

An Angular module is defined using the `@NgModule decorator`, which is applied to a class. The @NgModule decorator takes an object that contains properties that describe the module. The most important properties of the @NgModule decorator are:

- `declarations`: An array of components, directives, and pipes that are part of the module.
- `imports`: An array of other modules that the module depends on.
- `providers`: An array of services that are available to the module.
- `bootstrap`: The component that is the root component of the application.
  Here's an example of a simple Angular module:

**my-module.module.ts**

```typescript
import { NgModule } from "@angular/core";
import { CommonModule } from "@angular/common";
import { MyComponent } from "./my.component";
import { MyService } from "./my.service";

@NgModule({
  declarations: [MyComponent],
  imports: [CommonModule],
  providers: [MyService],
})
export class MyModule {}
```

## Creating Module using Ng-CLI

```
$ ng generate module my-module
```

OR

```
$ ng g m my-module
```

This command will create a new directory called `my-module` in the `src/app` directory, and inside it will contain a new file called `my-module.module.ts` which is the new module.

# Next Steps

[<-- Angular](Angular.md#angular) | [Bootstrap -->](Bootstrap.md#angular-bootstrap)

- [Bootstrap](Bootstrap.md#angular-bootstrap)
- [CLI](Angular-CLI.md#angular-cli)
