# 05. UML Basics and Fundamental Diagram Types

> 📝 _Learning log — notes we build together, lecture by lecture._

---

## Lecture 1 — What's UML?

### The problem UML solves
> *"Understanding a software system just by looking at its source code can be
> **very time consuming**. And communicating ideas about software design or
> business processes is **even more challenging** if there is no commonly
> accepted way to do it."*

Two pains, both about **communication**:
1. **Reading code is slow** — code tells you *how* something is implemented but
   buries the *big picture*.
2. **Talking about design is hard** without a shared language — if everyone draws
   differently, nobody understands anyone else.

UML is the answer to the "lack of a commonly accepted design language" problem
set up in Section 04, Lecture 4.

### What UML actually is
> *"UML is **not a textual programming language**, but rather a **graphical
> notation** consisting of **diagrams** that let us **model software systems**."*

| Part | What it means |
|---|---|
| "not a textual programming language" | UML is NOT code. You don't compile it, it doesn't run. |
| "a graphical notation" | A set of visual symbols and rules for drawing things (like music notation). |
| "consisting of diagrams" | The notation comes in the form of diagrams — pictures you draw. |
| "model software systems" | A model = a simplified representation. UML lets you create simplified visual models. |

**So: UML is a visual language for drawing simplified pictures of software
systems.** Not code. Pictures.

> *"We can use these diagrams to describe the **objects that form a system and
> their interactions**."* — our Section 03 vocabulary: UML draws objects (the
> things) and their interactions (how they talk to each other).

### The three families of UML diagrams ⭐

```
                          UML DIAGRAMS
                               │
            ┌──────────────────┼──────────────────┐
            ▼                  ▼                  ▼
       FUNCTIONAL          STRUCTURAL          BEHAVIORAL
            │                  │                  │
     Use Case Diagram   Class Diagram     Sequence Diagram
                                             Activity Diagram
                                           Statechart Diagram
```

| Family | Question it answers | Key diagram(s) | Section 03/04 connection |
|---|---|---|---|
| **Functional** | What does the system DO for the user? | Use Case Diagram | Section 04 use cases (visualized) |
| **Structural** | What are the THINGS & how are they built? | Class Diagram | Classes, attributes, operations, relations (the four pillars) |
| **Behavioral** | What HAPPENS & how do objects interact? | Sequence, Activity, Statechart | Object interactions & state changes |

