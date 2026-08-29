# ADE Human-Machine Framework

## ADE-Core Relationships

**Status:** Foundational Draft
**Repository:** ADE-Core
**Version:** 0.2.0

---

## 1. Purpose

This document defines how relationships between ADE concepts are represented and interpreted within the ADE Human-Machine Framework.

Relationships provide the structural connections through which Entities, Objects, Events, Actions, States, Attributes, Identity, Source, Time, Location, Authority, Authorization, and Intent can be understood in context.

The purpose of this document is to establish a consistent foundation for representing relationships across human, machine, and system environments.

---

## 2. Scope

ADE-Core defines relationships at the foundational semantic level.

This document establishes:

* The nature of ADE relationships
* Directionality
* Relationship meaning
* Inverse relationships
* Core relationship patterns
* Context associated with relationships
* Relationship lifecycle and validity
* Relationships involving identity, source, authority, and authorization
* Extensibility for specialized ADE frameworks

Domain-specific relationships may be defined by specialized ADE frameworks while remaining compatible with ADE-Core.

---

## 3. Relationship Principle

A Relationship represents a meaningful semantic connection between two or more ADE concepts.

The relationship itself carries semantic meaning.

For example:

```text
Technician ── performs ──> Repair
```

is semantically different from:

```text
Technician ── assigned to ──> Repair
```

or:

```text
Technician ── supervises ──> Repair
```

Although the same Entities may be involved, the Relationship determines how those Entities are understood in relation to one another.

---

## 4. Directional Relationships

ADE-Core defines Relationships as **directional**.

A directional Relationship identifies:

* A source concept
* A relationship meaning
* A target concept

Conceptually:

```text
Source Entity
     │
     │ Relationship
     ▼
Target Entity
```

Example:

```text
Technician
    │
    │ performs
    ▼
Repair
```

Direction provides a consistent structure for machine interpretation while remaining understandable to humans.

---

## 5. Inverse Relationships

A Relationship may have an inverse perspective.

For example:

```text
Technician ── performs ──> Repair
```

may be expressed from the opposite perspective as:

```text
Repair ── performed by ──> Technician
```

The inverse should represent the same underlying semantic relationship rather than being treated as an unrelated relationship.

Where appropriate, inverse relationships may be derived rather than independently stored.

This reduces the possibility of contradictory relationship information.

---

# 6. Core Relationship Patterns

ADE-Core establishes several fundamental relationship patterns.

### 6.1 Entity to Entity

Entities may be related directly.

```text
Person ── knows ──> Person
```

```text
Organization ── owns ──> Vehicle
```

---

### 6.2 Entity to Object

An Entity may have a relationship with an Object.

```text
Person ── owns ──> Vehicle
```

```text
Organization ── operates ──> Machine
```

---

### 6.3 Entity to Identity

An Entity may be associated with one or more Identities.

```text
Person
   │
   └── has identity ──> Identity
```

An Identity provides a reference to an Entity but does not by itself establish that the Entity has been authenticated or authorized.

---

### 6.4 Entity to Event

An Entity may participate in an Event.

```text
Person ── participates in ──> Meeting
```

```text
Machine ── participates in ──> Repair Event
```

Participation may be further qualified by specialized frameworks.

---

### 6.5 Entity to Action

An Entity may perform, initiate, authorize, receive, or otherwise participate in an Action.

```text
Technician ── performs ──> Repair Action
```

```text
Manager ── authorizes ──> Repair Action
```

Authorization should remain distinguishable from the underlying relationship between an Entity and an Action.

---

### 6.6 Action to Entity

An Action may affect, modify, create, or otherwise act upon an Entity.

```text
Repair Action ── affects ──> Machine
```

```text
Update Action ── modifies ──> Document
```

---

### 6.7 Event to Action

An Event may contain or reference one or more Actions.

```text
Repair Event
     │
     └── contains ──> Repair Action
```

An Event does not require an Action.

Some Events may occur without a performed Action.

---

### 6.8 Entity to State

An Entity may have a State.

```text
Machine ── has state ──> Available
```

State is understood in relation to Time and may change as a result of Events or Actions.

---

### 6.9 Entity to Attribute

An Entity may have Attributes.

```text
Machine ── has attribute ──> Temperature
```

The Attribute value may change over Time without changing the identity of the Entity.

---

### 6.10 Event to Time

An Event may have temporal context.

```text
Repair Event
    │
    └── occurs during ──> Time Interval
```

