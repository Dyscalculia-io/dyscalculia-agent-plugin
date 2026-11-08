# Dyscalculia.io — agent plugin

Cited dyscalculia statistics from dyscalculia.io: prevalence by study and age, 93 references with DOI/PMID, chart datasets on persistence, math anxiety, interventions and comorbidity, and how the five-game screening test works.

For any agent that speaks MCP or reads Agent Skills. Configuration only: one hosted MCP
server and one skill.

| | |
|---|---|
| MCP server | `https://mcp.dyscalculia.io/mcp` (Streamable HTTP, no sign-in, no key) |
| Skill | [`skills/dyscalculia-research`](skills/dyscalculia-research/SKILL.md) |
| Tools | 6, all read-only |
| Format | Agent Plugins v1 (`plugin.json` + `mcp.json` + `skills/`), plus Claude Code (`.claude-plugin/`, `.mcp.json`) |

## Install

```bash
# Skill only, for Claude Code, Cursor, Codex and 40+ other agents (skills.sh)
npx skills add Dyscalculia-io/dyscalculia-agent-plugin

# Hermes Agent (skill + MCP server)
hermes plugins install Dyscalculia-io/dyscalculia-agent-plugin
hermes plugins enable dyscalculia

# Claude Code, MCP server only
claude mcp add --transport http dyscalculia https://mcp.dyscalculia.io/mcp
```

Any other MCP client: add `https://mcp.dyscalculia.io/mcp` as a remote HTTP server.

## Tools

| Tool | What it returns |
|---|---|
| `get_prevalence` | Published prevalence figures by study, age or percent range |
| `list_studies` | Every cited source, filterable by topic |
| `get_reference` | Full citation with DOI/PMID for one key |
| `list_chart_data` | Chart and table datasets with CSV/JSON/SVG addresses |
| `explain_screening_test` | The five screening games and how they are scored |
| `get_citation` | License, citation text, credit link |

The screening test is a screening of basic number skills, not a diagnosis; the server scores no one.

## Disclosure

- Hosted-only connector with no local code. Every tool call, with its arguments, goes to
  `mcp.dyscalculia.io`. No account, key or personal data is needed or stored.
- All tools are read-only. No shell commands, no background processes, no telemetry
  from this package.
- The tool set is served by the remote server at runtime, so it is not covered by a pinned commit.

## License

Package: MIT. Compilation: CC BY 4.0; each figure belongs to its cited source.
Source of the server: [dyscalculia-mcp](https://github.com/Dyscalculia-io/dyscalculia-mcp).
Website: [dyscalculia.io](https://dyscalculia.io) · Docs: [docs.dyscalculia.io](https://docs.dyscalculia.io).
