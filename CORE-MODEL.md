# ADE Core Model

**ADE Human-Machine Framework**

**Document ID:** ADE-CORE
**Document Type:** Foundational Architecture
**Status:** Foundational Draft
**Version:** 0.3.0
**Maintained By:** ADE Human-Machine Framework

---

## 1. Purpose

The ADE Core Model defines the foundational concepts and relationships of the ADE Human-Machine Framework.

Its purpose is to provide a common semantic foundation for representing real-world things, occurrences, actions, conditions, relationships, time, location, and intent in a form that can be understood consistently by both humans and machines.

The Core Model is intentionally small and stable. Specialized ADE frameworks may extend the Core Model without redefining its foundational concepts.

---

## 2. Scope

The ADE Core Model establishes the foundational semantic vocabulary upon which the ADE Human-Machine Framework is built.

It defines:

* Core concepts
* Relationships between those concepts
* Temporal and spatial context
* State and change
* Intent
* Representation of incomplete information

It does not define the complete implementation of specialized ADE frameworks.

---

## 3. Core Design Principles

### 3.1 Human and Machine Understanding

ADE is intended to provide a common semantic structure through which humans and machines can represent and understand information without requiring the meaning to be reinterpreted for each system.

### 3.2 Small and Stable Core

The Core Model should remain limited to concepts that are fundamental across domains.

Domain-specific requirements should normally be implemented through extensions rather than by continually expanding the Core.

### 3.3 No False Precision

ADE should represent what is known without inventing what is unknown.

Incomplete information must remain distinguishable from false, zero, nonexistent, or not applicable information.

### 3.4 Context Matters

Information may depend on Time, Location, State, Relationships, Source, or other contextual conditions.

The Core Model should allow this context to be represented without requiring every contextual property to become a separate Core concept.

---

# 4. Core Concepts

ADE establishes ten foundational concepts.

1. Entity
2. Object
3. Event
4. Action
5. State
6. Attribute
7. Time
8. Location
9. Relationship
10. Intent

These concepts are related but are not necessarily equivalent in architectural role.

---

## 4.1 Entity

An **Entity** is something that can be identified, represented, referenced, or distinguished within an ADE context.

Entities may represent physical, digital, conceptual, organizational, or other subjects.

An Entity may have:

* Attributes
* States
* Relationships
* Locations
* Intent
* Participation in Events

### Specialized Entities

Some entities have more specific semantic roles.

Examples include:

* **Object** — a physical or digital thing
* **Event** — an occurrence or happening

Additional Entity types may be defined by future ADE frameworks.

---

## 4.2 Object

An **Object** is a specialized Entity representing a physical or digital thing that can be identified, described, located, related to other entities, and have changing states.

Examples include:

* Machine
* Vehicle
* Device
* Document
* Digital resource

An Object may participate in Events and Actions.

---

## 4.3 Event

An **Event** is a specialized Entity representing an occurrence, happening, or defined occurrence context.

An Event may:

* Involve Entities
* Contain or reference Actions
* Have Time
* Have Location
* Have Attributes
* Have State or lifecycle information
* Result in State changes
* Be associated with Intent

An Event does not require an Action.

For example, an earthquake may be represented as an Event even though no person performed an Action causing it.

Because an Event is an Entity, it can itself be identified, referenced, related to other Entities, and retained as part of a history.

### Event Lifecycle

An Event may represent different stages of an occurrence, including:

```text
Planned → Active → Completed
             │
             ├── Cancelled
             └── Failed
```

The exact lifecycle states may be defined by specialized ADE frameworks.

A planned Event and an Event that actually occurred must remain semantically distinguishable.

---

## 4.4 Action

An **Action** represents something performed, initiated, or carried out by an Entity.

An Action may:

* Be associated with an Event
* Be performed by an Entity
* Be directed toward an Entity
* Affect an Entity
* Change a State
* Have Intent
* Have Time
* Have Location

Example:

