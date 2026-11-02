# Search strategy

Status: **written, not executed.** The population does not exist yet. This file is published so the search can be criticized before it is run, and so that the executed version can be diffed against what was planned.

## Population

Publicly retrievable specifications for interfaces by which software commands laboratory instruments or orchestrates laboratory workflows, at an identified version as of a stated freeze date.

Stratified across four layers:

1. **Device control.** Interfaces that command an individual instrument.
2. **Orchestration and scheduling.** Interfaces that sequence work across instruments.
3. **Protocol representation.** Languages in which an experimental procedure is expressed for execution.
4. **Agent-to-tool.** Interfaces by which a software agent discovers and invokes capabilities.

## Sources to search

**Standards bodies and consortia.** The OPC Foundation specification register, including the laboratory and analytical device companion specifications. The SiLA Consortium. ISO and IEC catalogs. ASTM. SLAS. IEEE.

**Open-source registries.** Package and repository search for libraries that command laboratory instruments and publish an interface specification rather than only generated API reference.

**Vendor documentation portals** for instrument makers with the largest installed base, recording for each whether a specification is publicly retrievable without a commercial relationship.

**Citation chains.** Backward and forward from the laboratory automation standards literature and from the device standards themselves.

**Snowball.** Three practitioners asked to name interfaces the search missed. Every addition recorded with its source, so the snowball contribution is visible in the flow diagram.

## Inclusion

Include a document if it specifies an interface by which software commands a laboratory instrument or orchestrates a laboratory workflow, is publicly retrievable, is in English, and has an identifiable version as of the freeze date.

## Exclusion

Exclude pure data-format and results-reporting standards with no command semantics. Record the decision for each, since the boundary is a judgment and a reader may disagree.

Exclude internal documentation with no stable public location.

## Recorded as a result, not an exclusion

Every interface identified as in use for which **no specification is publicly retrievable**. This is a category of finding. If a substantial share of the installed base runs on documents nobody outside the vendor can read, that bounds what any external party can verify, independently of what the readable specifications say.

## Reporting

A flow diagram in the style of a systematic review: identified, screened, excluded with reasons, included, plus the separate count of identified-but-unretrievable.

## Known weaknesses

**"Largest installed base" is not operationalized.** No public register of installed laboratory instruments exists that I know of. The current plan is to use vendor self-reported deployment claims and published market analyses, both weak, and to state the weakness rather than imply a census.

**Language restriction to English** will exclude specifications from at least one major standards tradition. Recorded as a limitation.

**The four-layer stratification is mine.** A practitioner may reasonably cut the stack differently, and the panel critique exists partly to test it.
