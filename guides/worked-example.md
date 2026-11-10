# Worked example: retail monolith

Author: Lavan Nallainathan

This is the original teaching application and its AI-assisted outputs from the January source repository. It demonstrates how the agent roles connect. It does not demonstrate that the proposed migration was completed or that forecast savings were realised.

## What is included

The ASP.NET Core 9 Razor Pages application contains a product catalogue, cart, checkout, orders and inventory, with Entity Framework Core and SQL Server. A mock payment gateway keeps the example self-contained. The application remains at the repository root so project references and expected paths continue to work.

| Input or stage | Inspect the evidence |
| --- | --- |
| Application | [Program.cs](../Program.cs), [Pages](../Pages), [Services](../Services), [Models](../Models), [Data](../Data) |
| Screens | [Images](../Images) |
| Current-system analysis | [HLD](../docs/HLD.md), [LLD](../docs/LLD.md), [Runbook](../docs/Runbook.md) |
| Architecture and migration planning | [Target architecture](../docs/Target-Architecture.md), [Migration plan](../docs/Migration-Plan.md), [ADRs](../docs/ADR) |
| Testing | [Test strategy](../docs/Test-Strategy.md), [test source](../RetailMonolith.Tests), [CI workflow](../.github/workflows/ci.yml) |
| Programme and team | [Intelligent Migration plan](../docs/Intelligent-Migration-Plan.md), [team model](../docs/Intelligent-Team-Model.md) |
| Risk and economics | [Risk and governance](../docs/Risk-and-Governance.md), [ROI and budget](../docs/ROI-and-Budget.md) |

## Run the automated checks

Install a .NET 9 SDK compatible with the original project. From the repository root:

```sh
dotnet restore RetailMonolith.sln
dotnet build RetailMonolith.sln --configuration Release --no-restore
dotnet test RetailMonolith.sln --configuration Release --no-build
```

These tests use EF Core's in-memory provider. They do not require a live SQL Server. The packaging validation passed 21 tests; see [validation](validation.md) for environment and limits.

The tests cover cart and checkout services and application startup. They are a baseline, not comprehensive acceptance, browser, security or SQL Server compatibility coverage.

## Run the application locally

The interactive application needs SQL Server. On Windows, the original development configuration uses SQL Server LocalDB and the `RetailMonolith` database. Use a disposable sample database. Startup applies migrations and seeds example data.

With the .NET 9 SDK and LocalDB available:

```sh
dotnet run --project RetailMonolith.csproj --launch-profile http
```

Open `http://localhost:5068`. The original HTTPS profile uses `https://localhost:7108` and requires a trusted development certificate.

For another SQL Server instance, set `ConnectionStrings__DefaultConnection` in your local environment or secret store before starting the app. Supply your own development credentials; do not commit them. The retained `.devcontainer/` files are historical development scaffolding with an example database password. Review them before using Codespaces or containers; those paths were not validated during packaging.

The sample registers health-check services but does not map a `/health` endpoint in `Program.cs`. Some historical outputs say otherwise. Use the actual source and assertions as evidence and record discrepancies when evaluating agents.

## Walk through the agent workflow

1. **Create a branch.** Preserve the checked-in outputs so you can compare your run with the January snapshot.
2. **Documentation:** run the Documentation agent against the source. Check its descriptions of the cart, checkout, persistence and mock payment flow.
3. **Modernisation:** review the HLD/LLD and agree scope before requesting a new migration plan. Compare the first slice and rollback with the example.
4. **Testing:** inspect the baseline tests, run them and identify missing behaviours. Approve changes separately from migration implementation.
5. **Intelligent Migration:** supply real or explicitly hypothetical constraints. Review team, phase, risk and financial models as assumptions requiring decisions.
6. **Implementation:** choose one approved slice only after its prerequisites and review gates are satisfied. The repository contains the starting application and planning outputs, not a completed target architecture.

Example prompts and dependencies are in the [usage guide](usage.md). To compare runs, record the input commit, assistant and model, configuration, elapsed time, review corrections and final evidence.

## Read the historical outputs critically

The outputs are preserved rather than retrospectively rewritten. Some document headers contain `2025-01-23`; those embedded dates are not the provenance evidence. The verified source commits are dated January 2026. Some documents label themselves "Active", "Complete" or "Ready for migration"; those are historical generated statements, not current approval.

The ROI model contains hypothetical productivity improvements and figures that require reconciliation. Its summary investment range differs from the detailed labour table. It is useful as a review exercise and a structural example, not an approved budget or a measured benefit case.

The application contains teaching shortcuts, including a shared guest identity, mock payments and startup database migration. Do not use it as a production security or operational baseline. Choose and validate a supported stack for your own application.
