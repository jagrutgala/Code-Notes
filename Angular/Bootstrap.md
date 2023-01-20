# Angular Bootstrap

The entry point to every angular application is the `main.ts`, which contains the last line

```typescript
platformBrowserDynamic().bootstrapModule(AppModule);
```
The `platformBrowserDynamic()` part of this line of code indicates that we are about to boot Angular in a browser environment. As Angular can be used in Javascript host environments asides the browser (e.g. on the server or in a web worker), its thus imperative that we specify the environment in which our App is to be booted.

The `bootstrapModule()` function helps bootstrap our root module taking in the root module as its argument.

`AppModule` is our root module which is the entry module for our application, this can actually be any of the modules in our application but by convention AppModule is used as the root module.

In our AppModule, we then need to specify the component that will serve as the entry point component for our application. This happens in our `app.module.ts` file where we import the entry component (conventionally AppComponent) and supply it as the only item in our bootstrap array inside the `NgModule` configuration object.

```typescript
  bootstrap: [AppComponent]
```

<!-- # Next Steps
[<-- Angular](Angular.md) | [Bootstrap -->](Bootstrap.md#angular-bootstrap) -->
