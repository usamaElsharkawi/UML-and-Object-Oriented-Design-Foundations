# 02. Software Project Management Foundations

> 📝 _Learning log — notes we build together, lecture by lecture._

## Why this section comes first

Designing software is intricate and multifaceted. **UML and software design are
powerful tools, but a tool is only as good as the process that guides it.** This
section teaches us the frameworks (methodologies) *before* the tools (UML) —
because the methodology shapes *how* we apply UML.

- A building needs a blueprint **and** a construction plan. UML is the
  blueprint; the methodology is the construction plan.
- Learning the methodologies first means that when we draw UML later (Section 05),
  we'll draw the *right* diagrams the *right* way for each situation — not just
  pretty pictures.

### Tools × Process = Result

| Tools (UML) | Process (methodology) | Result |
|---|---|---|
| **What** to draw (class diagrams, use cases, …) | **When & how** to draw it | robust, scalable, maintainable software |

### The root of it all

Software development has one core problem that never goes away:

> **We rarely know exactly what we're building until we've started building it.**

This splits the industry into two camps:
- **Waterfall** — "Then let's figure it ALL out before we start." (fight the uncertainty upfront)
- **Agile** — "Then let's accept we can't, and learn as we go." (embrace the uncertainty)

Everything else flows from that one philosophical difference.

---

## Lecture 1 — Why You Shouldn't Skip This Module

**Big idea:** UML & software design are tools in our arsenal, but they're most
effective when applied within a framework that aligns with the nature and needs
of our projects — whether it's the **precision of Waterfall** or the
**flexibility of Agile**.

- Designing software needs a structured approach — you can't just sit down and
  start coding (beyond a simple "Hello world").
- A roadmap/structure ensures all bases are covered and nothing critical is
  overlooked.
- The methodology **shapes how we apply UML techniques and principles**.
- Goal of choosing the right approach: craft **robust, scalable, and
  maintainable** software.
- Understanding this empowers us to choose the best approach so our use of UML
  is both **effective and purposeful**.

---

## Lecture 2 — Waterfall vs. Agile Software Development Approaches

**Big idea:** There are different ways to develop software. Beyond a simple app,
you need a structured approach — especially when you're not flying solo.

- Without a well-defined process, even small teams descend into **chaos** as a
  project's complexity grows and more people get involved.
- We focus on two major approaches:

| | Waterfall | Agile |
|---|---|---|
| **Mental model** | Building a house from a detailed blueprint | The change-embracing, iterative counterpart |
| **Requirements** | Set in stone early | Can shift quickly |
| **Change** | Minimized during development | Embraced & adapted to throughout |
| **Best for** | Stable, well-understood problems | Projects where needs/goals evolve |

- **Important nuance:** No process maps out *every* step with perfect accuracy —
  but having a process in place is still crucial.
- A process synchronizes **all** aspects of development, not just writing code:
  design, product management, budgeting, testing, documentation, release, and
  maintenance.

---

## Lecture 3 — The Waterfall Model

**Big idea:** A **linear** approach — you finish one phase completely before
moving to the next, and you **don't go back**. The metaphor is a waterfall: water
cascades downward, never flowing back up.

```
   Requirements  ──┐
                   ▼
      Design     ──┐
                   ▼
  Implementation ──┐
                   ▼
   Verification  ──┐     ← flows down, never back up
                   ▼
    Maintenance
```

### The 5 phases

1. **Requirements** — Gather and scrutinize all expected functionality with
   stakeholders; everything is **meticulously documented**. This phase is
   **crucial** — it's the contract for the whole project. A well-done
   requirements phase sets the stage for success.
2. **Design** — Outline the software's architecture (the "blueprint"). Must be
   **clear and comprehensive**, answering: system components, security,
   performance, future scalability. Details depend on the requirements. **This
   is where UML lives in Waterfall.**
3. **Implementation** — Developers write code, broken into manageable units;
   each unit is built and tested against the design criteria. Code only starts
   after requirements + design are complete.
4. **Verification** — The whole product is tested against the **predefined
   requirements**: functional, performance, security, usability tests. This is a
   **late, big-bang testing** moment (not continuous).
5. **Maintenance** — Fix minor bugs; sometimes functional enhancements. **Huge
   rule:** significant new requirements at this stage typically warrant starting
   a **new Waterfall project** rather than disrupting the structured process.

### When Waterfall shines ✅
Projects with **well-defined, unchanging requirements**: life-control systems,
medical systems, military systems. The cost of getting it wrong (or changing
mid-stream) is enormous, so pinning everything down upfront is desirable.

