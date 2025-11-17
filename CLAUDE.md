# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview
The zenmux-cookbook is the official cookbook for ZenMux, containing a comprehensive collection of guides, workflows, and configuration snippets to help developers leverage ZenMux AI effectively.

## High-Level Architecture
The repository follows a modality-based organization with the following key directories:

- **Core Functionality**:
  - `generation-*`: Modality-specific generation recipes (3D, audio, image, text, video)
  - `embedding`: Embedding-related recipes
  - `rerank`: Reranking-related recipes
  - These directories use a consistent `X-to-Y` naming pattern for subfolders

- **Supporting Directories**:
  - `quickstarts/`: End-to-end walkthroughs
  - `patterns/`: Reusable code snippets and patterns
  - `integrations/`: SDK or third-party service samples
  - `scripts/`: Maintenance utilities (e.g., `update-references.sh`)
  - `images/`: Shared image assets
  - `.context/references/`: External reference repositories (managed via `scripts/update-references.sh`)

## Common Development Commands
- `uv run python main.py`: Sanity check the CLI entry point
- `uv pip install -e .`: Install the cookbook in editable mode
- `uv run python -m pytest`: Run the test suite (required before PRs)

## Key Guidelines
- **Module Organization**: Keep new guides in the closest matching modality folder with appropriate `X-to-Y` naming
- **Asset Location**: Co-locate sample assets in sibling `images/` or `data/` folders
- **Coding Style**: Python uses Black-compatible PEP 8 formatting with 4-space indents
- **Markdown Guides**: Follow existing heading hierarchy (`# Scenario`, `## Steps`, `### Code`) with explicit code fence languages
- **Testing**: Write `pytest`-ready tests with naming pattern `test_<feature>.py` and isolate external calls
- **Security**: Do not commit API secrets or large binaries; use `.env` files and relative asset paths

## References
External reference repositories are managed through `scripts/update-references.sh`, which:
- Clones/updates repositories from `.context/references/references-list.txt`
- Adds references to `.gitignore`
- Maintains them in the `.context/references/` directory
