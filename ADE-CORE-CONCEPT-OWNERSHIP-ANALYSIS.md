# ADE Human-Machine Framework

## ADE-Core Concept Ownership Analysis

**Status:** Working Analysis  
**Repository:** ADE-Core  
**Version:** 0.1.0

---

# 1. Purpose

This document records architectural analysis used to determine concept ownership within the ADE Human-Machine Framework.

The objective is to identify whether a concept is:

- An ADE-Core concept
- A framework-owned concept
- A shared concept
- A framework specialization of a Core concept
- An interoperability relationship between frameworks
- Undetermined pending further analysis

This document is an architectural analysis artifact and does not establish standards, specifications, or ownership decisions by itself.

---

# 2. Analysis Status

Analysis has not yet been completed.

Concept ownership decisions remain under review.

---

# 3. Concepts Under Review

- Entity
- Identity
- Authentication
- Authority
- Capability
- Authorization
- Source
- Assertion
- Provenance
- Confidence
- Time
- Location
- Relationship
- Intent
- State

---

# 4. Ownership Determination Process

```text
Concept
    ↓
Architectural Analysis
    ↓
Evidence
    ↓
Challenge
    ↓
Ownership Decision
    ↓
ADE-Core / Framework / Shared
```

---
# 5. Identity Ownership Analysis

**Status:** In Progress

## 5.1 Question

Determine the appropriate architectural ownership of **Identity** within the ADE Human-Machine Framework.

The analysis must determine whether Identity should be:

* An ADE-Core foundational concept
* An ADE-IF-owned concept
* A shared concept with a Core foundation and ADE-IF specialization
* Another architectural arrangement

No ownership decision is established by this section until the analysis is completed.

---

## 5.2 ADE-Core Current Position

The current ADE-Core Core Model defines **Identity** as a Core concept.

ADE-Core describes Identity as providing a persistent reference to a specific Entity within an ADE context.

The ADE-Core model distinguishes Identity from:

* Authentication
* Authority
* Capability
* Authorization

ADE-Core therefore currently treats Identity as a foundational semantic concept rather than only as an identity-framework implementation concept.

---

## 5.3 ADE-IF Current Position

The current ADE-IF Identity Model defines Identity as part of the identity architecture built upon ADE-Core.

ADE-IF identifies **Entity** as its primary ADE-Core dependency and then defines identity-specific concepts including:

* Identity
* Identity Reference
* Identity Identifier
* Identity Attribute
* Identity Claim
* Credential
* Authority
* Verification
* Authentication
* Authorization
* Identity Source
* Identity Context

ADE-IF therefore provides substantially more detailed semantics for Identity and its related concepts than the current ADE-Core Core Model.

---

## 5.4 Current Architectural Relationship

The current documents can be represented as:

```text
ADE-Core
    │
    └── Entity
          │
          ▼
       ADE-IF
          │
          ├── Identity
          ├── Identity Reference
          ├── Identity Identifier
          ├── Identity Attribute
          ├── Identity Claim
          ├── Credential
          ├── Verification
          ├── Authentication
          └── Authorization
```

However, ADE-Core currently also defines Identity:

```text
ADE-Core
    │
    ├── Entity
    │
    └── Identity
```

This creates an architectural overlap that requires resolution.

---

## 5.5 Evidence of Overlap

The overlap is not necessarily contradictory.

The two documents appear to operate at different levels of abstraction.

ADE-Core defines the general semantic meaning of Identity in relation to an Entity.

ADE-IF defines the identity-specific structures, processes, relationships, credentials, verification mechanisms, and authorization context that allow Identity to be used within an identity framework.

This suggests that the current documents may be describing different layers of the same concept.

---

## 5.6 Architectural Question

The central question is therefore:

> **Should ADE-Core establish the foundational semantic meaning of Identity while ADE-IF provides the specialized identity architecture built upon that foundation?**

If so, the relationship would resemble:

```text
ADE-Core
    │
    └── Identity
          │
          ▼
       ADE-IF
          │
          ├── Identity Reference
          ├── Identity Identifier
          ├── Identity Attribute
          ├── Identity Claim
          ├── Credential
          ├── Verification
          ├── Authentication
          └── Authorization
```

Under this model, ADE-Core would define only the minimum semantic foundation necessary for Identity to exist within the broader ADE architecture.

ADE-IF would define the specialized identity structures and mechanisms.

---

## 5.7 Alternative Ownership Model

