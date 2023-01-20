# Angular Component Styling

In Angular, there are several ways to style our components and application.

Component styles: We can define styles specific to a component by using the styles property of the `@Component decorator`. These styles will only be applied to the template of the component they are defined in.

**example-style.component.ts**

```typescript
@Component({
  selector: 'app-example',
  template: `<p>This is an example component.</p>`,
  styles: [`
    p {
      color: red;
    }
  `]
})
```

External stylesheets: We can also include external stylesheets by using the styleUrls property of the `@Component decorator` to reference a CSS file.

**example-external-style.component.ts**

```typescript
@Component({
  selector: 'app-example',
  template: `<p>This is an example component.</p>`,
  styleUrls: ['./example.component.css']
})

```

## ngStyle

The ngStyle directive allows you to add and remove inline styles based on the state of a component. You can bind the directive to a component property and use it to toggle a style based on the value of the property.

**reactive-style.component.ts**

```typescript
@Component({
  selector: "app-example",
  template: `<input
    [ngStyle]="{ color: val.value }"
    [(ngModel)]="myColor"
    #val="ngModel"
    type="text"
  />`,
})
export class ReactiveStyleComponent {
  myColor!: string;
}
```

## ngClass

The ngClass directive allows you to add and remove CSS classes based on the state of a component. You can bind the directive to a component property and use it to toggle a class based on the value of the property.

**reactive-class.component.ts**

```typescript
@Component({
  selector: "app-example",
  template: `<input
    [ngClass]="{ 'input-error': val.invalid }"
    [(ngModel)]="myColor"
    #val="ngModel"
    type="text"
  />`,
  styles: [
    `
      .input-error {
        color: red;
      }
    `,'
  ],
})
export class ReactiveStyleComponent {}
```
