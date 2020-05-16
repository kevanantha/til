# Decorator Execution

Let say there are two decorators

```typescript
function Logger(logString: string) {
  console.log('Logger')
  return function (constructor: Function) {
    console.log('Constructor Logger')
  }
}

function withTemplate(template: string, hookId: string) {
  console.log('Template')
  return function (constructor: any) {
    console.log('Constructor Template')
  }
}
```

And Car Class

```typescript
class Car {
  name: string = 'Kurama'

  constructor() {}
}
```

And call the decorators like this, right above the Car class

```typescript
@Logger('CLASS - CAR')
@withTemplate('<h1>hello</h1>', 'app')
class Car {
  name: string = 'Kurama'

  constructor() {
    console.log('creating person...')
  }
}
```

Here's the output

```
Logger
Template
Constructor Template
Constructor Logger
```

The `decorators` runs first and then execute "content" inside of the decorators **from above to top**

---

Refs

- [Udemy Course](https://www.udemy.com/course/understanding-typescript/learn/lecture/16935720#overview)

Tags

- #typescript