An alternative would be to remove Identity from ADE-Core and establish Identity entirely within ADE-IF.

The architecture would then become:

```text
ADE-Core
    │
    └── Entity
          │
          ▼
       ADE-IF
          │
          └── Identity
```

Under this model, ADE-Core would not define Identity as a foundational concept.

This would simplify ADE-Core but could make Identity unavailable as a general semantic concept to other ADE frameworks without depending directly on ADE-IF.

---

## 5.8 Current Assessment

Based on the current documents, there is evidence supporting a **layered ownership model** in which:

```text
ADE-Core
    └── Identity
         Foundational semantic meaning

ADE-IF
    └── Identity Framework
         Specialized identity semantics and structures
```

However, this remains an **analysis result rather than a finalized architectural decision**.

The distinction between foundational meaning and specialized implementation should be examined further before modifying either ADE-Core or ADE-IF.

---

## 5.9 Dependencies Requiring Further Analysis

The Identity decision affects the architectural placement of:

* Authentication
* Authority
* Capability
* Authorization
* Credential
* Verification
* Identity Claims
* Identity Attributes
* Identity Sources
* Provenance
* Source
* Confidence

These concepts should therefore be analyzed after the foundational Identity question is resolved.

---

## 5.10 Preliminary Conclusion

**Preliminary conclusion:**

Identity appears suitable for a **layered architectural model** in which ADE-Core defines the minimum foundational semantic meaning of Identity, while ADE-IF defines the specialized identity architecture and mechanisms built upon that foundation.

This conclusion is preliminary and remains subject to challenge and further architectural review.

No modification to the ADE-Core Core Model or ADE-IF Identity Model should be made solely on the basis of this preliminary conclusion.

---

## 5.11 Next Review

The next stage is to determine the minimum definition of **Identity** that genuinely belongs in ADE-Core.

The analysis should answer:

> **What is the smallest stable definition of Identity that ADE-Core needs, independent of ADE-IF?**

This will establish whether the current ADE-Core Identity definition is appropriately scoped or contains identity-framework-specific material that should be moved to ADE-IF.

---

## 5.12 Minimum Core Definition Test

The minimum ADE-Core definition of Identity should be evaluated against the following test:

> **Can Identity be used as a general semantic concept by ADE frameworks without requiring the specialized identity mechanisms defined by ADE-IF?**

If the answer is yes, Identity has a valid role at the ADE-Core level.

The Core definition should be limited to the minimum meaning required for that role.

### Candidate Core Meaning

The current candidate definition is:

> **Identity provides a persistent reference to a specific Entity within an ADE context.**

This definition establishes the relationship between Identity and Entity without requiring ADE-Core to define:

* Authentication
* Credentials
* Verification
* Authority
* Capability
* Authorization
* Identity Claims
* Identity Attributes
* Identity Sources
* Identity Context

These concepts may be defined by ADE-IF or other applicable frameworks.

### Cross-Framework Test

The candidate Core Identity should be usable by other ADE frameworks, including:

```text
ADE-HTF
    │
    └── Entity
          └── Identity

ADE-LF
    │
    └── Entity
          └── Identity

ADE-USLF
    │
    └── Entity
          └── Identity

ADE-IF
    │
    └── Entity
          └── Identity
                ├── Identity Reference
                ├── Identity Claim
                ├── Credential
                ├── Verification
                ├── Authentication
                └── Authorization
```

This would allow Identity to function as a common semantic foundation while allowing ADE-IF to provide specialized identity capabilities.

### Scope Boundary

The presence of Identity in ADE-Core should not imply that ADE-Core owns the complete identity domain.

The distinction is:

```text
ADE-Core
    Identity
    = foundational semantic concept

ADE-IF
    Identity Framework
    = specialized identity architecture
```

This distinction should be preserved throughout the ADE documentation.

### Preliminary Finding

The minimum Core Definition Test currently supports retaining **Identity as a foundational ADE-Core concept**, provided that the Core definition remains limited to its general semantic relationship with Entity.

The specialized identity structures and mechanisms should remain outside the Core unless future architectural analysis determines otherwise.

This remains a preliminary finding until the related concepts of Authentication, Authority, Capability, Authorization, Source, Provenance, and Confidence have been evaluated.
---
# 6. Authentication Ownership Analysis

**Status:** In Progress

## 6.1 Question

Determine the appropriate architectural ownership of **Authentication** within the ADE Human-Machine Framework.

The analysis must determine whether Authentication should be:

