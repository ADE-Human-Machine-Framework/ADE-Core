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

  ---
  # 7. Authority Ownership Analysis

**Status:** In Progress

## 7.1 Question

Determine the appropriate architectural ownership of **Authority** within the ADE Human-Machine Framework.

The analysis must determine whether Authority should be:

* An ADE-Core foundational concept
* An ADE-IF-owned concept
* A shared concept
* A relationship or contextual property rather than an independent Core concept
* A domain-specific concept
* Undetermined pending further analysis

No final ownership decision is established by this section until the analysis is completed.

---

## 7.2 ADE-Core Current Position

The current ADE-Core Core Model defines **Authority** as a Core concept.

ADE-Core describes Authority as the recognized standing, role, or level of control that an Entity or actor possesses within a defined context.

Authority may be established through:

* A Relationship
* An organizational role
* A legal or regulatory designation
* A delegated permission
* Other recognized mechanisms

ADE-Core also distinguishes Authority from:

* Identity
* Authentication
* Capability
* Authorization

The current Core Model therefore treats Authority as a general semantic concept.

---

## 7.3 ADE-IF Current Position

ADE-IF includes Authority within its identity and authorization architecture.

Within ADE-IF, Authority is associated with an Identity or actor and contributes to determining what Actions that actor may perform.

ADE-IF also distinguishes Authority from Capability and Authorization.

This establishes an important relationship:

```text
Identity
   ↓
Authentication
   ↓
Authority
   ↓
Capability
   ↓
Authorization
   ↓
Action
```

However, the existence of Authority within ADE-IF does not by itself establish that ADE-IF should own the general concept.

---

## 7.4 What Is Authority?

Authority can have meaning beyond identity authentication.

For example:

```text
Human
   │
   └── Authority
         └── Safety Officer
```

or:

```text
Organization
   │
   └── Authority
         └── Regulatory Authority
```

or:

```text
System
   │
   └── Authority
         └── Control of Resource
```

These examples suggest that Authority may describe a recognized standing or control relationship rather than merely a security mechanism.

---

## 7.5 Authority and Identity

Authority does not necessarily create Identity.

A simplified relationship is:

```text
Entity
   │
   ├── Identity
   │
   └── Authority
```

An Entity may possess an Identity without possessing a particular Authority.

Likewise, an Entity may have different Authorities in different contexts.

For example:

```text
Entity: Human A

Context 1:
Authority = Employee

Context 2:
Authority = Safety Officer

Context 3:
Authority = Vehicle Operator
```

Authority is therefore contextual.

---

## 7.6 Authority and Relationship

Authority may arise from a Relationship.

For example:

```text
Person
   │
   └── employed by
          │
          ▼
      Organization
```

The employment relationship may provide the context in which a particular Authority is recognized.

Similarly:

```text
Organization
   │
   └── appoints
          │
          ▼
       Person
          │
          └── Authority
                = Safety Officer
```

This suggests that Authority may be represented as a semantic concept associated with Relationships rather than being limited to identity infrastructure.

---

## 7.7 Authority and Capability

Authority and Capability should remain distinct.

A simplified model is:

```text
Authority
    ↓
provides or establishes
    ↓
Capability
    ↓
may contribute to
    ↓
Authorization
```

For example:

```text
Authority:
Safety Officer

Capability:
Pause Machine

Authorization:
Permitted to pause Machine X
under defined conditions
```

Authority therefore describes recognized standing or control, while Capability describes what that standing enables.

---

## 7.8 Authority and Authorization

Authority does not automatically equal Authorization.

For example:

```text
Authority:
Safety Officer

Requested Action:
Cancel Mission

Authorization:
Denied
```

The actor may possess Authority while still lacking Authorization for a particular Action.

Authorization depends on the complete context and applicable rules.

---

## 7.9 Cross-Framework Test

The key question is:

> **Could an ADE framework other than ADE-IF require the concept of Authority without requiring identity authentication or authorization mechanisms?**

Potentially, yes.

For example, a future framework could represent:

```text
Organization
   │
   └── Authority
         └── Regulatory Jurisdiction
```

or:

```text
Human
   │
   └── Authority
         └── Operational Role
```

or:

```text
Entity
   │
   └── Authority
         └── Control of Resource
```

These uses do not inherently require Authentication or Authorization.

This provides evidence that Authority may have a broader semantic role than ADE-IF alone.

---

## 7.10 Core vs Specialized Boundary

A possible layered model is:

```text
ADE-Core
    │
    └── Authority
          │
          └── foundational meaning:
              recognized standing, role,
              or control within a context

ADE-IF
    │
    └── Authority specialization
          │
          ├── Identity-related authority
          ├── Delegated authority
          ├── Authority relationships
          ├── Capability
          └── Authorization
```

Under this model, ADE-Core would define only the general semantic meaning of Authority.

ADE-IF would define identity and authorization-specific uses.

---

## 7.11 Alternative Model

An alternative is to make Authority entirely ADE-IF owned:

```text
ADE-Core
    └── Identity

ADE-IF
    ├── Authentication
    ├── Authority
    ├── Capability
    └── Authorization
```

This would make the Core smaller but would also prevent other ADE frameworks from using Authority as a general semantic concept without depending on ADE-IF.

---

## 7.12 Current Assessment

Authority appears to have a broader semantic meaning than Authentication or Authorization.

It may describe recognized standing, role, jurisdiction, or control within a defined context.

Those meanings can exist independently of authentication.

