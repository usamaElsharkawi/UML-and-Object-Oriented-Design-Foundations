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

_Notes for lectures 5–15 will be added as we progress._
