# ADE Human-Machine Framework

## ADE-Core — Cross-Framework Future Work Queue

**Status:** Foundational Development
**Version:** 0.1.0
**Document Type:** Architectural Future Work Queue

---

# 1. Purpose

This document records cross-framework architectural questions that have emerged during the development and challenge of ADE frameworks.

The purpose is to identify concepts that may require common ADE-level semantics, coordination, or architectural boundaries.

The presence of an item in this queue **does not establish that the concept belongs in ADE-Core**.

Each question must be examined before ownership or formal incorporation is determined.

---

# 2. Why This Queue Exists

As ADE develops multiple frameworks, the same semantic concepts may appear in more than one framework.

For example:

```text
ADE-IF
 ├── Identity
 ├── Authorization
 ├── Context
 ├── Authority
 └── Lifecycle

ADE-HTF
 ├── Time
 └── Temporal State

ADE-LF
 ├── Location
 └── Spatial Reference
```

Repeated appearance does not automatically mean that a concept should be moved into ADE-Core.

Instead, ADE must determine whether the concept is:

1. Foundational to ADE-Core;
2. Owned by a specific framework;
3. Shared between frameworks;
4. A framework-specific interpretation of a Core concept; or
5. An interoperability relationship between frameworks.

---

# 3. Architectural Principle

> **A concept appearing in multiple frameworks does not automatically become an ADE-Core concept.**

Ownership should be determined through architectural evidence.

The preferred progression is:

```text
Repeated Concept
      ↓
Cross-Framework Evidence
      ↓
Architectural Analysis
      ↓
Ownership Decision
      ↓
Definition / Specification
      ↓
Implementation
```

---

# 4. Status Definitions

| Status            | Meaning                                                                 |
| ----------------- | ----------------------------------------------------------------------- |
| **Open**          | Question identified; no determination made.                             |
| **Investigating** | Architectural analysis is underway.                                     |
| **Discussion**    | Question is being examined through architectural/community discussion.  |
| **Proposed**      | Potential architectural treatment has been proposed.                    |
| **Accepted**      | Architectural treatment has been formally accepted.                     |
| **Implemented**   | Accepted treatment has been incorporated into the appropriate artifact. |
| **Deferred**      | Deliberately postponed pending other work.                              |
| **Closed**        | No further action required.                                             |

---

# 5. Future Work Queue

## CF-001 — Context

**Status:** Open
**Priority:** High
**Origin:** ADE-IF Identity and Authorization

### Architectural Question

What is the formal role of **Context** within the ADE architecture?

Context appears in Identity and Authorization-related reasoning and may also be relevant to other ADE frameworks.

### Questions for Investigation

Determine:

* What constitutes Context?
* Is Context a foundational ADE concept?
* Is Context a container for other concepts?
* Can Context contain Time, Location, State, Purpose, or Entity information?
* How does Context differ from Scope?
* How does Context differ from Conditions?
* Can Context itself be nested?
* Is Context an Entity, Object, relationship, or semantic structure?

### Current Disposition

No change to ADE-Core or any framework.

### Desired Outcome

Establish whether ADE requires a common semantic definition of Context and, if so, its appropriate architectural position.

---

## CF-002 — Provenance

**Status:** Open
**Priority:** High
**Origin:** ADE-IF Identity Challenge

### Architectural Question

Should ADE establish a reusable cross-framework provenance model?

Provenance may describe the origin, source, authority, method, or history associated with information.

### Potential Elements

```text
Source
Authority
Issuer
Time
Method
Evidence
Verification
Transformation
Custodian
```

### Questions for Investigation

Determine:

* What constitutes provenance?
* Is provenance information itself an ADE object?
* How does provenance relate to Authority?
* How does provenance relate to Verification?
* How should provenance be represented across frameworks?
* Can provenance itself have provenance?

### Current Disposition

No change to ADE-Core.

### Desired Outcome

Determine whether a common ADE provenance model is necessary for interoperability.

---

## CF-003 — Lifecycle

**Status:** Open
**Priority:** Medium
**Origin:** Identity and Authorization

### Architectural Question

Should ADE establish common lifecycle semantics that can be applied to multiple ADE concepts?

Identity and Authorization both raise questions involving states such as:

```text
Created
Active
Suspended
Expired
Revoked
Restored
Retired
```

### Questions for Investigation

Determine:

* Whether lifecycle is a Core concept;
* Whether lifecycle states are universal or framework-specific;
* How lifecycle events should be represented;
* Whether lifecycle applies to Entities, Credentials, Authorizations, Claims, or other objects;
* How lifecycle transitions are recorded;
* How time relates to lifecycle state.

### Current Disposition

No change to ADE-Core.

### Desired Outcome

Determine whether ADE requires common lifecycle semantics or framework-specific lifecycle definitions.

---

## CF-004 — Authority

**Status:** Open
**Priority:** High
**Origin:** Identity and Authorization

### Architectural Question

What is the foundational ADE meaning of **Authority**?

Authority appears in both Identity and Authorization contexts but may represent different relationships.

### Questions for Investigation

Determine the distinctions among:

