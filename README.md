# TypeScript Interview Essentials: `keyof`, Union, and Intersection Types Explained

TypeScript is a powerful superset of JavaScript that introduces static typing. In this blog, we’ll cover two commonly asked interview topics:
1. The `keyof` keyword in TypeScript.
2. Union and intersection types.

These features are simple to understand but incredibly powerful in writing safe, scalable, and readable TypeScript code.

---

##  1. What is the use of the `keyof` keyword in TypeScript?

###  Explanation:

The `keyof` keyword is used to get a **union of the keys of an object type**. It’s especially helpful when working with generic functions, ensuring that keys you access or manipulate actually exist on the object.

###  Example:

```ts
type Person = {
  name: string;
  age: number;
};

type PersonKeys = keyof Person;
// PersonKeys is now: "name" | "age"

function getValue(obj: Person, key: keyof Person) {
  return obj[key];
}

const person: Person = { name: "Alice", age: 30 };

console.log(getValue(person, "name")); // Output: Alice
```

### 2. Example of **union** and **intersection** types in TypeScript

TypeScript gives us two powerful ways to combine multiple types:

- **Union type (`|`)** means a value can be one of several types.

- **Intersection type (`&`)** means a value has all properties from multiple types.

Let’s break this down with examples.

#### Union Type Example:
```ts
type Status = "success" | "error" | "loading";

function showStatus(status: Status) {
  console.log("Status is:", status);
}

showStatus("success"); // Output: Status is: success
```

In this example, the function only accepts one of the three string values: "success", "error", or "loading". This is a union type—it can be any of the defined values.

#### Intersection Type Example:
```ts
type Name = { name: string };
type Age = { age: number };

type Person = Name & Age;

const person: Person = {
  name: "Masud",
  age: 25
};
```

Here, we created a new type called **Person** that combines **Name** and **Age**. The object **person** must have both **name** and **age**. This is an intersection type—it must satisfy both.

#### When to use what?
- Use **union types** when a value can be one of several types.
- Use **intersection types** when you want to combine multiple types into one.

---



