# Datasheet

**What laboratory automation control interfaces actually specify for authorization, audit and reconstructability.**

A datasheet is the authoritative statement of what a component does and does not guarantee. This project produces one for every publicly published control interface by which software commands laboratory instruments.

Porcupine Labs. Maintained by John D. Tran, PhD.

---

## Why

When software commands a laboratory instrument, the instruction passes through an interface whose specification is a public document. That document sets the ceiling on what any safeguard built above it can do. If the specification defines no way to permit or deny a particular action, no deployment can enforce one, however the operator configures it. If it defines no record of what was commanded, no facility can produce one.

Every proposal to govern that boundary assumes an answer to this. Procurement language, institutional review conditions, model deployment commitments and funder requirements all rest on an assumption about what the interface permits. The assumption is currently untested, which makes it possible to write a requirement no shipping interface can satisfy, and equally possible to omit one that would have been free to include.

This repository holds the coding instrument, the worked example, and the coded results as they accumulate.

I searched for a systematic coding of this and did not find one. The people I asked, among them capability-evaluation organizations and engineers working inside autonomous laboratory companies, could not point me to one.

---

## Status, honestly

| Component | State |
| :-- | :-- |
| Coding frame | **v0.1, unreviewed.** Practitioner critique and a methods review are scheduled, not done. |
| Worked example | **One interface coded.** Model Context Protocol, 2025-03-26 revision. See `analysis/`. |
| Population | **Not yet defined.** The search strategy is written, not executed. |
| Coded dataset | **One row.** `data/codes.csv` carries the schema and the single worked example. |
| Agreement statistics | **None.** Single-coder so far, which is why this is a worked example and not a result. |
| Pre-registration | **Not yet posted.** |

Nothing here is a finding about the field. One interface coded by one person is a demonstration that the instrument works, and that is all it claims to be.

---

## The six dimensions

Each specification is coded on each dimension as **specified**, **partially specified**, **not specified**, or **not applicable**, against the written decision rules in `frame/coding-frame-v0.1.md`.

1. **Action authorization.** Can a specific command, or a class of commands, be permitted or denied independently of session-level access?
2. **Command record.** Is a record of what was commanded, with parameters and a timestamp, defined and required?
3. **Refusal distinguishable from failure.** Is a deliberate policy refusal distinguishable, in the return value, from a transient or mechanical failure?
4. **Revocation in flight.** Can a command be revoked after acceptance and before completion, with a stated effect on partially executed physical operations?
5. **Identity binding.** Is a command bound to the identity of the issuing party, and is a software agent distinguishable from a person?
6. **Record integrity and external readability.** Is the record defined as append-only or tamper-evident, and is any party other than the operator given access to it?

Dimension 6 is an addition to the original five. The first five ask whether a control exists. The sixth asks whether anyone outside the operator could ever check that it fired.

---

## What is in here

```
frame/coding-frame-v0.1.md   the instrument: dimensions, codes, decision rules
frame/search-strategy.md     how the population will be defined, before it is
analysis/mcp-2025-03-26.md   the worked example, with verbatim quotes
data/codes.csv               coded results, one row so far
CITATION.cff                 citation metadata
```

---

## Method commitments

**Every code carries a locator.** A code with no page or section reference supporting it is not a code.

**The frame is coded against the document, not against the implementation.** A vendor whose product does something the specification does not define still codes as not specified, because the point is what the published guarantees are.

**Two independent coders, with agreement reported.** Codes are ordinal, so agreement will be reported as Krippendorff's alpha with an ordinal distance metric rather than a plain kappa, which would treat a one-step disagreement as equal to a three-step one. Threshold 0.70. If the pilot falls below it, the frame is revised, the revision is documented, and both rounds are reported.

**Interfaces with no publicly retrievable specification are a result, not an exclusion.** If a substantial share of the installed base runs on documents nobody outside the vendor can read, that bounds what any external party can ever verify, and it belongs in the findings.

**Nothing here reports how to exploit anything.** Every statement is about what a published document does or does not define, which is a claim about absence in public material.

---

## Contributing

The frame is published at v0.1 specifically so it can be attacked before the population is coded. If you maintain one of these interfaces, or build on one, the most useful thing you can do is tell me which dimension is wrong, which is missing, or where a decision rule would make you code the same document two different ways.

Open an issue. Disagreements about a published code are the point, not a problem.

---

## License

Frame and data: CC BY 4.0. Attribute and reuse freely, including in a competing review.
