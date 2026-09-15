---
on:
  slash_command:
    name: hello
    events: [issues, issue_comment]
permissions:
  contents: read
max-ai-credits: 1
max-turns: 1
models:
  default-ai-credits-pricing:
    input: 1
    output: 4
engine:
  id: copilot
  model: openai/gpt-oss-20b
  env:
    COPILOT_MODEL: openai/gpt-oss-20b
    COPILOT_PROVIDER_BASE_URL: https://integrate.api.nvidia.com/v1
    COPILOT_PROVIDER_API_KEY: ${{ secrets.NVIDIA_API_KEY }}
    COPILOT_PROVIDER_TYPE: openai
network:
  allowed:
    - defaults
    - integrate.api.nvidia.com
safe-outputs:
  add-comment:
    max: 1
---

# Agentic Hello ChatOps

When an authorized repository collaborator types `/hello` in an issue or issue
comment, reply once in the same conversation.

Use the configured `add-comment` safe output with exactly this message:

`Hello from the NVIDIA GPT-OSS GitHub Agentic Workflow.`

Do not inspect files, make code changes, or perform any other actions.
