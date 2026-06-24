# Rules

Project-level agent rules that tell AI coding agents how to use APEX Skills
effectively — skill discovery, upstream source verification, and safety
guardrails.

## Usage

Copy `AGENTS.md` into your project root. Most AI coding agents (Codex, Cursor,
Gemini CLI, Kiro) discover it automatically via directory traversal.

```bash
cp rules/AGENTS.md /path/to/your/project/AGENTS.md
```

Or use the installer with `--rules`:

```bash
npx apex-skills --rules
```

### Claude Code

Claude Code reads `CLAUDE.md` instead of `AGENTS.md`. Either rename the file or
create a symlink:

```bash
cd /path/to/your/project
ln -s AGENTS.md CLAUDE.md
```

## What's inside

The rules file instructs agents to:

1. **Discover skills** — check installed APEX skills before relying on general
   knowledge.
2. **Verify against upstream sources** — when uncertain about version-specific
   details, fetch from authoritative open-source repos (Karpenter, VPC CNI,
   CoreDNS, etc.) rather than guessing.
3. **Use AWS documentation** — prefer the AWS MCP Server or official docs as
   authoritative sources.
4. **Follow IaC practices** — prefer Terraform, validate output.
5. **Stay safe** — no destructive ops without confirmation, no secrets in output.

## Compatibility

| Tool | Discovery | Notes |
|------|-----------|-------|
| OpenAI Codex | Native | Reads `AGENTS.md` from project root |
| Cursor | Native | Reads `AGENTS.md` from project root and subdirectories |
| Google Gemini CLI | Configurable | Add `"AGENTS.md"` to `context.fileName` in settings |
| Kiro | Native | Always reads `AGENTS.md` from workspace root |
| Claude Code | Symlink/rename | Reads `CLAUDE.md`; symlink `CLAUDE.md → AGENTS.md` |
| GitHub Copilot | `.github/copilot-instructions.md` | Copy relevant sections there |
