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

## Lecture 2 — Objects

**The simplest definition:** an object is a **THING**. Just like in real life,
objects can be simple or complex — a golf ball is an object, but so is a Falcon
Heavy rocket. OO doesn't invent a weird abstract concept; it borrows how our
brains already work: we think in terms of things every day.

- The way we define an object depends on the **level of detail** we need.
- **Objects can contain or refer to other objects.** (Falcon Heavy contains a
  Tesla Roadster, which contains Star Man. Objects nest inside each other — a
  seed for "composition" later in the course.)

### The three parts of an object ⭐

Every object is described using three things:

```
   ┌─────────────────────────────────────────┐
   │                 OBJECT                   │
   │   1. IDENTITY   ── "which one is this?"  │
   │   2. STATE      ── "what is it like?"    │
   │   3. BEHAVIOR   ── "what can it do?"     │
   └─────────────────────────────────────────┘
```

#### 1. Identity — "which one is this?"
Each object has its **own private identity** — a distinct, individual thing,
not a category but _one specific instance_.

> *"If we hit a golf ball, it won't affect all the other balls. Their state is
> independent. Each has its private identity."*

A bucket of 100 identical golf balls = 100 separate objects, each with its own
identity. Hit ball #47, and ball #12 doesn't move. **Identity = "this is a
distinct, individual thing, separate from all others."**

#### 2. State — "what is it like?"
State is described by **properties** (a.k.a. **attributes**) — the
characteristics of the object. Golf ball example: color (white/colored/glow),
weight, price, position, speed, acceleration.

**Crucial sub-point:** some properties change over time, some don't.

```
   Golf ball object
   ├── color:        white        ← stays the same
   ├── weight:       45.9g        ← stays the same
   ├── price:        $3           ← stays the same
   ├── position:     (120, 45)    ← CHANGES as it flies
   ├── speed:        0 m/s        ← CHANGES when hit
   └── acceleration: 0            ← CHANGES
```

**State = the collection of all an object's properties AND their current
values.** Two golf balls can share the same _properties_ but have different
_states_ (one sitting still, one flying at 50 m/s). Each object has its **own**
state, independent of every other object.

#### 3. Behavior — "what can it do?"
Behavior is **what the object can do** — its actions, the things it's capable of.

**The sentence trick** (reusable for object-oriented analysis later):

> **"The black dog barks."**

| Part of speech | Word | What it tells us |
|---|---|---|
| **Noun** | dog | the **object** itself |
| **Adjective** | black | a **property** (part of state) |
| **Verb** | barks | the **behavior** (what it can do) |

To find objects in a problem: look at the **nouns** (objects), **adjectives**
(properties), and **verbs** (behaviors).

### One complete object (golf ball)

```
   ┌──────────────────────────────────────────┐
   │           GOLF BALL  (object)            │
   │  IDENTITY:  this specific ball, separate │
   │             from all other balls         │
   │  STATE:     color=white, weight=45.9g,   │
   │             price=$3, position=(120,45), │
   │             speed=50m/s, accel=9.8m/s²   │
   │  BEHAVIOR:  roll(), bounce(), fly()      │
   └──────────────────────────────────────────┘
```

### The bridge to Lecture 3

> *"How can we make this work in our code? For that, we need to introduce a new
> concept: **the class**."*

Intuition: a **cookie cutter** 🍪 = the **class** (the blueprint/definition).
Each **cookie** pressed from it = an **object** (an individual instance). Same
shape, but each cookie is its own thing with its own state. An object is the
_thing_; a class is the _recipe for making the thing_.

---

## Lecture 3 — The Class

**One-sentence definition:** a class is the **blueprint of an object** — a plan,
a description of what an object will be. A class is **not** an object; it's the
**template** that *produces* objects.

```
   CLASS (blueprint)          OBJECTS (instances)
   the cookie cutter    →     the actual cookies
   the blueprint        →     the actual building
   the recipe           →     the actual cake
   the Pokémon class    →     Pikachu, Charmander, Squirtle...
```

