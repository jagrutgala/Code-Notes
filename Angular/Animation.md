# Angular Animation

To animate a DOM Element we have two ways to do it.

- using CSS.
- using Javascript (`Web Animations Api`)

In Angular, we have `@angular/animations` package which is an abstraction over the Web Animations Api.

Animation is a transition from one state to another. In angular we have 3 types of state:

- `void`: represents state of element that is not part of the DOM. For Example when we add a element to the DOM it transitions from `void => *`, and similarly when a element is removed from the DOM it transitions from `* => void`

- `default (*)`: all elements have a default state.
- `custom`: user created state. For Example if we have a `Accordion`, it is always visible in the DOM but it's state can change from `collapsed` to `expanded` and visa versa. Then collapsed and expanded are the two custom states that we will have to work with.

## Installing Angular Animations

```
$ ng add @angular/animations
```

Web Animations api is not supported in older browser versions. So we need to install polyfills for that. Then add them in `angular.json` config under `polyfills`

```
$ npm i -S web-animations-js
```

## Animation Module

Example of Angular component with fadeIn Animation

**item.component.ts**

```typescript
@Component({
  animations: [
    trigger('fadeIn', [
      state(...),
      transition(...)
    ])
  ],
})
export class ItemComponent {}
```

**item.component.html**

```html
<div @fadeIn>I am Animated</div>
```

We can use `@<triggerName>` to attach any trigger to a DOM element.

## Important Functions to Create Animations

**trigger**

**animate**

**style**

**state**

## Creating Reusable Animations

Separating animations into separate module.
