# 03. Core Object-Orientation Concepts

> 📝 _Learning log — notes we build together, lecture by lecture._

---

## Lecture 1 — A Brief History of Programming

**The big theme:** Every major shift in how we program happened because the
previous way couldn't handle how complex programs were becoming. The recurring
villain is **complexity**.

```
  Unstructured     →     Structured     →     Object-Oriented
  Programming            Programming          Programming
  (the beginning)        (late 1950s)        (1980s)
```

Three eras, one trajectory: toward modeling the real world.

### Era 1 — Unstructured Programming (the beginning)

- The earliest programming paradigm.
- Programs were **big, contiguous chunks of code** — sequentially ordered
  instructions, one statement per line, lines numbered or identified by a label.
- Execution just went top to bottom, line by line. (Example: Sinclair BASIC
  converting Fahrenheit → Celsius.)
- **The fatal flaw:** as problems grew in complexity, maintaining or even
  understanding such a codebase became challenging. Any change meant checking
  statements **line by line**, which got harder as the number of lines grew.
- This style earned the nickname **"spaghetti code"** 🍝 — a pejorative term for
  software that is complicated, difficult to understand, and impossible to
  maintain. Everything tangled into everything; change one thing, break ten.

### Era 2 — Structured Programming (late 1950s)

- Emerged as the answer to spaghetti code. **Core move: break the code down into
  logical steps.**
- Introduced **subroutines** (named blocks of code that carry out a set of
  instructions). Example in C (a procedural language): `main()` is the entry
  point, which calls `sum()` to add two numbers; you can define more functions
  (e.g., to average two numbers). Naming a chunk of logic was a huge leap for
  readability.
- **Variable** — a value of a given type identified by a name; we use the name
  to access (read/modify) the stored value at runtime.
- **Data structure** — a way of organizing and storing data (e.g., a structure
  aggregating the info needed to represent an employee).
- A **significant improvement**: named functions improved readability,
  development times dropped, quality improved.
- **But:** as programs got bigger, developers faced new challenges — structured
  programming **could not address all the increased complexity.** Complexity won
  again.

### The philosophical hinge between eras

> *"While structured programming relies on **actions**, object-oriented
> programming is organized around **objects**."*

- **Structured programming** thinks in **verbs / actions**: *"What do I need to
  DO? Let me write functions for those actions."*
- **Object-oriented programming** thinks in **nouns / things**: *"What THINGS
  exist in my system? Let me model those as objects."*

That single shift — from **actions** to **things** — is the soul of object
orientation.

### Era 3 — Object-Oriented Programming (1980s)

- The next big step in the evolution of programming paradigms; OO languages
  appeared in the 80s.
- **Main idea:** split the program apart into **self-contained objects**.
- Each object represents a part of the system mapped to a distinct entity;
  basically functions as **a separate program by itself** — it operates on its
  own data and has a specific role.
- The objects that form the system **interact with each other**.
- **The destination:** *"Object-orientation aims to bring the world of
  programming closer to the real world."* We model software the way our brains
  already model reality — as things (dogs, cars, phones) that have properties
  and do things.

```
   Real world              Object-oriented program
   ─────────               ───────────────────────
   a dog          →        a Dog object (color, breed… that barks)
   a car          →        a Car object (speed, fuel… that drives)
   a phone        →        a Phone object (battery, screen… that calls)
```

### The whole lecture in one picture

```
  COMPLEXITY keeps growing
        │
        ▼
  ┌──────────────┐  breaks down  ┌──────────────┐  breaks down  ┌──────────────────┐
  │ UNSTRUCTURED │ ────────────▶ │  STRUCTURED  │ ────────────▶ │ OBJECT-ORIENTED  │
  │ one big pile │              │ named funcs  │              │ self-contained   │
  │ of line-by-  │              │ + variables  │              │ objects that     │
  │ line code    │              │ + data       │              │ interact; models │
  │ spaghetti 🍝 │              │ structures   │              │ the real world   │
  │              │              │ thinks in    │              │ thinks in        │
  │              │              │ ACTIONS      │              │ THINGS           │
  └──────────────┘              └──────────────┘              └──────────────────┘
```

**Three eras. One villain (complexity). One trajectory (toward modeling the
real world).**

---

_Notes for lectures 2–7 will be added as we progress._
