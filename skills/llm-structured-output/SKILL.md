---
name: llm-structured-output
description: >
  Get reliable JSON, enums, and typed objects from LLMs using response_format, tool_use, and schema-constrained decoding across OpenAI, Anthropic, and Google APIs.
risk: safe
source: community
date_added: "2026-03-12"
---

# LLM Structured Output

## What This Skill Does

Extract typed, validated data from LLM API responses instead of parsing free-text. This skill covers the three main approaches: OpenAI's `response_format` with JSON Schema, Anthropic's `tool_use` block for structured extraction, and Google's `responseSchema` in Gemini. You will learn when each approach works, when it breaks, and how to build retry logic around schema validation failures that every production system encounters.

## When to Use This Skill

- The user needs to extract structured data (JSON objects, arrays, enums) from an LLM response
- The user is building a pipeline where LLM output feeds directly into code (database writes, API calls, UI rendering)
- The user asks about `response_format`, `json_mode`, `json_object`, or `json_schema` in OpenAI
- The user asks about using Anthropic's `tool_use` or `tool_result` blocks for data extraction (not for actual tool execution)
- The user asks about Zod schemas with `zodResponseFormat()` from the `openai` npm package
- The user needs to parse LLM output into Pydantic models using `instructor`, `marvin`, or manual validation
- The user is getting malformed JSON, missing fields, or wrong types from LLM responses and needs a fix
- The user asks about `controlled generation`, `constrained decoding`, or `grammar-based sampling` in local models

Do NOT use this skill when:
- The user wants free-form text generation (summaries, essays, chat)
- The user is asking about Zod for form validation or API input validation (use `zod-validation-expert` instead)
- The user needs prompt engineering for better text quality (not structure)
- The user wants to call real external tools/APIs (this skill covers using tool_use as a structured output hack, not actual tool orchestration)

## Core Workflow

## Examples

## Never Do This

## Edge Cases

## Best Practices