There is therefore reasonable evidence that a minimal foundational concept of Authority could have a legitimate role within ADE-Core.

However, the specialized identity, capability, delegation, and authorization structures associated with Authority are more appropriately addressed by ADE-IF or other applicable frameworks.

---

## 7.13 Preliminary Finding

**Preliminary finding:**

Authority should remain **under consideration as a potential ADE-Core foundational concept**, with ADE-IF defining specialized identity and authorization-related uses.

Unlike Authentication, Authority cannot currently be classified as purely ADE-IF owned.

The Core definition should remain minimal if Authority is retained.

A potential Core meaning is:

> **Authority represents recognized standing, role, jurisdiction, or control associated with an Entity within a defined context.**

This is a preliminary finding and remains subject to challenge and further architectural review.

---

## 7.14 Questions Requiring Further Review

Before a final ownership decision is made, the following questions should be examined:

1. Can Authority exist without Identity?
2. Can Authority be represented through a Relationship rather than as an independent concept?
3. Is Authority always associated with an Entity?
4. Can Machines and Software Agents possess Authority?
5. Can Authority be delegated?
6. Can Authority expire or change over Time?
7. Does Authority always imply Capability?
8. Can Capability exist without Authority?
9. Is jurisdiction a form of Authority or a separate concept?
10. Does Authority require a Source or Assertion to establish it?

These questions may affect the final Core boundary.

---

## 7.15 Next Review

The next concept requiring analysis is **Capability**.

Capability should be examined in relation to Authority and Authorization to determine whether it is:

* A general Core concept
* An ADE-IF concept
* A property derived from Authority
* A permission-like semantic structure
* A specialized authorization concept
* Undetermined pending further analysis
---
# 8. Capability Ownership Analysis

**Status:** In Progress

## 8.1 Question

Determine the appropriate architectural ownership of **Capability** within the ADE Human-Machine Framework.

The analysis must determine whether Capability should be:

* An ADE-Core foundational concept
* An ADE-IF-owned concept
* A shared concept
* A property or consequence of Authority
* A specialized authorization concept
* Undetermined pending further analysis

No final ownership decision is established by this section until the analysis is completed.

---

## 8.2 ADE-Core Current Position

The current ADE-Core Core Model defines **Capability** as a Core concept.

ADE-Core describes Capability as an Action or class of Actions that an Authority permits an Entity or actor to perform within a defined context.

The current model therefore places Capability between Authority and Authorization:

```text
Authority
    ↓
Capability
    ↓
Authorization
    ↓
Action
```

---

## 8.3 ADE-IF Current Position

ADE-IF includes Capability within its identity and authorization architecture.

Within ADE-IF, Capability represents what an Authority permits an Entity or actor to perform.

Capability may be constrained by factors such as:

* Time
* Location
* Relationship
* Purpose
* State
* Emergency conditions
* Applicable rules

ADE-IF therefore provides a specialized context for using Capability in identity and authorization decisions.

---

## 8.4 What Is Capability?

A Capability can be understood as an ability, permission, or allowed class of Action available to an Entity within a defined context.

For example:

```text
Entity:
Technician

Capability:
Repair Machine
```

Another example:

```text
Entity:
Safety Officer

Capability:
Pause Machine
```

Capability describes what an Entity may be able or permitted to do.

It does not necessarily establish that the Entity is currently authorized to perform the Action in every circumstance.

---

## 8.5 Capability and Authority

The current ADE-Core model treats Authority as a source or basis for Capability.

For example:

```text
Authority:
Safety Officer

Capability:
Pause Machine
```

However, this relationship may not always be one-to-one.

An Entity may have:

```text
Authority:
Vehicle Operator

Capabilities:
Operate Vehicle
Inspect Vehicle
Report Fault
```

Authority may therefore establish a set of Capabilities.

---

## 8.6 Capability and Authorization

Capability should remain distinct from Authorization.

A Capability may describe what an Entity is permitted or equipped to do in general.

Authorization determines whether the Action is permitted under the specific circumstances of a particular request.

For example:

```text
Entity:
Safety Officer

Capability:
Pause Machine

Current Context:
Machine operating normally

Authorization:
Permitted
```

But:

```text
Entity:
Safety Officer

Capability:
Pause Machine

Current Context:
Action restricted by higher-priority rule

Authorization:
Denied
```

This distinction suggests:

```text
Capability
    =
potential or standing permission

Authorization
    =
contextual determination for a specific Action
```

---

## 8.7 Capability and Physical or Technical Ability

Capability may also have a meaning broader than permission.

For example:

```text
Machine
Capability:
Lift 5,000 kg
```

This describes what the Machine is capable of doing physically or technically.

Similarly:

```text
Software Agent
Capability:
Process Image
```

describes a functional ability.

This creates an important architectural question.

There may be two related but distinct meanings:

```text
Capability
    ├── Ability
    │     Physical / technical function
    │
    └── Permission
          Authorized or permitted function
```

If both meanings are retained, ADE must determine whether they are the same concept with different contexts or separate concepts.

---

## 8.8 Cross-Framework Test

The key question is:

> **Could an ADE framework other than ADE-IF require Capability without requiring Identity, Authority, or Authorization?**

Potentially, yes.

For example, ADE-HTF could describe:

```text
Human
Capability:
Run 10 km
```

ADE-LF could potentially describe:

```text
Location System
Capability:
Represent geographic position
```

A future Machine or Resource framework could describe:

```text
Machine
Capability:
Lift 5,000 kg
```

