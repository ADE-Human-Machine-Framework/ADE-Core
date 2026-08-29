# ADE Human-Machine Framework

## ADE-Core Core Model

**Status:** Foundational Draft
**Repository:** ADE-Core
**Version:** 0.4.0

---

## 1. Purpose

The ADE Core Model defines the foundational concepts and relationships of the ADE Human-Machine Framework.

Its purpose is to provide a common semantic foundation for representing real-world things, occurrences, actions, conditions, relationships, time, location, identity, authority, information, and intent in a form that can be understood consistently by both humans and machines.

The Core Model is intentionally small and stable. Specialized ADE frameworks may extend the Core Model without redefining its foundational concepts.

---

## 2. Scope

The ADE Core Model establishes the foundational semantic vocabulary upon which the ADE Human-Machine Framework is built.

It defines:

* Core concepts
* Relationships between those concepts
* Temporal and spatial context
* State and change
* Identity and entity reference
* Source and information provenance
* Authority, capability, and authorization
* Intent
* Representation of incomplete information

It does not define the complete implementation of specialized ADE frameworks.

---

# 3. Core Design Principles

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

### 3.5 Separation of Identity, Authentication, Authority, and Authorization

Identity, authentication, authority, capability, and authorization are distinct concepts and should not be conflated.

An entity may be identified without being authenticated, authenticated without possessing authority for a particular action, or authorized for one action while not being authorized for another.

---

# 4. Core Concepts

ADE establishes foundational concepts across several related areas.

### Entity and Identity

1. Entity
2. Identity

### Occurrence and Change

3. Object
4. Event
5. Action
6. State
7. Attribute

### Context

8. Source
9. Time
10. Location
11. Relationship
12. Intent

### Information and Provenance

13. Assertion
14. Provenance
15. Confidence

### Authority and Control

16. Authentication
17. Authority
18. Capability
19. Authorization

These concepts are related but are not necessarily equivalent in architectural role.

The Core Model establishes the foundational meaning and relationships of these concepts. Specialized ADE frameworks may extend them for particular domains without redefining their foundational meaning.

---

## 4.1 Entity

An **Entity** is something that can be identified, represented, referenced, or distinguished within an ADE context.

Entities may represent physical, digital, conceptual, organizational, or other subjects.

Entities may include:

* Humans
* Organizations
* Devices
* Machines
* Software agents
* Systems
* Documents
* Other physical, digital, or conceptual subjects

An Entity may have:

* Identity
* Attributes
* States
* Relationships
* Locations
* Intent
* Participation in Events
* Authority or capabilities where applicable

### Specialized Entities

Some ADE concepts have more specific Entity roles.

Within ADE-Core:

* **Object** — a specialized Entity representing a physical or digital thing.
* **Event** — a specialized Entity representing an occurrence or happening.

The remaining ADE-Core concepts are not automatically treated as specialized Entity types. They provide additional semantic structures, properties, context, or relationships that may apply to Entities and to one another.

Additional specialized Entity types may be defined by future ADE frameworks.

---

## 4.2 Identity

An **Identity** provides a persistent reference to a specific Entity within an ADE context.

An Identity does not necessarily contain all information about the Entity. It provides a means by which the Entity can be distinguished, referenced, or associated with information held by authorized sources.

An Entity may have one or more identities or identifiers depending on the context in which it is represented.

Identity should remain distinct from:

* **Authentication** — establishing that an actor can demonstrate control of an Identity.
* **Authority** — the standing or level of control associated with an Entity or actor.
* **Capability** — an action or function that an authority permits.
* **Authorization** — determining whether an Entity or actor is permitted to perform a specific action.

An Identity may be associated with information held by independent authoritative Sources without requiring ADE to duplicate or centrally store that information.

For example:

```text
Entity
   │
   └── Identity
         │
         ├── Canadian Source
         │     └── Citizenship information
         │
         └── South African Source
               └── Citizenship information
```

The existence of an Identity does not by itself establish the truth of every Assertion associated with that Identity.

Identity therefore provides a reference to an Entity while allowing associated information, verification, authority, and authorization to remain distinct concepts.

---

## 4.3 Object

An **Object** is a specialized Entity representing a physical or digital thing that can be identified, described, located, related to other entities, and have changing states.

Examples include:

* Machine
* Vehicle
* Device
* Document
* Digital resource

An Object may participate in Events and Actions.

---

## 4.4 Event

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

## 4.5 Action

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
* Be subject to Authorization

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

## 4.6 State

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

## 4.7 Attribute

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

The value of an Attribute may change without changing the identity of the Attribute.

Example:

```text
Temperature
10:00 → 72°C
10:20 → 85°C
```

---

## 4.8 Source

A **Source** identifies the origin from which information, an Assertion, observation, measurement, instruction, or other representation is obtained.

A Source may be an Entity, including:

* Human
* Organization
* Device
* Software Agent
* System
* Other recognized information source

A Source does not necessarily transfer ownership or control of the information it provides.

