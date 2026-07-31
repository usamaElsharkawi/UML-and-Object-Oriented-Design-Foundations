# 04. Object-Oriented Analysis and Design

> 📝 _Learning log — notes we build together, lecture by lecture._

## The big idea: OOAD is a *process* with 4 phases

> *"Building an object-oriented application requires some preliminary steps.
> These steps are **similar regardless of the development methodology**."*

Whether Waterfall or Agile, you do these same four steps. *How* you do them
changes (Waterfall = all up front; Agile = a little at a time), but *what* you do
is universal. The progression goes **fuzzy → clear** and **text → pictures.**

```
   ┌──────────────────────────────────────────────────────────────────────┐
   │            THE OOAD PROCESS — 4 PHASES                               │
   │  Phase 1: COLLECT REQUIREMENTS                                      │
   │     "What's the problem? What must the app DO?"                     │
   │     → brainstorm, discuss, document (text only)                     │
   │  Phase 2: DESCRIBE THE APP (from the user's perspective)            │
   │     "How does the system behave for the user?"                     │
   │     → use cases / user stories (still text, but structured)         │
   │  Phase 3: IDENTIFY THE THINGS (entities/classes)                   │
   │     "What are the players in our system?"                           │
   │     → spot the potential classes                                    │
   │  Phase 4: DESCRIBE BEHAVIOR VISUALLY (UML)                         │
   │     "Let's DRAW the classes, attributes, behavior & interactions"  │
   │     → Unified Modeling Language diagrams                            │
   └──────────────────────────────────────────────────────────────────────┘
```

**Key insight:** Phases 1 & 2 need NO special tools — just text/pen & paper. It's
only at Phase 4 that you need a *design language* (UML). Each phase feeds the
next; clear earlier steps make later ones easier.

---

## Lecture 1 — Fundamental OOAD Concepts

The 4 phases (overview): (1) collect requirements, (2) describe the app from
the user's perspective, (3) identify the things (entities/classes), (4) describe
behavior visually (UML).

- Phases 1 & 2 need no special tools — text editing or pen & paper suffices.
- Phases 3 & 4 require us to **depict the classes** that form our system, how
  they behave, what attributes they need, and **visualize how the objects
  interact**.
- *"Picking the essential entities won't be challenging if we did a good job
  during the previous two steps."* — the phases are sequential; each makes the
  next easier.
- Phase 2 may include **visual mockups, wireframes, or prototypes** to
  communicate the vision to the client and avoid surprises/misleading
  expectations. (Example: an iOS version of an Android app will look & behave
  differently — a prototype helps the client understand.)

---

## Lecture 2 — Collecting Requirements

**Definition:** requirement = *"a thing that is needed or wanted."* We must
clarify what's needed or wanted in our application. This step **paves the way
for all other phases.**

### The two questions you must answer
1. What's the problem we're trying to solve?
2. What does our app need to do to accomplish that functionality?

Involves a lot of **brainstorming and discussion.** Once you reach agreement,
**document** the ideas.

### The golden rule of writing requirements
> *"The requirements need to be **as clear as possible**. Only write down the
> decisions that underline what the system is going to do. **Vague thoughts will
> lead to conflicts later on**."*

Write *decisions*, not vague thoughts.

### The two types of requirements ⭐

#### Functional requirements — "what the app DOES"
> *"The features of the system are the so-called **functional requirements** —
> what the app needs to provide feature-wise, how it should react to a particular
> input, or what the expected behavior is in a specific situation."*

About **behavior and features.** Runner-app example questions: should speed
always be visible? imperial or metric units? configurable or automatic?

#### Non-functional requirements — "the constraints & qualities"
> *"Not directly related to a feature or behavior, but important nonetheless."*

About **qualities and constraints.** Examples: **performance** (don't ruin UX
with an unresponsive app), **legal** (does it collect sensitive data? allow
browsing the Internet?), **documentation & support** (adhere to standards/
regulations).