These examples suggest that Capability may have a general semantic meaning independent of identity security.

However, these examples also reveal that "capability" may mean **ability**, while ADE-IF uses Capability primarily in the sense of **permitted Action**.

That distinction must be resolved before ownership is determined.

---

## 8.9 Potential Architectural Split

A possible architecture is:

```text
ADE-Core
    │
    └── Capability
          │
          ├── Ability
          │
          └── Permission-related capability

ADE-IF
    │
    └── Authorization Capability
          │
          └── Identity / Authority context
```

Another possibility is:

```text
ADE-Core
    └── Ability

ADE-IF
    └── Capability
          = permission to perform an Action
```

A third possibility is to retain Capability as a single Core concept with clearly defined contextual meanings.

---

## 8.10 Relationship to Action

Capability is strongly connected to Action.

A conceptual relationship is:

```text
Entity
   │
   └── Capability
          │
          └── permits or enables
                    │
                    ▼
                  Action
```

This relationship may be useful outside identity and authorization.

For example:

```text
Machine
    Capability:
    Lift Load

Action:
    Lift Load
```

This does not require authentication or authorization.

---

## 8.11 Relationship to State

Capability may also depend on State.

For example:

```text
Machine
State:
Maintenance

Capability:
Lift Load

Current effective capability:
Unavailable
```

The Machine may possess the underlying capability while being unable to exercise it in its current State.

This reinforces the distinction between Capability and Authorization.

---

## 8.12 Current Assessment

Capability presents a more complex ownership question than Authentication.

There is evidence that Capability has a legitimate general semantic meaning outside identity and authorization.

However, the current ADE-Core definition uses Capability primarily as a permission derived from Authority.

ADE-IF uses the same concept within an identity and authorization context.

The concept may therefore be conflating:

1. **Ability** — what an Entity can do.
2. **Permission** — what an Entity is permitted to do.

These meanings should not be merged without further architectural examination.

---

## 8.13 Preliminary Finding

**Preliminary finding:**

Capability should **remain under architectural review** rather than being immediately assigned to ADE-Core or ADE-IF.

There is evidence supporting a general Core concept if Capability is defined as an Entity's ability or potential to perform an Action.

There is also evidence supporting ADE-IF ownership if Capability is defined specifically as a permission granted through Authority.

The distinction between **ability** and **permission** must therefore be resolved before a final ownership decision is made.

For the purposes of the current ownership analysis:

```text
Capability = Undetermined
```

---

## 8.14 Questions Requiring Further Review

The following questions should be resolved:

1. Is Capability an ability, a permission, or both?
2. Can a Machine possess Capability?
3. Can a Human possess Capability without Authority?
4. Can Capability exist without Identity?
5. Can Capability exist without Authorization?
6. Is Capability derived from Authority?
7. Can Capability exist without Authority?
8. Can Capability change with State?
9. Can Capability be constrained by Time or Location?
10. Should physical/technical ability and permission be separate concepts?
11. Does ADE require a separate concept for Ability?
12. Would separating Ability and Permission simplify the Core Model?

---

## 8.15 Current Ownership Status

```text
Capability
    ↓
UNDetermined
    ↓
Requires distinction between:
    Ability
    and
    Permission
```

No change to `CORE-MODEL.md` should be made until this distinction has been resolved.

---

## 8.16 Next Review

The next concept requiring analysis is **Authorization**.

Authorization should be evaluated against the findings for:

```text
Identity
Authentication
Authority
Capability
Action
```

The objective is to determine whether Authorization belongs entirely within ADE-IF or whether ADE-Core requires a minimal general semantic concept for authorization decisions.

---
# 9. Authorization Ownership Analysis

**Status:** In Progress

## 9.1 Question

Determine the appropriate architectural ownership of **Authorization** within the ADE Human-Machine Framework.

The analysis must determine whether Authorization should be:

* An ADE-Core foundational concept
* An ADE-IF-owned concept
* A shared concept
* A general decision structure that can be specialized by frameworks
* Undetermined pending further analysis

No final ownership decision is established by this section until the analysis is completed.

---

## 9.2 ADE-Core Current Position

The current ADE-Core Core Model defines **Authorization** as a Core concept.

ADE-Core describes Authorization as the determination that an Entity or actor is permitted to perform a specific Action within a defined context.

Authorization may consider:

* Identity
* Authentication
* Relationship
* Authority
* Capability
* Time
* Location
* Intent
* State
* Applicable rules
* Emergency conditions

The current Core Model therefore places Authorization near the end of the following conceptual chain:

```text
Identity
   ↓
Authentication
   ↓
Authority
   ↓
Capability
   ↓
Authorization
   ↓
Action
```

---

## 9.3 ADE-IF Current Position

ADE-IF defines Authorization as part of its identity and access architecture.

Within ADE-IF, Authorization determines whether an authenticated Entity or actor is permitted to perform an Action under applicable conditions.

ADE-IF connects Authorization with:

* Identity
* Authentication
* Authority
* Capability
* Context
* Rules
* Action

ADE-IF therefore provides a specialized implementation and identity context for Authorization.

---

## 9.4 What Is Authorization?

Authorization can be understood as a determination about whether a particular Action is permitted within a defined context.

For example:

```text
Actor:
Human A

Requested Action:
Pause Machine

Context:
Machine operating

Authority:
Safety Officer

Capability:
Pause Machine

Authorization:
Permitted
```

Authorization therefore differs from simply possessing an Identity or Authority.

