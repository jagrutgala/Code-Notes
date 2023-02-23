# Dependency Injection in Angular

Angular has 2 types of injectors

1. Element Injector
1. Module Injector

## Angular Dependency Injector Cycle


```
Null Injector
    /\
    ||
Platform Injector
    /\
    ||
Root Module Injector
    /\      /\
    ||      ||
(Lazy Child Module Injectors)
```




