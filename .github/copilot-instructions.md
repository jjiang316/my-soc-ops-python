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

## Design Guide — Ghost Protocol

The UI uses a "Ghost Protocol" dark theme — near-black void where elements are barely visible and emerge on interaction.

- **Palette:** CSS variables in `:root` — `--void` (#080808) base, `--surface`/`--elevated` for layering, `--text-ghost` through `--text-bright` for progressive text visibility, `--cyan-*` for marked/accent states, `--win-*` for winning line
- **Font:** Share Tech Mono (Google Fonts) — military terminal monospace
- **Copy style:** Uppercase headings with `tracking-widest`/`tracking-wide`, military jargon ("Initiate", "abort", "Protocol", "Extracted")
- **Interactions:** `hover-brighten` class on text elements to reveal on hover; all effects are CSS-only (no JS)
- **Animations:** `animate-grid-reveal` with `.delay-0`–`.delay-24` for staggered board entry, `animate-ghost-pulse` for winning squares, `animate-fade-from-void` for modal
- **CRT overlay:** Scanline effect via `#app::after` pseudo-element — do not remove
- Full utility reference in `.github/instructions/css-utilities.instructions.md`
