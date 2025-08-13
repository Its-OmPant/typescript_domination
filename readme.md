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

### Void

Void represents a valueless entity. It's mostly used as a return type of function it it returns nothing.

```typescript
function xyz(): void {
	console.log("Holla");
}
```

### null & undefined

They behaves same as in JS.

### Never

It is a special type which represents, nothing will be returned from something neither a value nor control. It is rarely used in common scenarios but used sometimes with infinite loop/ error throwing code.

### Type Inference

Type inference means the type of data is automatically inferred based on its initialization.

### Type Annotation

When we explicitly define types of data, then it's called type annotation
e.g.

```typescript
let a: number;
let b: string | null;
let c: number | string | null;
```

## Interfaces and Type aliases

### Interface:

interface is used to declare shape of an object.

-   it can have multiple values.
-   values declared with a ? at the end are optional values
    eg.
-   skipping any non-optional value will throw errors

```typescript
interface User {
	username: string;
	email: string;
	password: string;
	gender?: string;
}
```

### Extending interfaces

We can also extend the interfaces to create another interfaces
e.g.

```typescript
interface User {
	username: string;
	email: string;
	password: string;
	gender?: string;
}

interface SuperUser extends User {
	hasPriviledge: boolean;
}
```

<b>NOTE: </b> interfaces with same name gets merged and behaves as single unit.

```typescript
interface abc {
	name: string;
}

interface abc {
	age: string;
}

// this will behave like
interface abc {
	name: string;
	age: string;
}
```

### Type aliases

We can define our own types by clubbing multiple pre-defined types. e.g.

```typescript
type a = string | number | null;
type arg_value = string | boolean;
```

### Type Union

Type union is nothing but defining multiple possible type values for our data.
e.g.

```typescript
let str = string | null;
```

-   This means the str will either be a string or null;

### Type Intersection

Type Intersection helps creating a Common type from multiple types
e.g.

```typescript
type User = {
	name: string;
	age: number;
};

type SuperUser = User & {
	isPrivileged: boolean;
};

const obj: SuperUser = {
	name: "a",
	age: 12,
	isPrivileged: true,
};
```

-   This is similar to Extending interfaces
