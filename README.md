# AI-Project-Scaffolding-Agent

Overview

AI Project Scaffolding Agent is an automation-focused AI agent designed to transform a high-level project idea into a ready-to-use starter codebase.

The goal of the agent is to allow a user to:

Provide a GitHub repository link

Provide a natural language prompt describing the desired project

Automatically:

Clone the repository

Generate a full project scaffold (files, folders, configs)

Commit and push the generated code back to GitHub

This project was built as part of an AI Agents Hackathon, with a focus on real-world orchestration, automation, and agent-driven development workflows.

Intended Architecture

The system was designed with the following components:

1. Webhook-based Agent Trigger (Kestra)

A webhook endpoint receives user input:

repo (GitHub repository URL)

prompt (project description)

Each webhook call triggers an isolated agent execution.

2. Orchestration Layer (Kestra)

Kestra is used as the orchestration engine to:

Manage executions

Handle retries and logging

Provide observability via UI

Each step of the agent (clone, generate, commit, push) was planned as an individual task.

3. Execution Environment (Docker-based)

Tasks were intended to run in containerized environments for:

Reproducibility

Isolation

Cloud portability

4. AI Code Generation (Planned)

An LLM-based step would:

Interpret the user prompt

Generate boilerplate code (e.g. Node.js API, auth setup, folder structure)

Write files into the cloned repository

5. GitHub Automation (Planned)

Final steps would:

Commit generated files

Push changes back to the user’s repository using a GitHub token

Current Status

⚠️ Project not fully completed

While the webhook trigger, orchestration flow, and execution pipeline were successfully designed and partially implemented, the project could not be fully completed within the hackathon timeframe due to environment-level execution constraints, including:

Container filesystem permission restrictions

Docker-in-Docker execution limitations

Plugin and execution sandbox constraints during local development

These issues prevented reliable filesystem mutation (e.g. git clone, file generation) inside the orchestrated execution environment.

What Was Successfully Achieved

✅ Webhook-triggered agent execution
✅ Orchestration using Kestra
✅ End-to-end execution visibility via Kestra UI
✅ Containerized execution model
✅ Clear agent workflow design
✅ Production-oriented architecture decisions

Lessons Learned

Real-world AI agents require robust orchestration, not just LLM calls

Infrastructure and execution environments are often the hardest part

Container permissions and execution models must be designed early

Separating orchestration from execution logic improves reliability

These learnings directly reflect real industry challenges in building autonomous developer agents.

Future Work

With more time, the following improvements would complete the agent:

Move filesystem-heavy tasks to a dedicated execution service

Use persistent repositories instead of in-memory storage

Integrate LLM-based code generation as a first-class step

Secure GitHub token handling via secrets management

Add templates for common project types (Node.js, Python, FastAPI, etc.)

Why This Project Still Matters

Even though the full automation loop was not completed, AI Project Scaffolding Agent demonstrates:

A realistic agent architecture

Production-grade orchestration thinking

Clear separation of concerns

Awareness of real infrastructure challenges

This project represents a strong foundation for a real AI developer agent, not a toy demo.
