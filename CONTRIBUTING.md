# Contributing Learning Notes

**Navigation:** [Home](README.md) | [Topic Index](docs/index.md)

## Add or Update a Topic

1. Find the canonical subject page in `docs/topics/` and check [the glossary index](docs/reference/glossary-index.md) before adding a definition.
2. Keep one logical topic or a small related group together. Use lowercase kebab-case filenames (for example, `memory-ordering.md`) if a new page is justified.
3. Lead with a plain-language meaning. Explain why it exists, where it is used, and a small example. Add an analogy, pseudocode, diagram, common confusion, and related terms when they help.
4. Link related notes with relative paths. Cite the most relevant official specification or documentation page, not a generic search result.
5. Update `docs/index.md`, `docs/reference/glossary-index.md`, and `SOURCES.md` when adding a topic or source.

## Review Before Sharing

- Confirm each acronym is expanded on first use and examples are clearly illustrative.
- Check terminology against primary references; note version-specific behavior.
- Read the Markdown in a renderer and inspect Mermaid diagrams.
- Use the calm blue-grey visual palette (`#AEC4D4`) for any SVG or stylesheet and ensure text contrast remains readable.
- Avoid app code, build infrastructure, dependencies, and duplicate term definitions.

There is no configured build, linter, or automated test command. Describe manual checks honestly in a change summary. Do not publish or push the repository without the owner's explicit approval.
