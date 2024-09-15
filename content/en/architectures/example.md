---
title: Example Arch
status: Completed
date: 2024-07-20
org_name: University of Michigan
org_team: Advanced Research Computing
org_url: https://arc-ts.umich.edu
email: killen.bob@gmail.com
org_description: |
  Advanced Research Computing provides research computing resources to The University of Michigan
  research projects and their collaborators. ARC provides High Performance Computing, machine
  learning, storage, data, private/public cloud analytical resources, along with a breadth of
  outreach and training services.
org_size: 10,000+ # size of entire org
user_size: 1,000+  # size of target userbase - could be internal team etc
industries:
- academia
- research
tags:
- academia
- hpc
- batch
- higher-ed
- private-cloud
- public-cloud
reference_architectures:
- AI/ML/Batch
- Secure CI/CD
---

Opening blurb Opening blurb Opening blurb Opening blurb Opening blurb Opening blurb Opening blurb Opening blurb Opening blurb Opening blurb Opening blurb Opening blurb 

## Diagram

```mermaid
sequenceDiagram
    autonumber
    Docsy user->>Discussion board: Ask question
    Discussion board->>Community member: read question
    loop Different strategies
    Community member->>Test instance: Investigate issue raised
    end
    Note right of Community member: After hours of investigation:
    Test instance-->>Community member: Come up with solution
    Community member-->>Discussion board: Propose solution
    Discussion board-->>Docsy user: check proposed solution
    Docsy user->>Discussion board: Mark question as resolved
    Docsy user->>Docsy user: Being happy
```