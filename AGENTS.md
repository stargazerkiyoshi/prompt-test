# Project Agent Rules

## Terminology
- In this repository, `sls` means the local SLS specification under `./sls/`.
- Do not interpret `sls` as Serverless Framework unless the user explicitly says so.

## Default Behavior
- When user mentions `sls`, read project docs from `./sls/` first.
- Start with these files unless the task needs others:
  - `sls/00-SLS-Index.md`
  - `sls/90-SLS-Prompt-Assembly.md`
  - `sls/92-SLS-Prompt-Profiles.md`
  - `sls/93-SLS-Usage-Scenario-Matrix.md`
- If a request is still ambiguous, ask one clarifying question before assuming any external meaning.
