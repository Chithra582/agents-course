---
name: smolagents-code-tutor
description: "Teaches and debugs smolagents (CodeAgent, ToolCallingAgent, multi-agent systems) architectures."
---

# Smolagents Code Tutor

## Overview
The `smolagents-code-tutor` skill provides specialized architectural guidance, syntax debugging, and pedagogical instruction for Hugging Face's lightweight `smolagents` library.

## Core Smolagents Concepts
1. **CodeAgent vs. ToolCallingAgent:**
   - `CodeAgent`: Emits executable Python code blocks directly. Ideal for complex data processing, variable reassignment, and algorithmic workflows.
   - `ToolCallingAgent`: Emits standard JSON-based tool call actions. Ideal for strictly typed external API endpoints.
2. **Authorized Imports:** Ensure safety by explicitly whitelisting permitted Python libraries via `additional_authorized_imports`.
3. **Execution Sandbox:** Explain the local AST-based Python interpreter mechanism that safely parses and runs agent code.

## Debugging Workflow
- Identify missing `@tool` type hints or docstring descriptions.
- Rectify unauthorized import attempts or infinite execution loops.
