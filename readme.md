# Typescript Domination

### Installation

```bash
    npm i -g typescript
```

-   this will install typescript compiler globally

### Executing TS file

```bash
    tsc index.ts -> index.js
```

-   Any valid js code is also valid TS code
-   If there are some errors in the TS code (which are errors for TS), it will show erros while compilation but still build the js file.
-   we can also run tsc in watch mode for automatic compilation on save.
    tsc --watch

### About tsconfig.json

Configuration File for typescript.
Can be generated via
tsc --init or npx tsx --init

## Data Types

-   Basic Types

    -   Primitives (Number, String, Boolean)
    -   Array
    -   Tuple
    -   Enum
    -   Any, Unknown, Void, Null, Undefined, Never

-   When types are not defined explicitly, TS infers types automatically from initializations;
    e.g.

```typescript
let arr = [1, 2, 3, 4]; //=> type [Number]
let arr2 = [1, 2, 3, "hello"]; //=> type [Number | String]
```

### Tuple:

A tuple in TS is a fixed size and fixed data type array. for eg-

```typescript
let arr: [string, number] = ["Hello", 23];
let arr2: [boolean, string] = [true, "hey"];
```

### Enums - Enumerations

Enums helps creating custome property value types. eg.

```typescript
enum UserRoles {
	ADMIN = "admin",
	GUEST = "guest",
	SUPER_USER = "super_user",
}

// accessing enum values
console.log(UserRoles.ADMIN);
```

### Any

Any is a default type for uninitialized variables, it represents that, a variable can have any type of value in future.

```typescript
let a; // a is of type any here
```

### Unknown

Unknown is a little more strict that any, it allows variables to have any type of data, but when doing any data specific operations then we have to define the type. this is aka Type Narrowing
ex-

```typescript
let a;
a = 12;
a = "hello"; // no ts errors

a.toUpperCase(); // error can't use it like this

// instead
if (typeof a === "string") {
	a.toUpperCase();
}
```
