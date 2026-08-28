# ADE Human-Machine Framework

## ADE-Core Terminology

**Status:** Foundational Draft
**Repository:** ADE-Core
**Version:** 0.1.0

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

ADE-Core establishes ten foundational concepts.

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

These concepts form the common semantic vocabulary of the ADE Human-Machine Framework.

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

Entity is the foundational concept upon which many other ADE concepts are built.

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

* Repair
* Meeting
* Transaction
* Earthquake
* Equipment inspection

**Notes**

Events may involve Entities, contain Actions, have Time and Location, and produce State changes.

Events may be planned, active, completed, cancelled, or failed.

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

---

### 4.9 Relationship

**Definition**

A Relationship represents a meaningful connection between two or more Entities.

**Examples**

* Works for
* Owns
* Participates in
* Occurs at
* Affects

**Notes**

Relationships provide the connective structure through which Entities can be understood in relation to one another.

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

## 5. Interpretation Principles

### Consistency

A term should retain the same meaning across ADE frameworks unless explicitly redefined through an approved standards process.

### Clarity

Definitions should prioritize semantic clarity over implementation-specific details.

### Extensibility

Specialized ADE frameworks may extend ADE terminology while maintaining compatibility with ADE-Core concepts.

### Stability

Foundational terminology should remain stable over time to support interoperability and long-term understanding.

---

## 6. Future Terminology

Future ADE frameworks may define additional concepts including, but not limited to:

* Source
* Evidence
* Assertion
* Confidence
* Provenance
* Identity
* Authorization
* Context

These concepts are not currently defined as ADE-Core foundational concepts.

---

## 7. Foundational Principle

> A shared vocabulary is a prerequisite for shared understanding.

ADE-Core terminology provides the common semantic language upon which the ADE Human-Machine Framework is built.