### Waterfall's fatal weakness ⚠️
Criticism for its **rigidity**, especially adapting to new requirements during
later stages. If there's a high chance of changing needs or overlooked design
elements → a more flexible approach is needed (that's Agile).

---

## Lecture 4 — Agile Software Development

**Big idea:** Born from the **Agile Manifesto (2001)** as a solution to the
heavy, bureaucratic methodologies cluttering the landscape. It embraces change
and uncertainty through **iterative development**.

### The 4 Agile Values

Each has the form "**X over Y**" — and crucially, this does **NOT** mean Y is
abandoned; it means X is **prioritized**.

1. **Individuals and interactions over processes and tools** — Agile still uses
   processes/tools, but doesn't let them hinder feature implementation or
   necessary changes. Instead of forcing a rigid process, Agile adapts and
   evolves. (In Waterfall the process is king; in Agile the **people** are king.)
2. **Working software over comprehensive documentation** — Agile does NOT skip
   documentation; it only produces documents that **add real value**. Focus stays
   on delivering functional software. _(This is exactly why in Agile we draw
   "just enough" UML, not a 200-page document nobody reads.)_
3. **Customer collaboration over contract negotiation** — Agile still needs
   contracts (cost/schedule), but prioritizes **partnership and cooperation**.
   Both sides understand requirements might evolve — it requires **trust and
   collaboration**.
4. **Responding to change over following a plan** — The **direct opposite** of
   Waterfall's core assumption. Agile still plans, but doesn't require exhaustive
   details up front; development can proceed without every question answered.

### How Agile fixes Waterfall's problems

| Problem with Waterfall | How Agile solves it |
|---|---|
| Everything planned up front; can't adapt | **Iterative development** — small increments |
| Testing happens late (big-bang) | **Testing integrated into development** continuously |
| Customer sees the product at the end | **Frequent review & feedback** every cycle |
| Developers "throw it over the wall" | **Whole team owns quality** |
| Customer involvement front-loaded only | **Business users involved throughout** |

### The engine of Agile: the Sprint ⚙️

The essence of Agile is **iterative development**, delivering functional software
in **small increments called sprints, typically 2–4 weeks.** At the end of each
sprint the team delivers a **product iteration, improving upon the last.** This
enables frequent review and feedback, keeping the project aligned with
stakeholder needs.

```
   Sprint 1        Sprint 2        Sprint 3        ...
  ┌────────┐     ┌────────┐     ┌────────┐
  │ plan   │     │ plan   │     │ plan   │
  │ build  │ ──▶ │ build  │ ──▶ │ build  │ ──▶ ...  (each loop = a better product)
  │ test   │     │ test   │     │ test   │
  │ review │     │ review │     │ review │
  └────────┘     └────────┘     └────────┘
```

- **Waterfall metaphor:** water flowing down, never back.
- **Agile metaphor:** a **spiral staircase** 🌀 — you keep revisiting the same
  activities (plan, build, test, review) but each loop you're one level higher.

### A crucial distinction 🧠

> **"Agile in itself is not a methodology — it's a *mindset* guided by the
> values and principles of the Agile Manifesto."**

- **Agile** = the philosophy / mindset / values
- **Scrum** and **Kanban** = specific *methodologies* that embody that
  philosophy, offering structured frameworks for implementing its principles.

Agile is the "what we believe"; Scrum/Kanban are the "how we do it day-to-day."

### When Agile shines ✅
Projects with **undefined or evolving requirements**, where uncertainty and
change are expected. The collaboration often leads to higher customer
satisfaction and increased team motivation.

---

## Lecture 5 — Waterfall or Agile? How to Choose

**Big idea:** Each has its rightful place. The choice comes down to one question:
**how much uncertainty is there?**

### The decision rule

- **High uncertainty** / requirements undefined or evolving / client needs to
  refine their vision → **⚡ Agile**
- **Clear view of the final product** / scope is fixed / requirements unlikely
  to change → **🌊 Waterfall**

### Two examples that make it stick

1. **Weapons control system → Waterfall 🌊** — Requirements must be defined
   upfront and remain stable. Changing them mid-project would cause costs to
   skyrocket in an already expensive project. Here Waterfall is "not just
   suitable; it's essential." _(When the cost of change is catastrophic and
   requirements are genuinely known, rigidity is a feature, not a bug.)_
2. **"The next big social media platform for iOS and Android" → Agile ⚡** — The
   scope is "nebulous at best, full of unknowns." Nobody knows what it actually
   is until users tell you. Building it without the flexibility to pivot and
   iterate "would be a recipe for failure." _(When you can't describe the
   destination clearly, you need a process designed to discover it as you go.)_

### The one-line summary

- **Waterfall** → when you have a **clear view of the final product** and the
  **scope is fixed.**
- **Agile** → when dealing with **high uncertainty, evolving requirements**, or
  the client needs the **freedom to refine their vision** as the project unfolds.

---

## 🔗 Tying it all back to UML

This is the payoff of learning project management first: **the methodology shapes
how we apply UML.** When we get to Section 05, we'll already know *why* we draw
diagrams the way we do.

| | Waterfall + UML | Agile + UML |
|---|---|---|
| **When do you draw?** | All diagrams up front, in the Design phase | A little per sprint, revising each cycle |
| **How much?** | Comprehensive & precise (the locked blueprint) | "Just enough" to ship the next slice |
| **Do diagrams change?** | Rarely — frozen after design | Constantly — living documents |
| **Who's involved?** | Stakeholders mainly in Requirements phase | Business users involved throughout, feedback each sprint |
| **Documentation?** | Comprehensive (Agile Value 2 warns against this) | Only what adds real value |

---

## Key takeaways

1. **Methodology comes before tools.** The framework you choose dictates how
   you use UML.
2. **Same UML, different usage.** In Waterfall you draw it all up front; in
   Agile you draw "just enough" and revise.
3. **A process covers the whole project**, not just writing code.
4. **Waterfall = linear, rigid, plan-driven.** Best for stable, well-defined
   requirements (medical, military, life-critical).
5. **Agile = iterative, flexible, change-embracing.** Best for uncertain,
   evolving requirements. It's a *mindset* (Manifesto values); Scrum/Kanban are
   the methodologies that implement it.
6. **Choosing = a question of uncertainty.** Clear scope → Waterfall; fuzzy /
   evolving scope → Agile.

---

## My understanding check 💡

> _"If a friend says 'I'm using Agile so I'll skip design and just start
> coding,' I'd say: Agile being iterative means you can iterate on the design
> too. Draw **just enough** UML to ship something, get feedback, learn, then
> change or enhance the design as you iterate on the product."_
>
> The trap: **Agile ≠ no design. Agile ≠ chaos.** Agile means *iterative*
> design — "flexible" does not mean "no plan at all."
