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

## Lecture 4 — Abstraction ⭐ (Pillar 1)

**One-sentence definition:** abstraction is a way of describing complex problems
in simple terms by **ignoring some details**. Eliminating the minutiae helps us
**focus on the bigger picture**. We can dig deeper once we have a broader
understanding.

Abstraction isn't being vague or lazy — it's a deliberate strategy for fighting
complexity: get the big picture first, drill into details only when needed.

### You're already an abstraction master 🧠
> *"If I say **cat**, you know instantly what I'm talking about. I don't need to
> say male, Persian, kitten or big/small. You understand I was talking about a
> cat."*

We don't freeze on every microscopic detail — we think in **categories and
concepts** (cat, house, car). Our brains are wired to understand abstract ideas.
Abstraction is literally how human cognition works: collapse a huge amount of
detail into one simple, usable idea.

```
   Reality (infinite detail)              Abstraction (what we think)
   a 3-yr-old female Persian cat,          "a cat" 🐱
   orange fur, green eyes, 4.2kg...
        ↓ throw away the minutiae ↓
        keep only the essential concept: "cat"
```

### How abstraction works in OO
> *"When we start defining a class, we **focus on the essential qualities** and
> **discard unimportant ones**."*

A class is the blueprint (Lecture 3). Designing a class means deciding **what
goes in and what gets left out** — that decision *is* abstraction.

Pokémon example: we kept name, armor, hit points, attack(), defend(). We ignored
age, weight, height. The magic phrase: **"unessential in our current
application."** Abstraction is **context-dependent** — what's "essential" vs
"irrelevant" depends on what you're building.

```
   Same real Pokémon → abstracted for a BATTLE GAME:
     keep name, armor, hitPoints, attack(), defend()
     IGNORE age/weight/height — who cares in battle?

   Same real Pokémon → abstracted for a BREEDING SIMULATOR:
     keep species, gender, age, parents, breedWith()
     IGNORE armor/hitPoints — who cares when breeding?
```

Same creature, two completely different classes — because abstraction keeps
only what matters for the job at hand.

> Instructor's summary: *"We **focus on what's important** and **ignore all the
> details we don't need**."*

### Why abstraction is Pillar 1
It's the one you exercise *first* every time you design anything:

