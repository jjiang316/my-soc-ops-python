# Project Guidelines

## Development Checklist

Before committing any changes, **all three must pass**:

1. `uv run ruff check .` — lint
2. `uv run pytest` — tests
3. `uv sync` — dependencies resolve

## Overview

SOC Ops — Social Bingo game. FastAPI + Jinja2 + HTMX, custom CSS utilities, no JS frameworks.

## Architecture

- `game_logic.py` — pure functions only (board gen, bingo detection), no side effects
- `game_service.py` — owns state mutations via `GameSession` dataclass
- `main.py` — FastAPI routes returning HTMX **partial HTML fragments** (not JSON, not full pages)
- `models.py` — Pydantic v2 models with `frozen=True`
- CSS utilities in `app/static/css/app.css`; see `.github/instructions/css-utilities.instructions.md`

## Conventions

- Python 3.13+ syntax: StrEnum, `X | Y` unions, type hints on all signatures, snake_case everywhere
- HTMX-only interactivity — no client-side JS frameworks
- Server-side state via signed cookies (SessionMiddleware + itsdangerous)
- In-memory session store (`_sessions` dict) — server restart clears all games
- Never preview with VS Code Simple Browser — HTMX requires a full browser