An Event may also have:

* Planned Time
* Actual Time
* Estimated Time
* Relative Time

---

### 6.11 Event to Location

An Event may have spatial context.

```text
Repair Event
    │
    └── occurs at ──> Maintenance Bay
```

---

### 6.12 Entity to Location

An Entity may have a Location at a particular point or interval in Time.

```text
Machine ── located at ──> Maintenance Bay
```

The Location of an Entity may change over Time.

---

### 6.13 Entity, Event, or Action to Intent

An Entity, Event, or Action may be associated with an Intent.

```text
Repair Action
    │
    └── intended to ──> Restore Machine Operation
```

Intent does not guarantee that an Action will occur or that its intended result will be achieved.

---

### 6.14 Source to Assertion

A Source may provide or originate an Assertion.

```text
Maintenance System
       │
       └── provides ──> Assertion
```

The Source and Assertion remain distinct concepts.

A Source may provide multiple Assertions about the same or different subjects.

---

### 6.15 Assertion to Subject

An Assertion may describe or refer to an Entity, Event, Action, State, Attribute, Relationship, or other ADE concept.

```text
Assertion
    │
    └── refers to ──> Machine
```

The existence of an Assertion does not by itself establish that the information asserted is true.

---

### 6.16 Assertion to Confidence and Provenance

An Assertion may have associated Confidence and Provenance.

```text
Assertion
    ├── has confidence ──> High
    │
    └── has provenance ──> Source / History
```

Confidence represents a qualified assessment associated with the information.

Provenance describes its origin or history.

Neither concept independently establishes truth.

---

### 6.17 Identity to Authentication

An Identity may be associated with an Authentication process.

```text
Identity
    │
    └── authenticated through ──> Authentication
```

Authentication establishes that an actor can demonstrate control of, or association with, an Identity.

Authentication does not itself establish Authorization.

---

### 6.18 Entity to Authority

An Entity may possess or be associated with Authority within a defined context.

```text
Human
   │
   └── has authority ──> Authority Level 3
```

Authority may be established through a Relationship, organizational role, legal or regulatory designation, delegation, or other recognized mechanism.

Authority may be contextual, time-limited, or otherwise qualified.

---

### 6.19 Authority to Capability

An Authority may provide one or more Capabilities.

```text
Authority Level 3
       │
       └── provides ──> Capability: Pause Machine
```

A Capability represents an Action or class of Actions that an Authority permits an Entity or actor to perform within a defined context.

---

### 6.20 Authorization to Action

Authorization determines whether an Entity or actor is permitted to perform a specific Action within a defined context.

```text
Identity
    │
Authentication
    │
Authority
    │
Capability
    │
Authorization
    │
    ▼
Action
```

Authorization may depend upon:

* Identity
* Authentication
* Authority
* Capability
* Time
* Location
* Relationship
* Intent
* State
* Applicable rules
* Emergency conditions

Authorization should remain distinct from Authentication.

---

# 7. Relationships and State

Relationships may describe State changes.

Example:

```text
Machine
Available
    │
    │ affected by
    ▼
Repair Action
    │
    ▼
Unavailable
```

The Action and resulting State change should remain distinguishable.

A Relationship describing an Action affecting an Entity does not itself become the State.

---

# 8. Relationships and Time

Relationships may have temporal context.

A relationship may:

* Begin at a particular Time
* End at a particular Time
* Exist for a Duration
* Apply during a Time Interval
* Be planned for a future Time
* Have an unknown temporal boundary

Example:

```text
Person ── employed by ──> Organization

Valid From: 2024-01-01
Valid Until: 2026-06-30
```

The same Entities may have different relationships at different times.

---

# 9. Relationships and Location

Relationships may also have spatial context.

Example:

```text
Technician ── performs ──> Repair
```

may occur:

```text
Location → Maintenance Bay 2
```

Spatial context may be exact, approximate, unknown, or otherwise qualified.

ADE should not require false precision.

---

# 10. Relationship Attributes

A Relationship may require additional descriptive information.

For example:

```text
Person ── employed by ──> Organization
```

may have:

```text
Role = Engineer
Start Date = 2024-01-01
End Date = Unknown
Status = Active
```

These properties describe the relationship and should not necessarily be interpreted as Attributes of either Entity.

---

# 11. Relationship State and Validity

A Relationship may have a lifecycle or validity condition.

For example:

```text
Employment Relationship
    │
    ├── Planned
    ├── Active
    └── Ended
```

