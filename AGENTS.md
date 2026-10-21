# Repository Guidelines

## Project Structure & Content

This is a Markdown-first learning glossary for software and systems terminology. Keep `README.md` as the landing page and `docs/index.md` as the topic directory. Organize subject guides under `docs/topics/` (for example, `docs/topics/apis-and-communication/` and `docs/topics/operating-systems/`); put term comparisons in `docs/comparisons/` and revision material in `docs/reference/`. Keep Mermaid diagrams beside the pages they explain, worked examples in `examples/`, and image assets in `assets/images/`. Use relative links between repository files, and add directories only when they contain substantive files.

## Build, Test, and Development

There is no application build or package-based test command. The notes should remain readable without installing a documentation framework. Preview Markdown in GitHub or a local Markdown viewer. When editing, check relative links and Mermaid diagrams in the target renderer.

## Writing Style and Naming

Use concise, beginner-friendly explanations and descriptive Markdown headings. Name files in lowercase kebab case, such as `api-vs-abi.md`. Keep one logical topic or a small related group per file. For each term, explain its meaning, purpose, basic operation, use, and a concrete example; add an analogy, related terms, common confusion, and trustworthy further reading where useful. Mark pseudocode and examples as illustrative. Use Mermaid for small diagrams and keep visual assets consistent with the documented palette, especially `#AEC4D4`.

## Testing and Review

No automated test framework or coverage requirement is configured. Review changes for technical accuracy, beginner readability, working relative links, rendered Mermaid, and discoverability from the index or glossary. For comparisons, use a table and include an example and when each concept is used.

## Commits and Pull Requests

Git history is not available here, so no existing commit convention can be confirmed. Use short, imperative commit subjects (for example, `Add API and ABI comparison`). Pull requests should describe the learning sections changed, note accuracy and link checks, and include screenshots when visual assets or rendered layouts change. Link related issues when applicable.

## Security and Publishing

Do not commit credentials, tokens, or private information. Publishing to GitHub requires the project owner's explicit approval; keep work local until that approval is given.