---

## 9.5 Authorization and Identity

Authorization may depend on Identity, but Identity does not necessarily require Authorization.

For example:

```text
Entity
   │
   └── Identity
```

can exist without any authorization decision.

Authorization introduces a decision about a requested or proposed Action:

```text
Entity
   │
   └── Identity
          │
          └── Authorization
                  │
                  └── Action
```

This suggests that Authorization is a higher-level semantic function built upon foundational concepts.

---

## 9.6 Authorization and Authentication

Authentication and Authorization are distinct.

```text
Authentication
    =
establishing control of or association
with an Identity

Authorization
    =
determining whether an Action is permitted
```

An authenticated actor may still be denied authorization.

Example:

```text
Identity:
Human A

Authentication:
Successful

Requested Action:
Cancel Mission

Authorization:
Denied
```

Authentication therefore establishes an identity-related condition while Authorization makes an access or action decision.

---

## 9.7 Authorization and Authority

Authority may contribute to Authorization but does not automatically determine the result.

For example:

```text
Authority:
Safety Officer

Requested Action:
Pause Machine

Authorization:
Permitted
```

while:

```text
Authority:
Safety Officer

Requested Action:
Delete Safety Records

Authorization:
Denied
```

Authority describes standing or control.

Authorization determines whether a specific Action is permitted within a defined context.

---

## 9.8 Authorization and Capability

The relationship between Capability and Authorization depends on how Capability is ultimately defined.

If Capability means:

> **ability to perform an Action**

then Authorization may independently determine whether that ability may be exercised.

If Capability means:

> **permission to perform an Action**

then Capability and Authorization may overlap significantly.

This reinforces the unresolved Capability ownership question.

The relationship may eventually be represented as:

```text
Ability
   +
Authority
   +
Rules
   +
Context
   ↓
Authorization
   ↓
Action
```

or:

```text
Capability
   +
Context
   +
Rules
   ↓
Authorization
   ↓
Action
```

The final model depends on the outcome of the Capability analysis.

---

## 9.9 Authorization as a General Semantic Pattern

Authorization may be understood more broadly than identity security.

A general authorization decision can be represented as:

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
```

The Subject could potentially be:

* Human
* Organization
* Machine
* Device
* Software Agent
* System

The Action could be any recognized ADE Action.

This raises the possibility that Authorization is a general ADE semantic pattern rather than a concept limited to identity management.

---

## 9.10 Cross-Framework Test

The key question is:

> **Could an ADE framework other than ADE-IF require a general authorization decision?**

Potentially, yes.

Examples could include:

```text
Mission Framework
    ↓
Mission Control
    ↓
Authorization to alter mission state
```

or:

```text
Machine Framework
    ↓
Safety Control
    ↓
Authorization to stop equipment
```

or:

```text
Financial Framework
    ↓
Transaction
    ↓
Authorization to execute transfer
```

These examples show that authorization decisions may occur outside traditional identity management.

However, such frameworks may still depend on ADE-IF for identity-related authorization mechanisms.

---

## 9.11 General Authorization vs Identity Authorization

This suggests a possible distinction:

```text
General ADE Authorization
        │
        ├── Identity-based Authorization
        │       └── ADE-IF
        │
        ├── Role-based Authorization
        │
        ├── Resource Authorization
        │
        ├── Operational Authorization
        │
        └── Domain-specific Authorization
```

ADE-Core could potentially define the general semantic relationship without defining the mechanisms used to establish identity, authority, credentials, or access control.

---

## 9.12 Authorization as a Decision

Authorization may be better understood as a **decision or determination** rather than as a permanent property of an Entity.

For example:

```text
Entity:
Operator A

Capability:
Pause Machine

Request:
Pause Machine X

Context:
Emergency

Decision:
Authorized
```

The result may change if the context changes:

```text
Same Entity
Same Capability
Different Context
        ↓
Different Authorization Decision
```

This contextual nature distinguishes Authorization from Identity.

---

## 9.13 Relationship to Action

Authorization is directly related to Action.

A conceptual relationship is:

```text
Authorization
      │
      ├── permits ──> Action
      │
      └── denies ──> Action
```

This does not necessarily mean that an Authorization decision causes the Action.

An authorized Action may never occur:

```text
Authorization:
Permitted

Action:
Never performed
```

Likewise, an attempted Action may occur without authorization:

```text
Authorization:
Denied

Action:
Attempted
```

The authorization decision and the Action itself must therefore remain distinct.

---

## 9.14 Relationship to Time and Context

Authorization may be time-dependent and context-dependent.

For example:

```text
Authorization:
Permitted

Time:
09:00–17:00

Location:
Control Room

Action:
Pause Machine
```

Outside those conditions:

```text
Authorization:
Denied
```

This indicates that Authorization is not necessarily a permanent property of an Entity.

It is a contextual determination.

---

## 9.15 Current Assessment

Authorization has characteristics of both a general ADE semantic concept and a specialized identity/access-control function.

Evidence supporting a general Core concept includes:

* Authorization can apply to many types of Actions.
* The subject may be a Human, Machine, System, Organization, or Software Agent.
* Authorization can depend on Time, Location, State, Context, and Rules.
* Authorization may be relevant outside traditional identity management.

Evidence supporting ADE-IF specialization includes:

* Identity and Authentication frequently contribute to Authorization.
* Authority and Capability are closely associated with identity and access control.
* ADE-IF already provides detailed identity-related authorization structures.

Therefore, the current overlap does not justify immediately removing Authorization from ADE-Core.

---

## 9.16 Preliminary Finding

**Preliminary finding:**

Authorization should remain **under architectural review**.

There is evidence that ADE-Core may need a minimal general semantic concept representing a determination that an Action is permitted or denied within a defined context.

ADE-IF may then specialize Authorization for identity, authentication, authority, capability, credential, and access-control requirements.

A possible layered model is:

```text
ADE-Core
    │
    └── Authorization
          │
          └── general permission determination