### How a class is built (Pokémon example 🎮)

Building an OO system starts by **identifying the potential objects, their
attributes and responsibilities** — connecting straight back to Lecture 2's
identity / state / behavior.

```
   ┌─────────────────────────────────────────────┐
   │              CLASS: Pokémon                  │
   │  PROPERTIES (attributes): name, armor level, │
   │                           hit points          │
   │  METHODS (behaviors):     attack(), defend() │
   └─────────────────────────────────────────────┘
```

#### 1. Properties (attributes) — the STATE
The class declares **what properties exist** but does **NOT** say what the
values are. *"The class tells us that each object has a name, armor level and
hit points. It doesn't say what the name or the armor level is."*

| | Class | Object |
|---|---|---|
| Properties | Declares that `name` exists | `name = "Pikachu"` |
| **Has values?** | **NO — just the definition** | **YES — concrete values** |

The class is a blank form with empty fields; the object is the form **filled in**.

#### 2. Methods (behaviors) — the ACTIONS
> *"We call these actions **methods**. Methods are blocks of code that can be
> called to execute certain operations."*

**Method** = the OO word for what structured programming called a **function**.
Methods are basically **functions embedded in a class** — a bridge back to
Lecture 1's structured programming era, where functions floated loose; in OO
they live inside a class as its behaviors. Methods can take **input parameters**
and **return values**.

### From class to object: creating instances

Two separate sources for what an object ends up with:

- The **class** provides the **methods** (behaviors) — every Pokémon can attack
  and defend.
- **You** provide the **values** for the properties when you create each object
  — this one is named "Pikachu" with armor 5 and 100 HP.

```
   CLASS: Pokémon  (ONE blueprint)
        ├──▶  Object 1:  name="Pikachu",    armor=5,  hitPoints=100
        ├──▶  Object 2:  name="Charmander", armor=3,  hitPoints=80
        ├──▶  Object 3:  name="Squirtle",   armor=7,  hitPoints=120
        └──▶  Object 4:  name="Bulbasaur",  armor=6,  hitPoints=110
```

Four objects, **one class**, zero duplicated code. Each object has its own
identity and its own state, but they all share the same behaviors defined once
in the class.

### The big extra benefit: reuse 📦
Classes can be packaged into **libraries or frameworks** and reused across
programs — we don't have to **reinvent the wheel**. All modern OO languages
ship built-in frameworks/libraries (buttons, lists, networking, file handling)
as pre-made classes. Realistic catch: premade classes rarely cover all needs, so
in practice we **both** use library classes **and** create our own.

### Tying Lectures 2 & 3 together

```
   CLASS                          OBJECT(S)
   the blueprint           ──▶    the actual instances
   (no values, just the    ──▶    (concrete values filled in
    shape)                         at creation)

   ┌─────────────┐    create      ┌─────────────┐
   │  Class: Dog │    instance    │  myDog      │
   │  - name     │  ──────────▶   │ name="Rex"  │  ◀── values you provide
   │  - color    │                │ color="blk" │
   │  bark()     │                │ can bark()  │  ◀── behavior from the class
   │  fetch()    │                │ can fetch() │
   └─────────────┘                └─────────────┘
```

**Three things to never confuse again:**
1. **Class** = the blueprint/definition (no values, just the shape). One per type.
2. **Object** = an actual instance (concrete values). Many per type.
3. **Instantiation** = the act of creating an object from a class (filling in
   the values). _(A class is a *mold*; an object is what you pour *into* the mold
   and pop out.)_

### The bridge forward

Next up: the **core object-orientation principles** — the **four pillars** ⭐:
1. Abstraction (L4) · 2. Encapsulation (L5) · 3. Inheritance (L6) · 4. Polymorphism (L7).
We now have the vocabulary (objects, classes, properties, methods) to tackle
them. The pillars are *how we use those things well*.

---

_Notes for lectures 4–7 will be added as we progress._
