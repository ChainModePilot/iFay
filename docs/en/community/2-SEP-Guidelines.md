# 2. SEP (Specification Enhancement Proposal) Guidelines

## What is a SEP

A SEP (Specification Enhancement Proposal) is the formal proposal process for changes to the iFay specification. Any substantive modification to the iFay specification — whether adding a new module, modifying protocol behavior, or adjusting the iFay Profile data model — should go through the SEP process.

## Why SEPs Are Needed

iFay is an open standards ecosystem with multi-vendor implementations, and every change to the specification can potentially affect all implementers. The SEP process ensures that specification evolution is orderly, transparent, and traceable, giving all stakeholders the opportunity to participate in discussion and review.

## SEP Lifecycle

A SEP goes through the following stages from proposal to final implementation:

### 1. Draft

The proposer creates a SEP Issue on GitHub using the standard template, describing the motivation, proposed solution, and impact. A SEP in the Draft stage may be incomplete, but should contain enough information for the community to understand the intent of the proposal.

### 2. Discussion

The SEP enters a public discussion period lasting at least **14 days**. During this period:

- Community members and relevant working groups discuss the proposal
- The proposer revises and refines the proposal based on feedback
- Maintainers of related sub-projects assess the proposal's impact on their respective domains

### 3. Review

After the discussion period ends, Core Maintainers conduct a formal review of the SEP. During the review, the proposer may be asked to make further revisions or additions, such as:

- Adding backward compatibility analysis
- Completing an iFACTS test impact assessment
- Providing a comparative analysis of alternative approaches

### 4. Accepted / Rejected

Core Maintainers decide the final outcome of the SEP through a vote:

- **Accepted**: The SEP is approved and moves to the implementation stage
- **Rejected**: The SEP is rejected, with reasons recorded. The proposer may revise and resubmit based on feedback

### 5. Implemented

An accepted SEP enters the implementation stage. Implementation work can be carried out by the proposer or other contributors. During implementation:

- Related specification documents should be updated
- Reference code should be implemented (if applicable)
- iFACTS test cases should be written or updated

### 6. Final

After implementation is complete and passes review, the SEP enters its final state. At this point:

- Specification documents have been updated
- The iFACTS test suite has been updated accordingly
- Related documentation and guides have been updated

## SEP Template

When submitting a SEP, please include the following:

- **Title**: A concise description of the proposal
- **Motivation**: Why is this change needed? What problem does it solve?
- **Detailed Design**: Technical details and implementation plan of the proposal
- **Backward Compatibility**: Analysis of impact on existing specifications and implementations
- **iFACTS Impact**: Which compliance tests need to be added or modified
- **Alternatives**: Other approaches considered and their comparative advantages and disadvantages

## Who Can Submit a SEP

Anyone can submit a SEP. Whether you are a Core Maintainer, Maintainer, Contributor, or a user of the iFay ecosystem, if you believe the specification needs improvement, you are welcome to submit a proposal.

## Special Notes

SEPs involving protocol changes require special attention: since each iFay protocol (Faying, Telepathy, ICP, CAP, DTP, SSP) corresponds to an independent sub-project, the maintainers of the relevant protocols must participate in the review. For example, a SEP that modifies the behavior of the Control Authority Protocol (CAP) requires WG-Protocols working group maintainers to assess its impact on related modules such as the Device Driver Hub and FayGer runtime.
