# Consuming Api using Angular

## Http Client

The Angular `HttpClient` module allows you to make HTTP requests in Angular applications. It is part of the `@angular/common/http` package and can be imported into your Angular component or service.

Once imported, you can use the HttpClient to make various types of HTTP requests, such as `GET`, `POST`, `PUT`, `DELETE`, etc.

Example of Using HttpClient in a service:

**example.service.ts**

```typescript
import { HttpClient } from '@angular/common/http';

export class ExampleService {
  constructor(private http: HttpClient) {}

  getData() {
    return this.http.get('https://api.example.com/data');
  }

    sendData(data: any) {
    return this.http.post('https://api.example.com/data', data);
  }

}
```
We can then inject this service in our components to communicate with apis.
