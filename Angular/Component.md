# Angular Components

Components are the building blocks of angular application. In Angular component consists of class with @Component decorator. `@Component` decorator provides angular with metadata about the component.

## Generating Components using CLI

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

## Example HelloWorld Component

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

## Inter Component Communication

By default all properties of components are only accessible inside those components only. To share data between parent and child components we use `@Input` and `@Output` decorators.

`@Input()` -> allows a parent component update data in the child component. We can think of **@Input() as props** passing to the child component.

```typescript
// Syntax:
@Input('alias') property : <type>

// Example
@Input() product: Product;
```

`@Output()` decorator in a child component or directive allows data flow from the child to the parent component.

**child.component.ts**

```typescript
import { Output, EventEmitter } from '@angular/core';

// Syntax:
@Output() newItemEvent = new EventEmitter<string>();

// Example
export class ItemOutputComponent {

  @Output() newItemEvent = new EventEmitter<string>();

  addNewItem(value: string) {
    this.newItemEvent.emit(value);
  }
}

```

**child.component.html**

```html
<label for="item-input">Add an item:</label>
<input type="text" id="item-input" #newItem />
<button type="button" (click)="addNewItem(newItem.value)">
  Add to parent's list
</button>
```

**parent.component.ts**

```typescript

addItem() {
  ... // some code
}

```

**parent.component.html**

```html
<app-item-output (newItemEvent)="addItem($event)"></app-item-output>
```

## Local References

`#localRef` allows us to select an input element or create a reference to an html element. We can access this local reference throughout out template file. To pass some values of data related to referenced element we pass it inside the methods which are accessible in .ts file

> Note
>
> local references are not accessible in our ts file

`@ViewChild` is an angular element of type `ElementRef` allows you to access the local reference created in your html template. By using `@ViewChild` you don’t need to pass values or data inside method calls to make it accessible into the TS file. To use ViewChild we need to import it from angular/core.

```typescript
import {ViewChild} from angular/core

@ViewChild('localRefInput') nameInput : ElementRef
Console.log(this.nameInput.nativeElement.value);
```

> Important
>
> Do not use `@ViewChild` to modify the dom elements.


## @ViewChild


## Life Cycle Hooks


**Next Steps**
* [Binding](Binding.md#angular-component-template-bindings)
* [Directives](Directives.md#angular-directives)