> *"Non-functional requirements are **equally important**. Ignoring them may
> cause **serious legal issues** and all sorts of other problems."*

| | Functional | Non-functional |
|---|---|---|
| **About** | What the system **does** | How **well** / constraints |
| **Answers** | "What features?" | "What qualities/rules?" |
| **Examples** | store expenses by trip; convert currencies | performance; legal; run on iOS 9+ |

### How to write them — the format & example (travel expense app)
Every requirement is a **short, concise phrase in the form "The app/system must
___."** Don't write lengthy descriptions.

**Functional requirements (example):**
- The app must store travel expenses organized by trip.
- Each trip must have a home currency. The default currency is fetched from the
  phone's settings. User settings must override the default home currency.
- Expenses can be entered in any of the supported currencies.
- The app must automatically convert the amounts to the home currency.

**Non-functional requirements (example):**
- The app must run on iOS 9 and newer versions.
- The app must avoid unnecessary network roundtrips to reduce data roaming fees
  and preserve battery.
- The app must include the support email and the link to the app's website.

### Tools & format
- Easiest way: just write them down.
- Eventually capture digitally, but at early stages **pen & paper or a whiteboard
  are fine** — just make sure you **save them** (e.g., take a photo).
- There are formal tools/systems, but the instructor skips them: *"this course is
  not about tools, but rather about **principles**."*

### Methodology callback 🔗
> *"If we are using a **Waterfall** approach, we need to **clarify all the
> requirements in advance**. For **Agile** projects it's perfectly acceptable if
> we continue without having all the answers. Agile lets us **revisit and refine**
> the requirements as we iterate."*

Same steps, different timing — Section 02 paying off in real time.
| **If ignored** | app does the wrong thing | app is slow/illegal/non-compliant |

---

## Lecture 3 — Mapping Requirements to Technical Descriptions

**Phase 2:** describe the system's functionality **from the user's perspective.**
Two tools, each tied to a methodology.

### Tool 1: Use Cases (preferred in Waterfall)

A **use case** documents one specific piece of system functionality.

```
   USE CASE = TITLE + ACTOR + SCENARIO
```

1. **Title** — a distinct functionality, e.g., "Create a new trip," "Add
   expense," "Convert currencies." Each use case = **one distinct functionality.**
2. **Actor** — who/what uses this functionality. Called "actor" because it can be
   **a human user OR a non-human entity like another system.** (An actor isn't
   necessarily a person — it can be another software system interacting with yours.)
3. **Scenario** — one or more sentences explaining **what and how** the system
   works in this particular case.

**Example — "Create a new trip":**
- **Title:** Create a new trip
- **Actor:** the user of the mobile app
- **Scenario:** The user can initiate creation from the main screen. The title is
  mandatory; all other settings optional. Optionally, write a short description and
  set start/end dates. The app assigns a default home currency from the phone's
  settings; users can override it. The app allows setting a budget (optional) and
  a custom thumbnail. Finally, the user can save or cancel.

Two rules that matter (format doesn't):
- **Avoid technical terms** — the description must be understood by **all
  stakeholders, including end users.**
- It's a **clear, human-friendly, textual description.** (We'll talk about use
  case *diagrams* — the visual version — later in Section 05.)

### Tool 2: User Stories (preferred in Agile)

**User stories** are shorter than use cases — usually **1–2 sentences.** Fixed
template:

> **"As a (type of user), I want (some goal) so that (some reason)."**

Examples:
- *"As a user, I want to add notes to my expenses so that I can identify them
  later on."*
- *"As a power user, I want to retrieve the app's database file so that I can
  inspect it on any computer."*

Three slots: **As a [role], I want [goal] so that [benefit].** Compact, focused
on the *value* to the user.

### The rule about size → Epics
> *"If you can't describe the user story in one or two sentences, you may need to
> **split it into multiple smaller user stories**."*

A too-big story = an **epic** — a bigger chunk of functionality that gets broken
down. Example:

> **Epic:** *"As a traveler, I want to track my expenses while abroad so that I
> don't exceed my budget."*

