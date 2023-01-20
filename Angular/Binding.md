# Angular Component-Template Bindings

## Interpolation

It allows us to include a expression as a part of literal string, in the html template.

Syntax for interpolation is `{{expression}}`

**home.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-home",
  templateUrl: "./home.component.html",
  styleUrls: ["./home.component.css"],
})
export class HomeComponent {
  title: string = "Home Page";
}
```

**home.component.html**

```html
<h1>{{title}}</h1>
```

## Property Binding

It allows us to bind a html element property with a property in the component.

Syntax for property is `[property-target]="property-source"`

**home.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-home",
  templateUrl: "./home.component.html",
  styleUrls: ["./home.component.css"],
})
export class HomeComponent {
  imagePath: string = "https://picsum.photos/300/200";
}
```

**home.component.html**

```html
<img [src]="imagePath" />
```

## Event Binding

It allows us to bind a html events with a method in the component.

Syntax for property is `(event-name)="method-name()"`

**home.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-home",
  templateUrl: "./home.component.html",
  styleUrls: ["./home.component.css"],
})
export class HomeComponent {
  showAlert() {
    alert("Yaaaa!");
  }
}
```

**home.component.html**

```html
<button (click)="showAlert()">Poof</button>
```

> Note
>
> To Pass the event object to the function we can use `$event`.
> `<button (click)="PoofElement($event)">Poof</button>`

## Two way binding

It allows us to bind a property both ways from component to template and visa versa.

Syntax for two way binding is `[(input-property)]="component-property"`


> Note
>
> Two way binding is also known as Banana-Box Binding


**app.module.ts**
```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from '@angular/forms';

import { AppComponent } from './app.component';
import { HomeComponent } from './components/home/home.component';

@NgModule({
  declarations: [AppComponent, HomeComponent],
  imports: [BrowserModule, FormsModule],
  providers: [],
  bootstrap: [AppComponent],
})
export class AppModule {}
```

**home.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-home",
  templateUrl: "./home.component.html",
  styleUrls: ["./home.component.css"],
})
export class HomeComponent {
  name: string = "";
}
```

**home.component.html**

```html
<input type="text" name="name" [(ngModel)]="name">
<p>{{name}}</p>
```

> Important
>
> We imported FormsModule in app.module.ts so we can use ngModel in the component template


**Next Steps**
* [Directive](Directives.md#angular-directives)
* [Forms](Forms.md#angular-forms)
