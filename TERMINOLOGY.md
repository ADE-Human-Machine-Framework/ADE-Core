# ADE Human-Machine Framework

## ADE-Core Terminology

**Status:** Foundational Draft
**Repository:** ADE-Core
**Version:** 0.2.0

---

## 1. Purpose

This document defines the foundational terminology used throughout the ADE Human-Machine Framework.

The purpose of this document is to establish a consistent semantic vocabulary so that concepts are interpreted consistently by humans, machines, and future ADE frameworks.

The definitions in this document should be considered authoritative unless superseded through an approved ADE governance process.

---

## 2. Scope

This document defines the primary concepts used by ADE-Core.

Specialized ADE frameworks may introduce additional terminology but should not redefine ADE-Core terminology without an approved standards process.

---

## 3. Foundational Concepts

ADE-Core establishes the following foundational concepts:

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
11. Identity
12. Authentication
13. Authority
14. Capability
15. Authorization
16. Source
17. Assertion
18. Confidence
19. Provenance

These concepts form the common semantic vocabulary of the ADE Human-Machine Framework.

Not every foundational concept is a specialized type of Entity. Some provide context, information about information, identity, authority, or relationships between other concepts.

---

## 4. Terminology Definitions

### 4.1 Entity

**Definition**

An Entity is something that can be identified, represented, referenced, or distinguished within an ADE context.

**Examples**

* Person
* Organization
* Machine
* Document
* Event
* Digital resource

**Notes**

Entity is a foundational ADE concept. Other ADE concepts may have defined relationships with Entities without necessarily being specialized types of Entity.

---

### 4.2 Object

**Definition**

An Object is a specialized Entity representing a physical or digital thing.

**Examples**

* Vehicle
* Machine
* Mobile device
* Computer system
* Document

**Notes**

Objects may possess Attributes, States, Locations, Relationships, and participate in Events.

---

### 4.3 Event

**Definition**

An Event is a specialized Entity representing an occurrence, happening, or defined occurrence context.

**Examples**

* Repair event
* Meeting
* Transaction event
* Earthquake
* Equipment inspection event

**Notes**

Events may involve Entities, contain Actions, have Time and Location, and produce State changes.

Events may be planned, active, completed, cancelled, or failed.

A planned Event and an Event that actually occurred must remain semantically distinguishable.

---

### 4.4 Action

**Definition**

An Action represents something performed, initiated, or carried out by an Entity.

**Examples**

* Repair
* Approve
* Purchase
* Inspect
* Communicate

**Notes**

Actions may affect Entities, change States, and occur within Events.

An Action may be authorized or unauthorized independently of whether it actually occurs.

---

### 4.5 State

**Definition**

A State represents the condition of an Entity at a particular point or interval of Time.

**Examples**

* Active
* Inactive
* Available
* Unavailable
* Approved
* Pending

**Notes**

States may change as a result of Actions or Events.

The State of an Entity should remain distinguishable from the Event or Action that caused a State change.

---

### 4.6 Attribute

**Definition**

An Attribute represents a characteristic, property, measurement, or descriptive value associated with an Entity.

**Examples**

* Name
* Temperature
* Weight
* Status code
* Identifier

**Notes**

Attribute values may change over Time without changing the identity of the Attribute itself.

---

### 4.7 Time

**Definition**

Time provides temporal context for Entities, Events, Actions, States, Attributes, and Relationships.

**Examples**

* Timestamp
* Duration
* Time interval
* Relative time

**Notes**

ADE recognizes Time Point, Duration, and Time Interval as fundamental temporal constructs.

ADE should distinguish between Scheduled Time, Actual Time, Estimated Time, Relative Time, and Unknown Time where applicable.

---

### 4.8 Location

**Definition**

Location provides spatial context for an Entity, Event, Action, State, or other ADE representation.

**Examples**

* Address
* Room
* Building
* Geographic coordinates
* Grid reference

**Notes**

Location may be represented at different levels of precision and through different reference systems.

ADE should not require false precision when the available location information is approximate, generalized, or unknown.

---

### 4.9 Relationship

**Definition**

A Relationship represents a meaningful semantic connection between two or more ADE concepts.

ADE-Core relationships are directional and may have an inverse perspective.

**Examples**

* Works for
* Owns
* Participates in
* Occurs at
* Affects
* Performs
* Authorizes
* Refers to

**Notes**

Relationships provide the connective structure through which ADE concepts can be understood in relation to one another.

The meaning of a Relationship should remain consistent within an ADE context.

---

### 4.10 Intent

**Definition**

Intent represents a purpose, objective, desired outcome, or reason associated with an Entity, Event, or Action.

**Examples**

* Restore machine operation
* Purchase a vehicle
* Schedule a meeting
* Deliver a service

**Notes**

Intent may exist before an Action occurs and does not guarantee that the intended outcome will be achieved.

---

### 4.11 Identity

**Definition**

Identity provides a reference or representation associated with an Entity within a defined context.

**Examples**

* Government-issued identity
* Organizational identity
* System identity
* Device identity
* Digital identifier

**Notes**

An Entity may have one or more Identities.

Identity does not by itself establish that an Entity or actor has been authenticated.

An Identity may be used as a reference without requiring all associated information to be disclosed.

---

### 4.12 Authentication

**Definition**

Authentication is a process through which an actor demonstrates control of, or association with, an Identity within a defined context.

**Examples**

* Credential verification
* Cryptographic proof
* Multi-factor authentication
* Device-based authentication

**Notes**

Authentication establishes an evidentiary relationship between an actor and an Identity within a particular context.

