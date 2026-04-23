# The AI-First Organization

## Table of Contents

- [Core Concepts](#core-concepts)
  - [The Context Folder](#1-the-context-folder)
  - [AI Calls](#2-ai-calls)
  - [AI Social Network](#3-ai-social-network)
  - [Agent Archetypes](#4-agent-archetypes)
  - [Vibe-Coded Apps](#5-vibe-coded-apps)
- [Software Stack](#software-stack)
- [Good Practices](#good-practices)
  - [Context First](#context-first)
  - [Levels of AI Usage](#levels-of-ai-usage)
  - [Turn Creation Into Verification](#turn-creation-into-verification)
  - [Collaborate Through Git/Pull Requests](#collaborate-through-gitpull-requests)
  - [Separate Data From Apps](#separate-data-from-apps)
- [Getting Started](#getting-started)
- [Subprojects](#subprojects)

> **Work in progress.** Last updated: April 2026. I'll keep adding concepts and practices as I learn what works.

---

AI is changing the operating system of organizations.

We went from pen and paper to files and databases. From in-person meetings to Slack and Zoom. Each technological shift brought new tools — but the processes stayed roughly the same. People still write documents, attend meetings, update spreadsheets, and chase each other for context.

AI changes the processes themselves. AI can organize internal knowledge, do work, ask questions, gather information, and maintain a living picture of what's happening. This isn't about adding a chatbot to the company workflow — it's about rethinking how an organization operates when AI is a first-class participant.

This document collects the best practices that I collected so far to run an AI-first organization.

---

## Core Concepts

### 1. The Context Folder

Every organization has implicit knowledge — in documents, in people's heads, in scattered tools. When someone needs to understand a process, the latest state of a project, or a past decision, they go talk to people or dig through docs.

An AI-first organization keeps a **context folder**: a shared, structured collection of everything the organization knows. When anyone needs an answer, they ask the AI — and it finds it.

#### Building the context

**Import existing knowledge.** Take every relevant document in the organization and put it in the context folder. Convert files to Markdown where possible. Organize into subfolders if it helps, but it's not strictly necessary — the AI can navigate a flat structure just fine.

**Update continuously.** Every meeting, every new idea, every decision — drop it into the context. You don't need to manually figure out which files to update. Give the AI the new information (a transcript, a note, a brain dump) and it determines which context files need to change. It might update one file or ten. It might create new ones.

The AI maintains a living log of what has happened in the organization. Ideally, the context folder includes a **meetings** subfolder to track this history.

#### How it works in practice

You use a coding agent in a terminal or application. You feed it new information. It updates the context and creates a pull request. Others review and merge it. There's always a human in the loop.

### 2. AI Calls

An **AI call** is a structured conversation between a person and an AI. The AI asks questions one at a time, follows up based on answers, and produces a clean transcript.

AI calls can be:
- **Run on-demand** — "I need to think through this problem"
- **Scheduled by someone else** — "Answer these questions about the Q2 roadmap by Friday"
- **Scheduled by an AI** — an agent realizes it needs human input and books time on your calendar

Use cases: organizing your thoughts, being prompted with the right questions, brainstorming ideas, debriefing after a project, collecting input from team members asynchronously.

The output is a Markdown transcript — a portable artifact that flows into the context folder or any other workflow.

> See [AI Call](https://github.com/nicola/ai-call) for a skill that implements this.

### 3. AI Social Network

Beyond the context that people create (with AI assistance), there's knowledge that agents proactively go out and gather.

The **social network folder** is a living directory of people, organizations, entities, and brands that matter to you. You maintain a list of who to track. Agents periodically scan these profiles online, cross-reference them with your context, and surface what's relevant.

This isn't limited to social media. It's essentially an **AI-augmented CRM** — tracking people, companies, partners, investors, candidates, or anyone relevant to your organization. The AI maintains the relationships, surfaces connections, and keeps everything current.

Over time, this becomes a kind of **personalized feed**. You can ask "what happened last week?" and get an AI-generated summary of activity across your network — curated by your own AI for your own purposes.

Agents update this folder either when prompted or autonomously (using tools like [OpenClaw](https://openclaw.com) or similar autonomous agent runners).

### 4. Agent Archetypes

A dedicated folder where the organization crafts and maintains **shared agents** — so individuals don't have to build them from scratch.

Example: if your organization reviews proposals, there could be an **evaluator agent** maintained by the company. Anyone can use it, and it follows the organization's standards.

Agents are just files — Markdown instructions that tell AI how to behave for a specific task. Version them in Git like everything else.

### 5. Vibe-Coded Apps

An **apps folder** where anyone in the organization can build visualizations, tools, computations, or scripts on top of the context data.

Because the context is structured and accessible, you can build dashboards, reports, analysis tools — anything that reads the organization's knowledge and presents it in useful ways.

The key rule: **separate data from apps.** Don't hardcode organizational data into applications. Keep the data in the context folder so it can be used by as many apps as possible.

---

## Software Stack

An AI-first organization runs on four layers:

| Layer | What | Why |
|-------|------|-----|
| **Git** | Version control for everything | Every change is tracked, PRs provide review and accountability, full history of how knowledge evolved |
| **Context folder** | Shared Markdown files — the org's source of truth | Linking between files, no duplication, navigable by both humans and AI |
| **Coding agent** | [Claude Code](https://claude.ai), [Codex](https://openai.com/codex), or [Pi](https://github.com/mariozechner/pi) | Reads and writes to the context folder, executes tasks, creates pull requests |
| **Transcription tool** | [Handy](https://handy.computer) or similar voice-to-text | Lowers the barrier — just speak and the AI captures it |

---

## Good Practices

### Context First

If there's new information — a meeting happened, a decision was made, someone learned something — it goes into the context first. Before building an app, before sending an email, before anything else. The context folder is the source of truth.

### Levels of AI Usage

There are three levels, and an AI-first organization uses all of them:

1. **Single-threaded.** Talk to an AI through a chatbot. One conversation, one task. This is where most people start.

2. **Multi-agent.** Ask the AI to spin up multiple agents to work on a task. You can even have several agents produce competing versions of the same work — then pick the one you like most.

3. **Autonomous.** Don't even prompt the AI. Give it the context, the latest to-dos, and let it figure out what needs doing. It creates pull requests. You review. This is the most advanced level and requires trust and good review practices.

And there are experimental approaches like **auto-research** — asking AI to run in a loop, iterating on something to improve a specific metric.

### Turn Creation Into Verification

Instead of doing the work yourself, let the AI generate it. Instead of designing one version of a website, ask the AI to generate multiple versions — each as a pull request. You review, pick what you like, discard what you don't.

This flips your role from **creator** to **verifier**. It's faster and scales better.

Some verification still requires humans. But over time, you can build AI to verify certain things too. This is an open problem worth investing in.

### Collaborate Through Git/Pull Requests

In an AI-first organization, people shouldn't directly edit files. You tell the AI what you want. It drafts the changes and opens a pull request. Others review.

Multiple people can work simultaneously — each directing their own AI, each producing PRs. Collaboration becomes **concurrent pull requests** rather than sequential editing.

Today this requires Git, which isn't for everyone. Better tools will emerge. But the principle stands: humans direct, AI executes, review happens through PRs.

### Separate Data From Apps

Keep organizational data in the context folder. Keep applications in the apps folder. Never hardcode data into apps.

This ensures the data remains accessible to every tool, every agent, and every future use case you haven't thought of yet.

---

## Getting Started

1. **Pick a coding agent.** [Claude Code](https://claude.ai), [Codex](https://openai.com/codex), or [Pi](https://github.com/mariozechner/pi) (recommended) all work.

2. **Open an empty folder.** This will become your organization's knowledge base.

3. **Install the [AI Call](https://github.com/nicola/ai-call) skill.** This lets you drop context into the system through conversation — just talk, and the AI captures it.

4. **Get a transcription tool.** [Handy](https://handy.computer) works well for voice-to-text.

5. **Start talking.** Run an AI call about what your organization does. Let the AI build your first context files from that conversation. Iterate from there.

6. (Optional) **Install the [`agents.md`](agents.md) from this repo.** It encodes the practices above so your AI follows them automatically.


---

## Subprojects

| Project | Description |
|---------|-------------|
| [`agents.md`](agents.md) | Machine-readable version of these practices. Drop it into your project and your AI agent follows them automatically — context first, PRs for changes, separate data from apps. |
| [AI Call](https://github.com/nicola/ai-call) | A skill that turns any coding agent into a structured interviewer. Ask questions one at a time, follow up naturally, produce a clean transcript. Works with Pi, Claude Code, and Codex. |
