---
type: Course Note
status: in-progress
started: 2026-05-12
finished:
tags:
  - generic
  - ChaiCode
  - Backend
  - Typescrip
MOCs:
---
# Notes
- **Dependency Tree** : The relation between various dependencies. ==***Package-lock-json keeps track of this dependency tree***==. It keeps info about the exact versions of other modules that a module is dependent upon.

## Why do we need typescript?
- for type validation. without it we may have to violate the DRY principle.

## Points to keep in mind while working with Typescript
1. Ts files are never run directly its first compiled into JS 
2. Keep all your Ts files in a separate folder. Do not mix it with Js files
3. create a file called ==tsconfig.json== using command ==tsc --init==
4. ==tsconfig.json== tells about which Ts files to compile, which js version to generate,how to compile etc
```json
{

// Visit https://aka.ms/tsconfig to read more about this file

"compilerOptions": {

// File Layout
"rootDir": "./src", //Folder path where TS files are present
"outDir": "./dist", //Folder path where compiled JS files will be stored

// Environment Settings

// See also https://aka.ms/tsconfig/module
"module": "nodenext",
"target": "esnext",
"types": [],

// Other Outputs
"sourceMap": true,
"declaration": true,
"declarationMap": true,

// Stricter Typechecking Options
"noUncheckedIndexedAccess": true,
"exactOptionalPropertyTypes": true,

// Recommended Options
"strict": true,
"jsx": "react-jsx",
"verbatimModuleSyntax": true,
"isolatedModules": true,
"noUncheckedSideEffectImports": true,
"moduleDetection": "force",
"skipLibCheck": true,

}

}
```

5. devDependecy : dependencies which are only required during development and not for production. use a -D flag while installing for this. eg:- `npm i typescript -D`
6. `npm i tsx -D ` : watches for any changes in ts files no neeed to compile manually everyting
7. 
```json
"scripts": {

"dev": "tsx watch src/index.ts"

//This enables npm run dev to continuosly watch the ts file compile it and on successfull compilation run the node dist/index.js command
},
```

8. `npm i @types/<PackageName> -D` for installing any package type definations for working smoothly in ts 

## Creating a server using express

1. **Zod** :- It is a ts schema defining and validating library. It helps in runtime validation of data that comes from outside.
### 1. JavaScript Classes (The Blueprint)

Think of a class as a **blueprint** or a factory for creating things. If we are making a video game, we might want a class to create players.

JavaScript

```
class Player {
    // The constructor is the setup phase when a new player is born
    constructor(playerName) {
        this.name = playerName;
    }

    // A method (an action the player can take)
    introduce() {
        console.log("Hi, I am " + this.name);
    }
}

// We use the blueprint to create two actual, distinct players
const player1 = new Player("Mario");
const player2 = new Player("Luigi");

player1.introduce(); // Output: "Hi, I am Mario"
player2.introduce(); // Output: "Hi, I am Luigi"
```

Everything makes sense so far. `player1` called the method, so `this.name` was Mario.

---

### 2. The `this` Keyword (The Pronoun)

In JavaScript, the word `this` acts exactly like the word **"my"** or **"I"** in English.

- If **Mario** says, "I am hungry," you know who is hungry because Mario is the one speaking.
    
- If **Luigi** says, "I am hungry," the meaning of "I" changes based on who is doing the talking.
    

In JavaScript, **`this` is not tied to the function itself. It is tied to _who called the function_.** Whenever you use a dot (`player1.introduce()`), the object on the left side of the dot is the one "speaking."

---

### 3. The Trap: Losing `this`

Here is where JavaScript gets weird and where your code breaks. What happens if we rip the function away from the object?

Imagine Mario writes a sticky note that says: **"Hi, I am [my name]."** He hands that sticky note to a random bystander (let's call them a `Button`).

JavaScript

```
const mario = new Player("Mario");

// We take the function AWAY from Mario and store it in a generic variable
const stickyNote = mario.introduce; 

// Now, we ask the generic variable to run the function
stickyNote(); 
```

**What happens? You get an error.** Why? Because when `stickyNote()` runs, there is no object on the left side of a dot. JavaScript looks at the sticky note, reads "Hi, I am [my name]," and says: _"Wait, who is speaking right now? I don't know who 'my' refers to!"_

Because JavaScript doesn't know who is talking, `this` becomes `undefined`. When it tries to read `undefined.name`, your program crashes.

This is the exact problem you face when you pass a class method to a button click in the browser, or to an Express router on a server. You are handing off a sticky note, and the function loses its memory of who it belongs to.

---

### 4. The Savior: `bind()`

How do we fix the sticky note problem? We use `bind()`.

`bind()` is a built-in JavaScript tool that lets you forcefully attach an identity to a function. It's the equivalent of crossing out "my" on the sticky note and writing "Mario's".

JavaScript

```
const mario = new Player("Mario");

// We create a NEW sticky note, and permanently attach Mario to it
const fixedStickyNote = mario.introduce.bind(mario);

// Now, no matter who reads the note or how it is called, it works.
fixedStickyNote(); // Output: "Hi, I am Mario"
```

When you write `mario.introduce.bind(mario)`, you are telling JavaScript: _"Create a copy of the introduce function, and whenever you see the word `this` inside it, I want you to permanently pretend that `mario` is the one speaking."_

---

### 5. The Modern Shortcut: Arrow Functions (`=>`)

Because developers got tired of writing `.bind()` everywhere, modern JavaScript introduced Arrow Functions.

Arrow functions are special because they **do not have their own `this`**. They are "dumb" in a good way—they automatically and permanently inherit the `this` from wherever they were created.

If we change our class to use an arrow function:

JavaScript

```
class Player {
    constructor(playerName) {
        this.name = playerName;
    }

    // Look at the = and => 
    introduce = () => {
        console.log("Hi, I am " + this.name);
    }
}

const mario = new Player("Mario");

// Even if we rip it away...
const stickyNote = mario.introduce;

// It still works perfectly! No bind() needed.
stickyNote(); // Output: "Hi, I am Mario"
```

With the arrow function, Mario essentially auto-signed his name to the sticky note the