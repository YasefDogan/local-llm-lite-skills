---
name: code-nav-lite
description: How to explore a codebase cheaply with the codebase-memory-mcp graph tools, and how to ask about any GitHub repo with deepwiki. Load before reading many files in an existing project, or when you need to understand a library/repo.
---

# code-nav-lite

Context is small (32K tokens). Do NOT open whole files to find things. Use the graph first.

## Existing project (codebase-memory-mcp tools)

1. `codebase-memory-mcp_index_repository` with the project root path, once per project
   (re-run only if the user says the code changed a lot).
2. `codebase-memory-mcp_get_architecture` -> overview: main modules, entry points.
3. `codebase-memory-mcp_search_graph` -> find a function/class/route by name or keyword.
4. `codebase-memory-mcp_get_code_snippet` -> read ONLY that symbol's source.
5. `codebase-memory-mcp_trace_path` -> who calls it / what it calls (before changing a function).
6. `codebase-memory-mcp_get_file_outline` -> list symbols in one file without reading it all.

Then edit with the normal edit tool. Use plain `read` only for small files (config, README)
or when the graph has no result. Use grep for exact strings/literals.

## Any GitHub repo or library (deepwiki tools)

- `deepwiki_ask_wiki_question` with repoName `owner/repo` and a specific question
  (e.g. "How do I configure X?", "Which function handles Y?"). Best first step for unknown libraries.
- `deepwiki_read_wiki_structure` -> list topics; `deepwiki_read_wiki_contents` -> read one topic.
- Questions are sent to an external service: never include secrets, keys or private code.

## Rules

- Search -> snippet -> edit. Not: read file -> read file -> read file.
- Summarize findings in 2-3 lines before continuing.
- If a tool errors twice, fall back to grep/read and tell the user.