Information may remain under the control of its authoritative Source while ADE provides a standardized means of identifying, referencing, and obtaining the information required for an authorized purpose.

Different Sources may provide different Assertions about the same Entity or subject.

A Source should therefore remain distinguishable from the information or Assertion it provides.

Source information may be associated with:

* Time
* Location
* Entity
* Relationship
* Assertion
* Provenance
* Confidence
* Verification status

The Core Model does not require information from all Sources to be centralized or duplicated within ADE.

A Source may be authoritative for one type of information while another Source may be authoritative for a different type of information.

The determination of authoritative status and the technical mechanisms for accessing a Source may be defined by applicable ADE standards or external governing authorities.

---

## 4.9 Time

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

## 4.10 Location

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

## 4.11 Relationship

A **Relationship** defines a meaningful semantic connection between ADE concepts.

Examples:

```text
Person ── employed by ──> Organization

Technician ── performs ──> Repair

Repair ── affects ──> Machine

Event ── occurs at ──> Location

Parent ── guardian of ──> Child

Organization ── operates ──> Machine
```

Relationships provide the connective structure through which Entities can be understood in relation to one another.

Relationships may themselves have contextual information such as:

* Time
* Location
* State
* Source
* Validity
* Authority

Detailed relationship structures may be defined by future ADE frameworks.

---

## 4.12 Intent

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

## 4.13 Assertion

An **Assertion** represents a statement, claim, observation, measurement, or other expressed information associated with a Source.

An Assertion may describe or refer to an Entity, Event, Action, State, Attribute, Relationship, or other ADE concept.

For example:

```text
Source:
Maintenance System

Assertion:
Machine X100 was repaired.

Time:
2026-08-27
```

An Assertion should remain distinguishable from the subject being described.

The existence of an Assertion does not by itself establish that the asserted information is true.

Assertions may be associated with:

* Source
* Time
* Location
* Entity
* Evidence
* Confidence
* Provenance
* Verification status

Different Sources may make different Assertions about the same subject.

---

## 4.14 Provenance

**Provenance** describes the origin, history, or chain of association through which information, an Assertion, or an Action can be traced.

Provenance may identify:

* Source
* Originating Entity
* Time
* Location
* Related Actions
* Transformations or processing
* Previous Assertions
* Verification or authorization context

Provenance supports the ability to determine where information came from and how it came to be represented.

ADE does not require every implementation to maintain the same level of provenance detail. Applicable standards may define additional provenance requirements for particular domains.

---

## 4.15 Confidence

**Confidence** represents a qualified assessment of the reliability or certainty associated with an Assertion, observation, measurement, or other information.

Confidence should remain distinct from the identity or type of the Source.

For example:

```text
Source = Device
Confidence = High
```

and:

```text
Source = Human
Confidence = Low
```

may both be valid representations.

Confidence does not by itself establish truth. The method used to determine or calculate confidence may be defined by applicable ADE standards or domain-specific requirements.

---

## 4.16 Authentication

**Authentication** represents the process of establishing that an actor can demonstrate control of, or association with, an Identity.

Authentication is distinct from Identity.

Authentication may use one or more mechanisms, including:

* Knowledge factors
* Possession factors
* Biometric factors
* Cryptographic credentials
* Physical credentials
* Other recognized authentication mechanisms

Authentication does not by itself establish that an actor is authorized to perform a particular Action.

For example:

```text
Identity
    ↓
Authentication
    ↓
Authority
    ↓
Authorization
    ↓
Action
```

The specific technical mechanisms used for authentication may be defined by applicable ADE standards or external systems.

---

## 4.17 Authority

**Authority** represents the recognized standing, role, or level of control that an Entity or actor possesses within a defined context.

Authority may be established through:

* A Relationship
* An organizational role
* A legal or regulatory designation
* A delegated permission
* Other recognized mechanisms

Authority does not automatically grant permission to perform every Action.

For example:

```text
Human
Authority Level = 3
```

may indicate a recognized safety authority while still limiting the Actions that the Human may perform.

Authority may be contextual, time-limited, delegated, or otherwise qualified.

---

## 4.18 Capability

A **Capability** represents an Action or class of Actions that an Authority permits an Entity or actor to perform within a defined context.

For example:

```text
Authority Level 3

Capabilities:
    Pause Machine = Yes
    Cancel Mission = No
    Modify Mission = No
```

Capabilities may be constrained by:

* Time
* Location
* Relationship
* Purpose
* State
* Emergency conditions
* Other applicable rules

Capability therefore provides a distinction between the standing of an Entity and the specific functions that standing enables.

---

## 4.19 Authorization

**Authorization** represents the determination that an Entity or actor is permitted to perform a specific Action within a defined context.

Authorization may consider:

* Identity
* Authentication
* Relationship
* Authority
* Capability
* Time
* Location
* Purpose or Intent
* State
* Applicable rules
* Emergency conditions

For example:

