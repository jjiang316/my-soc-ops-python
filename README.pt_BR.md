<!-- l10n-sync: source-file="README.md" -->
🌐 [Português (BR)](README.pt_BR.md) | [Español](README.es.md)

<div align="center">

# 🎲 Soc Ops

**Quebre o gelo. Preencha o tabuleiro. Grite BINGO!**

Um jogo de bingo social para encontros presenciais — circule pelo grupo,
encontre pessoas que correspondam a cada quadrado e corra para completar cinco em linha.

Construído com **Python · FastAPI · Jinja2 · HTMX** — zero frameworks JavaScript no cliente.

</div>

---

## ✨ Como Funciona

```
┌──────────┬──────────┬──────────┬──────────┬──────────┐
│ vai de   │ tem      │ toca um  │ fala     │ correu   │
│ bike     │ pet      │ instrum. │ 2+ idiom │ maratona │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ nasceu   │ conheceu │ sabe     │ já fez   │ ama      │
│ em outro │ famoso   │ malabar. │ paraqued │ cozinhar │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ tem      │ viajou   │ ESPAÇO   │ é        │ tem      │
│ jardim   │ p/ Ásia  │  LIVRE   │ canhoto  │ gêmeo    │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ joga     │ faz      │ tem um   │ ama      │ apareceu │
│ videogam │ yoga     │ talento  │ pimenta  │ na TV    │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ colecio- │ leu um   │ sabe     │ morou no │ prefere  │
│ na algo  │ livro    │ libras   │ exterior │ chá > ☕ │
└──────────┴──────────┴──────────┴──────────┴──────────┘
```

1. **Inicie um jogo** — cada jogador recebe um tabuleiro aleatório 5×5
2. **Circule** — encontre alguém que corresponda a um quadrado e toque nele
3. **Cinco em linha** — linha, coluna ou diagonal — isso é BINGO! 🎉

---

## 🚀 Início Rápido

```bash
# Clone e entre no projeto
git clone https://github.com/jjiang316/my-soc-ops-python.git
cd my-soc-ops-python

# Instale as dependências
uv sync

# Inicie o app
uv run soc-ops
```

Depois abra **http://localhost:8000** no navegador e comece a jogar.

> 💡 **Dica:** Uma configuração de DevContainer está incluída — abra no GitHub Codespaces ou VS Code para uma experiência sem configuração.

---

## 🏗️ Arquitetura

```
app/
├── main.py            # Rotas FastAPI → fragmentos HTML parciais HTMX
├── models.py          # Modelos Pydantic v2 (imutáveis)
├── game_logic.py      # Funções puras: geração de tabuleiro, detecção de bingo
├── game_service.py    # Mutações de estado via dataclass GameSession
├── data.py            # Perguntas e constantes
├── templates/         # Templates Jinja2 (base + componentes HTMX)
└── static/            # Utilitários CSS, HTMX, favicon
```

| Princípio | Detalhe |
|-----------|---------|
| **Sem frameworks JS** | HTMX gerencia toda a interatividade no servidor |
| **HTML sem estado** | Cada rota retorna um fragmento HTML parcial, nunca JSON |
| **Cookies assinados** | Estado de sessão via `SessionMiddleware` + `itsdangerous` |
| **Lógica pura** | `game_logic.py` não tem efeitos colaterais — fácil de testar |

---

## 🧪 Desenvolvimento

```bash
uv run ruff check .   # Lint
uv run pytest          # Testes
uv sync                # Verificar dependências
```

Os três devem passar antes de fazer commit.

---

## 📚 Guia do Lab

Este projeto faz parte do **GitHub Copilot Agent Lab** — um workshop prático
sobre engenharia de contexto, desenvolvimento design-first e fluxos multi-agente.

| Parte | Título | O Que Você Fará |
|-------|--------|-----------------|
| [**00**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=00-overview) | Visão Geral & Lista de Verificação | Pré-requisitos e configuração do ambiente |
| [**01**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=01-setup) | Configuração & Engenharia de Contexto | Ensine a IA sobre seu código com instruções |
| [**02**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=02-design) | Frontend Design-First | Redesenhe a UI com temas criativos |
| [**03**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=03-quiz-master) | Quiz Master Personalizado | Crie temas de quiz personalizados com agentes |
| [**04**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=04-multi-agent) | Desenvolvimento Multi-Agente | Construa funcionalidades com TDD e agentes de design |

> 📝 Os guias do lab também estão disponíveis na pasta [`workshop/`](workshop/) para leitura offline.

---

## 📄 Licença

Este projeto está licenciado sob a [Licença MIT](LICENSE).
