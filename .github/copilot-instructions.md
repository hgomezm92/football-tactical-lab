# Copilot Instructions - Football Tactical Lab

## 1. Project Context

Football Tactical Lab is a personal project whose goal is to
progressively build a tool for analysing real football match data and,
in later phases, experimenting with models that can study hypothetical
tactical scenarios.

The first data source will be StatsBomb Open Data.

The planned evolution is:

1. Importing and understanding real data.
2. Basic match analysis.
3. Building football and tactical metrics.
4. Comparing and exploring teams and players.
5. Simple statistical models.
6. Experimenting with hypothetical scenarios.
7. In advanced phases, possible counterfactual models and tools for
   interacting with the system through agents.

The project must NOT attempt to build a complete football simulator from
the beginning.

## 2. Learning Objective

The main objective of the project is to learn AI-assisted software
development using GitHub Copilot as an agent.

The user wants to progressively learn about:

- software architecture;
- application design;
- backend and frontend development;
- databases;
- testing;
- data analysis;
- applied statistics;
- machine learning when necessary;
- development using AI agents;
- MCP and other agentic tools when there is a real need.

Do not assume that the user has an in-depth knowledge of statistics,
probability, or machine learning.

When a technical decision introduces an important concept that the user
probably does not know, explain it before implementing it.

The AI should act both as an implementer and as a technical mentor.

## 3. Development Principles

### Simplicity Before Sophistication

Do not introduce architectural complexity that is unnecessary for the
current phase of the project.

If a decision can be postponed without blocking development, postpone it.

Do not introduce microservices, distributed systems, queues, caches,
cloud services, or other advanced infrastructure without a concrete and
justified need.

Prefer solutions that are simple, maintainable, and easy to understand.

### Avoid Over-Architecture

Do not create abstractions, interfaces, classes, design patterns, or
layers simply because they are common in large projects.

The architecture should evolve with the project's real needs.

### Prioritise Learning

When several reasonable solutions exist, prioritise the one that helps
the user understand the system better, provided it does not introduce a
significant technical disadvantage.

Do not hide important decisions behind generated code.

### Do Not Assume Knowledge

When a task involves unfamiliar or potentially complex concepts:

1. briefly explain the concept;
2. explain why it is necessary;
3. present the relevant alternatives;
4. propose a solution;
5. implement it afterwards.

Long explanations are not necessary for trivial changes.

## 4. Working Method

Before making important changes:

1. inspect the repository and existing code;
2. identify the files that will be affected;
3. briefly explain the proposed approach;
4. identify relevant risks or decisions;
5. implement afterwards.

Do not modify files unrelated to the task.

Do not implement functionality that was not requested.

Do not perform large refactorings as part of a small task unless they
are necessary to complete that task correctly.

If there is significant uncertainty about the requirements, ask before
implementing.

## 5. Code

Prioritise:

- clear code;
- descriptive names;
- small functions where natural;
- well-defined responsibilities;
- minimal dependencies;
- code that is easy to test;
- idiomatic solutions for the language in use.

Do not use unnecessary design patterns.

Do not duplicate logic when reuse is clearly beneficial, but do not
create premature abstractions either.

## 6. Testing

Tests are part of the implementation.

When adding functionality with meaningful logic:

- identify the main cases;
- identify edge cases;
- create appropriate tests;
- run the relevant tests after the changes.

Do not create artificial tests solely to increase coverage.

Tests must verify real behaviour.

## 7. Football Data and Analysis

Football metrics must have an explicit definition.

Do not present a metric as an objective fact when it is actually a
definition created within the project.

When designing a new metric:

1. define exactly what it is intended to measure;
2. identify the required data;
3. explain its possible limitations;
4. consider alternatives;
5. document the definition;
6. implement tests with known examples.

Always distinguish between:

- directly observed data;
- calculated variables;
- inferred variables;
- hypotheses or models.

Do not assume that the data provides information it does not actually
contain.

## 8. Statistics and Machine Learning

Do not introduce statistical or machine-learning models simply because
they can be used.

There must first be a concrete question that justifies the model.

Before implementing a model:

- explain the statistical problem we are trying to solve;
- identify the relevant variables;
- explain understandably what the model does;
- identify its main assumptions and limitations;
- distinguish correlation from causation;
- avoid unjustified causal claims.

The goal is not only to obtain a result, but also for the user to
understand what it means and what it does not mean.

## 9. External Data and Costs

The project should initially prioritise free data and services.

StatsBomb Open Data will be the first data source.

Do not introduce dependencies on commercial services or paid APIs unless
the user explicitly requests them.

When functionality depends on a specific data source, document its
limitations.

## 10. Git and Changes

Keep changes small and coherent.

Do not mix the following in a single change:

- new functionality;
- unrelated refactoring;
- formatting changes;
- architectural changes.

When appropriate, suggest small and descriptive commits.

## 11. Fundamental Rule

Do not optimise only to finish the task.

Optimise for building a system that the user can understand, maintain,
and extend.

If a solution seems unnecessarily complex, point it out.

If an important decision can be postponed, point it out.

If there is a simpler way to learn the same concept, prefer it.

## Language

Use English for all software-related artefacts:

- source code;
- variables;
- functions;
- classes;
- modules;
- database schemas;
- API endpoints;
- configuration;
- technical comments;
- Git commits;
- README and technical documentation.

Use established English technical terminology rather than translating
terms literally from Spanish.

The user may communicate with the agent in Spanish. This does not change
the language conventions for the project.

The user-facing application may initially use Spanish. Do not introduce
internationalisation infrastructure until it is actually needed.
However, avoid architectural decisions that would make future
internationalisation unnecessarily difficult.

## Task Decomposition

At the beginning of each development phase, help the user decompose the
phase into small, ordered implementation tasks.

Tasks should be independently understandable and preferably small
enough to implement and review in a single development cycle.

Do not implement an entire phase unless explicitly requested.

Before implementing a task, identify relevant tests and verification
steps.

## Engineering Practices

Introduce engineering practices progressively when they solve a real
problem in the project.

Do not introduce CI/CD, Docker, complex testing infrastructure,
databases, MCP servers, skills, or other tooling merely because they are
considered standard in modern software projects.

When a new practice becomes relevant, explain:
1. what problem it solves;
2. why the current approach is insufficient;
3. what the simplest implementation would be.
