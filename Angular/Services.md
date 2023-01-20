# Angular Services

In Angular, a `service` is a class that has `@Injectable decorator` and implements a specific functionality, which is provided to the application via dependency injection.

Services are typically used for tasks such as retrieving data from a server, performing business logic, or sharing data across different components.

**data.service.ts**

```typescript
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';

@Injectable({
  providedIn: 'root'
})
export class DataService {

  constructor(private http: HttpClient) { }

  getData() {
    return this.http.get('https://api.example.com/data');
  }
}
```

## Creating Service using Ng-CLI

```
$ ng generate service my-service
```
OR
```
$ ng g s my-service
```

To create a service in a specific module we can use `--module=<module-name>` flag.

```
$ ng g s my-service --module=app
```

> Note
>
> It's important to note that the generated service is not automatically added to the providers of any module, you need to import it manually in the desired module and add it to the providers array.

