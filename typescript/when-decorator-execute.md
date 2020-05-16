# When Decorator Execute

Just wonder when decorator excute because let say there is a class `Product` and add `decorator` in the property

The decorator can runs without instantiate the class

```typescript
function Log(property: any, target: string) {
  console.log('property decorator')
  console.log({ property, target })
}

function Log2(target: any, name: string, descriptor: PropertyDescriptor) {
  console.log('accessor decorator')
  console.log({ target, name, descriptor })
}

function Log3(target: any, name: string, descriptor: PropertyDescriptor) {
  console.log('method decorator')
  console.log({ target, name, descriptor })
}

function Log4(target: any, name: string, position: number) {
  console.log('parameter decorator')
  console.log({ target, name, position })
}

class Product {
  @Log
  title: string
  private _price: number

  @Log2
  set price(value: number) {
    if (value > 0) {
      this._price = value
    } else {
      throw new Error('Value must be positive!')
    }
  }

  constructor(title: string, price: number) {
    this.title = title
    this._price = price
  }

  @Log3
  getTaxWithTax(@Log4 tax: number) {
    return this._price * (1 + tax)
  }
}
```

## Conclusion

Decorator runs when we defined the class, not at runtime

## Refs

- [Udemy Course](https://www.udemy.com/course/understanding-typescript/learn/lecture/16935726#overview)

## Tags

- #typescript
