---
name: create-skill
description: "Use when turning a repeatable workflow into a reusable skill, creating a new SKILL.md for this repo, packaging multi-step guidance, or teaching Copilot a standard operating procedure as a discoverable workflow."
user-invocable: true
---

# Create a Reusable Workflow Skill

Use this skill when you need to package a process, review checklist, debugging method, or recurring workflow into a reusable skill for this repository or a user profile.

## Goal

Turn a repeatable workflow into a discoverable skill that an agent can invoke with clear triggers, practical steps, and verifiable completion criteria.

## Decision Flow

1. Determine whether the task is a repeated process or a single, one-off action.
2. If it is a broad, always-on pattern that should apply across most work, prefer an instruction instead of a skill.
3. If it is a scoped method, multi-step checklist, or playbook with decision points, use a skill.
4. If it is a single focused action with inputs, prefer a prompt instead.
5. If it needs separate tool restrictions or isolated context, prefer a custom agent instead of a skill.

## Process

### 1. Identify the workflow
- Capture the exact step-by-step sequence.
- Note any decision points or branching logic.
- Define what success looks like and what quality bar must be met.
- Separate hard constraints from preferences.

### 2. Choose the scope
- Workspace-wide and team-shared: place the skill under `.github/skills/<name>/SKILL.md`.
- Personal and reusable across multiple workspaces: use the user prompt customization area instead.

### 3. Draft the skill frontmatter
- `name`: short, clear, and consistent with the folder name.
- `description`: include real trigger phrases and explicit use cases in the form "Use when...".
- `user-invocable`: set to `true` when the skill should be discoverable as a slash-command workflow.
- Keep the frontmatter minimal and valid YAML.

### 4. Draft the body
Include these sections:
- A concise purpose statement
- Scope and constraints
- Decision flow or branching logic
- Ordered steps for execution
- Quality checks or completion criteria
- Output expectations or final summary format

### 5. Validate the skill
Before finalizing:
- Confirm the file is in the correct folder.
- Verify YAML frontmatter syntax is valid.
- Check that the description is specific enough to trigger the skill.
- Ensure the workflow is concrete, actionable, and not vague.
- Remove any content that is too broad or resembles general instructions.

## Quality Bar

A strong skill should:
- solve a real, recurring workflow
- be executable without excessive reasoning from the agent
- include clear decision points
- stay focused on one domain or method
- define a concrete completion checklist

## Output Expectation

After creating or updating a skill, return:
1. the location of the skill file
2. a brief summary of what the skill packages
3. any notable assumptions or follow-up improvements
4. suggested prompts the user can try with the new skill

## Example prompt

- "Create a reusable skill for validating HTML/CSS page changes before shipping."
- "Package our debugging workflow into a skill for this repository."
- "Turn our front-end review checklist into a reusable SKILL.md."
