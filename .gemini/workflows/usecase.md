---
description: Start a new AEM use case with requirements engineering interview before any code is written
---

# AEM Use Case — Requirements Engineering First

**CRITICAL: Do NOT write any code, create any files, scaffold anything, or start building until this entire workflow completes through Step 4.**

## Step 1: Interview Until 95% Confidence

Before doing anything else, interview the user until you have **95% confidence** about what they actually want — not what they think they should want.

Ask probing questions across these dimensions:

### Business & Functional Requirements
- What is the actual business problem being solved?
- Who are the end users? Authors? Developers? Site visitors?
- What does "done" look like? What's the acceptance criteria?
- Is this for AEM Author, Publish, or both?
- What AEM version? (This project uses **AEM 6.5.21**)

### Technical Architecture
- Does this involve custom components, templates, or pages?
- Does it need OSGi services, Sling servlets, or schedulers?
- Is there a frontend framework involved (React, Angular, vanilla)?
- Does it integrate with external systems (APIs, DAM, Analytics, Target)?
- Does it involve workflows, permissions, or replication?
- Headless (Content Services / GraphQL) or traditional (HTL/JSP)?

### Constraints & Context
- Are there performance requirements?
- Any existing code or components to build on?
- Timeline or complexity constraints?
- Does it need to work with Dispatcher caching?
- Any ACS AEM Commons utilities that could help?

### Assumptions to Challenge
- Dig into assumptions the user didn't know they had
- Ask "Why?" at least twice on key decisions
- Identify what they're NOT saying — gaps in the requirements
- Clarify edge cases and error handling expectations

**Keep asking questions until you genuinely feel 95% confident you understand the full picture. Tell the user your current confidence level after each round of questions (e.g., "I'm at about 60% confidence, let me ask a few more things...").**

## Step 2: Output Requirements Specification

Once you reach ~95% confidence, produce a **detailed requirements specification** as an artifact (`requirements.md`). Include:

- **Goal**: One-sentence summary of the use case
- **User Stories**: Specific user stories in "As a [role], I want [action], so that [benefit]" format
- **Functional Requirements**: Numbered list of what the system must do
- **Non-Functional Requirements**: Performance, security, scalability constraints
- **Out of Scope**: Explicitly state what this use case does NOT cover
- **Assumptions**: List every assumption made
- **Dependencies**: External systems, libraries, AEM features required

## Step 3: Architecture & Agent Plan

After the requirements spec, produce:

### Architecture Diagram
Create a **Mermaid diagram** showing:
- AEM components involved (components, templates, services, servlets, models, etc.)
- Data flow between layers (JCR → Sling Model → HTL → Frontend)
- Integration points with external systems
- Package/module structure within the aemlearnings project

### Implementation Plan
Create an `implementation_plan.md` artifact with:
- Proposed file/folder structure within `core/`, `ui.apps/`, `ui.content/`, `ui.frontend/`
- Ordered list of implementation steps
- Which existing project patterns to follow
- Testing strategy

## Step 4: User Approval Gate

**Present everything from Steps 2-3 to the user and explicitly ask:**

> "Here's my understanding and plan. Do I have your approval to start building? Any corrections?"

**DO NOT proceed to implementation until the user explicitly approves.**

## Step 5: Build

Only after explicit approval:

1. Create the `task.md` to track progress
2. Remember build/deploy requirements:
   - **JDK**: Use Jabba with JDK 11 (`jabba use adopt@1.11.0-11`)
   - **Deploy target**: `localhost:4502`
   - **Build command**: `mvn clean install -PautoInstallSinglePackage -Daem.host=localhost -Daem.port=4502`
3. Start implementation following the approved plan
4. Build incrementally — deploy and verify after each major milestone

## Step 6: Verify & Document

After implementation:
1. Build the full project and deploy to `localhost:4502`
2. Create a `walkthrough.md` summarizing what was built
3. Commit all changes to Git
