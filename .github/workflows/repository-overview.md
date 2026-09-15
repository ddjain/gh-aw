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
  model: nvidia/nemotron-3.5-lightning-30b-a3b
  env:
    COPILOT_MODEL: nvidia/nemotron-3.5-lightning-30b-a3b
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

Inspect the repository contents, open issues, open pull requests, and recent
commits. State the evidence you used and distinguish facts from recommendations.
Include:

1. A short inventory of the repository and its automation.
2. Current issue and pull-request activity.
3. Up to three practical next steps for a maintainer.

Do not modify files, labels, pull requests, or existing issues. Create exactly
one report issue using the configured safe output.