Splits into smaller stories:
- *"As a user, I want to create new trips so that I can track each trip
  individually."*
- *"As a business traveler, I want to tag my business trips so that I can
  separate them from my private travels."*

(Epics return in Section 06's case study — the note-taking app is broken into
Epics 1, 2, 3.)

### The physical culture of user stories
Often written on **sticky notes or index cards**, arranged on walls/tables during
meetings — the famous Agile "story wall." Reflects Agile's people-first,
collaborative philosophy (Value 1: individuals & interactions over processes &
tools).

### The crucial shared property
> *"Like use case descriptions, user stories **don't capture the feature
> details**. They serve as **discussion starters** instead. User stories are about
> **communication**."*

Neither use cases nor user stories are full specifications — they're
*conversation starters*. Details get worked out in discussion.

### Use Cases vs. User Stories

| | Use Cases | User Stories |
|---|---|---|
| **Length** | Longer (title + actor + scenario) | Short (1–2 sentences) |
| **Format** | Free-form text/bullets, non-technical | Fixed: "As a __, I want __ so that __" |
| **Detail** | More detailed scenario | Just goal + reason; details via discussion |
| **Purpose** | Clear human-friendly description | Discussion starter / communication |
| **Physical form** | Document | Often sticky notes / index cards on a wall |
| **When too big** | — | split into smaller stories; a big one = an **epic** |
| **Preferred in** | **Waterfall** | **Agile** |

The methodology you chose determines which documentation tool you reach for.
Waterfall → use cases (detailed, up front). Agile → user stories (lightweight,
iterative).

---

## Phase 3 — Identifying the Things (from Lecture 1)

> *"We aim to **identify the things that form our system** — the **potential
> players** that have a specific, well-defined role in our application."*

