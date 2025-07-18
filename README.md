# IPC-Solutions (Sequential and partial-order plans)

Repository containing solutions of IPC problems from classical domains, including partial-order plans generated using 1) minimum reordering (mr) based on Muise et al. (JAIR 2016), and 2) minimum reinstantiated reordering (mrr) based on Waters et al. (IJCAI 2020).
## Solution Approaches

| Approach | Description | Key Characteristics | Origin |
|----------|------------|---------------------|--------|
| **lama_solutions** |  Sequential Plans | satisfiable solutions using LAMA planner | LAMA (Richter et al., 2010)
| **op_solutions** | Sequential Plans | optimal solutions using LM-Cut optimal planner | LM-Cut (Helmert et al., 2009)
| **mr_opsb** | Partial-Order Plans, generated by Minimum Reordering (MR), from the solutions of LAMA | Allow reordering plan actions, encodes operator symmetry breaking constraints (OPSB) | [Muise et al. (JAIR 2015)] 
| **mrr_opsb** |  Partial-Order Plans, generated using Minimum Reinstantiated Reordering (MRR) | Allow reinstantiations of action parameters, encodes operator symmetry breaking constraints (OPSB) | [Waters et al. (IJCAI 2020)] 

## Repository Structure (Exact Layout)
```bash
IPC-Solutions/
├── IPC/ # IPC contests, domains, and problems
├── lama_solution/ # Satisfiable solutions
│ ├── contest/ # IPC contest number
│ │ ├── domain/ # Problem domain (e.g., blocksworld)
│ │ │ ├── problem/ # Specific problem instance
│ │ │ │ ├── sas_plan.1.lama # LAMA output plan
│ │ │ │ └── [...] # other LAMA output plans
│ │ │ └── [...] # Other problem instances
│ │ └── [...] # Other domains
│ └── [...] # Other contests
│
├── op_solutions/ # Optimal solutions
│ └── [Same structure as lama_solution/]
│
├── mr_opsb/ # Partial-order plans (LAMA → MR conversion)
│ ├── contest/
│ │ ├── domain/
│ │ │ ├── instances/problem/
│ │ │ │ ├── sas_plan.1.lama/mr_results # Reordered plans
│ │ │ │ └── [...] # Additional MR outputs
│ │ │ └── [...]
│ │ └── [...]
│ └── [...]
│
└── mrr_opsb/ # Partial-order plans (LAMA → MRR conversion)
└── [Same structure as mr_opsb/]
```
## Key Relationships

```mermaid
graph TB
    L[lama_solutions] -->|input| M[mr_opsb] --> P1[partial-order solutions]
    L -->|input| M2[mrr_opsb] -->  p2[partial-order solutions]
