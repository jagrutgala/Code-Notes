# Angular Directives

In Angular, a **directive** is a class that adds behavior to an element by attaching a custom attribute or a custom element to it. Directives allow you to extend the HTML language, and to create reusable components.

There are two types of directives in Angular:

- `Component directives`: These are directives that are associated with a template and a component class. They are used to create reusable UI components. Component directives are created by using the `@Component decorator`.

- `Structural directives`: These are directives that change the structure of the DOM. They are used to add or remove elements from the DOM. Structural directives are created by using the `@Directive decorator`.

## In-Built Structural Directives

### ngIf

`ngIf` directive is used to conditionally add or remove an element from the DOM based on a boolean expression. When the expression is evaluated as true, the element is added to the DOM, and when it's evaluated as false, the element is removed.

**home.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-home",
  templateUrl: "./home.component.html",
  styleUrls: ["./home.component.css"],
})
export class HomeComponent {
  isVisible: boolean = true;
  toggleVisibility() {
    isVisible = !isVisible;
  }
}
```

**home.component.html**

```html
<div>
  <p *ngIf="isVisible">😎</p>
  <button (click)="toggleVisibility()">Hide/ Show</button>
</div>
```

#### else block

We can also use `ngIf` with an `else` block to specify what should be displayed when the expression is false:

**home.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-home",
  templateUrl: "./home.component.html",
  styleUrls: ["./home.component.css"],
})
export class HomeComponent {
  isVisible: boolean = true;
  toggleVisibility() {
    isVisible = !isVisible;
  }
}
```

**home.component.html**

```html
<div>
  <p *ngIf="isVisible; else isVisibleElse">😎</p>
  <button (click)="toggleVisibility()">Hide/ Show</button>
</div>

<ng-template #isVisibleElse>
  <p>😴</p>
</ng-template>
```

### ngFor

We use ngFor to present a list of items. How to use ngFor

1. Define a block of HTML that determines how Angular renders a single item.
2. To list your items, assign the shorthand let item of items to \*ngFor.

**home.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-home",
  templateUrl: "./home.component.html",
  styleUrls: ["./home.component.css"],
})
export class HomeComponent {
  itemList: string[] = ["Blaze", "Zombie", "Skeleton", "Piglin", "Gaurdian"];
}
```

**home.component.html**

```html
<ul>
  <li *ngFor="let item of itemList">{{item}}</li>
</ul>
```

### ngSwitch

`ngSwitch` directive is used to conditionally add or remove elements from the DOM based on the value of an expression. It works similarly to a JavaScript switch statement.

The `*ngSwitchCase` directive is used to define the different cases for the ngSwitch directive, and the `*ngSwitchDefault` directive is used to specify what should be displayed when the expression doesn't match any of the cases.

**home.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-home",
  templateUrl: "./home.component.html",
  styleUrls: ["./home.component.css"],
})
export class HomeComponent {
  day: number = new Date().getDay();
}
```

**home.component.html**

```html
<div [ngSwitch]="day">
  <p *ngSwitchCase="0">Sunday</p>
  <p *ngSwitchCase="1">Monday</p>
  <p *ngSwitchCase="2">Tuesday</p>
  <p *ngSwitchCase="3">Wednesday</p>
  <p *ngSwitchCase="4">Thursday</p>
  <p *ngSwitchCase="5">Friday</p>
  <p *ngSwitchCase="6">Saturday</p>
  <p *ngSwitchDefault>Holiday</p>
</div>
```

> Note
>
> `ngSwitch` directive is depreciated and replaced by `ngIf` and `ng-template` based conditions.


## Creating Custom Directive

```
$ ng generate directive <directive-name>
```
OR

```
$ ng g d <directive-name>
```

**app-highlight.directive.ts**

```typescript
import { Directive, ElementRef, Input } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
  @Input() color: string;

  constructor(private el: ElementRef) { }

  ngOnInit() {
    this.el.nativeElement.style.backgroundColor = this.color;
  }
}
```

**Next Steps**
* [Binding](Binding.md#angular-component-template-bindings)
* [Forms](Forms.md#angular-forms)
