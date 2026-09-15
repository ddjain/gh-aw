---
on:
  workflow_dispatch:
permissions:
  contents: read
  issues: read
  pull-requests: read
max-ai-credits: 5
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
  create-issue:
    max: 1
    title-prefix: "[agentic-demo] "
---

# Repository Overview

Create one concise issue that reports the current state of this repository.

The repository is intentionally small. Do not search for conventional source
directories or use MCP issue tools. Gather evidence with only these commands:

```sh
git log --oneline -5
git ls-files
```

After those commands, create exactly one report issue with the safe-output CLI.
Do not try to invoke `create_issue` as a direct tool call. Instead, pipe a JSON
object containing final `title` and `body` strings to this command:

```sh
safeoutputs create_issue .
```

Do not return a normal-text answer or exit before the command succeeds. State
the evidence you used and distinguish facts from recommendations.
Include:

1. A short inventory of the repository and its automation.
2. Note that issue and pull-request activity was not inspected in this bounded
   demonstration.
3. Up to three practical next steps for a maintainer.

Do not modify files, labels, pull requests, or existing issues. Create exactly
one report issue using the configured safe output.
