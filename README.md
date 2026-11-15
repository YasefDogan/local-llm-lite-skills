# local-llm-lite-skills

Simplified, lightweight versions of well-known agent skills, made for local (small) LLMs.

## Why

Popular agent skills are written for large cloud models: they are long, cover many cases and eat a big part of the context window. Small local models (for example a 7-14B model running in Ollama with a 32K context) get lost in them. The skills here are trimmed down to short, direct rules and a few concrete commands, so a small model can actually follow them.

## Skills

| Skill | What it does |
|---|---|
| `agent-reach-lite` | Web search, page reading, YouTube search/subtitles and GitHub lookup through the `agent-reach` CLI, with small result limits and clear error-handling rules. Condensed from Agent Reach. |
| `code-nav-lite` | How to explore a codebase cheaply with the codebase-memory-mcp graph tools (index, search, snippet, trace) and how to ask about any GitHub repo with DeepWiki. |
| `design-taste-lite` | A condensed anti-template frontend design guide for websites, landing pages, portfolios and blogs, so generated pages look less generic. Condensed from taste-skill. |
| `ponytail-lite` | "Lazy senior dev" coding rules (smallest complete change) plus terse reply style. Condensed from ponytail. |

Each skill is a single `SKILL.md` file with YAML frontmatter (`name`, `description`).

## Install

Copy the skill folder(s) you want into your agent's skills directory. For OpenCode:

```bash
git clone https://github.com/YasefDogan/local-llm-lite-skills.git
cp -r local-llm-lite-skills/agent-reach-lite ~/.config/opencode/skills/
```

Other agents that read `SKILL.md` folders work the same way; only the target directory differs.

Some skills need extra tools to be useful: `agent-reach-lite` needs the Agent Reach CLI, `code-nav-lite` needs the codebase-memory-mcp and DeepWiki MCP servers.

## Credits

These are derivative, simplified works. All credit for the original ideas goes to the original authors. Please check the originals for the full versions:

- Agent Reach by Panniantong (MIT): https://github.com/Panniantong/Agent-Reach (basis of `agent-reach-lite`)
- taste-skill by Leonxlnx (MIT): https://github.com/Leonxlnx/taste-skill (basis of `design-taste-lite`; its license is kept in `design-taste-lite/LICENSE`)
- ponytail by DietrichGebert (MIT): https://github.com/DietrichGebert/ponytail (basis of `ponytail-lite`)
- `code-nav-lite` is original and only describes usage of the codebase-memory-mcp and DeepWiki tools.

## License

MIT, see [LICENSE](LICENSE), for the parts written in this repository. The upstream projects above are also MIT-licensed; `design-taste-lite` keeps its upstream license file.

---

## Türkçe

Bu depo, bilinen agent skill'lerinin yerel (küçük) LLM'ler için sadeleştirilmiş, hafif sürümlerini içerir. Orijinal skill'ler uzun ve karmaşıktır; küçük modeller bağlam penceresinde zorlanır. Burada kurallar kısaltıldı ve somut komutlara indirildi.

- `agent-reach-lite`: Agent Reach CLI ile web arama/okuma, YouTube ve GitHub sorguları.
- `code-nav-lite`: codebase-memory-mcp ve DeepWiki ile kod tabanını ucuz yoldan keşfetme.
- `design-taste-lite`: Web sitelerinin "yapay zeka yapmış gibi" görünmemesi için kısaltılmış tasarım rehberi.
- `ponytail-lite`: En küçük tam çözüm + kısa cevap tarzı.

Kurulum: istediğiniz klasörü agent'ınızın skills dizinine kopyalayın (OpenCode için `~/.config/opencode/skills`). Orijinal projelerin yapımcılarına yukarıdaki Credits bölümünden ulaşabilirsiniz.
