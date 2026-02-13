# PyHC-Chat-CLI

A specialized multi-agent CLI environment for exploring, using, and maintaining the Python in Heliophysics Community (PyHC) ecosystem.

## Overview

This repository provides a ready-to-use setup for Claude Code, Codex, and Gemini CLI that can answer questions about:
- The PyHC organization and community
- Any of the 96+ PyHC Python packages
- Package implementation details, usage, and code structure
- Working with package APIs and workflows (examples, debugging, and integration guidance)
- Developing and maintaining PyHC packages (bug fixes, tests, docs, and release support)
- Cross-package comparisons and recommendations
- General PyHC knowledge (standards, leadership, meetings, and project metadata)

The key insight: modern coding agents are excellent at navigating repositories to answer questions. This repo houses all PyHC package repos as git submodules, allowing agents to autonomously search through them and answer your questions.

## Quick Start

### Prerequisites
- One or more agent CLIs installed and authenticated:
  - [Claude Code](https://claude.ai/code)
  - [Codex](https://developers.openai.com/codex/cli)
  - [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- Git 2.13+ (for submodule support)

### Clone the Repository

**Important:** You must clone with the `--recursive` flag to download all PyHC packages:

```bash
git clone --recursive https://github.com/heliophysicsPy/pyhc-chat-cli.git
cd pyhc-chat-cli
```

**Or**, if you already cloned without `--recursive`:

```bash
git clone https://github.com/heliophysicsPy/pyhc-chat-cli.git
cd pyhc-chat-cli
git submodule update --init --recursive
```

This will download all 96 PyHC package repositories (~several GB).

### Start Chatting

Run the agent you want to use:

```bash
claude
```

```bash
codex
```

```bash
gemini
```

Then ask questions like:
- "How does SunPy use FITS/WCS metadata with solar coordinate frames and transformations?"
- "Which PyHC packages support CDF file reading?"
- "Show me how to download a HAPI dataset."
- "When should I use aacgmv2 vs apexpy for magnetic coordinate conversions?"
- "How do I use SpacePy coordinates in a workflow with PySPEDAS data?"
- "Who is on current PyHC leadership and where are the latest meeting reports?"
- "Help me add tests for this bug in my package and update the docs."

## For PyHC Members

You can use this repo as a practical maintenance and development workspace across the PyHC ecosystem. Typical tasks include:
- Tracing where behavior is implemented across packages
- Prototyping fixes and adding tests in your package
- Updating API docs and examples to match code changes
- Getting help aligning your package with PyHC standards and best practices
- Comparing patterns used by other PyHC packages before making design decisions

## Repository Structure

```
pyhc-chat-cli/
├── pyhc_packages/          # All 96 PyHC packages as git submodules
│   ├── heliophysicsPy.github.io/  # PyHC website (contains metadata)
│   └── ...                 # 95 more packages
├── CLAUDE.md               # Instructions for Claude Code
├── AGENTS.md               # Instructions for Codex
├── GEMINI.md.md            # Instructions for Gemini CLI
└── .github/workflows/      # Automated package updates
    └── update-submodules.yml
```

## Keeping Packages Updated

This repository automatically updates all PyHC packages nightly via GitHub Actions. The workflow:
1. Runs daily at midnight UTC
2. Updates all submodules to their latest commits
3. Commits and pushes if any packages changed

You can also manually trigger updates from the Actions tab on GitHub.

To update locally:

```bash
git pull
git submodule update --remote --merge
```

## Included Packages

96 PyHC packages including:

**Core Packages:**
- HAPI Client, Kamodo, PlasmaPy, pysat, pySPEDAS, SpacePy, SunPy

**Standards & Documentation:**
- heliophysicsPy.github.io (PyHC website)
- standards, pyhc-docs

**And 89+ specialized packages** for solar physics, magnetosphere science, ionosphere/thermosphere research, data access, visualization, and more.

See `pyhc_packages/heliophysicsPy.github.io/_data/` for complete package metadata.

## How It Works

1. **Git Submodules**: Each PyHC package is a git submodule pointing to its official repository
2. **Full Git History**: Each agent can access the complete development history of each package
3. **Automated Updates**: GitHub Actions keeps all packages synchronized with their upstream repos
4. **Agent Instructions**: Specialized instructions in `CLAUDE.md`, `AGENTS.md`, and `GEMINI.md.md` guide each agent on how to search packages, cite sources, and acknowledge limitations

## Contributing

This is an experiment in AI-assisted PyHC support. Contributions welcome:
- Add missing PyHC packages
- Improve agent instruction files (`CLAUDE.md`, `AGENTS.md`, `GEMINI.md.md`)
- Report issues with answers from Claude Code, Codex, or Gemini CLI
- Share interesting use cases

## Notes

- First clone will take several minutes and ~several GB of disk space
- Your selected agent may require an active subscription and/or API access
- This is a community tool, not an official PyHC project
- For authoritative answers, always consult official package documentation

## License

This repository structure is provided as-is. Individual packages retain their original licenses.