```text
Authority
Authoritative Source
Issuer
Delegator
Delegate
Validator
Custodian
Decision Maker
```

Determine whether these are:

* ADE-Core concepts;
* framework-specific roles;
* relationships;
* or contextual roles assigned to Entities.

### Current Disposition

No change to ADE-Core.

### Desired Outcome

Establish clear boundaries between Authority and the framework-specific uses of authority.

---

## CF-005 — Relationship

**Status:** Open
**Priority:** Medium
**Origin:** Multiple ADE Frameworks

### Architectural Question

Does ADE require a formal Core representation of **Relationship**?

ADE frameworks naturally describe relationships among Entities, Objects, Events, Actions, States, and other concepts.

### Questions for Investigation

Determine:

* What constitutes a Relationship?
* Is a Relationship itself an ADE object?
* Can Relationships have attributes?
* Can Relationships have Time?
* Can Relationships have Location?
* Can Relationships have State?
* Can Relationships have authority or provenance?
* Can Relationships themselves be subject to authorization?

### Example

```text
Entity A
   │
   │ Relationship
   ▼
Entity B
```

The relationship may itself contain semantic information.

### Current Disposition

No change to ADE-Core.

### Desired Outcome

Determine whether Relationship requires a formal Core definition.

---

## CF-006 — State

**Status:** Open
**Priority:** Medium
**Origin:** Multiple ADE Frameworks

### Architectural Question

Should ADE establish a common semantic foundation for **State** across frameworks?

State may describe the condition of an Entity, Object, Event, Authorization, Credential, or other ADE concept.

### Questions for Investigation

Determine:

* What constitutes State?
* How is State established?
* Can State be verified?
* Can State change?
* What causes a State transition?
* How does State relate to Time?
* How does State relate to Events?
* How does State relate to lifecycle?

### Example

```text
Authorization
      ↓
     State
      ↓
   Active
```

### Current Disposition

No change to ADE-Core.

### Desired Outcome

Determine whether common State semantics are required across ADE frameworks.

---

# 6. Coordinated Framework Dependencies

Some concepts already have dedicated framework homes.

These should **not automatically be duplicated in ADE-Core**.

## Time

Primary framework:

```text
ADE-HTF — Human Timeline Framework
```

ADE-Core should determine how common ADE concepts reference or depend upon Time without redefining the complete temporal framework.

## Location

Primary framework:

```text
ADE-LF — Location Framework
```

ADE-Core should determine how common ADE concepts reference or depend upon Location without duplicating the Location Framework.

This creates a distinction between:

```text
Core Relationship
       ≠
Framework Ownership
```

---

# 7. Cross-Framework Questions

Future analysis should examine whether the following concepts require common ADE semantics:

```text
Context
Provenance
Lifecycle
Authority
Relationship
State
```

Additional concepts may be added when evidence emerges from future framework development.

---

# 8. Evidence Requirements

An item should not be promoted into an ADE-Core requirement solely because it appears in multiple frameworks.

Evidence may include:

* Multiple independent framework requirements;
* Cross-framework use cases;
* Interoperability problems;
* Semantic contradictions;
* Repeated terminology conflicts;
* Machine interpretation requirements;
* Human interpretation requirements;
* Implementation experience;
* Challenge findings;
* Community review.

---

# 9. Ownership Decision

For each future-work item, ADE should eventually determine one of the following:

```text
ADE-Core Concept
      OR
Framework-Owned Concept
      OR
Shared Concept
      OR
Framework Interpretation of Core Concept
      OR
Interoperability Relationship
```

This prevents unnecessary expansion of ADE-Core.

---

# 10. Change-Control Principle

> **The Cross-Framework Future Work Queue records architectural questions; it does not create Core requirements.**

No concept should be incorporated into ADE-Core solely because it appears in this document.

A proposed Core change should follow:

```text
Question
   ↓
Evidence
   ↓
Challenge
   ↓
Architectural Analysis
   ↓
Ownership Decision
   ↓
Specification
   ↓
Core Model Change — if required
```

---

# 11. Current Queue Summary

| ID     | Concept      | Priority | Status | Current Owner |
| ------ | ------------ | -------: | ------ | ------------- |
| CF-001 | Context      |     High | Open   | Undetermined  |
| CF-002 | Provenance   |     High | Open   | Undetermined  |
| CF-003 | Lifecycle    |   Medium | Open   | Undetermined  |
| CF-004 | Authority    |     High | Open   | Undetermined  |
| CF-005 | Relationship |   Medium | Open   | Undetermined  |
| CF-006 | State        |   Medium | Open   | Undetermined  |

---

# 12. Architectural Position

This queue exists to protect the integrity of ADE-Core as the ADE framework family expands.

The objective is not to place every repeated concept into ADE-Core.

The objective is to determine, through evidence and architectural analysis, **which concepts truly require common ADE semantics and which should remain within individual frameworks.**

As ADE develops, this queue may grow, shrink, or result in concepts being assigned to different architectural layers.

That evolution is expected.

---

## ADE Architectural Principle

> **Define the foundation carefully, challenge it honestly, and expand it only when the architecture demonstrates that expansion is necessary.**
