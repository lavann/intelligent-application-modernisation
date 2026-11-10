# Adopting the pack as a team

Author: Lavan Nallainathan

The pack helps a team organise work and evidence across a migration. It is most useful when technical analysis, delivery planning and human decisions stay connected. Begin with one application and one bounded outcome.

## Start with a pilot

1. Choose an application with accessible source, an available subject-matter expert and a manageable first slice.
2. Record the delivery baseline: effort, cycle time, defects, test coverage and operational constraints. Distinguish measured data from estimates.
3. Review the pack against your approved tools, data handling, architecture and delivery rules.
4. Run documentation and planning first. Compare outputs with the actual system and the people who use it.
5. Establish a test baseline and agree the first implementation slice.
6. Review the pilot's results before expanding to more applications or increasing autonomy.

## Keep decision ownership explicit

| Role | Owns | Useful agent support |
| --- | --- | --- |
| Product or application owner | Business outcomes, behaviour to preserve, priorities and acceptance | Requirement and workflow clarification |
| Technical lead or architect | System evidence, architecture, boundaries and rollback design | Documentation and Modernisation |
| Delivery lead | Sequencing, dependencies, capacity and escalation | Intelligent Migration |
| Engineer | Implementation, tests, source control and operational changes | Testing and Implementation |
| Quality, security and operations reviewers | Independent checks and release readiness | Review of generated evidence |
| Sponsor or accountable owner | Investment, risk acceptance and major go/no-go decisions | Review of programme and financial assumptions |

Roles can be combined in a small team, but authoring and approval responsibilities should remain clear. An agent does not become the accountable owner of a decision because it drafted the document.

## Use the outputs as a shared delivery record

- Keep the architecture, migration plan, test strategy and governance records in version control with the application.
- Link every slice to its scope, acceptance criteria, tests and rollback steps.
- Record unresolved questions with an owner and a decision date.
- Review PRs for evidence and behaviour, not only whether generated prose looks complete.
- Carry lessons from completed slices into the next plan and configuration update.

The included team model and ROI document demonstrate possible structures. Their staffing levels, rates, productivity assumptions and financial conclusions are illustrative. Recalculate them from your own evidence and include uncertainty and sensitivity analysis.

## Measure outcomes without assuming a benefit

| Question | Useful evidence |
| --- | --- |
| Did the team deliver faster? | Comparable scope, elapsed time, human effort and review/rework time |
| Did quality improve? | Escaped defects, meaningful passing tests, regressions and user acceptance |
| Did the approach reduce risk? | Reversible slices, exercised rollback, fewer unsupported assumptions and closed risks |
| Was it economical? | Engineering/review costs, tool consumption, operating costs and actual benefits |
| Can another team reproduce it? | Setup time, missing prerequisites, configuration changes and reviewed outputs |

Report neutral or negative results as well as gains. Generated lines of code and documents are activity measures; they do not establish business value on their own.

## Scale through a maintained shared pack

Choose an owner for the shared configuration. Pin a known commit, review updates, and record local adaptations rather than silently changing every team's instructions. Revalidate after changes to models, tools, frameworks or organisational standards.

Use a short feedback cycle: observed problem, evidence, proposed instruction change, representative trial, review, then adoption. Keep the [MIT notice](../.github/AGENT-PACK-NOTICE.md) and source provenance with redistributed copies.
