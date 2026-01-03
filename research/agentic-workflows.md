# Research: Agentic Coding Workflows

**Status:** Active | **Last Updated:** Jan 02, 2026

## 🎯 Objective

Evaluating the efficiency of AI agents in establishing complex cloud infrastructures and identifying the boundary where AI automation fails.

## 🧪 Experiment: The "Single Prompt" Setup Myth

Attempted to delegate the entire environment setup (Secrets, Branching, Boilerplate) to an agent.

### Outcome: **FAILED**

- **Reason 1:** Context limitations regarding 3rd-party UI interactions (Neon Dashboard, Cloudflare Settings).
- **Reason 2:** Meta-framework volatility. TanStack Start/Vinxi is evolving faster than LLM training data, leading to legacy code suggestions.

## 🔄 Revised Strategy: "Human Architect, Agent Execution"

- **Architect (Human):** Defines the environment, pins versions, handles 3rd party linking/secrets.
- **Executor (Agent):** Scaffolds Drizzle schemas, writes server functions, generates UI boilerplate based on strict architectural rules.

## 📝 Findings

- AI is a **multiplier of competence**, not a replacement for fundamental knowledge.
- Infrastructure-as-Code (IaC) is the only way to eventually make agents "aware" of the cloud state.
