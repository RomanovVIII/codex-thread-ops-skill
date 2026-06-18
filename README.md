# Codex Thread Ops Skill

`codex-thread-ops` is a Codex skill for safe thread-structure operations: creating, renaming, forking, archiving, pinning, handing off between threads, and maintaining a project thread index such as `THREADS.md`.

The skill is intentionally narrow. It should trigger for thread management, not for ordinary phrases such as "read the current thread" or "based on this thread".

## What It Helps With

- Verify the exact target thread before a mutation: `threadId`, current title, and requested action.
- Avoid confusing a delegated `source_thread_id` with the active thread.
- Propose short, clear thread titles before creation or rename.
- Keep a project thread index updated when local project rules define one.
- Prefer reversible operations such as archive over deletion.
- Handle missing or limited thread tools explicitly instead of guessing.

## Install

### With Codex

Ask Codex to install this skill from GitHub:

```text
Use $skill-installer to install RomanovVIII/codex-thread-ops-skill with path codex-thread-ops.
```

Restart Codex after installation so the skill is discovered.

### Manual Install

1. Download `codex-thread-ops-skill.zip` from the latest GitHub release.
2. Extract the archive.
3. Copy the `codex-thread-ops` folder into your Codex skills directory, commonly:

```text
~/.codex/skills/
```

Depending on your Codex setup, the skills directory may differ. Use the directory that your Codex installation scans for user skills.

4. Restart Codex.

## Usage

Invoke it directly when you want thread-structure safety:

```text
Use $codex-thread-ops to create a new thread for the database migration plan.
```

It may also be invoked implicitly when a user clearly asks Codex to create, rename, fork, archive, pin, hand off, or migrate between Codex threads.

## Repository Layout

```text
codex-thread-ops/
  SKILL.md
  agents/
    openai.yaml
```

The repository README and license are intentionally outside the skill folder so the installed skill remains small and focused.

## License

MIT