```text
Technician
    ↓
performs
    ↓
Repair Action
    ↓
affects
    ↓
Machine
```

An Action may occur within an Event, but an Event does not necessarily require an Action.

---

## 4.5 State

A **State** represents a condition of an Entity at a particular point or interval of Time.

States may change as a result of Actions or Events.

Example:

```text
Machine
Available
    ↓
Repair
    ↓
Unavailable
    ↓
Repair completed
    ↓
Available
```

The State of an Event and the State of an Entity involved in that Event are distinct.

Example:

```text
Repair Event
State = Cancelled

Machine
State = Available
```

---

## 4.6 Attribute

An **Attribute** represents a characteristic, property, measurement, or descriptive value associated with an Entity.

Examples:

```text
Machine
Model = X100
Weight = 2,500 kg
Temperature = 72°C
```

An Attribute may be contextualized by information such as:

* Time
* Location
* Source
* Measurement conditions

The value of an Attribute may change without changing the identity of the Attribute.

Example:

```text
Temperature
10:00 → 72°C
10:20 → 85°C
```

---

## 4.7 Time

**Time** provides temporal context for Entities, Events, Actions, States, Attributes, and Relationships.

ADE recognizes at least three fundamental temporal constructs.

### Time Point

A specific point in time.

Example:

```text
2026-08-27 10:15:00
```

### Duration

The amount of elapsed time.

Example:

```text
40 minutes
```

### Time Interval

A bounded period between a beginning and an end.

Example:

```text
Start: 10:15
End:   10:55
```

A Duration may be derived from a Time Interval.

ADE should distinguish between:

* Scheduled Time
* Actual Time
* Estimated Time
* Relative Time
* Unknown Time

An exact timestamp must not be invented when only an approximate or relative time is known.

---

## 4.8 Location

**Location** provides spatial context for an Entity, Event, Action, State, or other ADE representation.

Location may be represented at different levels of precision and through different reference systems.

Examples include:

* Address
* Building
* Room
* Geographic coordinates
* Grid reference
* Earth reference
* Planetary reference

The ADE Location Framework (ADE-LF) may define standardized methods for representing and relating these locations.

A Location may be known, approximate, unknown, or otherwise qualified without forcing false precision.

---

## 4.9 Relationship

A **Relationship** defines a meaningful connection between Entities.

Examples:

```text
Person ── employed by ──> Organization

Technician ── performs ──> Repair

Repair ── affects ──> Machine

Event ── occurs at ──> Location
```

Relationships provide the connective structure through which Entities can be understood in relation to one another.

Relationships may themselves have contextual information such as:

* Time
* Location
* State
* Source
* Validity

Detailed relationship structures may be defined by future ADE frameworks.

---

## 4.10 Intent

**Intent** represents the purpose, objective, desired outcome, or reason associated with an Entity, Event, or Action.

Example:

```text
Action: Repair Machine
Intent: Restore machine operation
```

Intent may exist before an Action occurs.

An Intent does not guarantee that the intended Action will occur or that the intended result will be achieved.

Example:

```text
Intent
Purchase Vehicle
      ↓
Purchase Process
      ↓
Cancelled
```

The existence of an Intent therefore remains distinct from the occurrence or completion of an Event.

---

# 5. Core Relationships

The ADE Core Model establishes the following foundational relationships:

1. Entities may participate in Events.
2. Events may contain or reference Actions.
3. Actions may be performed by or involve Entities.
4. Actions may create, modify, or terminate States.
5. Entities may have Attributes.
6. Entities may have States.
7. Events, Actions, States, Attributes, and Relationships may have temporal context.
8. Events and Actions may have spatial context.
9. Entities may be connected through Relationships.
10. Entities, Events, and Actions may be associated with Intent.

These relationships are foundational and may be extended by specialized ADE frameworks.

---

# 6. Incomplete and Unknown Information

ADE must support the representation of incomplete knowledge without requiring false precision.

