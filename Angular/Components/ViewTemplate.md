# Component View Template

<!-- What is a Template in Angular -->


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


## @ViewChildren