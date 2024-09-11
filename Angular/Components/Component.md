# Angular Components

Components are the building blocks of angular application. In Angular component consists of class with `@Component` decorator. @Component decorator provides angular with metadata to anuglar about the component.

A component is made out of 3 things:
- [Template]()
- [Styles]()
- [Behaviour]()

## Generating Components using CLI

```bash
$ ng generate component <component-name>
```

## @Component Decorator
`@Component` decorator specifies the the following:

- `selector`: The CSS selector that identifies this directive in a template and triggers instantiation of the directive.

- `template`/ `templateUrl`: An inline HTML template for an Angular component. Or path to the HTML file that contains the template for an Angular component.

- `styles`/ `styleUrls` _(optional)_: One or more inline CSS stylesheets to use in this component. Or path to the CSS files that contain styles to use in this component.

- `standalone` _(optional)_: When true allows the components to directly import other components, directives, and pipes used in their templates.


## Example HelloWorld Component

**hello-world-msg.component.ts**
```typescript
import { Component } from "@angular/core";

@Component({
  selector: "hello-world-msg",
  template: `
    <h1>Hello World!</h1>
  `,
})
export class HelloWorldMsgComponent {
  // The code in this class drives the component's behavior.
}
```

**hello-world.component.ts**
```typescript
import { Component } from "@angular/core";

@Component({
  selector: "hello-world",
  template: `
    <hello-world-msg></hello-world-msg>
  `,
})
export class HelloWorldComponent {
  // The code in this class drives the component's behavior.
}
```


## Life Cycle Hooks

- `constructor`: Runs once when creating the component.
- `ngOninit`: Runs once when initailizing the component.
- `ngOnChanges`: Runs multiple times when inputs of the compnent change.
- `ngDoCheck`: 
- `ngAfterViewInit`: Runs once after the view template is initialized.
- `ngAfterViewChecked`: 
- `ngAfterContentInit`: Runs once after the projected content is initialized.
- `ngAfterContentChecked`: 
- `ngOnDestroy`: Runs once before destroying the component.


# Next Steps
[<-- Angular](./Angular.md#angular) | [Modules -->](./Modules.md#angular-modules)

# Also See
- [View Template](./ViewTemplate.md#component-view-template)
- [Component Communication](./ComponentCommunication.md#inter-component-communication)
- [Styling](./Styling.md#component-styling)
