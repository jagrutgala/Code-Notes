# Angular Forms

In angular there are 3 ways to make forms and apply validation.

- Template Driven
- Reactive Forms
- Forms Array

## Template Driven Forms

Template driven forms requires Forms Module from @angular/forms.

```typescript
import { FormsModule } from "@angular/forms";
```

1. use # to declare a ng-variable i.e. local variables.
2. use ngForm to expose form to angular.

```html
<form #myForm="ngForm">...form inputs</form>
```

3. bind inputs in this form using ngModel directive and name attribute.

```html
<input ngModel name="myInput" type="text" />
```

To group certain inputs in form object. Use ngModelGroup directive.

```html
<div ngModelGroup="address">
  <input ngModel name="flatno" type="text" />
  <input ngModel name="street" type="text" />
  <input ngModel name="city" type="text" />
  <input ngModel name="pincode" type="number" />
</div>
```

4. Validation

- Use Html validation attributes.
- Use exposed control models to validate

Different Controller validation attributes available in angular -

- required: cannot be blank
- pattern: must match a regex pattern
- min: must be greater than or equal to
- max: must be less than or equal to
- minlength: minimum number of characters
- maxlength: maximum number of characters

### Example

**form.ts**

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "template-form",
  templateUrl: "./template-form.component.html",
})
export class HomeComponent {
  firstname: string = "Bob";

  mySubmit(form: FormGroup) {
    // validation & submit code
  }
}
```

**template-form.component.html**

```html
<form #myForm="ngForm">
  <input
    ngModel
    name="firstName"
    [ngModel]="firstName"
    type="text"
    pattern="^([A-Z][a-z ])+[^ ]$"
    required
  />
  <button type="submit" (click)="mySubmit(myForm)">Submit</button>
</form>
```

## Reactive Forms

## Forms Array

## Dynamic Form Styling

use ngClass directive
