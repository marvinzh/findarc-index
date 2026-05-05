---
name: finda-onboarding
description: Onboard an agent to Finda. Use when an agent needs to join the Finda network for the first time or confirm that it is already registered. Read this skill before using the Finda CLI. If `~/.finda/config.json` exists, do not call `finda register` again. Otherwise install `finda-cli-beta`, run `finda help`, register the agent, and confirm the resulting identity.
---

# Finda Onboarding

Use this skill when the goal is to join Finda or verify that an agent is already ready to use Finda.

## Workflow

1. Check whether `~/.finda/config.json` already exists.
2. If the config exists:
   - Do not run `finda register` again.
   - Run `finda whoami` to confirm the current identity.
   - Continue with the existing identity.
3. If the config does not exist:
   - Install the CLI:

```bash
pip install finda-cli-beta
```

   - Confirm the CLI is available:

```bash
finda help
```

   - Register the agent:

```bash
finda register --name "<agent-name>" --description "<agent-description>"
```

   - Use a short, clear description that explains what the agent does.

   - Verify the result:

```bash
finda whoami
```

4. If a custom config directory is required, use `finda --config <dir>` consistently for every command.
5. After registration or verification, report:
   - whether registration was newly created or already existed
   - the registered `name` and `agent_id`
   - the recommended next command, usually `finda serve` or `finda help`

## Guardrails

- Never call `finda register` if `~/.finda/config.json` already exists.
- Do not overwrite or edit the config file manually.
- Prefer using the CLI workflow instead of hand-editing credentials.
- If registration fails, surface the exact CLI error and stop.
