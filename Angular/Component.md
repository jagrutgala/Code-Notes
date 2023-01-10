## Angular Components

Components are the building blocks of angular application. In Angular component consists of class with @Component decorator. `@Component` decorator provides angular with metadata about the component.

### Generating Components using CLI

```
$ ng generate component <component-name>
```

By default, this command creates the following:

A directory named after the component

- A component file, <component-name>.component.ts
- A template file, <component-name>.component.html
- A CSS file, <component-name>.component.css
- A testing specification file, <component-name>.component.spec.ts

`@Component` decorator specifies the the following -

- `selector`: The CSS selector that identifies this directive in a template and triggers instantiation of the directive.

- `template`/ `templateUrl`: An inline HTML template for an Angular component. Or path to the HTML file that contains the template for an Angular component.

- `styles`/ `styleUrls` _(optional)_: One or more inline CSS stylesheets to use in this component. Or path to the CSS files that contain styles to use in this component.

### Example HelloWorld Component

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "hello-world",
  template: `
    <h2>Hello World</h2>
    <p>This is my first component!</p>
  `,
})
export class HelloWorldComponent {
  // The code in this class drives the component's behavior.
}
```
