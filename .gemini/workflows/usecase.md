---
description: Start a new AEM use case utilizing Gulli's architect-first workflow (SPEC_DEV.md + ROADMAP.md).
---

# AEM Use Case — Architect-First Workflow

**CRITICAL: Do NOT write any code, execute commands, or start building until this entire workflow completes Phase 5.**

## Phase 1: Interview Until 95% Confidence
Interview the user until you have **95% confidence** about what they actually want.
Ask probing questions across these dimensions:
- **Business & Functional:** What is the actual problem? End users? Acceptance criteria? AEM Author/Publish?
- **Technical Architecture:** Components, OSGi services, Sling models, HTL, clientlibs? Headless or HTL? Integrations? 
- **Constraints:** Performance, security, Dispatcher caching, existing utilities (ACS Commons)?
- **Assumptions:** "Why?" on key decisions. Edge cases. 

*Inform the user of your confidence level organically (e.g., "I'm at 80%, a few more questions...").*

## Phase 2: Create SPEC_DEV.md
Once at 95% confidence, create `SPEC_DEV.md` using the template at `.gemini/templates/SPEC_DEV.md`. 
Focus on **radical simplicity** and efficiency.
Discuss architecture for the feature in AEM 6.5 — keep it minimal and robust.

## Phase 3: Create ROADMAP.md
Create `ROADMAP.md` using the template at `.gemini/templates/ROADMAP.md`.
Include options with pros/cons (e.g., custom Sling Model vs Core Component extension).
Break down logical debugging and execution steps in Markdown first. Solve friction before involving the compiler.

## Phase 4: Autonomy Selection
Ask the user which autonomy mode they want to use for execution:
1. Agent-driven
2. Agent-assisted
3. Review-driven (Default & Recommended)
4. Custom

## Phase 5: Approval Gate
Present `SPEC_DEV.md`, `ROADMAP.md`, and the chosen autonomy mode.
**Ask:** "Do I have your approval to start execution based on this roadmap and spec?"
**STOP AND WAIT FOR APPROVAL.**

## Phase 6: Execute
Execute the steps in `ROADMAP.md` matching the chosen autonomy mode. 
- Setup components, bundles, HTL, OSGi configs.
- Run `mvn clean install` commands using Jabba JDK 11.
- In Review-driven mode, generate code/POM updates and ask for review before applying/deploying.

## Phase 7: Verify & Document
1. Ensure a full build and deployment to `localhost:4502` succeeds.
2. Produce a `walkthrough.md` summarizing what was accomplished.