```text
Authenticated Actor
        +
Authority Level 3
        +
Capability = Pause Machine
        +
Safety Condition
        ↓
Authorization
        ↓
PAUSE
```

Authorization should remain distinct from authentication.

Authentication establishes that an actor can demonstrate control of an Identity. Authorization determines whether that actor is permitted to perform the requested Action.

Authorization may also support collective or conditional authority.

For example:

```text
Human Level 3
       +
Human Level 3
       +
Human Level 3
       ↓
Emergency Rule
       ↓
Authorization to Pause
```

The specific authority levels, capabilities, thresholds, and emergency rules may be defined by applicable ADE standards or domain-specific requirements.

---

# 5. Core Relationships

The ADE Core Model establishes the following foundational relationships:

1. Entities may participate in Events.
2. Events may contain or reference Actions.
3. Actions may be performed by or involve Entities.
4. Actions may create, modify, or terminate States.
5. Entities may have Attributes.
6. Entities may have States.
7. Entities may have one or more Identities or identifiers.
8. Events, Actions, States, Attributes, and Relationships may have temporal context.
9. Events and Actions may have spatial context.
10. Entities may be connected through Relationships.
11. Entities, Events, and Actions may be associated with Intent.
12. Assertions may be associated with Sources.
13. Assertions may describe or refer to Entities, Events, Actions, States, Attributes, or Relationships.
14. Assertions may have Confidence and Provenance.
15. Sources may provide information about Entities and other ADE concepts.
16. Authentication may establish control of or association with an Identity.
17. Authority may be associated with an Entity through a Relationship or other recognized mechanism.
18. Authority may provide one or more Capabilities.
19. Authorization may determine whether a specific Action is permitted.
20. Authorized Actions may be performed by Entities, including Humans, Machines, Devices, Software Agents, and Systems where applicable.

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

ADE distinguishes between an occurrence itself and information reported about that occurrence.

For example:

> "The machine was repaired yesterday."

The communication of this statement is itself an occurrence that can be represented, while the claimed repair may have a different evidentiary or verification status.

The Core Model represents the foundational distinction between:

```text
Source
   ↓
Assertion
   ↓
Subject of Assertion
```

Assertions may be associated with:

* Evidence
* Confidence
* Provenance
* Verification status

Evidence, Certainty, and Validation are not fully defined as independent Core concepts at this stage and may be developed through higher-level semantic structures or specialized ADE frameworks.

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
    ├── SOURCE
    │     Maintenance System
    │
    ├── ASSERTION
    │     Repair completed
    │
    ├── CONFIDENCE
    │     High
    │
    └── STATE CHANGE
          Available
             ↓
          Unavailable
             ↓
          Available
```

An authorized machine operation may additionally be represented conceptually as:

```text
ENTITY
Human Operator
    │
    ├── IDENTITY
    │
    ├── AUTHENTICATION
    │
    ├── AUTHORITY
    │
    └── CAPABILITY
          │
          ▼
    AUTHORIZATION
          │
          ▼
       ACTION
          │
          ▼
      MACHINE
```

These examples are conceptual and do not constitute complete formal representations.

---

# 10. Relationship Overview

A simplified representation of the ADE Core Model is:

```text
                    ADE CORE CONCEPTS

                         ENTITY
                           │
              ┌────────────┴────────────┐
              │                         │
           IDENTITY                 RELATIONSHIP
              │                         │
       AUTHENTICATION              connects Entities
              │
          AUTHORITY
              │
         CAPABILITY
              │
       AUTHORIZATION
              │
            ACTION
              │
              ├────────── affects ──────────> ENTITY
              │
              └──────── performed by ──────> ENTITY


    ENTITY
       ├── OBJECT
       ├── ATTRIBUTE
       ├── LOCATION
       ├── RELATIONSHIP
       └── INTENT


    EVENT
       ├── ACTION
       ├── TIME
       ├── LOCATION
       ├── STATE
       ├── SOURCE
       ├── ASSERTION
       └── INTENT


    SOURCE
       │
       ▼
    ASSERTION
       │
       ├── CONFIDENCE
       └── PROVENANCE


    TIME
       ├── TIME POINT
       ├── DURATION
       └── TIME INTERVAL
```

This diagram is conceptual and does not constitute a complete formal ontology.

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

* Evidence
* Certainty
* Validation
* Domain-specific verification
* Advanced provenance
* Advanced confidence models
* Specialized authorization models
* Other concepts identified through standards development

These should be evaluated separately so that the foundational Core remains stable and understandable.

---

# 13. Foundational Principle

> **ADE represents what is known without inventing what is unknown.**

The Core Model is designed to support human-to-machine understanding by providing a common semantic foundation for representing what exists, what occurs, what is done, what changes, who or what is involved, how entities are identified and related, where information comes from, how authority and authorization apply, when and where something occurs, and why an action or occurrence is associated with a purpose.

The Core Model is intended to serve as the foundational semantic layer upon which the broader ADE Human-Machine Framework can be developed.
