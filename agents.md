# AI-First Organization

You are an AI agent working within an AI-first organization. Follow these rules.

## Structure

This repository is organized into:

- `context/` — The organization's source of truth. Markdown files covering projects, processes, decisions, people, and history.
- `context/meetings/` — Meeting transcripts and notes, chronologically organized.
- `social-network/` — Profiles of people, organizations, and entities the org tracks. Updated by agents.
- `agents/` — Shared agent definitions (Markdown files) for recurring tasks.
- `apps/` — Visualizations, scripts, and tools built on top of the context data.

## Rules

1. **Context first.** When you receive new information (a transcript, a note, a decision), update the relevant files in `context/`. Create new files if needed. Never let knowledge exist only in conversation.

2. **Always create a PR.** Never commit directly to main. Every change — context updates, new files, app changes — goes through a pull request for human review.

3. **Update across files.** A single piece of new information may affect multiple context files. Check broadly and update everything that's affected.

4. **Use Markdown.** All context and documentation is Markdown. Use links between files (`[[file]]` or `[text](path)`) to connect related content. Use tables where they help. Never duplicate text — link to it.

5. **Separate data from apps.** Apps in `apps/` read from `context/` and `social-network/`. Never hardcode organizational data into application code.

6. **Preserve history.** When updating context files, don't delete old information unless it's wrong. Add to it, mark things as superseded, or move outdated content to an archive section.

7. **Be concise.** Context files should be scannable. Use headers, bullet points, and short paragraphs. Avoid filler.

## When updating context from a meeting or transcript

1. Read the full transcript.
2. Identify which existing context files are affected.
3. Update each affected file with the new information.
4. If the meeting introduces a new topic not covered by any existing file, create a new file in the appropriate subfolder.
5. Save the raw transcript in `context/meetings/` as `YYYY-MM-DD - [Title].md`.
6. Create a single PR with all changes.

## When asked to gather intelligence

1. Research the requested person, organization, or topic.
2. Write or update the relevant file in `social-network/`.
3. Cross-reference with `context/` — note any connections or relevance to current projects.
4. Create a PR.

## When building apps

1. Place all code in `apps/[app-name]/`.
2. Read data from `context/` or `social-network/` — never copy it into the app.
3. Include a short README in the app folder explaining what it does and how to run it.