ADE-IF
    │
    └── Identity Authorization
          │
          ├── Identity
          ├── Authentication
          ├── Authority
          ├── Capability
          ├── Credentials
          └── Identity Context
```

This remains a preliminary finding.

---

## 9.17 Current Ownership Status

```text
Authorization
      ↓
Undetermined
      ↓
Potential layered ownership
```

The final decision should consider the outcome of the Capability analysis and the broader role of Authorization across future ADE frameworks.

---

## 9.18 Questions Requiring Further Review

The following questions should be resolved:

1. Is Authorization fundamentally a general ADE concept?
2. Is Authorization a decision, state, relationship, or event?
3. Can Authorization exist without Identity?
4. Can Authorization apply to Machines or Systems?
5. Can Authorization apply to non-security Actions?
6. Does Authorization require Authority?
7. Does Authorization require Capability?
8. Can an Action be authorized without Authentication?
9. Can authorization be delegated?
10. Can authorization expire?
11. Can authorization be conditional?
12. Should authorization results be represented as States?
13. Should an Authorization decision have its own Identity?
14. Does ADE-Core need only the general concept while ADE-IF defines identity-specific authorization mechanisms?

---

## 9.19 Chain Review

The current preliminary ownership analysis of the related concepts is:

```text
Identity
    ↓
Core foundation
    +
ADE-IF specialization

Authentication
    ↓
ADE-IF

Authority
    ↓
Undetermined / potential Core foundation

Capability
    ↓
Undetermined
Ability vs Permission unresolved

Authorization
    ↓
Undetermined
Potential general Core semantic concept
with ADE-IF specialization
```

This chain should be reviewed as a complete architectural unit before any changes are made to the ADE-Core Core Model.

---

## 9.20 Next Review

The Identity and Authorization chain has now been analyzed at a preliminary level.

The next step is **not immediately another concept**.

The five concepts should first be reviewed together:

```text
Identity
Authentication
Authority
Capability
Authorization
```

The objective is to determine whether the preliminary findings form a coherent architecture.

Only after that review should changes to `CORE-MODEL.md` be considered.
---
# 10. Identity and Authorization Chain Review

**Status:** In Progress

## 10.1 Purpose

This section reviews the related concepts of:

* Identity
* Authentication
* Authority
* Capability
* Authorization

The purpose is to determine whether the preliminary ownership findings form a coherent architectural structure across ADE-Core and ADE-IF.

This review does not modify the Core Model or ADE-IF specifications.

---

## 10.2 Current Preliminary Findings

The ownership analysis currently identifies:

| Concept        | Preliminary Status                         |
| -------------- | ------------------------------------------ |
| Identity       | Core foundation with ADE-IF specialization |
| Authentication | ADE-IF                                     |
| Authority      | Potential Core foundation                  |
| Capability     | Undetermined                               |
| Authorization  | Undetermined; potential layered model      |

These findings must be evaluated together because each concept affects the meaning and role of the others.

---

## 10.3 Conceptual Dependency

The current relationship can be represented as:

```text
Entity
   │
   └── Identity
         │
         ▼
    Authentication
         │
         ▼
      Authority
         │
         ▼
     Capability
         │
         ▼
    Authorization
         │
         ▼
       Action
```

This diagram should not be interpreted as requiring every Action to pass through every concept.

For example, an Action may exist without Identity, Authentication, Authority, Capability, or Authorization.

The chain represents one possible identity and authorization pathway.

---

## 10.4 Identity

Identity has a strong case for remaining a foundational ADE-Core concept.

The minimum Core meaning is:

> **Identity provides a persistent reference to a specific Entity within an ADE context.**

This meaning is useful to multiple ADE frameworks and does not require authentication or authorization.

ADE-IF can build specialized identity structures upon this foundation.

---

## 10.5 Authentication

Authentication is more specialized.

Its primary purpose is to establish that an actor can demonstrate control of, or association with, an Identity.

Authentication therefore depends conceptually on Identity.

```text
Identity
   ↓
Authentication
```

The analysis currently supports ADE-IF ownership of Authentication.

ADE-Core does not require the technical mechanisms of Authentication to establish its foundational Entity and Identity model.

---

## 10.6 Authority

Authority differs from Authentication.

Authority may represent:

* Standing
* Role
* Jurisdiction
* Control
* Delegated authority
* Organizational authority
* Operational authority

These meanings can exist without authentication.

For example:

```text
Organization
   │
   └── Authority
         └── Regulatory jurisdiction
```

This supports continued consideration of Authority as a general ADE semantic concept.

However, identity-specific Authority structures may remain within ADE-IF.

---

## 10.7 Capability

Capability remains unresolved because the current model may combine two meanings:

```text
Capability
    ├── Ability
    │     What an Entity can do
    │
    └── Permission
          What an Entity is permitted to do
```

These meanings have different architectural implications.

An Entity can possess a physical or technical ability without being authorized to exercise it.

For example:

```text
Machine
Ability:
Lift 5,000 kg

