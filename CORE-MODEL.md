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

16. Authority
17. Ability
18. Authorization

These concepts are related but are not necessarily equivalent in architectural role.

The Core Model establishes the foundational meaning and relationships of these concepts. Specialized ADE frameworks may extend them for particular domains without redefining their foundational meaning.

Identity and Authority are foundational ADE-Core concepts that may be specialized by ADE-IF and other ADE frameworks.

Authentication is not defined as an independent ADE-Core concept. Detailed authentication architecture is provided by ADE-IF.

Ability represents what an Entity can do and is distinct from Permission, which represents what an Entity is permitted to do.

Authorization provides the foundational semantic determination of whether an Action is permitted within a defined context. Specialized authorization mechanisms may be defined by ADE-IF and other ADE frameworks.


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

An Identity does not necessarily contain all information about the Entity. It provides a means by which the Entity can be distinguished, referenced, or associated with information held by authorized Sources.

An Entity may have one or more identities or identifiers depending on the context in which it is represented.

Identity is a foundational ADE-Core concept and should remain distinct from specialized identity mechanisms defined by ADE-IF or other ADE frameworks.

Identity should remain distinct from:

* **Authentication** — establishing that an actor can demonstrate control of, or association with, an Identity.
* **Authority** — the recognized standing, responsibility, or level of control associated with an Entity within a defined context.
* **Ability** — what an Entity can do.
* **Authorization** — determining whether an Entity or actor is permitted to perform a specific Action within a defined context.

ADE-Core defines the general semantic meaning of Identity. ADE-IF may extend this foundation with specialized identity architecture, including credentials, identity claims, identity verification, authentication, identity federation, and identity-related authority.

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

Detailed identity-management and identity-assurance mechanisms are outside the scope of ADE-Core and may be defined by ADE-IF or other specialized ADE frameworks.

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

Authentication is **not defined as an independent foundational concept within ADE-Core**.

Authentication establishes that an actor can demonstrate control of, or association with, an Identity. It is therefore distinct from Identity and from Authorization.

The foundational distinction is:

```text
Identity
    ↓
may be subject to
    ↓
Authentication
```

ADE-Core recognizes Authentication as a concept that may be required when establishing identity assurance, but does not define authentication methods, credentials, protocols, assurance levels, or security mechanisms.

Detailed Authentication architecture is defined by **ADE-IF — Identity Framework** and may include:

* Authentication methods
* Credentials
* Cryptographic proofs
* Possession factors
* Knowledge factors
* Biometric factors
* Authentication assurance
* Identity verification mechanisms
* Authentication status

Authentication does not by itself establish that an actor is authorized to perform a particular Action.

The distinction is therefore:

```text
Identity
    ↓
Authentication
    ↓
Authorization
    ↓
Action
```

The specific technical mechanisms used for Authentication are outside the scope of ADE-Core.

---

## 4.17 Authority

**Authority** represents the recognized standing, responsibility, role, jurisdiction, or level of control that an Entity possesses within a defined context.

Authority may be established through:

* A Relationship
* An organizational role
* A legal or regulatory designation
* A delegated responsibility
* A recognized operational role
* Other recognized mechanisms

Authority is contextual and does not automatically grant permission to perform every Action.

For example:

```text
Entity
    ↓
Authority
    ↓
Recognized responsibility
```

An Entity may possess Authority without being authorized to perform a particular Action.

For example:

```text
Authority
    ↓
Safety Officer
    ↓
Recognized responsibility
```

does not necessarily mean:

```text
Safety Officer
    ↓
Authorized
    ↓
Every possible Action
```

Authority may be:

* Contextual
* Time-limited
* Delegated
* Conditional
* Restricted by Location
* Restricted by State
* Associated with a Relationship

ADE-Core defines the general semantic meaning of Authority.

ADE-IF may specialize Authority for identity-related purposes, including:

* Identity authorities
* Credential authorities
* Identity registration authorities
* Identity verification authorities
* Delegated identity authority
* Authority associated with identity claims

Authority should remain distinct from:

* **Identity** — the reference by which an Entity may be distinguished or represented.
* **Authentication** — establishing control of, or association with, an Identity.
* **Ability** — what an Entity can do.
* **Permission** — what an Entity is permitted to do.
* **Authorization** — determining whether a specific Action is permitted within a defined context.

Authority therefore represents recognized standing, responsibility, or control rather than the permission to perform every possible Action.

---

## 4.18 Ability

**Ability** represents what an Entity can do, perform, support, or otherwise accomplish within a defined context.

Ability describes capability in the general semantic sense and does not by itself establish that an Entity is permitted to perform an Action.

Examples include:

```text
Human
Ability:
Lift 50 kg
```