Authentication does not by itself establish Authorization.

---

### 4.13 Authority

**Definition**

Authority represents the recognized ability, standing, or permission of an Entity or actor to exercise specified control or responsibility within a defined context.

**Examples**

* Organizational authority
* Administrative authority
* Regulatory authority
* Emergency authority
* Delegated authority

**Notes**

Authority may be contextual, time-limited, delegated, restricted, or hierarchical.

Authority does not necessarily mean that a specific Action has been authorized.

---

### 4.14 Capability

**Definition**

Capability represents an Action or class of Actions that an Entity or actor is permitted or enabled to perform within a defined context.

**Examples**

* May approve
* May pause
* May cancel
* May modify
* May access

**Notes**

Capabilities may be derived from Authority, Authorization, system rules, roles, or other applicable conditions.

A Capability should remain distinguishable from the actual Action performed.

---

### 4.15 Authorization

**Definition**

Authorization determines whether an Entity or actor is permitted to perform a specific Action within a defined context.

**Examples**

* Authorized to approve
* Authorized to pause
* Authorized to cancel
* Authorized to access

**Notes**

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

Authorization is distinct from Authentication.

Authentication establishes a relationship concerning Identity.

Authorization establishes whether an Action is permitted.

Authorization does not guarantee that the Action will actually occur.

---

### 4.16 Source

**Definition**

A Source identifies the origin or provider of information represented within an ADE context.

**Examples**

* Person
* Organization
* Sensor
* Device
* Database
* Application
* External information system

**Notes**

A Source may provide or originate an Assertion.

A Source should remain distinguishable from the information being provided.

---

### 4.17 Assertion

**Definition**

An Assertion is a representation of information stated, reported, claimed, or otherwise presented about an ADE concept.

**Examples**

* A machine reports that it is operational.
* A person states that an inspection occurred.
* A system reports a scheduled event.
* A sensor reports a measured temperature.

**Notes**

An Assertion may refer to an Entity, Event, Action, State, Attribute, Relationship, or other ADE concept.

The existence of an Assertion does not by itself establish that the information asserted is true.

---

### 4.18 Confidence

**Definition**

Confidence represents a qualified assessment associated with the reliability, certainty, or degree of belief assigned to an Assertion or other information.

**Examples**

* High confidence
* Moderate confidence
* Low confidence
* Numerical confidence value

**Notes**

Confidence is contextual and does not itself establish truth.

A high-confidence Assertion remains distinguishable from an established fact.

The specific representation or calculation of Confidence may be defined by applicable ADE standards.

---

### 4.19 Provenance

**Definition**

Provenance represents information about the origin, history, derivation, or transformation of information.

**Examples**

* Original Source
* Time of creation
* System that generated information
* Transformation history
* Chain of contributing Sources

**Notes**

Provenance helps establish how information came to exist or how it has changed.

Provenance should remain distinguishable from the information itself.

---

## 5. Interpretation Principles

### Consistency

A term should retain the same meaning across ADE frameworks unless explicitly redefined through an approved standards process.

### Clarity

Definitions should prioritize semantic clarity over implementation-specific details.

### Extensibility

Specialized ADE frameworks may extend ADE terminology while maintaining compatibility with ADE-Core concepts.

### Stability

Foundational terminology should remain stable over time to support interoperability and long-term understanding.

### Explicit Distinction

Concepts with different semantic purposes should not be treated as equivalent.

For example:

```text
Identity ≠ Authentication

Authentication ≠ Authorization

Authority ≠ Capability

Authorization ≠ Action

Source ≠ Assertion

Assertion ≠ Fact

Confidence ≠ Truth

Provenance ≠ Information
```

---

## 6. Incomplete and Unknown Information

ADE terminology must support information that is incomplete, unavailable, or not yet determined.

The following conditions should remain semantically distinguishable:

* Known
* Unknown
* Unavailable
* Not Applicable
* Not Yet Determined

For example:

```text
Actor Identity = Unknown
```

does not mean:

```text
Actor Identity = None
```

The same principle applies to Source, Authority, Authorization, Time, Location, and other ADE concepts.

---

## 7. Contextual and Conditional Meaning

Some ADE concepts have meaning only within a defined context.

Identity, Authentication, Authority, Capability, and Authorization may depend upon factors such as:

* Time
* Location
* Relationship
* Role
* State
* Applicable rules
* Emergency conditions

A statement that an actor is authorized should therefore be understood within the context in which that authorization applies.

An authorization granted for one Action, system, location, or time does not automatically imply authorization for another.

---

## 8. Human and Machine Interpretation

ADE terminology is intended to support a common semantic vocabulary for both humans and machines.

Definitions should therefore be:

* Human understandable
* Machine interpretable
* Consistent across implementations
* Independent of natural language
* Independent of a specific technology

---

## 9. Future Terminology

Future ADE frameworks may define additional concepts including, but not limited to:

* Evidence
* Validation
* Certification
* Delegation
* Policy
* Role
* Credential
* Verification
* Additional domain-specific concepts

New terminology should be evaluated against ADE-Core to determine whether it belongs in the Core or should remain part of a specialized framework or semantic layer.

---

## 10. Foundational Principle

> **A shared vocabulary is a prerequisite for shared understanding.**

ADE-Core terminology provides the common semantic language upon which the ADE Human-Machine Framework is built.

The terminology is intended to allow humans and machines to distinguish not only **what something is**, but also **what is known about it, where the information came from, how it is identified, who or what is authorized to act, and under what context that meaning applies.**