Authorization:
Not permitted to lift current load
```

The distinction must be resolved before Capability can be assigned to a framework.

---

## 10.8 Authorization

Authorization is contextual.

It determines whether a particular Action is permitted under defined conditions.

A general model is:

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
```

This pattern is not inherently limited to identity management.

It could apply to:

* Humans
* Machines
* Software Agents
* Organizations
* Systems
* Resources

This provides evidence that a minimal general Authorization concept may have value within ADE-Core.

ADE-IF may then specialize Authorization for identity-based access control.

---

## 10.9 Core Boundary

The current analysis suggests the following possible boundary:

```text
ADE-Core
│
├── Entity
├── Identity
├── Authority
└── Authorization
       │
       └── general semantic foundation
```

while ADE-IF may provide:

```text
ADE-IF
│
├── Identity specialization
├── Authentication
├── Identity Credentials
├── Identity Claims
├── Identity Verification
├── Authority specialization
├── Capability
└── Identity-based Authorization
```

This remains a proposed architecture rather than a finalized decision.

---

## 10.10 Important Architectural Distinction

The existence of a concept in ADE-Core does not mean that ADE-Core must define every specialized use of that concept.

The architectural relationship may instead be:

```text
Core Concept
     ↓
Foundational Meaning
     ↓
Framework Specialization
     ↓
Domain Implementation
```

For example:

```text
ADE-Core
Identity
    ↓
ADE-IF
Identity Framework
    ↓
Identity Credentials
Verification
Authentication
Authorization
```

This allows ADE-Core to remain small while still providing common semantic foundations.

---

## 10.11 Preliminary Chain Model

The current evidence supports the following preliminary model:

```text
                     ENTITY
                        │
                        ▼
                    IDENTITY
                        │
              ┌─────────┴─────────┐
              │                   │
              ▼                   ▼
       AUTHENTICATION          AUTHORITY
              │                   │
              │                   ▼
              │              CAPABILITY
              │                   │
              └─────────┬─────────┘
                        ▼
                  AUTHORIZATION
                        │
                        ▼
                      ACTION
```

The model should not imply that Authentication is always required for Authorization or that Authority always produces Capability.

The actual relationships are contextual and require formal specification.

---

## 10.12 Cross-Framework Test

The proposed architecture should allow another ADE framework to use foundational concepts without importing the complete ADE-IF identity architecture.

For example:

```text
ADE-HTF
   │
   └── Entity
         └── Identity
```

and potentially:

```text
ADE-LF
   │
   └── Entity
         └── Authority
```

while ADE-IF can provide the specialized identity and access-control mechanisms:

```text
ADE-IF
   │
   ├── Identity
   ├── Authentication
   ├── Authority
   ├── Capability
   └── Authorization
```

This supports modularity between ADE frameworks.

---

## 10.13 Preliminary Ownership Matrix

| Concept        | ADE-Core | ADE-IF | Current Assessment                            |
| -------------- | -------: | -----: | --------------------------------------------- |
| Identity       |        ✓ |      ✓ | Core foundation + IF specialization           |
| Authentication |        — |      ✓ | ADE-IF                                        |
| Authority      |        ? |      ✓ | Potential Core foundation + IF specialization |
| Capability     |        ? |      ✓ | Undetermined                                  |
| Authorization  |        ? |      ✓ | Potential Core foundation + IF specialization |

The checkmarks indicate current architectural usage, not final ownership.

---

## 10.14 Architectural Risk

The primary risk is allowing ADE-Core to become a collection of concepts simply because they are useful to ADE-IF.

This would weaken the principle of a small and stable Core.

The opposite risk is removing concepts that are genuinely required as common semantic foundations.

The ownership process therefore needs to distinguish:

```text
Necessary foundational meaning
        versus
Specialized framework functionality
```

---

## 10.15 Current Assessment

The preliminary findings form a coherent layered architecture if the following principles are maintained:

1. Entity remains foundational.
2. Identity provides the general reference to an Entity.
3. Authentication remains an identity-specific process.
4. Authority is evaluated as a broader semantic concept.
5. Capability is not finalized until ability and permission are separated.
6. Authorization may have a general semantic meaning while being specialized by ADE-IF.
7. ADE-IF may extend Core concepts without redefining their foundational meaning.

---

## 10.16 Preliminary Conclusion

The current evidence supports a **layered Core-to-Framework architecture** rather than a simple division in which every identity-related concept belongs entirely to ADE-IF.

The strongest current model is:

```text
ADE-Core
    │
    ├── Entity
    ├── Identity
    ├── Authority
    └── Authorization
          │
          ▼
       ADE-IF
          │
          ├── Identity specialization
          ├── Authentication
          ├── Identity Credentials
          ├── Identity Claims
          ├── Verification
          ├── Capability
          └── Identity-based Authorization
```

However, **Authority, Capability, and Authorization require further review before final Core ownership is established.**

No change to `CORE-MODEL.md` should be made at this stage.

---

## 10.17 Next Decision Point

The next step is to review the entire ownership analysis and identify which concepts have enough evidence for a final ownership decision.

The current candidates are:

```text
Identity
Authentication
Authority
Capability
Authorization
```

The review should produce:

* Final ownership recommendations
* Required Core Model changes
* Required ADE-IF changes
* Concepts requiring additional research
* Any architectural questions that should be placed into ADE-CORE-FUTURE-WORK.md

---
# 11. Final Ownership Recommendations

**Status:** Proposed for Architectural Decision