```text
Machine
Ability:
Lift 5,000 kg
```

```text
Software Agent
Ability:
Process Images
```

An Ability may be constrained or qualified by:

* State
* Time
* Location
* Resources
* Conditions
* Other applicable context

Ability should remain distinct from:

* **Authority** — the recognized standing, responsibility, role, jurisdiction, or control associated with an Entity.
* **Permission** — what an Entity is permitted to do.
* **Authorization** — the determination that a specific Action is permitted within a defined context.

For example:

```text
Machine
    │
    ├── Ability
    │     └── Lift 5,000 kg
    │
    └── Permission
          └── Lift 2,000 kg loads
```

An Entity may therefore have an Ability without having Permission to exercise that Ability in a particular context.

Detailed Permission and identity- or access-related Capability models may be defined by ADE-IF or other specialized ADE frameworks.

ADE-Core uses Ability to describe what an Entity can do without implying that the Entity is authorized or permitted to perform the corresponding Action.

---

## 4.19 Authorization

**Authorization** represents the determination that an Entity or actor is permitted or denied to perform a specific Action within a defined context.

Authorization is a foundational semantic concept and is distinct from Identity, Authentication, Authority, Ability, and Permission.

The general authorization pattern is:

```text
Subject
    +
Requested Action
    +
Context
    +
Applicable Rules
    ↓
Authorization Decision
    ↓
Permitted / Denied
```

Authorization may consider:

* Identity
* Authentication
* Authority
* Ability
* Permission
* Time
* Location
* State
* Relationship
* Intent or Purpose
* Applicable rules
* Emergency conditions
* Other defined context

Authorization does not mean that an Action actually occurred.

For example:

```text
Authorization
    ↓
Permitted
    ↓
Action never performed
```

is distinct from:

```text
Authorization
    ↓
Permitted
    ↓
Action performed
```

Similarly:

```text
Authorization
    ↓
Denied
    ↓
Action attempted
```

may represent an attempted Action that was not authorized.

ADE-Core defines the general semantic meaning of Authorization as a contextual determination concerning whether an Action is permitted or denied.

ADE-IF may specialize Authorization for identity and access-control purposes, including:

* Identity-based authorization
* Authentication-dependent authorization
* Permission evaluation
* Access-control policies
* Credential-based authorization
* Delegated authorization
* Identity-related authorization rules

Authorization should remain distinct from:

* **Identity** — the reference by which an Entity may be distinguished or represented.
* **Authentication** — establishing control of, or association with, an Identity.
* **Authority** — recognized standing, responsibility, role, jurisdiction, or control.
* **Ability** — what an Entity can do.
* **Permission** — what an Entity is permitted to do.
* **Action** — something performed, initiated, or carried out by an Entity.

The specific mechanisms used to evaluate or enforce Authorization are outside the scope of ADE-Core unless explicitly defined by a future Core standard.

---

# 5. Core Relationships

The ADE Core Model establishes foundational relationships between ADE concepts.

These relationships describe general semantic connections and do not prescribe a specific technical implementation.

1. Entities may participate in Events.
2. Events may contain or reference Actions.
3. Actions may be performed by or involve Entities.
4. Actions may create, modify, or terminate States.
5. Entities may have Attributes.
6. Entities may have States.
7. Entities may have one or more Identities or identifiers.
8. Entities may possess Authority within a defined context.
9. Entities may have Abilities that describe what they can do.
10. Events, Actions, States, Attributes, and Relationships may have temporal context.
11. Events and Actions may have spatial context.
12. Entities may be connected through Relationships.
13. Entities, Events, and Actions may be associated with Intent.
14. Assertions may be associated with Sources.
15. Assertions may describe or refer to Entities, Events, Actions, States, Attributes, or Relationships.
16. Assertions may have Confidence and Provenance.
17. Sources may provide information about Entities and other ADE concepts.
18. Authentication may establish control of or association with an Identity.
19. Authority may be associated with an Entity through a Relationship or other recognized mechanism.
20. Authorization may determine whether a specific Action is permitted or denied within a defined context.
21. Authorized Actions may be performed by Entities, including Humans, Machines, Devices, Software Agents, and Systems where applicable.
22. Specialized ADE frameworks may extend these relationships without redefining their foundational Core meaning.

The following conceptual relationships summarize important distinctions within the Core Model:

