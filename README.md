🌐 [Português (BR)](README.pt_BR.md) | [Español](README.es.md)

<div align="center">

# 🎲 Soc Ops

**Break the ice. Fill the board. Call BINGO!**

A social bingo game for in-person mixers — mingle with the crowd,
find people who match each square, and race to get five in a row.

Built with **Python · FastAPI · Jinja2 · HTMX** — zero client-side JS frameworks.

</div>

---

## ✨ How It Works

```
┌──────────┬──────────┬──────────┬──────────┬──────────┐
│ bikes to │ has a    │ plays an │ speaks   │ has run  │
│ work     │ pet      │ instrume │ 2+ langs │ marathon │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ born in  │ has met  │ can      │ has been │ loves    │
│ diff st. │ a celeb  │ juggle   │ skydiving│ cooking  │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ has a    │ traveled │   FREE   │ is left  │ has a    │
│ garden   │ to Asia  │  SPACE   │ handed   │ twin     │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ plays    │ does     │ has a    │ loves    │ has been │
│ video gm │ yoga     │ hidden   │ spicy fd │ on TV    │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ collects │ read a   │ knows    │ lived    │ prefers  │
│ somethin │ book     │ sign lng │ abroad   │ tea > ☕ │
└──────────┴──────────┴──────────┴──────────┴──────────┘
```

1. **Start a game** — each player gets a randomized 5×5 board
2. **Mingle** — find someone who matches a square and tap it
3. **Five in a row** — row, column, or diagonal — that's BINGO! 🎉

---

## 🚀 Quick Start

```bash
# Clone & enter the project
git clone https://github.com/jjiang316/my-soc-ops-python.git
cd my-soc-ops-python

# Install dependencies
uv sync

# Launch the app
uv run soc-ops
```

Then open **http://localhost:8000** in your browser and start playing.

> 💡 **Tip:** A DevContainer config is included — open in GitHub Codespaces or VS Code for a zero-setup experience.

---

## 🏗️ Architecture

```
app/
├── main.py            # FastAPI routes → HTMX partial HTML fragments
├── models.py          # Pydantic v2 models (frozen)
├── game_logic.py      # Pure functions: board gen, bingo detection
├── game_service.py    # State mutations via GameSession dataclass
├── data.py            # Question pool & constants
├── templates/         # Jinja2 templates (base + HTMX components)
└── static/            # CSS utilities, HTMX, favicon
```

| Principle | Detail |
|-----------|--------|
| **No JS frameworks** | HTMX handles all interactivity server-side |
| **Stateless HTML** | Every route returns a partial HTML fragment, never JSON |
| **Signed cookies** | Session state via `SessionMiddleware` + `itsdangerous` |
| **Pure logic layer** | `game_logic.py` has zero side effects — easy to test |

---

## 🧪 Development

```bash
uv run ruff check .   # Lint
uv run pytest          # Test
uv sync                # Verify dependencies
```

All three must pass before committing.

---

## 📚 Workshop Lab Guide

This project is part of the **GitHub Copilot Agent Lab** — a hands-on workshop
on context engineering, design-first development, and multi-agent workflows.

| Part | Title | What You'll Do |
|------|-------|----------------|
| [**00**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=00-overview) | Overview & Checklist | Prerequisites and environment setup |
| [**01**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=01-setup) | Setup & Context Engineering | Teach AI about your codebase with instructions |
| [**02**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=02-design) | Design-First Frontend | Redesign the UI with creative themes |
| [**03**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=03-quiz-master) | Custom Quiz Master | Create custom quiz themes with agents |
| [**04**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=04-multi-agent) | Multi-Agent Development | Build features with TDD and design agents |

> 📝 Lab guides are also available in the [`workshop/`](workshop/) folder for offline reading.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
