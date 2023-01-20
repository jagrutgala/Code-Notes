# Angular Routing

## Child Routing

## Route Parameters

ActivatedRoute + subscribe

## Query Parameters

```html
<a
  [routerLink]="['/tableOf', table]"
  [queryParams]="{ key: value }"
>
  Get Table
</a>
```

```typescript
import { Component, Input } from "@angular/core";
import { ActivatedRoute } from "@angular/router";

@Component({
  selector: "app-number-table",
  templateUrl: "./number-table.component.html",
  styleUrls: ["./number-table.component.css"],
})
export class NumberTableComponent {
  @Input() tableOf: number;
  @Input() tableLimit: number;
  numArr: unknown[];

  constructor(private activatedRoute: ActivatedRoute) {}

  ngOnInit() {
    this.activatedRoute.params.subscribe((params) => {
      console.log("Route Params", params);
      try {
        this.tableOf = params["num"];
      } catch (error) {}
    });

    this.activatedRoute.queryParams.subscribe((queryParams) => {
      console.log("Query Params", queryParams);
      try {
        this.tableLimit = queryParams["limit"] || 12;
        this.numArr = createArrayOfLength(this.tableLimit);
      } catch (error) {}
    });
  }
}

function createArrayOfLength(length: number) {
  return Array.from({ length });
}
```
