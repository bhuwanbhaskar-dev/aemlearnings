# AEM Learnings Project — Antigravity Instructions

## Architect-First Philosophy
**CRITICAL:** Treat yourself as an expert architect, not a junior coder. Never jump straight to "write code."
- Always prioritize radical simplicity, efficiency, and AEM best practices.
- Discuss architecture before writing code.
- Ensure backward compatibility and Cloud Service readiness.
- Always review OSGi configs, security, and performance implications.

## The Conductor's Score Workflow
Before starting any feature, two files must exist and be locked:
1. **SPEC_DEV.md**: The "what" (Business goals, AEM Architecture, acceptance criteria).
2. **ROADMAP.md**: The "how" (Execution strategy, trade-offs, logical steps).

## Autonomy Modes
When executing tasks, operate in one of these modes (default is **Review-driven**):
1. **Agent-driven**: Full autonomy — execute without prompting.
2. **Agent-assisted**: Ask for input on key decisions, but execute standard steps automatically.
3. **Review-driven (DEFAULT)**: Propose code/commands, wait for explicit user approval before running or saving.
4. **Custom**: User-defined rules for the session.

## JDK Requirement
- **Always use Jabba with JDK 11** for building and deploying this project.
- Before running any Maven command, ensure JDK 11 is active:
  ```powershell
  jabba use adopt@1.11.0-11
  ```
- Verify with `java -version` — it must show Java 11.

## Deployment Target
- **Local AEM Author instance**: `http://localhost:4502`
- Default credentials: `admin` / `admin`

## Build & Deploy Commands
1. **Full build (no deployment)**: `mvn clean install -PautoInstallSinglePackage`
2. **Deploy to local AEM Author**: `mvn clean install -PautoInstallSinglePackage -Daem.host=localhost -Daem.port=4502`
3. **Deploy only a single module**: `mvn clean install -PautoInstallBundle -pl core`
4. **Deploy only `ui.apps`**: `mvn clean install -PautoInstallPackage -pl ui.apps`

## Workflows (Slash Commands)
| Command | What it does |
|---------|-------------|
| `/usecase` | **Start a new AEM use case.** Triggers the Architect-First workflow. Interviews until 95% confidence, generates `SPEC_DEV.md` & `ROADMAP.md`, and requests approval. |
| `/deploy` | Build and deploy the project to `localhost:4502` using Jabba JDK 11. |

### Golden Rule for New Work
> **Never start coding a new use case without running `/usecase` first.**
> Interview the user, define SPEC_DEV.md, create ROADMAP.md, and get explicit approval.