A Relationship that has ended remains distinguishable from a Relationship that never existed.

Historical relationships may therefore be retained as part of an Entity's history.

---

# 12. Unknown and Incomplete Relationships

ADE must support relationships where some information is unknown or incomplete.

For example:

```text
Machine ── repaired by ──> Unknown
```

means that the repair relationship is known but the identity of the actor is unknown.

This is different from:

```text
Machine ── repaired by ──> Not Applicable
```

or:

```text
Machine ── repaired by ──> None
```

Unknown information must not be interpreted as false, zero, nonexistent, or not applicable.

The same principle applies to Identity, Source, Authority, Authorization, and other relationship context.

---

# 13. Relationships and Reported Information

A Relationship may be reported rather than directly observed.

Example:

> "The technician repaired the machine."

The communication of this statement is distinct from the underlying repair relationship.

Conceptually:

```text
Communication Event
       │
       └── reports ──> Assertion
                            │
                            └── refers to ──> Repair Event

Technician
       │
       └── performed ──> Repair
```

The Assertion may therefore carry additional contextual information concerning:

* Source
* Evidence
* Confidence
* Provenance
* Verification status

The Assertion remains distinct from the underlying Event or Relationship it describes.

---

# 14. Semantic Independence from Natural Language

ADE Relationships represent semantic connections independently from the natural language used to express them.

For example, the relationship:

```text
Technician ── performs ──> Repair
```

may be expressed in different human languages while preserving the same underlying semantic relationship.

The human-readable expression may therefore vary while the ADE semantic structure remains consistent.

Conceptually:

```text
French
    ↓
Human / System Interpretation
    ↓
ADE Semantic Relationship
    ↑
Human / System Interpretation
    ↑
English
```

ADE does not require all participants or systems to use the same natural language.

The Core Model instead establishes a common semantic structure that can be represented and interpreted by different human and machine environments.

---

# 15. Relationship Consistency

A relationship should have one defined semantic meaning within a given ADE context.

For example:

```text
performs
```

should not mean "owns" in one context and "supervises" in another.

Where a different meaning is required, a distinct relationship should be defined.

This supports predictable interpretation by both humans and machines.

---

# 16. Relationship Extensibility

Specialized ADE frameworks may define additional relationship types.

For example:

```text
ADE-HTF
├── temporal relationships

ADE-USLF
├── semantic relationships

ADE-LF
├── spatial relationships
```

Specialized relationships should:

1. Remain compatible with ADE-Core concepts.
2. Preserve directional semantics.
3. Have clearly defined meanings.
4. Avoid redefining established ADE-Core relationships.
5. Support derivation of inverse relationships where appropriate.

---

# 17. Core Relationship Model

A simplified conceptual representation is:

```text
                         ENTITY
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
          ▼                 ▼                 ▼
       IDENTITY          OBJECT            EVENT
          │                 │                 │
          ▼                 │            ┌────┴────┐
   AUTHENTICATION            │            ▼         ▼
          │                  │         ACTION      TIME
          ▼                  │            │
      AUTHORITY              │            ▼
          │                  │          STATE
          ▼                  │
     CAPABILITY              │
          │                  │
          ▼                  │
    AUTHORIZATION ───────────┘
          │
          ▼
        ACTION


ENTITY ── has ──> ATTRIBUTE
ENTITY ── located at ──> LOCATION
ENTITY ── related to ──> ENTITY
ENTITY ── associated with ──> INTENT

SOURCE ── provides ──> ASSERTION
ASSERTION ── refers to ──> ADE CONCEPT
ASSERTION ── has ──> CONFIDENCE
ASSERTION ── has ──> PROVENANCE
```

This diagram is conceptual and does not constitute a complete formal ontology.

---

# 18. Foundational Principle

> **Relationships carry meaning between ADE concepts.**

ADE-Core uses directional relationships to provide a consistent semantic structure through which humans and machines can interpret how ADE concepts are connected.

The underlying semantic relationship should remain independent of the natural language or system-specific representation used to express it.

---

# 19. Future Development

Future ADE specifications may define:

* Formal relationship identifiers
* Relationship vocabularies
* Relationship constraints
* Inverse relationship rules
* Relationship cardinality
* Relationship validation
* Relationship inheritance
* Temporal relationship models
* Spatial relationship models
* Advanced provenance and evidence models
* Domain-specific authorization and capability models

These mechanisms should extend the ADE-Core relationship model without unnecessarily redefining its foundational principles.