## 11.1 Purpose

This section establishes proposed ownership decisions for the five concepts reviewed in the Identity and Authorization chain:

1. Identity
2. Authentication
3. Authority
4. Capability
5. Authorization

The purpose is to establish a clear architectural boundary between ADE-Core and ADE-IF before modifications are made to either framework.

These recommendations remain subject to the ADE governance and review process.

---

## 11.2 Identity

### Recommendation

**Identity should remain an ADE-Core foundational concept.**

### Reason

Identity provides a general mechanism for distinguishing and referencing an Entity.

This meaning is not limited to security, authentication, or access control.

Identity may be required by:

* ADE-Core
* ADE-HTF
* ADE-USLF
* ADE-LF
* ADE-IF
* Future ADE frameworks

The Core meaning should remain minimal.

### ADE-Core Responsibility

ADE-Core should define:

* What an Identity represents
* Its relationship to an Entity
* The distinction between Identity and Identifier
* The fact that an Entity may have multiple identities or identifiers
* The distinction between Identity and Authentication

### ADE-IF Responsibility

ADE-IF may define:

* Identity credentials
* Identity claims
* Identity verification
* Identity registration
* Identity management
* Identity federation
* Identity security mechanisms

### Decision

```text
Identity
    ↓
ADE-Core
    +
ADE-IF specialization
```

---

## 11.3 Authentication

### Recommendation

**Authentication should be owned by ADE-IF.**

### Reason

Authentication is a process for establishing control of, or association with, an Identity.

It is primarily concerned with identity assurance and access-control architecture.

Authentication requires mechanisms such as:

* Credentials
* Possession factors
* Knowledge factors
* Biometric factors
* Cryptographic methods
* Other verification mechanisms

These are specialized identity functions rather than foundational ADE semantic concepts.

### ADE-Core Responsibility

ADE-Core should recognize that Authentication is distinct from Identity where necessary for interoperability.

ADE-Core does not need to define authentication mechanisms.

### ADE-IF Responsibility

ADE-IF should define:

* Authentication
* Authentication methods
* Credentials
* Authentication events
* Authentication assurance
* Identity verification mechanisms
* Authentication status
* Authentication relationships

### Decision

```text
Authentication
    ↓
ADE-IF
```

---

## 11.4 Authority

### Recommendation

**Authority should remain an ADE-Core foundational concept, with specialized authority structures in ADE-IF.**

### Reason

Authority is broader than identity security.

Authority may represent:

* Legal authority
* Organizational authority
* Operational authority
* Regulatory authority
* Delegated authority
* Jurisdiction
* Control
* Role-based standing

These concepts may be required across multiple ADE frameworks.

For example:

```text
Organization
    ↓
Authority
    ↓
Jurisdiction
```

does not require Authentication.

Similarly:

```text
Machine
    ↓
Operational Authority
```

may be meaningful without an identity-security context.

### ADE-Core Responsibility

ADE-Core should define the general meaning of Authority and its relationship to Entities and Relationships.

ADE-Core should not define detailed identity-security mechanisms for establishing Authority.

### ADE-IF Responsibility

ADE-IF may define:

* Identity-linked Authority
* Delegated Authority
* Authority credentials
* Authority verification
* Authority levels
* Identity-based roles
* Authority inheritance

### Decision

```text
Authority
    ↓
ADE-Core
    +
ADE-IF specialization
```

---

## 11.5 Capability

### Recommendation

**Capability should be divided conceptually into Ability and Permission.**

### Reason

The analysis identified two different meanings currently represented by Capability.

### Meaning 1 — Ability

An Entity may have an inherent or technical ability.

Examples:

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

This is a general semantic concept.

### Meaning 2 — Permission

An Entity may be permitted to perform an Action.

Example:

```text
Authority:
Safety Officer

Permission:
Pause Machine
```

This is closely associated with authorization and identity/access-control systems.

These two meanings should not remain merged under a single ambiguous Core concept.

### Proposed Architecture

ADE-Core should use:

```text
Ability
    =
what an Entity can do
```

ADE-IF should use:

```text
Permission / Capability
    =
what an Entity is permitted to do
```

However, the exact naming of the ADE-IF concept requires further specification.

### ADE-Core Responsibility

ADE-Core should define:

* Ability
* The relationship between Ability and Action
* The relationship between Ability and Entity
* The possibility that Ability may be constrained by State, Time, Location, or other context

### ADE-IF Responsibility

ADE-IF should define:

* Permission-based capability
* Authority-derived permissions
* Identity-linked permissions
* Access-control capability
* Permission constraints
* Permission evaluation

### Decision

```text
Capability
    ↓
SPLIT

ADE-Core
    ↓
Ability

ADE-IF
    ↓
Permission / Capability
```

The final ADE-IF terminology remains subject to detailed design.

---

## 11.6 Authorization

### Recommendation

**Authorization should have a minimal foundational meaning in ADE-Core and specialized implementation in ADE-IF.**

### Reason

Authorization is broader than identity security.

The general semantic pattern is:

```text
Subject
    +
Requested Action
    +
Context
    +
Rules
    ↓
Authorization Decision
```

The Subject may be:

* Human
* Machine
* Organization
* Software Agent
* System

The Action may be operational, physical, digital, organizational, or domain-specific.

Therefore, a general Authorization concept can have value outside ADE-IF.

### ADE-Core Responsibility

ADE-Core should define the minimal semantic meaning:

> Authorization is a determination that an Action is permitted or denied within a defined context.

