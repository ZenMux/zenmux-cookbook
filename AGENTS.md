# Repository Guidelines

## Project Structure & Module Organization
- `generation-*`, `embedding`, and `rerank` host cookbook recipes grouped by modality (image, audio, video, text, 3D). Keep new guides inside the closest matching subfolder and mirror the `text-to-*` / `*-to-text` naming already in use.
- `quickstarts/` contains end-to-end walkthroughs; `patterns/` catalogs reusable snippets; `integrations/` is for SDK or third-party samples; `scripts/` holds maintenance utilities such as `update-references.sh`.
- Co-locate sample assets within a sibling `images/` or `data/` folder, and keep large binaries out of the repo.

## Build, Test, and Development Commands
- `uv run python main.py` – sanity check the CLI entry point.
- `uv pip install -e .` – install the cookbook in editable mode for local tooling.
- `uv run python -m pytest` – run the shared test suite once tests are added (required before every PR).

## Coding Style & Naming Conventions
- Python code uses Black-compatible formatting (PEP 8, 4-space indents). Prefer descriptive module names such as `text_to_image.py` over abbreviations.
- Markdown guides follow the existing heading hierarchy (`# Scenario`, `## Steps`, `### Code`). Use code fences with explicit languages and keep line length under ~100 characters.
- Reference assets with relative paths (`../images/sample.png`) so guides remain portable.

## Testing Guidelines
- Favor executable examples: include `pytest`-ready functions or notebooks under `tests/` mirroring the source tree.
- Name tests `test_<feature>.py` and isolate external calls behind mocks or fixtures. Target at least smoke coverage for every new recipe and document manual validation steps inside the guide’s “Verification” section.

## Commit & Pull Request Guidelines
- Follow the concise, imperative history already present: `Add text-to-video quickstart`, `Fix rerank sampling logic`, etc.
- Each PR should describe scope, linked ZenMux issue/ticket, validation evidence (command output snippets), and screenshots for UI-related guides.
- Keep diffs focused; split unrelated recipe updates across PRs and tag reviewers owning the affected modality folder.

## Security & Configuration Tips
- Do not commit `.context/references` clones or API secrets; the script already adds them to `.gitignore`.
- Store sensitive keys in `.env` files excluded from Git and show contributors how to export them temporarily (`export ZENMUX_API_KEY=...`).
- When referencing external data sets, note licensing and provide download commands instead of bundling archives.