This is where **Section 03 pays off directly.** "Identifying the things" =
finding your **objects/classes** (the noun-hunt from Lecture 2's sentence trick).
*"Picking the essential entities won't be challenging if we did a good job during
the previous two steps"* — clear requirements + clear use cases → the classes
almost jump out. This is **abstraction** (Pillar 1) in action.

Examples: a class representing an **item** (name, price, other attributes), a
class responsible for **securely communicating with the server**, a class to
**manage local persistence**, and so on.

---

## Phase 4 + Lecture 4 — Why We Need a Common Descriptive Language

### What Phase 4 is
> *"In the final phase, we describe the behavior of our system in a **formal
> way** — creating **visual representations** of our classes, their attributes and
> behavior. We also model the **interaction between the objects**."*

Now we go from text to **pictures** — formal, visual representations. We draw
two things: (1) the **classes** (attributes + behavior) = the *structure*; (2)
the **interactions between objects** = the *behavior/dynamics*.

### The tool: UML
> *"We rely on the **Unified Modeling Language**, or UML for short. UML is a form
> of **graphical notation** that provides a set of **standard diagrams**. These
> diagrams let us describe object-oriented systems in a **standard way**."*

**UML = a graphical notation = a set of standard diagrams** for describing OO
systems. We go deep on it in Section 05.

### The argument: why a *common* language? (Lecture 4)

**Step 1 — Phases 1 & 2 need no special language:** *"The first two steps don't
require any special tool or design language — even a piece of paper or a
whiteboard would be sufficient."* Requirements and use cases are *text* — anyone
can read text.

**Step 2 — But the next phases DO need to depict classes & interactions:** *"The
next steps require us to depict the classes, how they behave, what attributes
they need, and visualize how the objects interact."* You can't easily describe
class structure or object interaction in plain prose — you need to *draw* it.

**Step 3 — The problem: without a standard, everyone invents their own:** *"The
lack of a commonly accepted design language led to the proliferation of different
non-standard approaches."* No standard → every team draws differently → nobody
understands each other's diagrams → miscommunication → the "chaos" Section 02
warned about. Like every architect using personal symbols for doors and walls.

**Step 4 — We could invent one, but we don't have to:** *"Luckily we don't have
to."*

**Step 5 — UML already exists as the standard:** *"The Unified Modeling Language
is a common design language released in **1997**. UML provides a set of
**standard diagram types** that describe both the **structure** and the
**behavior** of software systems."*

UML is the *answer* to "everyone draws differently" — the shared, standard
visual vocabulary for OO systems, covering both **structure** (classes) and
**behavior** (interactions). That's the bridge into Section 05.

---

## Tying the whole section together

```
   FUZZY IDEAS (in your head)
        │
        ▼
   PHASE 1 — COLLECT REQUIREMENTS
   "What must the system do / satisfy?"
   ├── functional requirements  (features/behavior: "the app must ___")
   ├── non-functional requirements (qualities/constraints: performance, legal, docs)
   ├── format: short "the system must ___" sentences
   └── Waterfall: all up front | Agile: revisit & refine
        │
        ▼
   PHASE 2 — DESCRIBE THE APP (user's perspective)
   "How does the system behave for the user?"
   ├── Use Cases (title + actor + scenario)  → Waterfall
   └── User Stories ("As a __, I want __ so that __")  → Agile
        both = discussion starters, non-technical, human-friendly
        big story = epic → split into smaller stories
        │
        ▼
   PHASE 3 — IDENTIFY THE THINGS
   "What are the players/classes in our system?"
   → noun-hunt: spot the classes (item with name/price, server comm, persistence...)
   → abstraction (Pillar 1) in action
        │
        ▼
   PHASE 4 — DESCRIBE BEHAVIOR VISUALLY (UML)
   "Let's DRAW the classes & interactions in a standard way"
   → UML (released 1997): standard diagrams for structure + behavior
   → solves the problem of "everyone draws differently"
        │
        ▼
   SECTION 05 — UML BASICS & DIAGRAM TYPES  (where we're going next!)
```

### How prior sections show up in OOAD

| Concept from before | Where it shows up in OOAD |
|---|---|
| **Waterfall vs Agile** (Section 02) | Timing of Phase 1 (all vs iterative); tool for Phase 2 (use cases vs user stories) |
| **Objects & classes** (Section 03 L2-3) | Phase 3 = identifying the classes/objects |
| **Abstraction** (Pillar 1) | Phase 3 = deciding which entities are essential |
| **Encapsulation** (Pillar 2) | Phase 4 = drawing classes with public/private parts |
| **Inheritance & Polymorphism** (Pillars 3-4) | Phase 4 = modeling class relationships & interactions |
| **The "blueprint" metaphor** | UML diagrams ARE the blueprints |

---

## Key takeaways — Section 04

1. **OOAD is a 4-phase process:** collect requirements → describe the app (user's
   perspective) → identify the things → describe behavior visually (UML). The same
   regardless of methodology.
2. **Phase 1 — Requirements:** a requirement = "a thing needed or wanted." Two
   types: **functional** (what the app does) and **non-functional**
   (constraints/qualities like performance, legal, docs). Write clear *decisions*
   in "the app must ___" format — vague thoughts cause conflicts later.
3. **Phase 2 — Use cases vs user stories:** Use case = title + actor + scenario
   (Waterfall). User story = "As a __, I want __ so that __" (Agile). Both are
   non-technical, human-friendly *discussion starters*, not full specs. A too-big
   user story = an **epic** → split into smaller stories.
4. **Phase 3 — Identify the things:** noun-hunt for the classes; abstraction
   (Pillar 1) in action. Easier if Phases 1 & 2 were done well.
5. **Phase 4 — UML:** the standard visual language (released 1997) for drawing
   both the **structure** (classes) and **behavior** (object interactions) of OO
   systems.
6. **Why a common language matters:** without a standard, every team draws
   differently → miscommunication → chaos. UML is the shared visual vocabulary
   that solves this.
7. **The bridge:** Phases 1 & 2 are text-only (no special language); Phases 3 & 4
   require drawing → that's why UML exists → Section 05 is where we learn it.
