<div align="center">

🌐 [Português (BR)](README.pt_BR.md) | [Español](README.es.md)

# 🎱 Soc Ops

**Social Bingo for real-world networking events**

*Find someone who matches each square — get 5 in a row to win!*

[![Python](https://img.shields.io/badge/Python-3.13+-3776ab?logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![HTMX](https://img.shields.io/badge/HTMX-powered-3d72d7?logo=html5&logoColor=white)](https://htmx.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

---

## ✨ Features

- 🎲 **Randomized 5×5 board** — every player gets a unique card
- 🆓 **Free center square** — always marked to get you started
- ✅ **Instant bingo detection** — rows, columns, and diagonals
- 🔄 **Reset & replay** — start a fresh game at any time
- 📱 **Works on any device** — responsive, no app install required

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | [FastAPI](https://fastapi.tiangolo.com) + Python 3.13 |
| Frontend | [Jinja2](https://jinja.palletsprojects.com) templates + [HTMX](https://htmx.org) (no JS frameworks) |
| Styling | Custom CSS utility classes |
| State | Signed cookies via [itsdangerous](https://itsdangerous.palletsprojects.com) |
| Server | [Uvicorn](https://www.uvicorn.org) ASGI |

---

## 🚀 Quick Start

```bash
# 1. Install dependencies
uv sync

# 2. Start the dev server
uv run uvicorn app.main:app --reload
```

Open **http://localhost:8000** and start playing! 🎉

---

## 🧑‍💻 Development Checklist

> ⚠️ **Mandatory** — all three must pass before every commit:

```bash
uv run ruff check .   # lint (unused vars, type hints, style)
uv run pytest         # tests
uv sync               # dependencies resolve cleanly
```

---

## 📚 Lab Guide

| Part | Title |
|------|-------|
| [**00**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=00-overview) | Overview & Checklist |
| [**01**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=01-setup) | Setup & Context Engineering |
| [**02**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=02-design) | Design-First Frontend |
| [**03**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=03-quiz-master) | Custom Quiz Master |
| [**04**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=04-multi-agent) | Multi-Agent Development |

> 📝 Lab guides are also available in the [`workshop/`](workshop/) folder for offline reading.
