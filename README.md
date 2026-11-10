# Intelligent Application Modernisation

**Agents, skills and a worked example for teams modernising applications with AI assistance.**

Author: **Lavan Nallainathan** · [MIT licence](LICENSE) · [January 2026 provenance](PROVENANCE.md)

This pack connects system discovery, migration planning, testing, programme governance and implementation. Each agent has a defined job, supporting procedures, expected outputs and a human review gate. Teams can use the whole sequence or adopt one role at a time.

The original agents and skills were recorded in January 2026 in [ads_monolith_agents_skills_270126](https://github.com/lavann/ads_monolith_agents_skills_270126). This repository preserves that Git history and makes the pack, worked outputs and adoption guidance easier to find. The original agent and skill files are unchanged. See [Provenance](PROVENANCE.md) for exact commits and the distinction between the original work and this November 2026 publication.

## Start here

| What you want to do | Start with |
| --- | --- |
| Understand the approach and run your first agent | [Usage guide](guides/usage.md) |
| Explore the application, reports and tests | [Worked retail example](guides/worked-example.md) |
| Introduce the approach to a delivery team | [Team adoption guide](guides/team-adoption.md) |
| Check the origin, attribution and original versions | [Provenance and source history](PROVENANCE.md) |
| Browse the generated example deliverables | [Worked outputs index](docs/README.md) |

## The agent pack

| Agent | What it does | Main outputs |
| --- | --- | --- |
| [Documentation](.github/agents/documentation.agent.md) | Establishes what the existing system actually does. | HLD, LLD, ADRs and runbook |
| [Modernisation](.github/agents/modernisation.agent.md) | Plans an incremental, reversible migration. | Target architecture, migration plan and decision records |
| [Testing](.github/agents/testing.agent.md) | Establishes a safety net around current behaviour. | Test strategy, automated tests and CI |
| [Intelligent Migration](.github/agents/intelligent-migration.agent.md) | Connects the technical plan to delivery, governance and economics. | Programme plan, team model, risk/governance and ROI model |
| [Implementation](.github/agents/implementation.agent.md) | Implements one approved migration slice at a time. | Reviewed code, tests, documentation and rollback evidence |

The five supporting [skills](.github/skills) cover [system discovery](.github/skills/system-discovery.skill.md), [architecture reasoning](.github/skills/architecture-reasoning.skill.md), [test synthesis](.github/skills/test-synthesis.skill.md), [intelligent migration](.github/skills/intelligent-application-migration.skill.md) and [incremental refactoring](.github/skills/incremental-refactoring.skill.md).

These are the original Markdown procedures referenced by the agents. They retain their January `*.skill.md` format; do not assume they will be discovered as modern `SKILL.md` packages. The [usage guide](guides/usage.md) explains how to supply them explicitly and records a historical metadata mismatch.

## Try the worked example

The repository root contains the original .NET 9 retail monolith, its tests, and the agent-produced documents. Keeping the original layout preserves the agents' `.github/` and `/docs/` references.

```sh
git clone https://github.com/lavann/intelligent-application-modernisation.git
cd intelligent-application-modernisation
dotnet test RetailMonolith.sln --configuration Release
```

The automated tests use an in-memory database and do not need SQL Server. Running the application itself needs SQL Server or Windows SQL Server LocalDB; follow the [worked-example instructions](guides/worked-example.md).

To use the pack on another application, copy the five agent files, five skill files and [pack licence notice](.github/AGENT-PACK-NOTICE.md), then review them against that project's architecture, commands and approval rules. Full steps and example prompts are in the [usage guide](guides/usage.md).

## How teams use it

1. Establish a factual baseline with the Documentation agent and subject-matter review.
2. Agree a target architecture and a small first slice with the Modernisation agent.
3. Establish meaningful tests and CI before changing behaviour.
4. Agree delivery roles, risk controls, phase gates and cost assumptions with the Intelligent Migration agent.
5. Implement one approved slice, review the evidence and repeat.

Humans own scope, architecture decisions, approvals and release. Agent instructions assist delivery; repository permissions, CI and review controls enforce the boundaries. See the [team guide](guides/team-adoption.md) for roles, adoption stages and useful measures.

## Status and limitations

- This is a reusable reference pack with a teaching application, not a production service or a completed microservices migration.
- The worked documents are historical, AI-assisted examples. Cost estimates, productivity gains and completion statements inside them must be revalidated for any real engagement.
- The example preserves its original .NET 9 dependencies and known limitations. Assess the stack and update it for your own supported environment before production use.
- The existing application test suite passed **21/21** during packaging on **10 November 2026**. That verifies the included tests, not the effectiveness of every agent or a successful end-to-end migration. See [validation](guides/validation.md).

## Licence and attribution

The pack and original example are provided under the [MIT licence](LICENSE). Retain the copyright and permission notice when distributing copies or substantial portions. The [pack notice](.github/AGENT-PACK-NOTICE.md) provides a copy that can travel with the agent files. Bundled third-party libraries retain their own notices.

Suggested credit: **Lavan Nallainathan, Intelligent Application Modernisation — agents, skills and worked example; original agent pack recorded January 2026.** Source and commit links are in [PROVENANCE.md](PROVENANCE.md); citation metadata is in [CITATION.cff](CITATION.cff).
