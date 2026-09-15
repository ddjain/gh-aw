---
on:
  slash_command:
    name: hello
    events: [issues, issue_comment]
permissions:
  contents: read
max-ai-credits: 1
engine: codex
safe-outputs:
  add-comment:
    max: 1
---

# Agentic Hello ChatOps

When an authorized repository collaborator types `/hello` in an issue or issue
comment, reply once in the same conversation.

Use the configured `add-comment` safe output with exactly this message:

`Hello from the Codex-powered GitHub Agentic Workflow.`

Do not inspect files, make code changes, or perform any other actions.