* An ADE-Core foundational concept
* An ADE-IF-owned concept
* A shared concept
* A specialized process built upon Core Identity
* Another architectural arrangement

No final ownership decision is established by this section until the analysis is completed.

---

## 6.2 ADE-Core Current Position

The current ADE-Core Core Model defines **Authentication** as a Core concept.

ADE-Core describes Authentication as the process of establishing that an actor can demonstrate control of, or association with, an Identity.

ADE-Core explicitly distinguishes Authentication from:

* Identity
* Authority
* Capability
* Authorization

The current Core Model therefore treats Authentication as a foundational semantic concept.

---

## 6.3 ADE-IF Current Position

ADE-IF defines Authentication within its identity architecture.

Authentication is associated with establishing or verifying an actor's control of an Identity and is connected to identity credentials, verification, and authorization.

ADE-IF provides the specialized identity context in which Authentication operates.

The technical mechanisms and requirements for Authentication are intended to be defined by applicable standards rather than by the foundational ADE-Core model alone.

---

## 6.4 Dependency Relationship

Authentication depends conceptually on Identity.

A simplified relationship is:

```text
Entity
   │
   └── Identity
         │
         ▼
    Authentication
```

Authentication does not create the underlying Identity.

Instead, Authentication provides a means of establishing that an actor can demonstrate control of, or association with, an existing Identity.

---

## 6.5 Cross-Framework Test

The key question is:

> **Could another ADE framework require the general concept of Authentication without requiring the specialized identity architecture provided by ADE-IF?**

Authentication is fundamentally concerned with establishing control of or association with an Identity.

While other ADE frameworks may consume the result of Authentication, they do not necessarily need to define or implement Authentication themselves.

For example:

```text
ADE-HTF
    │
    └── uses authenticated Entity
              │
              ▼
          ADE-IF
              │
              └── Authentication
```

This suggests that Authentication may be a specialized identity function rather than a general Core concept.

---

## 6.6 Foundational vs Specialized Meaning

The distinction between Identity and Authentication is important.

```text
Identity
    =
reference to an Entity

Authentication
    =
process of establishing control of,
or association with, that Identity
```

Identity can exist without Authentication.

For example:

```text
Entity
   │
   └── Identity
```

may be represented without establishing whether the current actor controls that Identity.

Authentication introduces an additional process or determination:

```text
Entity
   │
   └── Identity
          │
          └── Authentication
```

This additional function is more closely associated with the identity domain than with the general semantic foundation of ADE.

---

## 6.7 Relationship to Authorization

Authentication should also remain distinct from Authorization.

A simplified relationship is:

```text
Identity
   ↓
Authentication
   ↓
Authority / Capability
   ↓
Authorization
   ↓
Action
```

Authentication establishes an identity-related condition.

Authorization determines whether an Action is permitted.

Successfully authenticating an actor does not automatically authorize every possible Action.

---

## 6.8 Current Assessment

The current documentation provides evidence that Authentication is more appropriately treated as a specialized identity function than as an ADE-Core foundational concept.

The general ADE architecture can understand that an Entity may have an Identity without requiring ADE-Core to define the mechanisms by which control of that Identity is established.

ADE-IF provides the natural architectural context for those mechanisms.

---

## 6.9 Preliminary Finding

**Preliminary finding:**

Authentication should be **ADE-IF owned** rather than an ADE-Core foundational concept.

ADE-Core does not need to define Authentication in order to establish the foundational meaning of Entity and Identity.

ADE-IF can build Authentication upon the Core Identity concept and define the specialized structures, credentials, verification processes, and technical mechanisms required for authentication.

This finding remains subject to challenge and review.

---

## 6.10 Potential Core Model Implication

If this preliminary finding is confirmed, the following change may eventually be required in `CORE-MODEL.md`:

```text
Current:

Identity
Authentication
Authority
Capability
Authorization

Potential future Core boundary:

Identity
```

The specialized concepts would remain within ADE-IF or other applicable frameworks.

No change should be made to `CORE-MODEL.md` until the related ownership analysis has progressed sufficiently to ensure that removing Authentication does not create unintended architectural gaps.

---

## 6.11 Next Review

The next concept requiring analysis is **Authority**.

Authority is more difficult than Authentication because it may have meaning beyond identity and security.

The analysis should determine whether Authority is:

* A general ADE relationship or concept
* An ADE-IF identity/security concept
* A domain-specific concept
* A shared concept with different framework specializations
* Undetermined pending further analysis
