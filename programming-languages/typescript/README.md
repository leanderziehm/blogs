# Typescript

[https://www.w3schools.com/typescript/index.php](https://www.w3schools.com/typescript/index.php)

[https://www.w3schools.com/typescript/typescript\_simple\_types.php](https://www.w3schools.com/typescript/typescript_simple_types.php)

## Types:

string, number, boolean



## Boolean

```
let isActive: boolean = true;
let hasPermission = false; // TypeScript infers 'boolean' type
```

## Number

```
let decimal: number = 6;
let float: number = 3.14;      // Floating point
let hex: number = 0xf00d;       // Hexadecimal
let binary: number = 0b1010;     // Binary

```

## String

```
let color: string = "blue";
let fullName: string = 'John Doe';
let age: number = 30;
let sentence: string = `Hello, my name is ${fullName} and I'll be ${age + 1} next year.`;
```



## Bigint (ES2020+)

```
const hugeNumber = BigInt(9007199254740991);
```



## Symbol

```
const uniqueKey: symbol = Symbol('description');
const obj = {
  [uniqueKey]: 'This is a unique property'
};
console.log(obj[uniqueKey]); // "This is a unique property"
```



## Special Types

unknown, never, undefined, null

* `undefined` means a variable has been declared but not assigned a value
* `null` is an explicit assignment that represents no value or no object





## Arrays

```typescript
// Array of numbers
scores: number[] = [100, 95, 98];

const names: string[] = [];

const names: readonly string[] = ["Dylan"];
```

## Tuple

```typescript
const ourReadonlyTuple: readonly [number, boolean, string] = [5, true, 'The Real Coding God'];
```

## Named Tuple

```
const graph1: [x: number, y: number] = [55.2, 41.3];
const graph2: [number, number] = [55.2, 41.3];
const [x, y] = graph2;
```



## Object Types

[https://www.w3schools.com/typescript/typescript\_object\_types.php](https://www.w3schools.com/typescript/typescript_object_types.php)



## Type Alias and Interface

[https://www.w3schools.com/typescript/typescript\_aliases\_and\_interfaces.php](https://www.w3schools.com/typescript/typescript_aliases_and_interfaces.php)



## Union Types

```
let a: string|number = "jo" ;
```



## Functions

```
function greet(name: string): string {
return `Hello, ${name}!`;
}

function printHello(): void {
  console.log('Hello!');
}

// the `?` operator here marks parameter `c` as optional
function add(a: number, b: number, c?: number) {
  return a + b + (c || 0);
}

function pow(value: number, exponent: number = 10) {
  return value ** exponent;
}

function divide({ dividend, divisor }: { dividend: number, divisor: number }) {
  return dividend / divisor;
}

function add(a: number, b: number, ...rest: number[]) {
  return a + b + rest.reduce((p, c) => p + c, 0);
}


type Negate = (value: number) => number;

// in this function, the parameter `value` automatically gets assigned the type `number` from the type `Negate`
const negateFunction: Negate = (value) => value * -1;
```



## Casting&#x20;



as&#x20;

<>



force cast:

```
let x = 'hello';
console.log(((x as unknown) as number).length); // x is not actually a number so this will return undefined
```

## Class

pulic private

```
class Person {
  // name is a private member variable
  public constructor(private name: string) {}

  public getName(): string {
    return this.name;
  }
}

const person = new Person("Jane");
console.log(person.getName());



// Abstract classes
abstract class Polygon {
  public abstract getArea(): number;

  public toString(): string {
    return `Polygon[area=${this.getArea()}]`;
  }
}

class Rectangle extends Polygon {
  public constructor(protected readonly width: number, protected readonly height: number) {
    super();
  }

  public getArea(): number {
    return this.width * this.height;
  }
}
```

## Generics

```
function createPair<S, T>(v1: S, v2: T): [S, T] {
  return [v1, v2];
}
console.log(createPair<string, number>('hello', 42)); // ['hello', 42]
```



## Utility Types

[https://www.w3schools.com/typescript/typescript\_utility\_types.php](https://www.w3schools.com/typescript/typescript_utility_types.php)



