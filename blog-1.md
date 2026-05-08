# How Generics Help Build Reusable and Strictly Typed Code in TypeScript

## Introduction

TypeScript is widely used because it combines JavaScript flexibility with strong type safety. One of the most powerful features of TypeScript is **Generics**. Generics allow developers to write reusable functions, classes, and components while still maintaining strict typing.

Without generics, developers often need to write duplicate code for different data types. Generics solve this problem by allowing code to work with multiple types safely.

In this blog, we will explore how generics improve code reusability and maintain type safety in TypeScript applications.

---

# What Are Generics?

Generics are a way to create reusable code components that can work with different data types.

Instead of specifying a fixed type, we use a placeholder type such as `T`.

## Example Without Generics

```typescript
function getString(value: string): string {
  return value;
}
```

This function only works with strings.

If we want the same logic for numbers, we would need another function:

```typescript
function getNumber(value: number): number {
  return value;
}
```

This creates repetitive code.

---

# Using Generics

With generics, we can write one reusable function.

```typescript
function getValue<T>(value: T): T {
  return value;
}
```

Now the same function works with different data types.

```typescript
console.log(getValue<string>("Hello"));
console.log(getValue<number>(100));
console.log(getValue<boolean>(true));
```

---

# Benefits of Generics

## 1. Code Reusability

Generics reduce duplicate code by allowing one function or class to support multiple types.

```typescript
function createArray<T>(item: T): T[] {
  return [item];
}

console.log(createArray<number>(5));
console.log(createArray<string>("TypeScript"));
```

---

## 2. Strong Type Safety

Generics preserve type information.

```typescript
function firstElement<T>(arr: T[]): T {
  return arr[0];
}

const result = firstElement(["apple", "banana"]);
```

Here, TypeScript automatically understands that `result` is a string.

---

## 3. Better Developer Experience

Generics provide autocomplete and error checking in modern code editors.

```typescript
interface User {
  id: number;
  name: string;
}

function getProperty<T, K extends keyof T>(obj: T, key: K) {
  return obj[key];
}

const user = {
  id: 1,
  name: "John"
};

console.log(getProperty(user, "name"));
```

If we try to access a property that does not exist, TypeScript will show an error.

---

# Generics in Classes

Generics can also be used with classes.

```typescript
class DataStore<T> {
  private data: T[] = [];

  add(item: T): void {
    this.data.push(item);
  }

  getAll(): T[] {
    return this.data;
  }
}

const numberStore = new DataStore<number>();

numberStore.add(10);
numberStore.add(20);

console.log(numberStore.getAll());
```

This class can now store any type safely.

---

# Real-World Use Cases

Generics are heavily used in:

- API response handling
- React components
- Utility functions
- Database models
- Collections and data structures

They help developers build scalable and maintainable applications.

---

# Conclusion

Generics are one of the most useful features in TypeScript. They allow developers to create reusable and flexible code without losing type safety.

By using generics, developers can:
- Reduce code duplication
- Improve maintainability
- Catch errors early
- Build scalable applications

For modern TypeScript development, understanding generics is essential.