- **Use case diagram** — the functional model; functionality from the user's
  point of view (the visual version of Section 04's use cases).
- **Class diagram** — the structure of a system in terms of objects, attributes,
  operations and relations (a picture of the four pillars).
- **Behavioral diagrams** (sequence, activity, statechart) — dynamic behavior;
  what happens and the interactions between objects.

### The best part: UML is language-independent 🌍
> *"The best part about UML is that it's **independent of any particular
> programming language**."*

A UML diagram doesn't say "Java" or "Python" or "Swift." It describes the design
in a neutral way:

> *"We can start coding object-oriented software based on UML diagrams. If those
> diagrams are detailed enough, they can be **converted to source code**."*

**Design once in UML → implement in any OO language.** The diagram is the shared
blueprint; the language is just the building material.

### When do you actually USE UML? (three real scenarios)

**Scenario 1 — When the solution isn't trivial: sketch BEFORE you code.**
> *"It may be tempting to open up your IDE and just start coding. The next thing
> you know, **hours have disappeared** and you are **desperately searching
> StackOverflow** for the answer. However, it's hard to find a solution if we
> couldn't first formulate the question. We need to **figure out what to
> implement before writing a single line of code**."*

Whenever something is unclear, quickly sketch a few diagrams to represent a
specific part of the software or new functionality.

The two benefits of sketching:
1. **Deeper understanding** — by thinking about classes, objects and
   interactions, we gain a deeper understanding of what should be implemented
   **without being distracted** by crashing ideas or strange compiler error
   messages. The diagram is a distraction-free thinking tool.
2. **Better communication** — a design helps us communicate ideas with other
   developers effectively; UML diagrams are a starting point for discussions
   without delving into source code.

> *"Although checking the actual code is useful, it will often **distract us
> from answering the real questions**, and turn the design discussion into a
> **code inspection**."*

**Scenario 2 — Reverse engineering: diagrams FROM existing code 🔄.**
> *"Another frequent use of UML is drawing diagrams **from existing code**. This
> technique is called **reverse engineering**, and it helps uncover the **dirty
> little secrets of undocumented software systems**."*

UML works both directions:
```
   Design first  →  UML diagram  →  code from the diagram   (forward)
   Code exists   →  UML diagram  →  understand the code     (reverse)
```

**Scenario 3 — Detailed blueprints (especially Waterfall) 🏗️.**
> *"Detailed UML blueprints are usually **required for software developed using a
> Waterfall approach**, and **less frequently for Agile projects**."*

Section 02 callback: Waterfall wants everything planned up front → detailed UML
blueprints essential. Agile iterates → draw "just enough" UML and refine. The
methodology determines how much UML you draw and when.

### Beyond software: UML is versatile 🌐
> *"UML is platform and programming-language independent, making it a **versatile
> modeling tool** not limited to software projects. UML has been used in
> multidisciplinary areas, including **scientific research, transportation,
> banking and defense**."*

Because UML is just "a way to model systems with objects," many real-world
systems can be modeled this way — the visual notation is genuinely universal.

### Tying it all back together

| Prior concept | How it shows up in "What's UML" |
|---|---|
| Section 02 — Waterfall vs Agile | Determines how much UML & when |
| Section 03 — Objects & classes | UML diagrams draw objects, classes, attributes, operations, relations |
| Section 03 — The four pillars | Class diagrams picture abstraction, encapsulation, inheritance, polymorphism |
| Section 04 — Use cases | Use case diagram = the visual version of use cases |
| Section 04 — OOAD process | Phase 4 (describe behavior visually) = UML. This lecture IS Phase 4. |
| Section 04 — "Why a common language" | This lecture answers it: UML is that common language |

### The map for the rest of Section 05

```
   Lecture 1 (done): What's UML  ← the map & the why
   Lectures 2-4:  Use Case Diagrams     (functional family)
   Lectures 5-7:  Class Diagrams        (structural family)
   Lecture 8:     Visibility            (encapsulation in UML)
   Lectures 9-11: Relations/Associations (inheritance, composition, etc.)
   Lecture 12:    Sequence Diagrams     (behavioral family)
   Lecture 13:    Activity Diagrams     (behavioral family)
   Lecture 14:    Statechart Diagrams   (behavioral family)
   Lecture 15:    Test Your UML Skills  (quiz)
```

---

## Lectures 2-4 — Use Case Diagrams (theory + challenge + solution)

### Lecture 2: The Theory

**Purpose:** visualize the functional requirements of the system — an **overview of
the system**, not a single use case. You rarely create a use case diagram for one
use case; it shows **groups of related use cases**. The visual version of
Section 04's use cases.

### The four building blocks ⭐

| Block | Symbol | Meaning |
|---|---|---|
| **Use Case** | Oval 🥚 with a title | One piece of functionality (verb phrase: "Create a Trip Entry") |
| **Actor** | Stick figure 🧍 (or box for systems) | Who/what interacts with the system (human OR system) |
| **Association** | Line 〰️ | This actor can perform this use case |
| **System Boundary** | Frame ▭ | What's inside (yours) vs. outside (not yours) |

- **Use Case:** draw an oval, put the title inside. (Travel app examples: "Create
  a Trip Entry," "Edit Trip," "Export App Database.")
- **Actor:** stick figures; the actor's name goes below. Actors = human beings OR
  other systems that interact with the system (Section 04 callback). **Layout
  convention:** primary actors on the left, secondary ones on the right.
- **Association:** a line between an actor and a use case = "this actor can
  perform this use case." Example: a mobile User can create/edit a trip entry
  but **cannot** export the database; the Power User can do **all** actions.
  **The absence of a line is meaningful** — it shows what an actor canNOT do.
- **System Boundary:** a frame around all use cases/actors that belong to a
  given system, showing where the system ends. External systems are drawn as
  separate actors on the right, with a different visual representation (e.g., a
  box labeled «system») to show they're not human. Example: the travel app
  relies on external cloud storage → cloud is an actor outside the frame; the
  "Create a Trip Entry" and "Edit Trip" use cases connect to it.

### What the diagram communicates
> *"A clear way to communicate the **high-level features and the scope** of the
> system. You can quickly tell what our system does just by looking at this Use
> Case diagram."*

Reading the travel app diagram: the system lets users create/edit trips; power
users can export the database; the app relies on an external cloud system. **The
absence of use cases shows what the system doesn't do** — a customer can easily
spot missing features before a single line of code is written.

### Two important caveats
1. **Ignore advanced relationships** («include», «extend», generalization between
   use cases) — they overcomplicate with questionable benefits. Focus on actors,
   use cases, and their interactions.
2. **The diagram does NOT replace written use cases.** The diagram = the
   overview/map; the written use case (Section 04's title + actor + scenario) =
   the detail/directions. You need **both**.

### Lecture 3: The Challenge

> *"Draw a Use Case diagram that provides an overview of an **elevator system**."*

Questions to answer first: (1) What actors interact with an elevator? (2) What
are the main functions of an elevator? Hint: elevators require **regular
maintenance and repair** (a second actor hides here — the technician).

### Lecture 4: The Solution (step-by-step build)

1. **Identify the system → draw the frame.** System = "Elevator."
2. **Identify the primary actor → the User.** One generalized actor representing
   all passengers (abstraction at work). Placed on the left.
3. **List the User's use cases** (read the control panel like a menu): Call
   Elevator, Select Floor, Ride the Elevator, Operate Doors, Trigger Alarm.
4. **Identify the secondary actor → the Technician.** Placed on the right. Has
   different use cases: Inspect Elevator, Service Elevator, Repair Elevator.
5. **The crossover:** the Technician can ALSO call the elevator, select the
   floor, etc. But the average User should NOT perform maintenance/repair —
   **those cases are exclusive to the technician role.** The absence of lines
   shows what's forbidden.

### The repeatable recipe (apply to ANY system)

```
   1. Identify the SYSTEM → draw the frame (boundary)
   2. Identify the PRIMARY actor(s) → stick figure(s) on the left
   3. List that actor's USE CASES → ovals; connect with lines
   4. Identify SECONDARY actor(s) → stick figure(s)/boxes on the right
   5. List their use cases → ovals; connect with lines
   6. Connect crossover use cases (if an actor can do another's cases)
   7. Remember: the ABSENCE of a line = "can't do this"
```

### Instructor's summary
> *"Use cases help us understand the essential functional requirements. They
> provide a **quick external overview** of the system. Make sure to keep your use
> case diagram **simple** and focus on the **actors and the textual use case
> descriptions**."*

- **Quick external overview** — the diagram shows the system from the *outside*
  (who uses it, what they can do); not about internals.
- **Keep it simple** — focus on actors + use cases + descriptions; don't
  overcomplicate with fancy relationships.

---

## Lectures 5-7 — Class Diagrams (theory + challenge + solution)

### Lecture 5: The Theory

Class diagrams are the **most frequently used** UML diagram type. After
identifying the entities (Phase 3 of OOAD), we create class diagrams for each.
A class = a **rectangle with three compartments** (top to bottom: name,
attributes, operations).

```
   ┌─────────────────────────────────────┐
   │               Trip                   │  ← NAME (noun, Upper Camel Case)
   ├─────────────────────────────────────┤
   │  name : String                       │  ← ATTRIBUTES (Lower Camel Case)
   │  createdAt : Date                    │     format:  name : Type
   │  homeCurrency : String               │
   │  startsAt : Date                     │
   │  endsAt : Date                       │
   ├─────────────────────────────────────┤
   │  setName(value: String)              │  ← OPERATIONS (verbs, Lower Camel Case)
   │  getName() : String                  │     format:  name(params) : ReturnType
   │  getEntries(from: Date, to: Date) : List │
   └─────────────────────────────────────┘
```

**Top = what it IS. Middle = what it HAS. Bottom = what it DOES.**

### Naming conventions ⭐

| Compartment | Part of speech | Naming style | Example |
|---|---|---|---|
| **Name** | Noun, singular | **Upper Camel Case** | `Trip`, `ElevatorMaintenanceUnit` |
| **Attributes** | Noun-ish | **Lower Camel Case** + `: Type` | `name: String`, `createdAt: Date` |
| **Operations** | **Verb** | **Lower Camel Case** + `(params): ReturnType` | `diagnose()`, `setName(value: String)` |

**Camel Case** = starting each word in a compound word with a capital (the humps
look like a camel's back 🐪).
- **Upper Camel Case** = first letter ALSO capitalized → **class names**
- **Lower Camel Case** = first letter lowercase → **attributes & methods**

### Why naming conventions matter
> *"A naming convention lets us focus on important issues instead of arguing over
> syntax and names. With a commonly accepted set of rules, we can easily read the
> source code written by other developers, even if they are from another company,
> country or continent. Standards are useful."*

Without standards → everyone names things their own way → chaos. With standards →
any developer on Earth can read your work. Standards remove trivial arguments so
you can focus on real design.

### Attributes — the details
- Format: **`attributeName : Type`** (type separated by a colon).
- Types are generic (`String`, `Date`, `Integer`) — adjusted to your programming
  language when coding. UML is language-independent; the diagram is the shared
  blueprint, the language-specific types are the building material.
- Trip class example: `name`, `createdAt`, `homeCurrency`, `startsAt`, `endsAt`.

### Operations — the details
- Method names are **verbs** in Lower Camel Case.
- **Parameters:** appear within parentheses as `name:Type` pairs, e.g.,
  `setName(value: String)`.
- **Return type:** add a colon after the closing parenthesis, then the type, e.g.,
  `getName() : String`.
- A method can have BOTH params and a return type: `getEntries(from: Date,
  to: Date) : List`.
- Keep it loose — `List` is enough; don't specify `List<Expense>`. The diagram is
  about design, not implementation minutiae. (Abstraction at work!)

### Lecture 6: The Challenge

Connects back to the elevator use case challenge — the Technician actor. "In the
not too distant future, such tasks will be automated."

> *"Create the class diagram of an **elevator maintenance robot**."*

Clues (guided challenge):
1. Name your class using Upper Camel Case.
2. Each robot needs a **unique identifier** — type `String` or any numeric type.
3. The robot can **diagnose, service, and repair** the elevator → map to operations.
4. Keep your class simple; adhere to naming conventions.

### Lecture 7: The Solution (step-by-step build)

1. **Name the class → `ElevatorMaintenanceUnit`** (Upper Camel Case ✅, noun ✅,
   meaningful & specific). Lesson: names matter — a good name communicates intent
   instantly.
2. **Add the attribute → `identifier : String`** (Lower Camel Case ✅). Type choice:
   String over Int because strings give more leeway (can be `"ELEV-001"`, a UUID,
   etc.). The type choice encodes a design decision about flexibility.
3. **Add 3 operations → `diagnose()`, `service()`, `repair()`** (verbs, Lower Camel
   Case). Simple versions — no params or return types (the challenge said keep it
   simple).

**The complete solution:**
```
   ┌─────────────────────────────────────┐
   │       ElevatorMaintenanceUnit        │
   ├─────────────────────────────────────┤
   │  identifier : String                 │
   ├─────────────────────────────────────┤
   │  diagnose()                          │
   │  service()                           │
   │  repair()                            │
   └─────────────────────────────────────┘
```

**Teaser for next lecture:** the `+` signs next to attributes/operations in UML
tools are **visibility tags** → connects to encapsulation (Pillar 2). That's
Lecture 8.

### The repeatable recipe (for any class diagram)

```
   1. Draw a rectangle divided into 3 compartments
   2. TOP: class NAME — noun, singular, Upper Camel Case
   3. MIDDLE: ATTRIBUTES — Lower Camel Case, format: name : Type
   4. BOTTOM: OPERATIONS — verbs, Lower Camel Case,
              format: name(params) : ReturnType
   5. Use generic types (String, Date, Int) — translate to your language later
   6. Keep it simple — don't over-specify (e.g., List not List<Expense>)
```

---

## Lecture 8 — Visibility: Public, Private, Protected, Package

### The connection: this is encapsulation (Pillar 2) made visual

Encapsulation had two halves (Section 03, L5): (1) **bundle** data + behavior, (2)
**hide** the internals (data hiding). The class diagram (L5-7) showed the
bundling. **Visibility is the *hiding* half, made visual** — it answers "who is
allowed to touch each attribute and method?"

> *"UML allows us to **control who can access** the attributes and the methods of
> our classes."*

### The four visibility levels ⭐

From most open → most restricted:

```
   + (public)   ~ (package)   # (protected)   - (private)
   everyone      same package   class + children  only the class itself
```

| Symbol | Name | Who can access it? | Analogy |
|---|---|---|---|
| `+` | **Public** | Anyone (code outside the object) | The touchscreen |
| `~` | **Package** | Any class in the same package/namespace | Your department's shared tool |
| `#` | **Protected** | The class + its child/subclasses | A family secret |
| `-` | **Private** | Only the class itself | The logic board |

- **`+` public:** *"A class method or attribute marked as public can be used by
  code outside of the object."* = the public interface.
- **`-` private:** *"Private attributes and methods can only be used within the
  class that defines them. Cannot be accessed directly from other classes."* =
  data hiding, the core of encapsulation.
- **`#` protected:** *"Only child classes and the defining class will be able to
  access that attribute or method."* A middle ground that **only exists because
  of inheritance (Pillar 3)** — "you + your kids," but not strangers. The pillars
  interlock: protected exists *because* inheritance exists.
- **`~` package:** *"Makes sense in languages that let us group code into logical
  units and provide a namespace. Available within its enclosing package."* Like a
  department in a company — anyone in your package, not other packages.

**The pattern:** as you move from `+` to `-`, access gets **tighter**. Public =
everyone → Package = your group → Protected = your family → Private = only you.

### The one rule for ALL OO languages 📏
> *"UML provides these visibility tags, but it's up to us to adapt it to the
> language we're using."* (Not every language supports all four — you translate
> to your target language.)

> *"There is only one rule that's commonly applicable to all object-oriented
> languages: **Expose only as much as needed and hide everything else.**"*

That's the golden rule of encapsulation restated — default to hiding; expose only
what must be exposed.

### The pattern that makes encapsulation work: Getters & Setters 🔒

**The problem — public attributes = no control.** If `Trip.name` is `+` public,
anyone can write `trip.name = "ab"`. But what if names must be ≥ 3 characters?
*"There is **no way to enforce this requirement**."* Same for dates: startsAt
must be earlier than endsAt, yet callers can "freely set any start or end date."

**The solution — private attributes + public getters/setters:**
1. Flip every attribute to `-` (private): now other objects can't set/retrieve
   them directly. *"They are, well, private to the Trip class."*
2. Provide **public getters and setters** for each — the controlled doorway.

**The payoff — now you have CONTROL 🎛️:**
> *"We are now in **full control of our class's internal data**. Setters let us
> check the input argument, and getters allow us to modify the value before
> returning it."*

- **Setters** = control what goes *in* (validation): `setName()` can reject names
  < 3 chars; `setStartsAt()` can reject dates after `endsAt`.
- **Getters** = control what comes *out* (transformation): e.g., return a date in
  the user's time zone even though stored in UTC internally.

**Before vs. after:**
```
   BEFORE: + name : String        ← public: anyone sets ANYTHING, no validation
   AFTER:  - name : String        ← private: sealed inside
           + getName() : String   ← public getter (controlled read)
           + setName(value:String)← public setter (validates: ≥ 3 chars)
```

**The pattern:** attributes are `-` (private) or `#` (protected) — *hide the
data*; getters/setters are `+` (public) — *expose controlled access*. Not dogma:
if nobody outside needs an attribute, don't add a getter/setter — hide it
completely. **Expose only as much as needed.**

### The bridge forward
> *"So far, we've seen how to represent a **single class**. Class diagrams let us
> also show the **relationships between the classes** in our system. We'll talk
> about relationships next."*

L5-8 drew one class at a time. Next (L9-11): the **lines between classes** —
associations, generalization (inheritance!), dependency/aggregation/composition/
realization. Where Pillar 3 and relationships get their visual notation.

### Tying it back to the pillars

| Pillar | How it appears in visibility |
|---|---|
| **Encapsulation (Pillar 2)** | The whole point — hide internals (`-`), expose the interface (`+`) |
| **Inheritance (Pillar 3)** | `#` protected only exists because children inherit |
| **Abstraction (Pillar 1)** | We choose which attributes/methods to even put on the diagram; visibility is the next layer of that choice |

**Visibility = encapsulation made visual**, with a nod to inheritance (via
protected). The four symbols are the standard notation for "who can touch this?"

---

## Lecture 9 — Associations

### Where this fits
For four lectures (5-8) we drew **one class at a time**. Now: the **relationships
between classes** — the lines you draw *between* the rectangles. Use cases/user
stories (Section 04) help reveal not just the classes but *how they connect*.

Example (travel expense app user story): *"As a traveller, I want to track my
expenses while abroad..."* → two classes jump out: **Trip** and **Expense**. The
relationship: *"Each Trip will include its travel expenses."*

### The association: a solid line between classes
> *"To express this relationship, we draw a **solid line** between these classes.
> This line represents an **association**. The association tells us that the
> classes refer to each other."*

```
   ┌──────────┐                    ┌──────────┐
   │   Trip   │ ─────────────────  │  Expense │
   └──────────┘                    └──────────┘
```

A solid line = "these two classes are associated; they refer to each other."

### Bidirectional vs. Directed associations ⭐

A plain solid line = **bidirectional** (both classes refer to each other). This
creates **tight coupling** — a Section 03 / Pillar 2 callback:

> *"What happens if the Expense also refers to the Trip? We'd need to also bring
> the Trip class with it. This doesn't make sense, since we should be able to use
> the Expense **without the Trip**. Tight coupling is something you should
> definitely try to avoid."*

**The solution: a directed association (an open arrowhead):**
> *"UML lets us express **directed associations**: by drawing a solid line that
> ends with an **open arrowhead**, we show that only one of the classes refers to
> the other. The arrow points to the class that's **referred to**."*

```
   ┌──────────┐                    ┌──────────┐
   │   Trip   │ ─────────────────▶ │  Expense │
   └──────────┘   open arrowhead   └──────────┘
```

Read: **Trip → Expense** = "Trip knows about Expense, but Expense does NOT know
about Trip." Now Expense is **free** — reusable anywhere without dragging Trip
along. A tightly-coupled bidirectional relationship becomes a **loosely-coupled
directed** one.

| Type | Symbol | Meaning | Coupling |
|---|---|---|---|
| **Bidirectional** (plain) | Solid line `───` | Both classes refer to each other | Tighter ⚠️ |
| **Directed** (arrow) | Solid line + open arrowhead `───▶` | Only ONE class refers to the other | Looser ✅ |

**Rule of thumb:** prefer the directed association unless you genuinely need both
classes to know about each other. Keeps coupling low and classes reusable.

### Multiplicity: "how many?" ⭐

A relationship also says *"how many of one are connected to how many of the
other?"* — called **multiplicity.** Put the notation at the end of the line near
the class it describes.

| Notation | Read as | Meaning | Travel app example |
|---|---|---|---|
| `*` | "zero or more" | any number, including none | A trip can have zero or more expenses |
| `1` | "exactly one" | one, required (**the default**) | A trip must have exactly one home currency |
| `0..1` | "zero or one" | optional single | A trip may or may not have a single note |
| `1..*` | "one or more" | at least one, required | (extension) |
| `0..*` | "zero or more" | same as `*` | (extension) |

```
   ┌──────────┐                  ┌──────────┐
   │   Trip   │ 1 ──────────── * │  Expense │
   └──────────┘                  └──────────┘
                  ↑                ↑
       "one trip"            "has many expenses"
```

- Multiplicities can appear at **both ends** of the line.
- **The default is `1`** — if no multiplicity is shown, assume exactly one.

### One more detail: naming the property
You can label the line with the **name of the class property** that holds the
reference (e.g., "expenses" if Trip has an `expenses` attribute). Ties the visual
relationship to the actual attribute. Nice-to-have, not essential.

### The bridge forward
> *"The Association isn't the only kind of relationship. Next, we're going to talk
> about **Generalization**."*

Associations = the **simplest** relationship ("these classes refer to each
other"). Next: **Generalization** = the UML name for **inheritance (Pillar 3)** —
where parent/child class hierarchy gets its visual notation.

### Tying it back

| Concept from before | How it appears in associations |
|---|---|
| Encapsulation / coupling (Pillar 2) | Bidirectional = tight coupling (avoid); directed = loose coupling (prefer) |
| Phase 3 → relationships (Section 04) | Use cases/user stories reveal how classes connect |
| Objects containing other objects (Section 03, L2) | "objects may contain or refer to other objects" — associations draw exactly this |

**Association = "these classes refer to each other"**, drawn as a solid line,
refined with a direction (arrow) to control coupling, and refined with
multiplicity (`*`, `1`, `0..1`) to say *how many*.

---

## Lecture 10 — Generalization

### The big reveal: generalization IS inheritance (Pillar 3)
Generalization is the **UML name for inheritance**. The concept is identical to
Section 03, Lecture 6 — parent/superclass, child/subclass, shared code up, unique
code down. This lecture just gives that concept its **standard visual symbol.**

> *"In UML, we use **generalization** to express that one model element is **based
> on another** model element."*

("Based on another" = "inherits from another." Called *generalization* because
the arrow points from the *specific* child to the *general* parent.)

### The symbol: solid line + HOLLOW arrowhead → parent
> *"Generalization is represented as a **solid line with a hollow arrowhead** that
> points to the parent."*

```
                                      hollow arrowhead (empty triangle ▷)
   ┌──────────────┐                                          ┌──────────┐
   │ BusinessTrip │ ────────────────────────────────────────▶ │   Trip   │
   │  (child)     │           solid line                      │ (parent) │
   └──────────────┘                                          └──────────┘
```

Read: **BusinessTrip → Trip** = "BusinessTrip inherits from Trip." Arrow points
from the *specific* child to the *general* parent.

### The crucial symbol distinction ⚠️

| Relationship | Symbol | Arrowhead | Points to | Meaning |
|---|---|---|---|---|
| **Directed association** (L9) | Solid line + arrow | **Open** ▶ (simple V) | The class being *referred to* | "A refers to/uses B" |
| **Generalization** (L10) | Solid line + arrow | **Hollow** ▷ (empty triangle) | The **parent** | "A inherits from B" |

> **The hollow triangle is the universal sign for inheritance in UML.** See it
> pointing at a class → the class at the tail is a subclass.

### What goes in the child class
> *"Because BusinessTrip inherits everything from its parent, we must **only
> specify the attributes and operations that are specific to the child**."*

The "shared code up, unique code down" principle from Section 03, L6. The child
doesn't repeat the parent's attributes — it only declares its *own extras*.
BusinessTrip automatically gets Trip's name, createdAt, homeCurrency,
getters/setters… without writing them again.

### The "IS-A" vs "HAS-A" test ⭐ (the key mental model)

The classic way to decide which relationship to use:

```
   "Is X a Y?"        → YES → generalization (inheritance)
   "Does X have a Y?" → YES → association (or aggregation/composition)
```

**"IS-A" → Generalization:** Is a `BusinessTrip` a `Trip`? ✅ / Is a
`WaterPokémon` a `Pokémon`? ✅ / Is a `Car` a `Vehicle`? ✅ — the child *is a
specialized version of* the parent.

**"HAS-A" → Association:** Does a `Trip` have `Expenses`? ✅ / Does a `Library`
have `Books`? ✅ / Does a `Car` have an `Engine`? ✅ — one class *contains or
uses* the other.

> 🚨 **The #1 beginner design mistake:** using inheritance (IS-A) when you should
> use association (HAS-A). "A Car IS-A Engine" sounds wrong → it's not inheritance,
> it's an association. The IS-A/HAS-A test catches this instantly — if the
> sentence sounds weird, it's not generalization.

> 🎁 **Teaser for L11:** "HAS-A" comes in two flavors — **aggregation** (parts can
> exist on their own) vs **composition** (parts die with the whole). Both are
> "HAS-A," but the lifecycle differs. Lecture 11 refines "HAS-A."

### A parent can have multiple children
One parent, many children (the Pokémon family: Pokémon → Electric/Water/Flying).
Multiple arrows all point up to the same parent.

### Multiple inheritance — the debate
> *"A parent can have multiple children. We can also have child classes that
> inherit from different parents. Some languages support **multiple inheritance**
> — C++, Perl, Python."*

> *"Many **modern** languages only allow **single inheritance** — inheriting from
> one parent. Single inheritance **reduces complexity** and avoids the **ambiguity**
> that comes with multiple inheritance."*

The ambiguity: if two parents both have a `save()` method, which one runs when
the child calls `save()`? (The "diamond problem.") Single inheritance = simpler
& safer (modern default: Java, Swift, C#). Multiple inheritance = more powerful
but error-prone. UML can draw either; you translate to whatever your language
supports.

### Generalization isn't only for classes
> *"UML does not restrict generalization to classes. It can also be used in use
> case or component diagrams — a child element receives its parent's attributes,
> operations, and relationships."*

The hollow-triangle symbol & meaning ("inherits from") are reusable across
diagram types (e.g., a specialized actor inheriting from a general one).

### Tying it back to the pillars

| Concept from before | How it appears in generalization |
|---|---|
| **Inheritance (Pillar 3)** | The whole point — generalization IS inheritance, drawn |
| Parent/superclass, child/subclass | Arrow from child → parent; parent at the hollow arrowhead |
| "Shared code up, unique code down" | Child only declares its OWN extras; inherits the rest |
| Granularity & separation of concerns | Specialized children stay focused; no bloated god-class |
| **Encapsulation (Pillar 2)** | `#` protected (L8) exists *because* of this — protected = "class + its children" |

Beautiful interlock: **visibility (L8) + generalization (L10) together express
"who can touch what, across a family of classes."** Protected members are
accessible to exactly the classes reachable by the hollow-triangle arrows.

### The relationships so far

| Relationship | Symbol | Meaning | "test" | Pillar |
|---|---|---|---|---|
| **Association** (L9) | Solid line (+ optional ▶) | "A refers to/uses B" | "HAS-A" | objects referring to objects |
| **Generalization** (L10) | Solid line + **hollow** ▷ → parent | "A inherits from B" | "IS-A" | **Inheritance (Pillar 3)** |

Lecture 11 adds: dependency, aggregation, composition, realization — completing
the toolkit. The two most important ones are now locked in.

---

_Notes for lectures 11–15 will be added as we progress._
