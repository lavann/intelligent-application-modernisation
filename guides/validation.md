# Publication validation

Author: Lavan Nallainathan

Date: 10 November 2026

## Scope

Validation covers preservation of the source pack, repository guidance and the existing application's automated tests. It does not establish that every agent produces correct results on an arbitrary application, that the proposed migration is complete, or that sample ROI assumptions are realised benefits.

## Application baseline

Source revision: `c3ed208326eccf0c6237dbd5c0fb6c171bcf0b7e`.

Environment: Windows x64, .NET SDK **9.0.314**.

```sh
dotnet test RetailMonolith.sln --configuration Release --logger "trx;LogFileName=baseline.trx" --results-directory TestResults
```

Result: **21 passed, 0 failed, 0 skipped**. Restore and Release build completed. The original source produced five nullable-reference compiler warnings. Tests use the in-memory database provider; a SQL Server-backed interactive run and the historical dev-container configuration were not validated.

The repository retains its CI workflow so the published revision can be checked independently in GitHub Actions. Refer to the actual workflow run for its result; local success is not a claim of remote CI success.

## Source and documentation checks

The source manifest records byte-level hashes and original Git blob IDs. Packaging checks compare preserved files against that manifest, resolve relative file links in the new guidance and confirm the agent-to-skill dependencies are present.

The January metadata mismatch in `intelligent-application-migration.skill.md`, the unimplemented `/health` route mentioned in historical text, and sample documents' inconsistent dates and financial assumptions are described in the usage and worked-example guides. They are retained as historical source, rather than silently presented as corrected or newly approved results.

## Further validation for an adopting team

Run a representative task with the team's actual assistant, model, tool permissions and source application. Review outputs against code and stakeholder knowledge, measure rework, and verify execution evidence before expanding use. Add acceptance, integration, accessibility, security and operational checks appropriate to the application.
