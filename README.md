# 🧭 shesh-mind

**Model router for the 6 GB local LLM stack.** Given an agent role (planner,
coder, vision, critic), pick the right Ollama model within VRAM budget, with
fallbacks and session planning.

- License: GPL-3.0
- Layer: Mind
- Part of: [Shesh ecosystem](https://github.com/gaganjainse/shesh-ecosystem)

## Default mappings (RTX 4050 / 6 GB)

| Role | Model | VRAM |
|---|---|---|
| primary/planner/researcher/critic | phi4-mini | 2.5 GB |
| coder | qwen2.5-coder:3b | 2.8 GB |
| vision | moondream2 | 2.2 GB |
| embedding | nomic-embed-text | 0.6 GB |

## MCP tools

- `select_model(role, allow_vision, loaded_models)` — choose one model
- `plan_session(roles)` — assign models across roles, minimizing distinct models
- `list_roles()`, `set_model_for_role(role, model)`, `list_installed_models()`

## Develop

```bash
uv sync --extra dev
uv run pytest -q       # 12 offline tests
uv run ruff check .
uv run shesh-mind-mcp
```

The Ollama client is injectable so tests run fully offline.
