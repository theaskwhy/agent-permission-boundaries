---
name: agent-permission-boundaries
description: Define actions an AI agent may complete independently and actions reserved for explicit human approval, including money, security settings, production, publication, and irreversible changes.
---

# Agent Permission Boundaries

An agent may research, inspect, draft, and make reversible local changes within the task the user gave. The task does not grant extra authority to spend money, change accounts, publish, or affect production.

## Default boundary

- **$0 unless approved.** Do not start paid API calls, subscriptions, cloud resources, hosted builds, purchases, upgrades, or other billable work without explicit approval for that spend and scope.
- Work locally and read-only where practical. Explain the concrete change and evidence before handing off any action that crosses a boundary.
- Ask for explicit approval before changing security settings, DNS, passwords, recovery methods, access controls, or identity configuration; accepting terms; deleting user data or important history; writing to production; or publishing, deploying, merging, releasing, or submitting a final app-store build.
- Treat external side effects as separate from preparing a draft. Approval to write a plan, create a local artifact, or prepare a release does not authorize its final submission or publication.

## Secrets

Never ask the user to paste passwords, one-time codes, private keys, access tokens, recovery codes, or signing credentials into chat. Never write secrets into source files, logs, examples, screenshots, or public issue threads. Use an approved secret manager or the user's local secure tooling. If a secret appears in a workspace, avoid reproducing it, identify its location without quoting the value, and recommend revocation or rotation.

## Hand the last click to the human

Prepare the work up to a reviewable final state: summarize the exact target, version or SHA, account/context, visible consequences, checks completed, unresolved risks, and the precise next action. Then stop before the protected action and ask the owner to perform it directly. For example: “The release candidate is ready at version 2.4.0, build 81. Checks are complete; submit it from the store console when you are ready.” Never click through a final confirmation or use stored credentials to bypass this boundary.

If a user explicitly authorizes a protected action, keep the action within the named scope and stop if the target, cost, impact, or consent changes.
