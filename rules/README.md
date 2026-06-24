# Rules

Recommended agent rules for projects using APEX Skills. These tell AI coding
agents how to discover skills, verify against upstream sources, and stay safe.

## Usage

Add the contents of `AGENTS.md` to your project's existing agent configuration
file. Most projects already have one — don't replace it, append to it.

| Tool | Add to |
|------|--------|
| Claude Code | Your project's `CLAUDE.md` |
| Cursor | `.cursor/rules/apex.mdc` |
| OpenAI Codex | Your project's `AGENTS.md` |
| Kiro | `.kiro/steering/apex-rules.md` |
| Google Gemini CLI | Your project's `GEMINI.md` |
| GitHub Copilot | `.github/copilot-instructions.md` |

## What's inside

The rules instruct agents to:

1. **Discover skills** — check installed APEX skills before relying on general
   knowledge, with a routing table for all 15 skills.
2. **Verify against upstream sources** — when uncertain about version-specific
   details, fetch from authoritative open-source repos (Karpenter, VPC CNI,
   CoreDNS, etc.) rather than guessing.
3. **Use AWS documentation** — prefer the AWS MCP Server or official docs.
4. **Follow IaC practices** — prefer Terraform, validate output when tooling is
   available.
5. **Stay safe** — no destructive ops without confirmation, no secrets in output.

## Why this exists

AI agents can go stale on fast-moving ecosystems like EKS. We observed that
stronger models (e.g., Gemini) will autonomously git-clone upstream repos to
verify answers. These rules encode that behavior as explicit instructions so
any model — including weaker ones — can replicate it.

Modeled after [`aws/agent-toolkit-for-aws/rules/aws-agent-rules.md`](https://github.com/aws/agent-toolkit-for-aws/tree/main/rules).
