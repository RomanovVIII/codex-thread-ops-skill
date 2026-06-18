---
name: codex-thread-ops
description: >-
  Safe workflow for managing Codex thread-structure operations when the user invokes $codex-thread-ops or clearly asks to create, rename, fork, archive/unarchive, pin/unpin, hand off to, message, select, or migrate between Codex threads. Also use for maintaining a project thread index such as THREADS.md when local instructions define one. Do not use for ordinary mentions of a thread, reading or summarizing the current conversation, or content work inside a thread.
---

# Codex Thread Ops

Use this skill when the user is asking to manage the structure of Codex threads, not merely to discuss or summarize the current conversation. Treat it as a safety workflow for thread mutations, thread handoffs, and optional project thread indexes.

## Scope Gate

Before using thread tools or reading a project thread index, decide whether the request is about thread structure.

Use this workflow for:

- creating a Codex thread;
- renaming a thread;
- forking a thread;
- archiving or unarchiving a thread;
- pinning or unpinning a thread;
- sending a handoff or message to another thread;
- selecting an existing thread for a topic migration;
- creating or maintaining a project thread index, commonly `THREADS.md`.

Do not use this workflow for ordinary references such as "current thread", "read this thread", "based on this thread", summarizing conversation history, or doing content work inside the current discussion.

If this skill was selected but the request is not a thread-structure operation, state that the skill does not apply and continue without thread-index work.

## Source Priority

1. Read local project instructions first when they exist, especially `AGENTS.md` or equivalent local agent guidance.
2. Local instructions override this skill for project-specific paths, naming conventions, confirmation rules, and index maintenance.
3. If local instructions define a thread index file, use that file. If no path is defined, treat `THREADS.md` in the project root as the conventional default, not a requirement.
4. Discover currently callable thread tools from the active session. Use `tool_search` when thread tools are not already visible.
5. Prefer verified current-session tool behavior over remembered behavior. If a thread tool is unavailable, state the limitation.

Known Codex App thread tools may include `list_threads`, `read_thread`, `create_thread`, `fork_thread`, `send_message_to_thread`, `handoff_thread`, `set_thread_title`, `set_thread_archived`, and `set_thread_pinned`. Do not assume a deletion tool exists.

## Project Bootstrap

If the project has no thread index, do not treat that as an error. For a one-off operation, continue without an index unless the user asks for one or local instructions require one.

Recommend creating a project thread index when:

- the project has multiple active Codex threads;
- thread operations are recurring;
- the user wants agents to avoid repeatedly rediscovering thread history;
- topic boundaries are important enough to track across sessions.

Do not create or edit project instructions or a thread index without explicit user confirmation.

Suggested project instruction block:

```md
## Codex Threads

`THREADS.md` is a technical index of active Codex threads for this project.

Use it only for thread-structure operations: creating, renaming, forking, archiving, pinning, topic migration, or updating the thread index.

Do not open `THREADS.md` for ordinary mentions of the current thread, reading conversation history, or content work inside the current discussion.

Before changing a thread, explicitly verify the target: `threadId`, current title, and requested action. Do not treat `source_thread_id` from a handoff or delegation as the current thread.

After a confirmed thread-structure operation, update `THREADS.md` in the same task when this project uses that index.
```

Suggested thread index template:

```md
# Codex Threads

Technical index of active Codex threads for this project.

## Active Threads

- `Thread title` - one short sentence about the topic.
```

Track active threads only by default. Do not maintain an archived-thread section unless local rules explicitly require it and the platform can list archived threads reliably.

## Mutation Safety

Before any thread mutation, explicitly identify the target:

- target `threadId`;
- current thread title;
- requested action;
- new title or destination when applicable;
- whether the target is the current thread or another thread.

Never treat `source_thread_id` from a delegation, handoff, or compacted context as the current thread. Verify the target through live thread tools.

If the target thread is ambiguous, stop and ask. Do not guess based on title alone when multiple candidates exist.

For destructive or hard-to-reverse operations, prefer archive over delete. Delete only when a callable deletion tool exists and the user explicitly requested deletion. If deletion is unavailable, explain that and ask before using archive as a fallback.

## Operation Rules

Creating a thread:

- Use a short, thesis-like title. Prefer a clear noun phrase of 2-5 words.
- Avoid long action titles when a shorter topic title is clear.
- If the title or seed content is missing, propose them before creating the thread.
- Seed content should include goal, project or folder, topic boundary, important files, known facts, and what not to do.

Renaming a thread:

- Verify the exact target `threadId` and current title immediately before renaming.
- Confirm that the new title is short and understandable.
- After renaming, verify by reading or listing the target thread when the available tools allow it.

Forking a thread:

- Identify the source thread and the reason for the fork.
- Put only relevant handoff context into the fork. Do not carry unrelated topics forward.
- After the fork, update the project thread index when one exists and local rules require it.

Archiving or pinning:

- Verify the target `threadId` and title before the action.
- After the action, verify through the live list/read behavior available in the session.
- If archived threads cannot be listed, do not add or maintain an archived-thread section in the project index by default.

Sending a message or handoff to another thread:

- Verify the destination thread by `threadId` and title.
- Keep the message focused on the destination thread's topic.
- Do not leak secrets. Redact sensitive values.

## Thread Index Maintenance

When the agent performs a confirmed thread-structure action and the project has a thread index, update that index in the same task unless local instructions say otherwise.

Before editing the thread index, compare it with the live thread list when the active tools can provide the relevant current threads. If a thread was renamed, archived, created, or is no longer visible, reconcile the active list conservatively.

Keep entries concise:

```md
- `Thread title` - one short sentence about the topic.
```

Do not put usage rules into the thread index. Keep rules in project instructions and in this skill. The index is a technical list, not the main project knowledge base.

## Verification And Report

After a thread operation, verify both sides of the change:

- live thread state through available thread tools;
- local thread index content when it was changed.

Final response should be brief and include:

- what thread action was done;
- what files were touched;
- what was verified;
- any limitation, such as unavailable deletion or incomplete archived-thread visibility.