```text
ENTITY
   │
   ├── IDENTITY
   │
   ├── AUTHORITY
   │
   ├── ABILITY
   │
   ├── ATTRIBUTE
   │
   ├── STATE
   │
   └── RELATIONSHIP


IDENTITY
   │
   └── may be subject to
          │
          ▼
     AUTHENTICATION
     (specialized by ADE-IF)


AUTHORITY
   │
   └── may contribute to
          │
          ▼
     AUTHORIZATION
          │
          ▼
        ACTION


ABILITY
   │
   └── describes what an Entity can do

PERMISSION
   │
   └── describes what an Entity is permitted to do
       (specialized by ADE-IF)


AUTHORIZATION
   │
   ├── considers context and applicable rules
   │
   └── determines:
          ├── Permitted
          └── Denied
```

These relationships are conceptual and do not constitute a complete formal ontology.

Authentication, Permission, and specialized identity or access-control mechanisms may be defined by ADE-IF.

The Core Model establishes the general semantic relationships required for interoperability while allowing specialized ADE frameworks to provide more detailed models and implementation requirements.

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
    ├── AUTHORITY
    │
    ├── ABILITY
    │     Pause Machine
    │
    └── AUTHORIZATION
          │
          ├── Context
          │
          ├── Applicable Rules
          │
          └── Decision
                │
                ▼
             PERMITTED
                │
                ▼
              ACTION
                │
                ▼
             MACHINE
```

Where identity assurance is required, a specialized ADE-IF process may establish Authentication of the Human Operator's Identity before Authorization is evaluated:

```text
IDENTITY
    │
    ▼
AUTHENTICATION
   (ADE-IF)
    │
    ▼
AUTHORIZATION
    │
    ▼
ACTION
```

Ability and Authorization remain distinct.

For example, an operator may have the Ability to pause a machine but may not be Authorized to do so in a particular context.

These examples are conceptual and do not constitute complete formal representations.
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
    ├── AUTHORITY
    │
    ├── ABILITY
    │     Pause Machine
    │
    └── AUTHORIZATION
          │
          ├── Context
          │
          ├── Applicable Rules
          │
          └── Decision
                │
                ▼
             PERMITTED
                │
                ▼
              ACTION
                │
                ▼
             MACHINE
```

Where identity assurance is required, a specialized ADE-IF process may establish Authentication of the Human Operator's Identity before Authorization is evaluated:

```text
IDENTITY
    │
    ▼
AUTHENTICATION
   (ADE-IF)
    │
    ▼
AUTHORIZATION
    │
    ▼
ACTION
```

Ability and Authorization remain distinct.

For example, an operator may have the Ability to pause a machine but may not be Authorized to do so in a particular context.

These examples are conceptual and do not constitute complete formal representations.

---

# 10. Relationship Overview

A simplified representation of the ADE Core Model is:

```text
                    ADE CORE CONCEPTS

                         ENTITY
                           │
              ┌────────────┼────────────┐
              │            │            │
           IDENTITY     AUTHORITY      ABILITY
              │            │            │
              │            │            └── What Entity can do
              │            │
              │            └── Recognized standing,
              │                responsibility, role,
              │                jurisdiction, or control
              │
              └── Reference by which
                  Entity may be distinguished


                         ENTITY
                           │
              ┌────────────┼────────────┐
              │            │            │
           OBJECT         EVENT        ACTION
                           │            │
                           │            ├── performed by → ENTITY
                           │            │
                           │            └── affects → ENTITY
                           │
                           ├── TIME
                           ├── LOCATION
                           ├── STATE
                           ├── SOURCE
                           ├── ASSERTION
                           └── INTENT


                       IDENTITY
                           │
                           │ may be subject to
                           ▼
                    AUTHENTICATION
                      (ADE-IF)
                           │
                           │ may provide identity assurance
                           ▼
                     AUTHORIZATION
                           │
                           ├── considers Authority
                           ├── considers Ability
                           ├── considers Permission
                           ├── considers Context
                           └── considers Rules
                           │
                           ▼
                    PERMITTED / DENIED
                           │
                           ▼
                         ACTION


                       SOURCE
                           │
                           ▼
                       ASSERTION
                           │
                    ┌──────┴──────┐
                    │             │
                CONFIDENCE    PROVENANCE


                         TIME
                           │
              ┌────────────┼────────────┐
              │            │            │
          TIME POINT    DURATION   TIME INTERVAL
```

### Foundational distinctions

The Core Model maintains the following distinctions:

```text
IDENTITY
Who or what is being referenced?

AUTHENTICATION
Can control of or association with that Identity be established?

AUTHORITY
What recognized standing, responsibility, role, jurisdiction,
or control does the Entity possess?

ABILITY
What can the Entity do?

PERMISSION
What is the Entity permitted to do?

AUTHORIZATION
Is a specific Action permitted within this context?

ACTION
What is actually performed?
```

Authentication, Permission, and specialized identity or access-control mechanisms may be defined by ADE-IF.

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
