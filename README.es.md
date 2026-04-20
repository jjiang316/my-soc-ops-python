<!-- l10n-sync: source-file="README.md" -->
🌐 [Português (BR)](README.pt_BR.md) | [Español](README.es.md)

<div align="center">

# 🎲 Soc Ops

**¡Rompe el hielo. Llena el tablero. Canta BINGO!**

Un juego de bingo social para encuentros presenciales — socializa con el grupo,
encuentra personas que coincidan con cada casilla y compite por conseguir cinco en fila.

Construido con **Python · FastAPI · Jinja2 · HTMX** — cero frameworks JavaScript del lado del cliente.

</div>

---

## ✨ Cómo Funciona

```
┌──────────┬──────────┬──────────┬──────────┬──────────┐
│ va en    │ tiene    │ toca un  │ habla    │ corrió   │
│ bici     │ mascota  │ instrum. │ 2+ idiom │ maratón  │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ nació en │ conoció  │ puede    │ hizo     │ le gusta │
│ otro est │ famoso   │ malabars │ paracaid │ cocinar  │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ tiene    │ viajó    │ ESPACIO  │ es       │ tiene    │
│ jardín   │ a Asia   │  LIBRE   │ zurdo/a  │ gemelo/a │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ juega    │ hace     │ tiene    │ ama la   │ salió    │
│ videojue │ yoga     │ talento  │ comida   │ en TV    │
├──────────┼──────────┼──────────┼──────────┼──────────┤
│ coleccio │ leyó un  │ sabe     │ vivió en │ prefiere │
│ algo úni │ libro    │ señas    │ el extr. │ té > ☕  │
└──────────┴──────────┴──────────┴──────────┴──────────┘
```

1. **Inicia un juego** — cada jugador recibe un tablero aleatorio de 5×5
2. **Socializa** — encuentra a alguien que coincida con una casilla y tócala
3. **Cinco en fila** — fila, columna o diagonal — ¡eso es BINGO! 🎉

---

## 🚀 Inicio Rápido

```bash
# Clona y entra al proyecto
git clone https://github.com/jjiang316/my-soc-ops-python.git
cd my-soc-ops-python

# Instala dependencias
uv sync

# Inicia la aplicación
uv run soc-ops
```

Luego abre **http://localhost:8000** en tu navegador y comienza a jugar.

> 💡 **Consejo:** Se incluye configuración de DevContainer — ábrelo en GitHub Codespaces o VS Code para una experiencia sin configuración.

---

## 🏗️ Arquitectura

```
app/
├── main.py            # Rutas FastAPI → fragmentos HTML parciales HTMX
├── models.py          # Modelos Pydantic v2 (inmutables)
├── game_logic.py      # Funciones puras: generación de tablero, detección de bingo
├── game_service.py    # Mutaciones de estado vía dataclass GameSession
├── data.py            # Preguntas y constantes
├── templates/         # Plantillas Jinja2 (base + componentes HTMX)
└── static/            # Utilidades CSS, HTMX, favicon
```

| Principio | Detalle |
|-----------|---------|
| **Sin frameworks JS** | HTMX maneja toda la interactividad del lado del servidor |
| **HTML sin estado** | Cada ruta devuelve un fragmento HTML parcial, nunca JSON |
| **Cookies firmadas** | Estado de sesión vía `SessionMiddleware` + `itsdangerous` |
| **Lógica pura** | `game_logic.py` no tiene efectos secundarios — fácil de probar |

---

## 🧪 Desarrollo

```bash
uv run ruff check .   # Lint
uv run pytest          # Tests
uv sync                # Verificar dependencias
```

Los tres deben pasar antes de hacer commit.

---

## 📚 Guía del Laboratorio

Este proyecto es parte del **GitHub Copilot Agent Lab** — un taller práctico
sobre ingeniería de contexto, desarrollo orientado al diseño y flujos multi-agente.

| Parte | Título | Qué Harás |
|-------|--------|-----------|
| [**00**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=00-overview) | Visión General y Lista de Verificación | Requisitos y configuración del entorno |
| [**01**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=01-setup) | Configuración y Context Engineering | Enseña a la IA sobre tu código con instrucciones |
| [**02**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=02-design) | Desarrollo Frontend Orientado al Diseño | Rediseña la UI con temas creativos |
| [**03**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=03-quiz-master) | Quiz Master Personalizado | Crea temas de quiz personalizados con agentes |
| [**04**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=04-multi-agent) | Desarrollo Multi-Agente | Construye funcionalidades con TDD y agentes de diseño |

> 📝 Las guías del laboratorio también están disponibles en la carpeta [`workshop/`](workshop/) para lectura sin conexión.

---

## 📄 Licencia

Este proyecto está licenciado bajo la [Licencia MIT](LICENSE).
