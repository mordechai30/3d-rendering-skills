Source: [https://developer.apple.com/documentation/xcode/investigating-gpu-issues-with-ai-agents](<https://developer.apple.com/documentation/xcode/investigating-gpu-issues-with-ai-agents>)

<a id="investigating-gpu-issues-with-ai-agents"></a>

# Investigating GPU issues with AI agents

Find the root cause of an issue in a large GPU trace by handing the trace to an AI agent for autonomous investigation.

<a id="overview"></a>

## Overview

To help you investigate issues in GPU traces, the `gpudebug` command-line tool provides a text-based, self-discoverable interface that you can use programmatically, making it well-suited for AI agents.

Each row in the `list` command’s output shows node names and available actions, and the `go` command prints the destination’s children. An agent can explore an unfamiliar trace by following the actions each node advertises — without requiring any prior knowledge of the trace structure.

> Tip: For AI agents, point them at `man gpudebug` and a `.gputrace` file. That’s all they need to start investigating autonomously.

<a id="reuse-a-session-for-multiple-commands"></a>

## Reuse a session for multiple commands

For any investigation involving more than one command, create a session once and reuse it. Trace loading and replayer startup can take seconds to minutes depending on the size of the trace; reusing a session avoids paying that cost on every invocation:

```shell
% gpudebug -t trace.gputrace -c "list"
Session 412 created.
...
% gpudebug -s 412 -c "go commands/cb0/re0/draw0" -c "info pipeline"
% gpudebug -s 412 -c "fetch color0"
% gpudebug -s 412 -c "next" -c "fetch color0"
% gpudebug --terminate 412
```

Each `-s` invocation reuses the already-loaded trace and replayer instantly.

<a id="run-one-off-queries-with---oneshot"></a>

## Run one-off queries with `--oneshot`

For an isolated single-command query where session management is a burden, use `--oneshot`. The option creates a session, runs the commands, and terminates, but it pays the full trace load cost on every invocation:

```shell
% gpudebug --oneshot -t trace.gputrace -c "go commands/cb0/re0/draw0" -c "info pipeline"
```

For the full command reference, see the `gpudebug(1)` man (manual) page (`man gpudebug`).

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
