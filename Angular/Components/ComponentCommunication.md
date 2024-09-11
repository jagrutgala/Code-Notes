# Inter Component Communication

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
