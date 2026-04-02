# AEM Learnings Project — Antigravity Instructions

## Project Overview

This is an **AEM 6.5.21** project ("aemlearnings") generated from the AEM Project Archetype. It uses **ACS AEM Commons** and the **WKND guide** as learning references.

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

1. **Full build (no deployment)**:
   ```powershell
   jabba use adopt@1.11.0-11
   mvn clean install -PautoInstallSinglePackage
   ```

2. **Deploy to local AEM Author** (`localhost:4502`):
   ```powershell
   jabba use adopt@1.11.0-11
   mvn clean install -PautoInstallSinglePackage -Daem.host=localhost -Daem.port=4502
   ```

3. **Deploy only a single module** (e.g., `core`):
   ```powershell
   jabba use adopt@1.11.0-11
   mvn clean install -PautoInstallBundle -pl core
   ```

4. **Deploy only `ui.apps`**:
   ```powershell
   jabba use adopt@1.11.0-11
   mvn clean install -PautoInstallPackage -pl ui.apps
   ```

## Important Notes

- Never use JDK versions other than 11 for this project. AEM 6.5 requires Java 11.
- Always activate Jabba JDK 11 before any `mvn` command.
- The deployment target is always `localhost:4502` unless explicitly stated otherwise.

## Workflows (Slash Commands)

| Command | What it does |
|---------|-------------|
| `/usecase` | **Start a new AEM use case.** Interviews you first (requirements engineering) until 95% confidence, produces a requirements spec + architecture diagram, gets your approval, and only THEN starts building. **Always use this when starting something new.** |
| `/deploy` | Build and deploy the project to `localhost:4502` using Jabba JDK 11. |

### Golden Rule for New Work

> **Never start coding a new use case without running `/usecase` first.**
> The agent must interview you, clarify assumptions, produce a spec, and get explicit approval before writing a single line of code.
