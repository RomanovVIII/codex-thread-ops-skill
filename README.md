# Codex Thread Ops Skill

[![GitHub stars](https://img.shields.io/github/stars/RomanovVIII/codex-thread-ops-skill?style=social)](https://github.com/RomanovVIII/codex-thread-ops-skill/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

**Keep your Codex threads organized before they turn into a forgotten pile.**

![Codex Thread Ops social preview](assets/social-preview.png)

`codex-thread-ops` is a community Codex skill for people who work with many Codex threads across projects. It helps prevent duplicate discussions, unclear thread names, accidental operations on the wrong thread, and lost context across long-running projects.

**In short:** it gives Codex a safe workflow to create, rename, fork, archive, pin, hand off, and index project threads.

⭐ **If this skill is useful to you, star the repository.** It helps other Codex users discover the project.

[Русская версия](README.ru.md)

> Community skill. Not an official OpenAI project.

## Why Use It?

When you use Codex seriously, the thread list grows quickly. Without a simple system, the same topic gets discussed twice, useful context gets forgotten, and thread names stop being meaningful.

Codex Thread Ops adds a lightweight operating layer around thread management without turning your thread index into another knowledge base.

## What This Skill Does

`codex-thread-ops` gives Codex a workflow for thread hygiene:

- maintain a lightweight project thread index, commonly `THREADS.md`;
- record what active threads exist and what each one is about;
- compare that index with the live Codex thread list when thread structure is being changed;
- help decide whether to continue in an existing thread, create a new one, or rename/archive an old one;
- suggest short, memorable thread titles;
- verify the exact target before changing a thread: `threadId`, current title, and requested action;
- avoid confusing delegated `source_thread_id` values with the current thread.

The thread index is not a project knowledge base. It is a technical map of Codex conversations, used only when managing thread structure.

## Example Situations

- You want to start a new Codex thread, but the topic may already exist.
- You have too many old threads and want to archive stale ones.
- You need a concise title that will still make sense later.
- You want Codex to hand off a topic to another thread without mixing unrelated context.
- You want project-specific rules for when `THREADS.md` should be read or updated.

## Quick Start

Ask Codex to install this skill from GitHub:

```text
Use $skill-installer to install RomanovVIII/codex-thread-ops-skill with path codex-thread-ops.
```

Restart Codex after installation so the skill is discovered.

## Download

Download the ready-to-use ZIP from the latest release:

[Download codex-thread-ops-skill.zip](https://github.com/RomanovVIII/codex-thread-ops-skill/releases/latest/download/codex-thread-ops-skill.zip)

Manual install:

1. Extract the ZIP.
2. Copy the `codex-thread-ops` folder into the skills directory that your Codex installation scans, commonly:

```text
~/.codex/skills/
```

3. Restart Codex.

## Example Prompts

```text
Use $codex-thread-ops to check whether this topic already has a Codex thread.
```

```text
Use $codex-thread-ops to create a new thread for the database migration plan and suggest a short title first.
```

```text
Use $codex-thread-ops to archive stale threads and update THREADS.md.
```

## When Not To Use It

Do not use this skill for normal conversation summaries or content work inside a thread:

- "read the current thread"
- "summarize this thread"
- "based on this thread, write a plan"

Those are conversation tasks, not thread-structure operations.

## Repository Layout

```text
codex-thread-ops/
  SKILL.md
  agents/
    openai.yaml
```

The repository README, license, and preview image live outside the skill folder so the installed skill stays focused.

## Support The Project

If Codex Thread Ops helps you avoid duplicate threads, lost context, or a wrong-thread rename/archive/handoff, **give the repository a ⭐**.

Issues, pull requests, ideas, and feedback are welcome.

## License

MIT