The following conditions are semantically distinct:

| Condition          | Meaning                                       |
| ------------------ | --------------------------------------------- |
| Known              | A value is known                              |
| Unknown            | A value may exist but is not known            |
| Unavailable        | A value cannot currently be obtained          |
| Not Applicable     | The property does not apply                   |
| Not Yet Determined | The value is expected to be established later |

Example:

```text
Repair Time = Yesterday
Exact Time = Unknown
Location = Unknown
Actor = Unknown
```

Unknown information must not be interpreted as zero, false, nonexistent, or not applicable.

---

# 7. Planned, Actual, and Non-Occurrence

ADE should distinguish between an intended or planned occurrence and an occurrence that actually took place.

For example:

```text
Planned Event
    ↓
Cancelled
```

does not mean that the underlying activity occurred.

Similarly:

```text
Intent
    ↓
Action never initiated
```

must remain distinguishable from an Action that occurred and was later cancelled or reversed.

This distinction is important for accurate machine interpretation.

---

# 8. Reported and Observed Information

ADE may need to distinguish between an occurrence itself and information reported about that occurrence.

For example:

> "The machine was repaired yesterday."

The communication of this statement is itself an occurrence that can be represented, while the claimed repair may have a different evidentiary status.

Future ADE semantic layers may define concepts such as:

* Source
* Assertion
* Evidence
* Confidence
* Certainty
* Provenance

These are intentionally not established as additional Core concepts at this stage.

The Core Model should remain small and stable while allowing these concepts to be developed as higher-level semantic structures.

---

# 9. Core Model Example

A machine repair can be represented conceptually as:

```text
ENTITY
Machine
    │
    │ participates in
    ▼
EVENT
Machine Repair
    │
    ├── ACTION
    │     Repair
    │
    ├── TIME
    │     Start: 10:15
    │     End:   10:55
    │     Duration: 40 minutes
    │
    ├── LOCATION
    │     Maintenance Bay 2
    │
    ├── INTENT
    │     Restore operation
    │
    └── STATE CHANGE
          Available
             ↓
          Unavailable
             ↓
          Available
```

This example is conceptual and does not constitute a complete formal representation.

---

# 10. Relationship Overview

A simplified representation of the ADE Core Model is:

```text
                         ENTITY
                            │
             ┌──────────────┼──────────────┐
             │              │              │
          OBJECT          EVENT          OTHER
                            │
                   ┌────────┼────────┐
                   │        │        │
                ACTION     TIME    LOCATION
                   │
                   ▼
                 STATE
                   │
              STATE CHANGE

ENTITY
  ├── ATTRIBUTE
  ├── STATE
  ├── RELATIONSHIP
  ├── LOCATION
  └── INTENT
```

This diagram is conceptual rather than a complete formal ontology.

---

# 11. Framework Extensions

The ADE Core Model provides the foundation for specialized ADE frameworks.

Examples include:

* **ADE-HTF — Human Timeline Framework**
* **ADE-USLF — Universal Semantic Language Framework**
* **ADE-LF — Location Framework**

Specialized frameworks may extend the Core Model but should not redefine its foundational meaning without an established governance process.

---

# 12. Future Semantic Layers

The Core Model intentionally does not attempt to define every possible aspect of information representation.

Potential higher-level semantic layers may address:

* Source
* Assertion
* Evidence
* Provenance
* Confidence
* Certainty
* Validation
* Context
* Authorization
* Identity

These should be evaluated separately so that the foundational Core remains stable and understandable.

---

# 13. Foundational Principle

> **ADE represents what is known without inventing what is unknown.**

The Core Model is designed to support human-to-machine understanding by providing a common semantic foundation for representing what exists, what occurs, what is done, what changes, when and where something occurs, how entities are connected, and why an action or occurrence is associated with a purpose.

The Core Model is intended to serve as the foundational semantic layer upon which the broader ADE Human-Machine Framework can be developed.