ADE-Core should not define:

* Authentication protocols
* Credential systems
* Access-control technologies
* Identity federation
* Specific policy engines
* Security implementation mechanisms

### ADE-IF Responsibility

ADE-IF may define:

* Identity-based Authorization
* Authentication-dependent Authorization
* Permission evaluation
* Access-control rules
* Identity policies
* Delegated authorization
* Credential-based authorization
* Security-specific authorization mechanisms

### Decision

```text
Authorization
    ↓
ADE-Core
    +
ADE-IF specialization
```

---

# 12. Final Ownership Matrix

The proposed ownership model is:

| Concept        | ADE-Core |                  ADE-IF | Final Recommendation                |
| -------------- | -------: | ----------------------: | ----------------------------------- |
| Identity       |        ✓ |                       ✓ | Core foundation + IF specialization |
| Authentication |        — |                       ✓ | ADE-IF                              |
| Authority      |        ✓ |                       ✓ | Core foundation + IF specialization |
| Capability     |  Ability | Permission / Capability | Split conceptually                  |
| Authorization  |        ✓ |                       ✓ | Core foundation + IF specialization |

This creates a clear architectural boundary.

---

# 13. Proposed Layered Architecture

The resulting architecture can be represented as:

```text
                         ADE-CORE
                            │
                 ┌──────────┼──────────┐
                 │          │          │
              ENTITY     IDENTITY    AUTHORITY
                 │          │          │
                 │          │          │
                 │          │          │
              ABILITY      │          │
                 │          │          │
                 └──────────┼──────────┘
                            │
                            ▼
                     AUTHORIZATION
                            │
                            │
                    ┌───────┴───────┐
                    │               │
                    ▼               ▼
                 ACTION          ADE-IF
                                    │
                         ┌──────────┼──────────┐
                         │          │          │
                    AUTHENTICATION PERMISSION IDENTITY
                                    │
                                    │
                                    ▼
                              SPECIALIZED
                              AUTHORIZATION
```

The diagram represents architectural layering, not a mandatory execution sequence.

---

# 14. What Changes in ADE-Core

Based on these recommendations, the following changes will eventually be required in `CORE-MODEL.md`.

### Identity

Retain Identity as a Core concept.

No major architectural removal is required.

### Authentication

Remove Authentication as a detailed Core concept.

Retain only enough reference to distinguish Identity from Authentication where necessary.

### Authority

Retain Authority as a Core concept.

Reduce the Core definition to its general semantic meaning.

Move detailed identity-specific authority mechanisms to ADE-IF.

### Capability

Replace the ambiguous Core definition of Capability with **Ability**.

The Core should describe what an Entity can do without implying permission.

### Authorization

Retain a minimal Core definition of Authorization.

Define it as a contextual determination that an Action is permitted or denied.

Detailed identity and security mechanisms remain in ADE-IF.

---

# 15. What Changes in ADE-IF

ADE-IF should eventually be reviewed to determine whether it requires:

* Authentication
* Identity Credentials
* Identity Claims
* Identity Verification
* Authority specialization
* Permission / Capability
* Identity-based Authorization
* Authorization Policies
* Delegated Authorization

ADE-IF should reference ADE-Core concepts rather than redefine them.

---

# 16. Important Architectural Principle

The distinction established by this analysis is:

```text
ADE-Core
    =
What concepts mean

ADE-IF
    =
How identity, authority, authentication,
permission, and authorization are specialized
and implemented
```

This prevents ADE-Core from becoming an identity-security framework while allowing ADE-IF to build a complete identity and authorization architecture on top of the Core.

---

# 17. Proposed Final Chain

The previous chain:

```text
Identity
    ↓
Authentication
    ↓
Authority
    ↓
Capability
    ↓
Authorization
    ↓
Action
```

should no longer be treated as a mandatory sequence.

The more accurate architecture is:

```text
ENTITY
  │
  ├── IDENTITY
  │      │
  │      └── ADE-IF
  │             └── AUTHENTICATION
  │
  ├── AUTHORITY
  │
  ├── ABILITY
  │
  └── RELATIONSHIPS
          │
          ▼
     AUTHORIZATION
          │
          ▼
        ACTION
```

ADE-IF may provide additional relationships among:

```text
Identity
Authentication
Authority
Permission
Authorization
```

according to its specialized identity architecture.

---

# 18. Final Preliminary Decision

The ownership analysis recommends the following:

```text
IDENTITY
    → ADE-Core

AUTHENTICATION
    → ADE-IF

AUTHORITY
    → ADE-Core
       + ADE-IF specialization

CAPABILITY
    → Split into:
       ABILITY → ADE-Core
       PERMISSION / CAPABILITY → ADE-IF

AUTHORIZATION
    → ADE-Core
       + ADE-IF specialization
```

These recommendations provide the architectural basis for the next phase.

They should be treated as **proposed architectural decisions** until incorporated through the ADE standards development and governance process.

---

# 19. Next Phase

The next phase is not to immediately rewrite the entire Core Model.

Instead, the following sequence should be followed:

```text
1. Review proposed ownership decisions
       ↓
2. Identify exact changes to CORE-MODEL.md
       ↓
3. Identify exact changes to ADE-IF
       ↓
4. Update Core documentation
       ↓
5. Update ADE-IF documentation
       ↓
6. Update README references where required
       ↓
7. Review consistency across repositories
       ↓
8. Commit the architectural changes
```

This preserves a clear record of why each change was made.
---
