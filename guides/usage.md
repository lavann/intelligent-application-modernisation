# Using the agents and skills

Author: Lavan Nallainathan

## Choose a starting point

For a first run, clone this repository and work on a new branch. The retail source, agents, skills, tests and sample outputs are already in the expected locations. Start with documentation: it is a bounded way to check whether the agent reads the real system and produces useful evidence.

For an existing application, create a branch in that application's repository. Copy the five files from `.github/agents/`, the five files from `.github/skills/`, and `.github/AGENT-PACK-NOTICE.md` into the same paths there. Review filename collisions individually and merge with existing project conventions. Keep the notice with the copied pack.

Do not copy the retail application's generated `/docs/` into another project as if it described that project. Use the worked outputs as examples of structure; generate and validate your own content.

## Configure the assistant

The pack contains `.agent.md` definitions for GitHub Copilot-compatible custom-agent tooling. In VS Code, open the repository folder, select the intended harness, inspect the custom-agent configuration, and choose the required agent from the agent dropdown. Check that it loads without file errors. Current setup and verification steps are in [VS Code's custom-agent guide](https://code.visualstudio.com/docs/agent-customization/custom-agents).

Explicitly attach or ask the assistant to read the agent's referenced skill files. Verify from its response and tool activity that it used the right source files. If the agent is not discovered, check the selected harness, repository folder and file errors before changing its instructions.

For other assistants, supply the selected agent and its skill files as task context and translate tool configuration to that assistant's supported format. This is a manual adaptation route, not a claim that the pack has been tested on every assistant.

### Historical format and compatibility

The five skill files are Markdown procedures at `.github/skills/*.skill.md`. They are preserved as authored in January 2026. They are not packaged as directories containing `SKILL.md`, and automatic skill discovery is not assumed.

The original `intelligent-application-migration.skill.md` has an inconsistent YAML header: it names `incremental-refactoring` and describes implementation, while the body contains the intended programme-level procedure. For the preserved example, reference the file explicitly and use its **Reasoning Framework** for programme planning alongside `intelligent-migration.agent.md`. It does not authorise implementation. When adapting the pack, correct that metadata in your own reviewed commit before using metadata-based discovery.

The original agent files contain a `version` field and do not declare tool allowlists. Check configuration errors and actual permissions in your assistant. Prose such as "no code changes" is an instruction, not a technical permission boundary. Planning roles need repository reading and document editing; implementation and testing roles need separately approved execution capabilities.

## Run the stages

Read each agent's inputs, guardrails and acceptance criteria before invocation. Review the output before authorising the next stage.

| Stage | Agent | Supporting skills | Human acceptance |
| --- | --- | --- | --- |
| Understand | Documentation | System discovery | Technical owner verifies source references, behaviours and gaps. |
| Plan | Modernisation | System discovery; architecture reasoning | Architecture and product owners approve boundaries, first slice and rollback. |
| Protect | Testing | Test synthesis | Engineer verifies meaningful assertions, test results and known gaps. |
| Govern | Intelligent Migration | Intelligent application migration | Delivery, business and technical owners agree responsibilities, risks and assumptions. |
| Deliver | Implementation | Incremental refactoring; test synthesis | Reviewer checks the approved slice, passing tests, operational changes and rollback. |

The sample favours container deployment and incremental service extraction. Treat those as design choices to review for your application. Modularisation or retaining the monolith may be more appropriate; agree any adaptation before implementation.

## Example prompts

Select the named agent and include its supporting files before sending a prompt.

### Documentation

```text
Document this repository using documentation.agent.md and system-discovery.skill.md.
Cite the real paths and symbols you inspect. Produce or update the HLD, LLD,
ADRs and runbook. Record missing evidence. Do not change application code.
Finish with a list of files changed and the questions requiring human review.
```

### Modernisation

```text
Using the reviewed HLD, LLD and ADRs, propose an incremental migration plan.
Read the architecture-reasoning skill. State the deployment and data constraints,
compare plausible boundaries, and define one small first slice with tests,
acceptance criteria and rollback. Stop for review before implementation.
```

### Testing

```text
Use the approved migration plan and test-synthesis skill to establish a baseline.
Protect the existing cart and checkout behaviour. Run the tests, report actual
results and known gaps, and explain any minimal changes needed for testability.
Do not implement a migration slice in this task.
```

### Intelligent Migration

```text
Read the approved system documentation, migration plan and test strategy.
Use intelligent-migration.agent.md and the Reasoning Framework in
intelligent-application-migration.skill.md to prepare a delivery plan, team model,
risk/governance record and ROI model. Label assumptions, identify decision owners,
and ask for missing business constraints. Do not treat sample savings as evidence.
```

### Implementation

```text
Implement only the approved slice named [slice name] in docs/Migration-Plan.md.
Check the programme, architecture, test and risk documents first. If a required
input is missing or contradictory, stop. Run the agreed checks and report the
changes, results, remaining risks and rollback steps for human review.
```

## Review and repeat

Keep the model, assistant version, input commit, chosen agent, changed files and test evidence with each run. Check unsupported claims against the application and its users. Update the plan when evidence changes, and obtain approval for changes in scope. Each implementation slice should remain small enough to inspect and reverse.
