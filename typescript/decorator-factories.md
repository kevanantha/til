# Decorator Factories

## What is decorators?

A Decorator is a special kind of declaration that can be attached to a `class declaration`, `method`, `accessor`, `property`, or `parameter.` Decorators use the form `@expression`, where `expression` must evaluate to a function that will be called at runtime with information about the decorated declaration.

This is an example of _Decorator Factory_

A Decorator Factory is simply a function that returns the expression that will be called by the decorator at runtime.

```typescript
function Logger(log: string) {
  return function (constructor: Function) {
    console.log({ log, constructor })
  }
}

class Car {
  name: string = 'Kurama'

  constructor() {
    console.log('Creating Car...')
  }
}
```

## Usage
Call the function `Logger` right on the top of the class

```typescript
@Logger('Class - Car)
class Car {
  name: string = 'Kurama'

  constructor() {
    console.log('Creating Car...')
  }
}
```

Result:
```typescript
Class - Car
[Function: Car]
```

---

## Refs
- [Typescript Official Docs](https://www.typescriptlang.org/docs/handbook/decorators.html)

## Tags
- #typescript