1. **Abstraction** — decide what to include / ignore (design the class's contents)
2. **Encapsulation** — bundle & protect what you included (Pillar 2)
3. **Inheritance** — reuse classes via parent/child (Pillar 3)
4. **Polymorphism** — treat different objects through a common interface (Pillar 4)

Every class is an abstraction. Every UML diagram is an abstraction. When you
draw a class diagram and decide "I'll show these 4 properties and 2 methods, but
not those 10 other things" — that's abstraction in action.

### Abstraction vs. Encapsulation — don't confuse them! 🚨

| | Abstraction | Encapsulation |
|---|---|---|
| **What it does** | Decides **what** to include / ignore | Decides **how to protect & bundle** what you included |
| **Question it answers** | *"Which details matter for this app?"* | *"Who's allowed to touch these details?"* |
| **When** | At **design** time, choosing contents | At **implementation** time, hiding internals |
| **Analogy** | Choosing what to put on the menu | Putting the kitchen behind a wall so diners only see the menu |

> **Abstraction** is about *relevance* — what matters. **Encapsulation** is about
> *protection* — what's hidden.

### Two extra examples that cement it

**1. A map 🗺️** — abstraction in physical form. The same patch of Earth becomes
a road map (keep roads, drop elevation), a topographic map (keep elevation, drop
street names), or a political map (keep borders, drop roads). Same reality,
three different maps — each kept only what mattered for its job. A map that
showed everything would be the size of the Earth itself: useless. **Being
incomplete is what makes a map — and a class — useful.**

**2. A `Student` — same person, three different classes 👩‍🎓.** Maya gets
abstracted differently depending on the system:
- **Grading system:** keeps studentId, name, courses, grades, gpa — ignores dorm,
  meal plan, blood type.
- **Housing/dorm system:** keeps studentId, dormRoom, roommate, mealPlan —
  ignores GPA, courses, blood type.
- **Health clinic:** keeps studentId, bloodType, allergies, vaccinations —
  ignores GPA, dorm, meal plan.

Same person, three classes. None is "the real Student" — each is an abstraction
sculpted for a purpose. Smart question to ask of any class: *"What was
deliberately left out, and why?"*

### The pattern underneath all abstraction

```
   REALITY (infinite, messy)
        │  "What is this FOR?"
        ▼
   PURPOSE decides what's ESSENTIAL vs IRRELEVANT
        │
        ▼
   ABSTRACTION (keep the essential, drop the rest)
```

The single question that drives all abstraction: **"What is this for?"** Answer
that, and you instantly know what to keep and what to ignore.

---

## Lecture 5 — Encapsulation & Data Hiding ⭐ (Pillar 2)

**One-sentence definition:** encapsulation means **packing together our
properties and methods in a class, AND hiding the inner workings** so the
outside world only sees what it needs to.

Two parts — most people only remember the second. Encapsulation is **both** the
bundling **and** the hiding.

### Part 1: Bundling — "packing things together"
> *"Think of how medicine is enclosed in a shell called **capsule**. In
> object-orientation, this translates to **packing together our properties and
> methods in a class**."*

A medical capsule holds the medicine inside one tidy package. The data and the
code that works on that data live together in one unit — the class. This fixes a
weakness of structured programming (Lecture 1), where functions and data floated
around separately: the functions *operated on* data but didn't *belong to* it.

> **Encapsulation Part 1 = "the data and the behavior that belong together, live
> together."**

### Part 2: Hiding — "don't show the gears and levers"
> *"We can use a **phone** without understanding electronics. We don't need to
> know how the touchscreen, the camera or the logic board works. Similarly, we
> **don't want to expose the inner workings of our class**. An object should only
> reveal the essential features. This concept is called **data hiding**."*

```
   ┌─────────────────────────────────────────────────────────┐
   │                    YOUR PHONE                           │
   │   WHAT YOU SEE (public interface):                      │
   │     touchscreen, power button, camera app, volume       │  ◀── you touch these
   │   ════════════════ HIDDEN INSIDE ════════════════       │
   │   WHAT YOU DON'T SEE (private internals):               │
   │     logic board, battery cells, radio antenna, CPU      │  ◀── protected from you
   └─────────────────────────────────────────────────────────┘
```

- **Public parts** (some methods) = the touchscreen — what other code may use.
- **Private parts** (most properties, internal helper methods) = the logic board
  — hidden from the outside.

### Why do we hide? (the "so what?")

1. **Protection from external interference 🛡️** — hiding internal details
   protects the object from other code modifying it in unplanned ways, whether
   *intentional or accidental*. (Like sealing a battery inside a case so nobody
   pokes it with a screwdriver or spills water on it.)

2. **Freedom to change the internals 🔧** — *"If you replace your phone's
   battery, it won't affect the way you use your phone. Changes in the inner
   workings of your phone don't matter to you."* If the outside world only
   touches a class through its public interface, you can rip out and replace the
   internals without breaking anyone — the interface stays the same, nothing
   breaks. Huge for maintainability.

3. **Preventing ripple effects 🌊** — if other code reaches directly into
   private properties, your class and that code become tangled. Change your
   property, you break theirs. Hide it, they can't depend on it, you're free to
   change it.

### The rule of thumb 📏
> *"Expose only as much of your class properties and methods as needed for normal
> usage."*

Not "hide everything", not "expose everything" — **expose the minimum that lets
people use the object correctly.** Just the touchscreen, not the logic board.

### The payoff: loose coupling vs. tight coupling 🔗
> *"Data hiding keeps dependencies between objects to a minimum. A
> **tightly-coupled** system, with most objects depending on each other, is an
> obvious sign of **bad design**. Any tiny modification will **cascade down** and
> require changes elsewhere. It's like a never ending nightmare."*

```
   ❌ TIGHTLY COUPLED (no encapsulation):
   A reaches INTO B's internals, B reaches INTO C's internals.
   Change one internal → ripples through ALL of them. Nightmare. 🌊

   ✅ LOOSELY COUPLED (with encapsulation):
   A talks to B via B's public interface, B talks to C via C's public interface.
   Change one internal → only that object knows. Others unaffected. ✅
```

**Encapsulation is the tool that makes loose coupling possible.** By hiding
internals, you prevent other code from depending on them, so the system stays
flexible and maintainable.

### Abstraction vs. Encapsulation — airtight version

| | Abstraction (Pillar 1) | Encapsulation (Pillar 2) |
|---|---|---|
| **What it does** | Decides **what** to include / ignore | Decides **how to bundle & protect** what you included |
| **Question it answers** | *"Which details matter for this app?"* | *"Who's allowed to touch these details?"* |
| **When** | At **design** time, choosing contents | At **implementation** time, hiding internals |
| **Analogy** | Choosing what to put on the menu | The wall between kitchen & dining room; diners only see the menu |
| **The word** | About **relevance** | About **protection** |

They work together: **abstraction decides what's on the menu; encapsulation
builds the wall between the kitchen and the dining room.** You need both.

### The whole pillar in one picture

```
   ENCAPSULATION = BUNDLE + HIDE
   ┌──────────────────────────────────────────┐
   │                 CLASS                     │
   │   ╔══════════════════════════════════╗   │
   │   ║  PRIVATE (hidden internals)      ║   │  ← the "gears & levers"
   │   ║   • properties (data)            ║   │     nobody outside can touch
   │   ║   • internal helper methods       ║   │
   │   ╚══════════════════════════════════╝   │
   │   ─────── public interface ──────────    │
   │   • the methods outsiders ARE allowed    │  ← the "touchscreen"
   └──────────────────────────────────────────┘
        other code talks ONLY through the public interface
```

**Bundle the data with the behavior. Hide the internals. Expose just enough.
Keep coupling loose.**

---

## Lecture 6 — Inheritance ⭐ (Pillar 3)

**The problem it solves:** *"Without inheritance, we'd end up writing **similar
code over and over again**."* The villain of this lecture is **duplication**.
Inheritance = **reusing** an existing class implementation in new classes.

### The Pokémon problem 🎮

We need new types: Electric, Water, Flying Pokémon. Each has **everything the
base Pokémon has + one special move:**

```
   Electric:  name, armor, hitPoints, attack(), defend()  +  Wild Charge()
   Water:     name, armor, hitPoints, attack(), defend()  +  Aqua Tail()
   Flying:    name, armor, hitPoints, attack(), defend()  +  Dragon Ascent()
```

First five things identical across all; only the special move differs.

### ❌ Bad Option 1: Dump everything into the Pokémon class
> *"We'd end up in a class that has **too many responsibilities**. Suddenly, all
> Pokémon objects could swim, and fly, and discharge electricity. We definitely
> don't want that."*

A Pikachu using "Aqua Tail" makes no sense. Two design principles violated:

- **Granularity** = keep classes small and focused, not huge and bloated.
- **Separation of concerns** = each class handles ONE concern (one job), not many.

> *"Creating **one-size-fits-all monolithic classes** is a major mistake in
> object-oriented software development."*

📌 **Bookmark this:** "Granularity and separation of concerns" — one class, one
job. One of the most important principles in all of software design.

### ❌ Bad Option 2: Keep the classes completely separate
Each class now has a well-defined purpose — but `name`, `armor`, `hitPoints`,
`attack()`, `defend()` are **copy-pasted into all four classes.** A bug in
`attack()` must be fixed in four places. Adding a shared property means editing
four places. Maintenance nightmare — the duplication pain from the start.

```
   Option 1: one bloated class  → everything can do everything (wrong)
   Option 2: separate classes   → code repeated everywhere (wasteful)
   We need: shared code WHERE shared, separate code WHERE separate.
```

### ✅ The solution: Inheritance
> *"A class can **inherit all attributes and behavior from another class**."*

```
            ┌─────────────────────────────────────────────┐
            │              CLASS: Pokémon                  │
            │  (PARENT / SUPERCLASS)                       │
            │  PROPERTIES:  name, armor level, hit points  │
            │  METHODS:     attack(), defend()             │
            └─────────────────────────────────────────────┘
                               ▲
            ┌──────────────────┼──────────────────┐
              inherits            inherits            inherits
            ▼                   ▼                   ▼
   ┌────────────────┐  ┌────────────────┐  ┌────────────────┐
   │ ElectricPokémon│  │  WaterPokémon  │  │ FlyingPokémon  │
   │ (CHILD/SUBCLASS)│  │ (CHILD/SUBCLASS)│  │(CHILD/SUBCLASS)│
   │ + Wild Charge()│  │ + Aqua Tail()  │  │ + DragonAsc()  │
   └────────────────┘  └────────────────┘  └────────────────┘
```

- The **superclass** (Pokémon) holds all the **shared** stuff.
- Each **subclass** **automatically gets** all of that, *without writing a single
  line of code*.
- Each child then adds **only its own extra**: its special move.

Wrote the shared code **once** in the parent → three children reuse it for free.
No duplication, no bloated god-class, each class stays focused.

### The vocabulary 📖

| Term A | Term B | Meaning |
|---|---|---|
| **Parent** class | **Superclass** | the class being inherited FROM (Pokémon) |
| **Child** class | **Subclass** | the class that inherits (Electric/Water/Flying) |

Both pairs mean the same thing; used interchangeably in the real world.

### The bonus power: changes propagate automatically 🔄
> *"If we **enhance or modify** the Pokémon class, all the other classes will
> **automatically receive those changes**."*

Fix a bug in `attack()` once in the superclass → every subclass is fixed
instantly. Add a new shared method `rest()` → every subclass can now rest().
Inheritance turns "fix it everywhere" into "fix it once."

### The deeper design lesson
The whole problem was about **where to put shared vs. unique code:**

```
   SHARED code → goes UP in the superclass  (written once)
   UNIQUE code → goes DOWN in the subclass  (each adds its own)
```

Thinking tool forever: when several classes have overlapping code, ask *"What's
shared? What's unique? Shared up in a parent, unique down in the children."*
This serves granularity + separation of concerns + no duplication all at once —
focused classes AND no repeated code.

### The bridge to Pillar 4
> *"Inheritance... finally paves the road to another handy feature called
> **Polymorphism**."*

Inheritance gives a *family* of related classes. Polymorphism lets you treat
that whole family as *one* — grab a mixed bunch and tell them all "attack!"
without caring which type each is; each attacks its own way. That's Pillar 4.

### The whole pillar in one picture

```
   INHERITANCE = "is like that class, PLUS extras" — code reuse via parent/child

            ┌───────────────────────────┐
            │   SUPERCLASS (parent)     │
            │   holds the SHARED code   │  ← written ONCE
            └─────────────┬─────────────┘
                          │ inherits
           ┌──────────────┼──────────────┐
           ▼              ▼              ▼
     ┌──────────┐   ┌──────────┐   ┌──────────┐
     │ SUBCLASS │   │ SUBCLASS │   │ SUBCLASS │
     │  (child) │   │  (child) │   │  (child) │
     │ + unique │   │ + unique │   │ + unique │  ← each adds ONLY its own extra
     └──────────┘   └──────────┘   └──────────┘
   shared code → UP (one place) | change parent → all children get it automatically
```

---

## Lecture 7 — Polymorphism ⭐ (Pillar 4 — the final pillar)

### The name is the definition
> *"The word has Greek origins: **'polys'** means **many, much**, and **'morfé'**
> means **form, shape**."*

- **poly** = many · **morph** = form → **Polymorphism = "many forms."**
> Dictionary: *"the condition of occurring in **several different forms**."*

### Step 1 — revisit inheritance first
Polymorphism doesn't make sense without inheritance. Back to our Pokémon family:
all subclasses inherit name, armor, hitPoints, attack(), defend() from Pokémon.
New requirement: Water Pokémon should cause **more damage** than basic Pokémon →
need a **specialized implementation** of attack.

### Step 2 — method overriding (the mechanism that makes polymorphism possible)
> *"This is what we call **method overriding**. By **overriding** a method of the
> superclass, we tell that we want a **different behavior in our subclass** than
> the one we inherited."*

When a subclass inherits a method, it gets the parent's version for free. But
sometimes you want your *own* version. Overriding = "I know I inherited this
method, but I'm replacing it with my own implementation."

The strict rule:
```
   To OVERRIDE a method, the subclass method must have:
     ✅ the SAME name        (attack)
     ✅ the SAME parameters  (none here)
   ...but a DIFFERENT body (its own behavior)
```
Same signature, different guts.

Consequence (the seed of polymorphism):
```
   an_ElectricPokémon.attack()  →  runs Pokémon's attack()      (inherited)
   a_FlyingPokémon.attack()     →  runs Pokémon's attack()      (inherited)
   a_WaterPokémon.attack()      →  runs WaterPokémon's attack() (OVERRIDDEN)
   a_basic_Pokémon.attack()     →  runs Pokémon's attack()      (it IS a Pokémon)
```
**Same method name, `attack()`. Different objects. Different behavior.**

### Step 3 — the magic: work with them all as "just Pokémon"
> *"Polymorphism lets us work with objects created from **any** of these classes.
> We **don't need to know** whether it's a Water-, Flying- or Electric Pokémon
> instance to call any of the common methods defined in the superclass."*

**You can treat any subclass object as if it were a superclass object — call the
common methods on it — and the RIGHT version runs automatically.**

> *"We could create an **army of mixed Pokémon** and tell them to **attack at
> once**. Each of them will execute the **right attack method** without us having
> to know their exact type."*

```
   ARMY (mixed list, all stored as Pokémon):
     [ Pikachu(Electric), Squirtle(Water), Charmander(basic), Pidgey(Flying) ]
        │  for each pokémon in army:
        │      pokémon.attack()      ← ONE line, no if/else, no type-checking
        ▼
   Pikachu.attack()    → Pokémon.attack()        (inherited)
   Squirtle.attack()   → WaterPokémon.attack()   (OVERRIDDEN — more damage)
   Charmander.attack() → Pokémon.attack()        (inherited)
   Pidgey.attack()     → Pokémon.attack()        (inherited)
```
The code says `pokémon.attack()` — NOT "if Water call this, if Electric call
that." No if statements. Yet each runs the correct version for its actual type.
The runtime figures it out automatically.

> **THAT is polymorphism** — *"many forms"* = the single method `attack()` takes
> **many forms** depending on which object calls it, and you don't have to care
> which is which.

Instructor's one-line definition:
> *"Polymorphism is about working **freely** with instances of **many different
> classes** that share a **common super class**."*

The recipe (3 ingredients):
1. **many different classes** (a family: Electric, Water, Flying…)
2. **a common superclass** (Pokémon)
3. **work freely** — treat them all as the common type, call common methods;
   each does the right thing automatically.

### Step 4 — the Swift demo (seeing it in real code)
```swift
class Pokémon { func attack() { print("Pokémon attacks!") } }
class ElectricPokémon: Pokémon { }                 // inherits, no override
class WaterPokémon: Pokémon {
    override func attack() { print("Water Pokémon attacks harder!") }  // OVERRIDES
}
class FlyingPokémon: Pokémon { }                   // inherits, no override

let army = [Pokémon(), WaterPokémon(), ElectricPokémon(), FlyingPokémon()]
for pokémon in army { pokémon.attack() }           // ONE line — polymorphism!
```
- Swift marks overrides with the `override` keyword (safety: no accidental
  overrides). Only WaterPokémon overrides attack().
- The `army` list holds **mixed** types but treats them all as **Pokémon** (the
  common superclass) — the "work freely" part.

Output:
```
   Pokémon attacks!                   ← basic
   Water Pokémon attacks harder!      ← WaterPokémon (OVERRIDDEN!)
   Pokémon attacks!                   ← ElectricPokémon (inherited)
   Pokémon attacks!                   ← FlyingPokémon (inherited)
```
Same single line `pokémon.attack()` → 4 outputs, one different. The code never
asked "what type are you?" **The same call, many forms.**

### Why it's so powerful — Open/Closed
Polymorphism lets you write code that's **open to new types without changing the
old code.** Add a `FirePokémon` that also overrides `attack()` → the army loop
stays **unchanged**; the new type just slots in.

This is the **Open/Closed Principle**: *open* to extension (add new types),
*closed* to modification (don't rewrite existing code). Add a new type →
existing code keeps working untouched.

```
   ❌ WITHOUT polymorphism: a growing if/elif chain you must edit every time.
   ✅ WITH polymorphism:  for pokémon in army: pokémon.attack()  ← never changes
```
Every new type = another `elif` = another edit to working code = another chance
for a bug. Polymorphism collapses all of that into one line that never changes.

---

## 🏛️ The Four Pillars — complete

| Pillar | One-word essence | Question it answers | Pokémon example |
|---|---|---|---|
| **1. Abstraction** | **Choosing** | "What details matter?" | Kept name/armor/hitPoints; ignored age/weight |
| **2. Encapsulation** | **Protecting** | "Who can touch these details?" | Bundled data+behavior; hid the internals |
| **3. Inheritance** | **Reusing** | "Where does shared vs. unique code go?" | Shared up in Pokémon; specials down in subclasses |
| **4. Polymorphism** | **Unifying** | "How do I treat the whole family as one?" | Mixed army, one attack() call, each does the right thing |

They build on each other in order:
```
   Abstraction ──▶ Encapsulation ──▶ Inheritance ──▶ Polymorphism
   (choose)         (protect)          (reuse)          (unify)
```

**That's object-oriented programming.** Four pillars, one philosophy: model the
real world as things (objects) described by blueprints (classes), showing only
what matters (abstraction), protecting their insides (encapsulation), reusing
shared structure (inheritance), and treating families as one (polymorphism).
Everything in UML (Section 05) is just *drawing* these ideas on paper.

---

## Key takeaways — Section 03

1. **Programming evolved to fight complexity:** unstructured (spaghetti code) →
   structured (named functions) → object-oriented (self-contained objects that
   model the real world).
2. **An object** is a THING with **identity** (which one), **state**
   (properties + current values), and **behavior** (what it can do). Nouns =
   objects, adjectives = properties, verbs = behaviors.
3. **A class** is the **blueprint**; an **object** is an **instance**. The class
   declares properties (no values) and methods (functions embedded in the
   class); you fill in values when creating objects. One class → many objects.
4. **Abstraction (Pillar 1):** focus on what's important, ignore the rest.
   Context-dependent — "what is this for?" decides what's essential.
5. **Encapsulation (Pillar 2):** bundle data + behavior together AND hide the
   internals (data hiding). Expose only as much as needed. Enables loose
   coupling.
6. **Inheritance (Pillar 3):** reuse — shared code up in the superclass, unique
   code down in the subclasses. No duplication, no bloated god-class. Changes to
   the parent propagate to children automatically.
7. **Polymorphism (Pillar 4):** unify — treat a family of classes as their
   common superclass; call a common method and each runs its own (possibly
   overridden) version. Enables the Open/Closed Principle (open to extension,
   closed to modification).
