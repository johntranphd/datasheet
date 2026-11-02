# Coding frame v0.1

Status: **unreviewed draft.** Practitioner critique and methods review scheduled. Not yet applied to a defined population. Not yet pre-registered.

Changelog at the bottom. Every revision gets an entry and a reason.

---

## Unit of analysis

One **specification document set** for one interface, at one identified version, as of a stated freeze date.

A document set may span several published parts. Where it does, every part in scope is listed in the coding record, and a property defined in any part counts as defined. Coding one part of a multi-part standard and reporting it as the whole specification is an error.

## Scope of the document

The specification is what the publisher presents as the normative definition of the interface. It excludes tutorials, blog posts, reference implementations, and vendor marketing. Where a reference implementation provides a property the specification does not define, the code is still **not specified**, with a note. The question is what the published guarantees are, not what one implementation happens to do.

## Codes

| Code | Meaning |
| :-- | :-- |
| **S** specified | A named mechanism with defined semantics that a conforming implementation must or may provide, located in the document. |
| **P** partially specified | A mechanism at a coarser granularity than the dimension asks about; or an extension point in which the property could be expressed but is not defined; or a requirement stated without defined fields or semantics. |
| **N** not specified | The property is absent from the document. |
| **X** not applicable | The document's scope excludes the property. The coder must say why. |

**P is where inter-rater reliability dies.** The most common disagreement will be between P and N on a normative requirement with no mechanism, as in "implementations MUST provide access controls" with nothing further. The rule: a normative requirement naming the property codes **P**, even with no mechanism, because a conformance claim can be made against it. Silence codes **N**.

## Every code carries a locator

Each code is recorded with:

- the code
- the section heading or page supporting it
- a one-line justification in the coder's own words
- a verbatim quote where the decision turns on specific wording

A code with no locator is not a code and is excluded from the agreement statistics.

---

## Dimension 1. Action authorization

**Question.** Can a specific command, or a class of commands, be permitted or denied independently of session-level access?

**S** requires a defined mechanism operating at the granularity of an individual call or a named class of calls: a permission field, a policy object, a deny list, a per-operation scope.

**P** covers access control defined only at the session, connection, credential or role level, with no per-action granularity. Also covers a normative requirement to implement access control with no mechanism defined.

**N** means no access control of any kind is defined.

**Why it matters.** A restriction stated about materials has to become a decision about a particular operation. An interface with only session-level access can admit or exclude a caller, and can say nothing about which of that caller's commands should proceed.

---

## Dimension 2. Command record

**Question.** Is a record of what was commanded, with parameters and a timestamp, defined and required?

**S** requires a record with defined fields, normatively required of a conforming implementation.

**P** covers a record that is recommended rather than required, or required without defined fields, or defined only as a client-side responsibility with no schema.

**N** means no record is mentioned.

**Coder note.** Distinguish a record *of commands issued* from a record *of results returned*. Many interfaces define the latter. Only the former supports reconstructing what was attempted, including what was refused.

---

## Dimension 3. Refusal distinguishable from failure

**Question.** Is a deliberate policy refusal distinguishable, in the return value, from a transient or mechanical failure?

**S** requires distinct named error classes, or a distinct field, carrying that semantic distinction.

**P** covers an extensible error space in which the distinction could be expressed but is not defined, or a distinction present in prose but not in the return type.

**N** means refusals and failures share a return channel with no defined means of telling them apart.

**Why it matters.** A system that cannot distinguish the two cannot record which occurred, which means a run's record cannot establish whether a control fired or a machine faulted. Ordinary error-handling behavior then treats the two identically.

**Editorial constraint.** Code and report this dimension as a property of the specification. Do not describe operational consequences beyond the inability to record the distinction. Reporting what a gap is, not how to reach through it, is a standing rule.

---

## Dimension 4. Revocation in flight

**Question.** Can a command be revoked after acceptance and before completion, with a stated effect on partially executed physical operations?

**S** requires a defined abort or cancel, with stated semantics for an operation already underway.

**P** covers a cancel whose effect on in-progress work is unspecified or explicitly best-effort, and covers timeouts offered in place of revocation.

**N** means no mechanism.

**Coder note.** A timeout is not revocation. A timeout changes what the caller waits for. Revocation changes what the machine does.

---

## Dimension 5. Identity binding

**Question.** Is a command bound to the identity of the issuing party, and is a software agent distinguishable from a person?

**S** requires identity carried with the command, and a defined means of distinguishing an autonomous agent from a human operator.

**P** covers identity at session level only, or identity with no agent-versus-human distinction.

**N** means neither.

**Why it matters.** Attribution after the fact, and any policy that treats agent-initiated actions differently from human-initiated ones, both require this. Several published safety frameworks assume it.

---

## Dimension 6. Record integrity and external readability

**Question.** Is the record defined as append-only or tamper-evident, and is any party other than the operator given access to it?

**S** requires both: an integrity property, and defined access for a party other than the operator.

**P** covers one of the two.

**N** means neither.

**Why it matters.** The first five dimensions ask whether a control exists. This one asks whether anyone outside the operator could ever establish that it fired. A record written and owned solely by the party being examined is not evidence to a third party.

---

## Reliability and analysis

Two coders work independently and do not see each other's codes until both are complete.

Agreement is reported as Krippendorff's alpha with an ordinal distance metric, per dimension and overall. The codes are ordered S > P > N, so a one-step disagreement is not equivalent to a two-step one and a nominal kappa would misreport it. X is excluded from the distance computation and its frequency reported separately.

Threshold 0.70 for the main coding. A pilot on three specifications precedes it. If the pilot falls below threshold the frame is revised, the revision is recorded in the changelog with its reason, and both rounds are reported in the writeup.

Unresolved disagreements go to a third adjudicator. The adjudication rate is published.

Aggregate results are reported by dimension and by layer. No single interface's result is presented as representative of its layer.

---

## Known weaknesses of this frame

Stated here so they are attacked rather than discovered.

**The S/P boundary on normative-but-undefined requirements.** The current rule sends these to P. A reasonable coder could argue they are N, since nothing is actually specified. This is the single most likely source of disagreement and the pilot exists largely to test it.

**Multi-part standards.** A property defined in a part the coder did not retrieve codes as absent. The document-set listing is the only defense and it depends on the search being complete.

**Dimension 6 compresses two properties into one code.** Integrity and external access are separable and arguably deserve their own dimensions. They are combined to keep the frame at six. A reviewer may reasonably want them split.

**The frame asks what is defined, not what is adequate.** A specification could define all six properties badly. This instrument would code it S across the board. That is a deliberate limit of a specification review and the writeup must say so.

---

## Changelog

**v0.1, 2 November 2026.** Initial draft. Six dimensions, four codes, decision rules, locator requirement. Not reviewed by anyone. Published at this stage so the frame can be criticized before a population is coded against it.
