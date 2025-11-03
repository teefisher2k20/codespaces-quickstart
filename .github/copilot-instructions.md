# Rasa Codespaces Quickstart - AI Agent Instructions

## Project Overview
This is a **Rasa quickstart template** for GitHub Codespaces that provides a pre-configured development environment for building conversational AI assistants. The repository serves as a blank template - users initialize their actual Rasa project after the environment is set up.

## Architecture & Environment Setup

### Key Components
- **Dev Container**: Python 3.10 environment with Rasa Pro pre-installed via `uv` package manager
- **Virtual Environment**: `.venv/` contains Rasa Pro and dependencies (activated via `source .venv/bin/activate`)
- **License Management**: `.env` file stores `RASA_LICENSE` key (must be set before using Rasa)

### Environment Activation Workflow
```bash
# Required sequence for any Rasa operations:
source .env                    # Load license key
source .venv/bin/activate     # Activate Python environment
```

## Development Patterns

### Project Initialization
- Users run `rasa init --template tutorial` to scaffold actual chatbot project
- This creates standard Rasa structure: `config.yml`, `domain.yml`, `data/`, `actions/`
- The template approach means NO existing Rasa files in this repo - it's intentionally minimal

### Core Workflow Commands
```bash
rasa train                     # Train ML model from training data
rasa inspect                   # Launch web-based chat interface (auto-opens in Codespaces)
```

### Custom Actions Architecture
- Rasa 3.10+ automatically runs custom actions alongside the assistant
- Requires `endpoints.yml` with `actions_module: "actions"` configuration
- Re-run `rasa inspect` after modifying custom actions (no separate action server needed)

## VS Code Integration

### Recommended Extensions
The `.vscode/extensions.json` includes:
- Python development tools
- Azure services extensions (Functions, Container Apps, Cosmos DB)
- AI/ML development tools (Windows AI Studio, AI Foundry)

### Python Configuration
- Default interpreter: `.venv/bin/python`
- Auto-activates environment in terminal
- Max predictions limit: 50 (via `MAX_NUMBER_OF_PREDICTIONS` env var)

## Codespaces-Specific Considerations

### Port Forwarding
- `rasa inspect` automatically forwards ports for web interface access
- GitHub Codespaces handles notifications for opened services

### License Key Security
- `.env` file contains placeholder - users must add real license key
- License key required for all Rasa Pro features

## Project State Awareness
- This is a **template repository** - actual Rasa project files appear only after `rasa init`
- Don't assume existence of `config.yml`, `domain.yml`, or training data until initialization
- Focus on environment setup and template usage rather than chatbot development until project is initialized