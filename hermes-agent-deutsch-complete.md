# 🤖 Hermes Agent - Umfassende Deutsch Dokumentation

> **Das sich selbst verbessernde KI-Agent** — Langlebig, intelligent, allgegenwärtig  
> ⭐ **115.000+ Stars** auf GitHub | 📦 **MIT Lizenz** | 🔧 **47+ integrierte Tools**

---

## 📖 Inhaltsverzeichnis

1. [Einleitung](#-einleitung)
2. [Was ist Hermes Agent?](#-was-ist-hermes-agent)
3. [Kernkonzepte](#-kernkonzepte)
4. [Systemanforderungen](#-systemanforderungen)
5. [Installation](#-installation)
6. [Erste Schritte](#-erste-schritte)
7. [Konfiguration](#-konfiguration)
8. [CLI-Befehle](#-cli-befehle)
9. [Messaging Gateway](#-messaging-gateway)
10. [Memory System](#-memory-system)
11. [Skills-Erstellung](#-skills-erstellung)
12. [Tools Übersicht](#-tools-übersicht)
13. [Modell-Anbieter](#-modellanbieter)
14. [Plattformunterstützung](#-plattformunterstützung)
15. [Docker Deployment](#-docker-deployment)
16. [Remote Zugriff](#-remote-zugriff)
17. [Sicherheit](#-icherheit)
18. [Troubleshooting](#-troubleshooting)
19. [FAQ](#-faq)
20. [Glossar](#-glossar)
21. [Beispiel-Aufgaben](#-beispielaufgaben)
22. [Weiterführende Ressourcen](#-weiterfuhrende-ressourcen)

---

## 📝 Einleitung

**Hermes Agent** ist ein **autonomer KI-Agent**, der persistent auf deinem Server läuft, was er lernt, speichert und **sich selbst verbessert**. Es löst das fundamentale Problem aller anderen KI-Tools: *"Exzellent in diesem Moment, schwach mit der Zeit."*

### 💡 Das Kernversprechen

- **Langlebig**: Merkt sich alles, was du ihm sagst
- **Intelligent**: Erstellt automatisch Skills aus Erfahrungen
- **Allgegenwärtig**: Verfügbar über Telegram, Discord, Slack, Email, CLI und mehr
- **Kostenlos**: Läuft auf deiner eigenen Hardware
- **Offen**: MIT Lizenz, transparent, auditable

### 🎯 Zielgruppe

- **Entwickler**: Automatisierung von Code-Reviews und Testing
- **Schriftsteller**: Blog-Updates, Newsletter automatisch schreiben
- **Manager**: Daily Reports, Meeting-Zusammenfassungen
- **Forscher**: Paper-Tracking, Literatur-Recherche
- **Power-User**: Alle oben genannten + benutzerdefinierte Workflows

---

## 🤖 Was ist Hermes Agent?

### 🔍 Definition

Hermes Agent ist ein **autonomer, sich selbst verbessernder KI-Agent**, der:
- Persistent auf deinem Server läuft
- Memory von Sitzung zu Sitzung behält
- Skills automatisch aus Workflows erstellt
- Sich selbst optimiert basierend auf Benutzerfeedback
- Über 47 verschiedene Tools bereitstellt
- Mit 200+ Modell-Anbietern kompatibel ist

### 🆚 Vergleich zu anderen KI-Tools

| Merkmal | Hermes Agent | ChatGPT / Copilot / Andere |
|---------|-------------|----------------------|
| **Memory** | Persistenter, survives Reboots | Session-basiert, flüchtig |
| **Skills** | Auto-generiert, dauerhaft | Manuelles Konfigurieren |
| **Location** | Deine Hardware | Cloud (Daten privat!) |
| **Kosten** | Nur Hardware-Kosten | $20-100+/Monat |
| **Privacy** | Alles lokal | Daten zu Anbietern |
| **Zusammenhang** | Behält Kontext über Tage/Wochen | Nur während der Session |

### 🏗️ Architekturübersicht

```
┌────────────────────────────────────────────────────┐
│                    User                            │
│         (Telegram/Discord/CLI)                      │
└──────────────┬─────────────────────────────────────┘
               │
┌──────────────▼─────────────────────────────────────┐
│              Hermes Gateway                         │
│  - Multi-Channel Routing                            │
│  - Message Queue                                    │
│  - Scheduling Engine                                │
└──────────────┬─────────────────────────────────────┘
               │
┌──────────────▼─────────────────────────────────────┐
│              Hermes Agent Core                      │
│  ┌───────────┬───────────┬───────────┬───────────┐ │
│  │   Memory  │   Skills  │   Tools   │  Plans    │ │
│  └───────────┴───────────┴───────────┴───────────┘ │
└──────────────┬─────────────────────────────────────┘
               │
┌──────────────▼─────────────────────────────────────┐
│              LLM Backend (Optional)                 │
│  - Nous Portal                                      │
│  - OpenRouter (200+ Modelle)                        │
│  - API Keys (OpenAI, Anthropic, etc.)               │
│  - Local Models (Ollama, vLLM)                      │
└────────────────────────────────────────────────────┘
```

---

## 🧠 Kernkonzepte

### 1️⃣ **Memory, das sich verbessert**

**Speicherung:**
- Layered memory-System
- Lokal gespeicherte Markdown-Dateien in `~/.hermes/`
- Überlebt jeden Reboot und Modelloptausch
- 8 externe Memory-Provider verfügbar (Mem0, Supermemory, Vektordatenbanken)

**Persistenz:**
- Merkt sich alles über Tage, Wochen, Monate
- Behält Kontext über mehrere Sitzungen hinweg
- Aktualisiert sich proaktiv basierend auf Feedback
- Sucht durch eigene Vergangenheit mit FTS5 Volltextsuche

**Portabilität:**
- Markdown-Dateien sind menschenlesbar
- Einfache Inspektion und Backup
- Kompatibel mit allen Versionen
- Keine Vendor-Lock-in

### 2️⃣ **Autonomes Zeitplanen**

**Mechanismus:**
- Eingebaute Cron-Scheduler-Funktionalität
- Läuft auf deinem Server mit vollem Zugriff
- Natürlichsprachliche Automatisierungsdefinition

**Use Cases:**
- Morning News Briefings täglich um 08:00 Uhr
- PR Reviews jede Stunde
- Testsuite Monitoring nachts
- Blog-Tracker für neue Artikel
- Daily Standup Reports
- Wochenberichte automatisch

### 3️⃣ **Zugriff von überall (Multi-Surface)**

**Oberflächen:**
- ✅ Telegram
- ✅ Discord
- ✅ Slack
- ✅ WhatsApp
- ✅ Signal
- ✅ Matrix
- ✅ Email
- ✅ SMS
- ✅ Home Assistant
- ✅ Browser
- ✅ CLI Terminal

**Kontext:**
- Wechsle Oberflächen mittendrin in der Unterhaltung
- Behalte Kontext über alle Geräte hinweg
- Gleicher Agent, verschiedene Kanäle
- Voice Memo Transkription von Telegram nach CLI

---

## 💻 Systemanforderungen

### ✅ Mindestanforderungen

| Komponente | Version | Anmerkung |
|-----------|---------|-----------|
| **RAM** | 1 GB Min, 2 GB empfohlen | VPS $4-8/Monat möglich |
| **CPU** | 1 vCPU | Für 200+ Token pro Minute |
| **Speicher** | 10-20 GB SSD | Für Models und Caches |
| **OS** | Linux, macOS, WSL2, Android | Ubuntu 22.04+ empfohlen |
| **GPU** | **NICHT erforderlich!** | CPU-Ausführung ist völlig ausreichend |

### 🚀 Empfohlene Konfiguration

Für produktiven Einsatz:
- **RAM**: 4 GB
- **CPU**: 2 vCore
- **Storage**: 40 GB NVMe SSD
- **Optionale**: GPU für lokale Modelle (Ollama, vLLM)

**Kosten:**
- VPS: ~$4-8/Monat (Hetzner CX22)
- Hardware-to-go: $10-50 einmalig
- Serverless (Modal): Nur bei Bedarf

### 📱 Plattformunterstützung

| Platform | Status | Hinweis |
|----------|--------|---------|
| **Linux** | ✅ Full Support | Debian, Ubuntu, CentOS, Arch |
| **macOS** | ✅ Full Support | M1/M2/M3 Chips arbeiten |
| **WSL2** | ✅ Full Support | Windows Subsystem für Linux |
| **Windows** | ⚠️ Nur via WSL2 | Native Windows nicht empfohlen |
| **Android** | ✅ Termux | Spezielle Installation via Termux |
| **Chrome OS** | ⚠️ WSL2 | Nur wenn WSL2 verfügbar ist |

---

## 🚀 Installation

### ✅ One-Line Install (Empfohlen)

```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```

**Was dieser Befehl tut:**

1. **Installiert Tooling:**
   - Pullt `uv` Python-Installer
   - Installiert Python 3.11+
   - Clont GitHub Repository

2. **Konfiguriert Environment:**
   - Erstellt `~/.hermes/` Verzeichnis
   - Wiret Dependencies auf
   - Setupt `.env` mit Beispielen

3. **Startet Setup-Wizard:**
   - Interaktives Konfiguration
   - Modell-Anbieter Auswahl
   - Tools Enable/Disable

4. **Fertig:**
   ```bash
   hermes  # Starte Chatting!
   ```

### 📋 Alternative Installation Methoden

#### Method 1: Manuelle Installation

```bash
# 1. Dependencies installieren (falls nötig)
curl -fsSL https://cli.python.org/install.sh | bash
# oder
sudo apt update && sudo apt install python3.11 python3.11-venv

# 2. Tooling installieren
curl -fsSL https://github.com/astral-sh/uv/releases/download/uv/uv -o uv
sudo mv uv /usr/local/bin/uv

# 3. Repository klonen
git clone https://github.com/NousResearch/hermes-agent.git
cd hermes-agent

# 4. Python Virtual Environment
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt

# 5. Installation
pip install -e .
```

#### Method 2: Docker Container

```bash
# Image pullen
docker pull ghcr.io/nousresearch/hermes-agent:latest

# Container starten
docker run -d \
  --name hermes-agent \
  -e ANTHROPIC_API_KEY=sk-ant-... \
  -v ~/.hermes:/home/user/.hermes \
  -v ~/workspace:/workspace \
  -p 8642:8642 \
  ghcr.io/nousresearch/hermes-agent:latest
```

#### Method 3: Docker Compose (Empfohlen für Production)

```yaml
version: '3.8'

services:
  hermes-gateway:
    image: ghcr.io/nousresearch/hermes-agent:latest
    container_name: hermes-agent
    ports:
      - "8642:8642"
    volumes:
      - ~/.hermes:/home/hermes/.hermes
      - ~/workspace:/workspace
    environment:
      - ANTHROPIC_API_KEY=${ANTHROPIC_API_KEY}
      - OPENAI_API_KEY=${OPENAI_API_KEY}
    restart: unless-stopped
    mem_limit: 2g
  hermes-webui:
    image: ghcr.io/nesquena/hermes-webui:latest
    ports:
      - "8787:8787"
    volumes:
      - ~/.hermes:/home/hermeswebui/.hermes
      - ~/workspace:/workspace
    restart: unless-stopped
```

### 🔧 Post-Installation

Nach erfolgreicher Installation:

```bash
# 1. Shell neu laden
source ~/.bashrc    # oder: source ~/.zshrc

# 2. Setup Wizard starten
hermes setup

# 3. Modell-Anbieter wählen
hermes model

# 4. Interaktive CLI starten
hermes

# 5. Optional: Gateway setup
hermes gateway setup
hermes gateway start
```

### 🔄 Upgrade

```bash
# Always einfach:
hermes update

# Oder manuell:
git pull
uv sync
hermes update
```

---

## 🎯 Erste Schritte

### ✈️ Quick Start (60 Sekunden)

```bash
# 1. Install
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash

# 2. Setup Wizard
hermes setup

# 3. Model wählen
hermes model

# 4. Starten
hermes
```

### 📊 Erste Sitzung

Nach der Installation:

```bash
hermes
```

**Erstes Prompt:**
```
🤖 Hermes Agent v1.0.0

📚 Tools verfügbar: search, terminal, files, vision, browser, ...
💾 Memory: ~/.hermes/
🛠️ Gateway: hermes gateway

Welche helfe kann ich geben?
```

**Beispiel-Interaktion:**
```
HerMES: Hallo, ich bin Hermes Agent! 🦂

Was möchtest du erledigen?
→ Website recherchieren?
→ Code schreiben?
→ E-Mail schreiben?
→ Datei analysieren?
```

### 🎮 CLI Grundlagen

Starte eine interaktive Session:

```bash
hermes
```

**Verfügbare Befehle:**
- `/new` — Neue Konversation
- `/model [provider:model]` — Model wechseln
- `/skills` — Skills browse
- `/memory` — Memory ansehen
- `/usage` — Token-Nutzung Check
- `/compress` — Kontext komprimieren
- `/undo` — Letzten Schritt rückgängig
- `/retry` — Vorherigen Schritt erneut

**Unterbrechung:**
- `Ctrl+C` — Arbeit stoppen
- `/stop` — Gateway-Befehl (Messaging)

---

## ⚙️ Konfiguration

### 📝 Grundlegende Konfiguration

**1. Setup Wizard:**

```bash
hermes setup
```

**Fragt nach:**
- LLM-Provider (Anthropic, OpenAI, OpenRouter, Local)
- Default Model
- Tools Enable/Disable
- Gateway Platforms
- Memory Provider

**2. Modell Konfigurieren:**

```bash
hermes model
```

**Beispiele:**
- `anthropic:clauser-3-5-sonnet`
- `openrouter:mistral:open-mistral-7b`
- `openai:gpt-4o`
- `ollama:llama3`
- `Nous:portal`

**3. Tools Konfigurieren:**

```bash
hermes tools
```

**Kategorien:**
- `web_search` — Google, Bing, Brave suchen
- `browser` — Browser Automation
- `terminal` — Kommandozeilen Execution
- `files` — File Operations
- `code_exec` — Code Run (Python)
- `vision` — Image Analysis
- `tts` — Text zu Sprache
- `subagent` — Sub-Agent Delegation

---

### 🌐 API Keys Konfigurieren

**Environment Variablen:**

```bash
# In ~/.hermes/.env oder via setup
export ANTHROPIC_API_KEY=sk-ant-...
export OPENAI_API_KEY=sk-...
export OPENROUTER_API_KEY=sk-or-v1-...
export GOOGLE_API_KEY=AIza...
```

**Best Practices:**
- Verwende `.env` Datei
- Füge KEINE Keys in Git
- Nutze Secrets Manager (Vault, AWS Secrets)
- Regelmäßige Rotation
- Unterschiedliche Keys für Prod/Test

### 💻 Gateway Konfiguration

**1. Setup:**

```bash
hermes gateway setup
```

**2. Start:**

```bash
hermes gateway start
# Oder als Dienst installieren (systemd)
hermes gateway install
systemctl enable hermes-gateway
systemctl start hermes-gateway
```

**3. Plattformen aktivieren:**

```bash
hermes gateway sethome --platform=telegram
hermes gateway sethome --platform=discord
hermes gateway sethome --platform=slack
```

**4. Status prüfen:**

```bash
hermes gateway status
hermes gateway platforms
```

---

## ⌨️ CLI Befehle

### 📋 Daily Commands

| Befehl | Beschreibung | Beispiel |
|--------|-------------|----------|
| `hermes` | Interaktive Session | `hermes` |
| `hermes setup` | Setup Wizard | `- `hermes setup` |
| `hermes model` | Model wählen | `hermes model anthropic:clauser-3-5-sonnet` |
| `hermes update` | Upgrade | `hermes update` |
| `hermes tools` | Tools konfigurieren | `hermes tools` |
| `hermes config set` | Individual config | `hermes config set memory_store memory.md` |
| `hermes gateway` | Gateway starten | `hermes gateway start` |
| `hermes claw migrate` | OpenClaw Migrate | `hermes claw migrate` |
| `hermes doctor` | Diagnose | `hermes doctor` |

### 🎯 Session Commands

```bash
hermes              # Starte neue Session
hermes /new         # Neue Konversation
hermes /model gpt-4o # Model wechseln
hermes /skills      # Skills durchsuchen
hermes /memory      # Memory ansehen
hermes /usage       # Token-Budget Check
hermes /compress    # Kontext komprimieren
hermes /undo        # Letzten Schritt rückgängig
hermes /retry       # Vorherigen erneut
hermes /stop        # Aktuelle Arbeit stoppen
hermes /insights    # Insights über Sessions
```

### ⚙️ Config Commands

```bash
# Config anzeigen
hermes config

# Config setzen
hermes config set memory_store memory.md
hermes config set default_model anthropic:clauser-3-5-sonnet
hermes config set tools_all true

# Config auslesen
python -c "from hermes import config; print(config.memory_store)"

# Config exportieren
hermes config export > config.json
```

### 🔍 Debug Commands

```bash
# Status
hermes status

# Logs
tail -f ~/.hermes/logs/*.log

# Memory Inspect
cat ~/.hermes/memory.md

# Skills Liste
ls ~/.hermes/skills/

# Clear Memory (Vorsicht!)
rm ~/.hermes/memory.md
```

---

## 💾 Memory System

### 📚 Memory Struktur

```
~/.hermes/
├── memory.md           # Haupt-Memory (Präferenzen, Fakten)
├── user.md             # User Profile & Context
├── sessions/           # Session-Historie
│   ├── 2026-01-15T10-30-00.md
│   ├── 2026-01-15T11-45-00.md
│   └── ...
├── skills/             # Auto-generierte Skills
│   └── skill-name/SKILL.md
├── plans/              # Task-Pläne
├── trajectories/       # Forschungsdaten
└── logs/               # Agent-Logs
```

### 📝 Memory Management

**Speichern:**

```bash
hermes config set memory_store memory.md
```

**Manuelle Updates:**

```bash
nano ~/.hermes/memory.md

# Inhalt:
# User Preferences:
# - Liebt Kaffee ☕
# - Nutzt Telegram als primäres Messaging
# - Entwickelt in Python mit VSCode
# - Budget: €1000/Monat für Services
```

**Suche im Memory:**

```bash
# FTS5 Volltextsuche
sqlite3 ~/.hermes/sessions.db "SELECT * FROM sessions WHERE content LIKE '%Python%'"
```

### 🔒 Memory Privacy

```bash
# Memory Backup
tar -czvf ~/.hermes_backup.tar.gz ~/.hermes/

# Memory Encryptieren
gnupg --gen-key
echo "Sensitive Data" | gpg --symmetric --cipher-algo AES256 > encrypted.txt
```

---

## 🛠️ Skills-Erstellung

### 🎯 Skill Lifecycle

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Workaround    │ ───▶│   Skill Create  │ ───▶│   Skill Use     │
│   Interaktiv    │     │   Auto-Save     │     │   Slash Cmd     │
└─────────────────┘     └─────────────────┘     └─────────────────┘
                                   │
                                   ▼
                          ┌─────────────────┐
                          │   Self-Improve  │
                          │   During Use    │
                          └─────────────────┘
```

### 📄 Skill Struktur

Ein Skill wird als `SKILL.md` Datei gespeichert:

```markdown
# Skill: Social Media Tweet Generator

## 📋 User Profile

**Name:** Twitter Developer Voice
**Context:** Tech Lead, writes about Python, AI, development
**Audience:** Mid-to-senior level developers

## 🎭 Voice

**Personality:** Pragmatic und skeptisch
**Tone:** Fachlich, nicht übertrieben
**Word Choices:**
  - ✅ "really good" statt "incredible"
  - ✅ "effizienter" statt "game-changing"
  - ✅ "funktioniert" statt "revolutionär"

## 📝 Emoji Usage

- Moderately: Max 2-3 pro Tweet
- Preferred: 💻, 🐍, 🤖, 🚀
- Avoid: ✨, 💎, 😍

## 🎯 Guidelines

1. Tweet length: ~400 chars
2. Include code snippet examples
3. Link to GitHub repository
4. Tag @python
5. Avoid clickbait

## 📦 Dependencies

- Python 3.11+
- GitHub API access
- Twitter Developer Account

## 👤 Examples

Input: Script für Python Tips
Output: Thread über 3 Tweets mit Codebeispielen
```

### 🎨 Skill Erstellen

Nach einem Workaround kann Hermes den Skill automatisch speichern:

```bash
hermes  # Interaktive Session
# ... komplexer Task ...
# Nach Abschluss:
hermes skill save --name my-social-media-tweets
```

Das erstellt:
```
~/.hermes/skills/social-media-tweets/SKILL.md
```

### 🔧 Custom Skills

Manuelle Erstellung:

```bash
mkdir ~/.hermes/skills/mein-custom-skill
cd ~/.hermes/skills/mein-custom-skill
nano SKILL.md
```

**Beispiel: E-Mail Zusammenfassung Skill**

```markdown
# Skill: E-Mail Daily Digest

## 🎯 Funktion
Zusammenfassung aller E-Mails am Morgen.

## 🔧 Workflow
1. Email Provider API verbinden
2. New Mail Check (SMTP IMAP)
3. Zusammenfassung generieren
4. Als E-Mail versenden

## 📝 Prompt
"Bitte fasse alle neuen E-Mails von heute zusammen.
Konzentriere dich auf wichtige Aktionen.
Formatiere als kurze Übersicht."

## ⏰ Schedule
Frühschicht: 08:00 Uhr
```

---

## 🧰 Tools Übersicht

Hermes bietet **47+ integrierte Tools**, kategorisiert nach Anwendungsbereich.

### 🔍 Web & Search

| Tool | Beschreibung |
|------|-------------|
| `google_search` | Google Suche mit Kontext |
| `bing_search` | Bing Alternativ |
| `brave_search` | Brave Suche (Privacy) |
| `duckduckgo` | DDG für Privacy |

**Beispiel:**
```bash
/ search "Python 1000 lines code performance 2026"
```

### 🌐 Browser Automation

| Tool | Beschreibung |
|------|-------------|
| `browser_snapshot` | Screenshot der Webseite |
| `browser_click` | Klicks auf Elemente |
| `browser_type` | Formular ausfüllen |
| `browser_navigate` | Navigation |
| `browser_vision` | Vision Analyse |
| `browser_console` | Console Logs |

**Workflow:**
1. `navigate` zu URL
2. `snapshot` für Elements
3. `click` und `type` Interaktion
4. `go_back` History

### 🖥️ Terminal Execution

| Tool | Beschreibung |
|------|-------------|
| `terminal` | Shell Befehle |
| `terminal_background` | Hintergrund Prozesse |
| `process_poll` | Process Status |
| `process_kill` | Process Termination |

**Beispiel:**
```bash
hermes
> /terminal ls -la
> /terminal python --version
> /terminal git status
```

### 📁 File Operations

| Tool | Beschreibung |
|------|-------------|
| `read_file` | Datei lesen (mit Paginierung) |
| `write_file` | Datei schreiben (vollständig überschreiben) |
| `search_files` | Suche in Dateien/Verzeichnissen |
| `patch` | Find-and-Replace Edit |

**Workflow:**
```bash
# Datei lesen
/read_file path=README.md limit=50

# Datei schreiben
/write_file path=config.json content={"key": "value"}

# Suchen
/search_files pattern="*.py" target=content limit=10

# Editieren
/patch path=script.py old_string=def hello():\n new_string=def hello():\n    print("Hello")
```

### 💻 Code Execution

| Tool | Beschreibung |
|------|-------------|
| `code_exec` | Python Code Execute |
| `jupyter_notebook` | Jupyter Zell Ausführung |

**Beispiel:**
```bash
/code_exec
Paste Python code
> import pandas as pd
> df = pd.read_csv('data.csv')
> print(df.head())
```

### 👁️ Vision Analysis

| Tool | Beschreibung |
|------|-------------|
| `vision_analyze` | Image Analyse mit AI |

**Workflow:**
1. Image path oder URL
2. Frage formulieren
3. AI analysiert

**Beispiel:**
```bash
/vision_analyze image_url=https://example.com/chart.png question="Was zeigt dieser Diagramm?"
```

### 🔊 Media

| Tool | Beschreibung |
|------|-------------|
| `text_to_speech` | Text zu Audio (MP3) |
| `audio_to_text` | Audio Transkribieren |

**Beispiel:**
```bash
/text_to_speech text="Hallo, dies ist ein Beispiel." output_path=~/voice-memos/hello.mp3
```

### 🔌 MCP Servers

| Tool | Beschreibung |
|------|-------------|
| `mcp_register` | MCP Server registrieren |
| `mcp_call` | MCP Tool aufrufen |

**Server Beispiele:**
- File System
- Database (PostgreSQL, MySQL)
- GitHub
- Local Database
- Custom Tools

### 🤖 Sub-Agent

| Tool | Beschreibung |
|------|-------------|
| `delegate_task` | Sub-Agent erstellen |
| `orchestrator` | Multi-Agent Workflows |

**Beispiel:**
```bash
# Parallel Workstreams
delegate_task tasks=[
  {goal: "Forschung: Längeschnur Analyse", context: "Projekt XY"},
  {goal: "Code schreiben: Vergleichsfunktion", context: "Python"}
]

# Ergebnis aggregieren
# Beide Sub-Agenten parallel, Ergebnisse zusammenführen
```

---

## 🌍 Modell-Anbieter

### 🔗 Compatibility

Hermes funktioniert mit **200+ Modellen**, unterstützt durch:
- **Nous Portal** (Proprietär)
- **OpenRouter** (200+ Modelle)
- **Anthropic** (Claude)
- **OpenAI** (GPT)
- **Google** (Gemini)
- **Local** (Ollama, vLLM, LM Studio)
- **Custom** (Every OpenAI-compatible endpoint)

### 📊 Provider Vergleich

| Provider | Kosten | Vor-Teile | Nachteile |
|----------|--------|-----------|-----------|
| **Nous Portal** | Abonnement | Support, Integration | Closed, Subscription |
| **OpenRouter** | Pay-per-use | 200+ Modelle, günstige Optionen | API Limit bei High-Volumen |
| **OpenAI** | Pay-per-use | Hochwertige Modelle | Teuer, API Key Management |
| **Anthropic** | Pay-per-use | Claude 3.5 Sonnet (Top) | Teuer für lange Kontexte |
| **Google** | Pay-per-use | Great Context Window | API Key Management |
| **Ollama** | Kostenlos | Vollständig lokal, Privacy | Slower für große Modelle |

### 🎯 Modell Switching

```bash
# In der CLI
/model anthropic:clauser-3-5-sonnet

# Direkt über Config
hermes config set default_model openai:gpt-4o

# Provider wechseln
hermes model openrouter:deepseek:deepseek-r1
```

**Dynamic Switching:**
Während einer Session auf ein schnelleres/günstigeres Modell wechseln:
```bash
/model z-ai/glm-5-turbo  # Für iterative Feedback
```

### 🔑 API Keys

**Sicherer Umgang:**

```bash
# Generieren mit API Provider
# OpenRouter: https://openrouter.ai/
# Anthropic: https://console.anthropic.com/settings/keys
# Google: https://aistudio.google.com/

# In ~/.hermes/.env
ANTHROPIC_API_KEY=sk-ant-...
OPENAI_API_KEY=sk-...
OPENROUTER_API_KEY=sk-or-v1-...

# Secure Storage
gnupg --gen-key
echo "API_KEY=..." | gpg --symmetric > secure.txt
```

---

## 🖥️ Plattformunterstützung

### ✅ Offizielle Plattformen

**Messaging:**
- ✅ Telegram (Best Supported)
- ✅ Discord
- ✅ Slack
- ✅ WhatsApp
- ✅ Signal
- ✅ Matrix
- ✅ Email (SMTP)
- ✅ SMS (Twilio, etc.)

**Remote Access:**
- ✅ CLI Terminal
- ✅ Browser Web UI (Community)
- ✅ SSH Terminal (Remote)
- ✅ Home Assistant (Voice)

**Platform Commands:**

```bash
# Gateway Plattformen ansehen
hermes gateway platforms
hermes gateway status

# Plattform Konfigurieren
hermes gateway sethome --platform=telegram --user=8728423814
hermes gateway sethome --platform=discord --id=123456789
```

---

## 🐳 Docker Deployment

### 📦 Docker Compose

**docker-compose.yml:**

```yaml
version: '3.8'

services:
  hermes-agent:
    image: nousresearch/hermes-agent:latest
    container_name: hermes-agent
    platforms:
      - linux/amd64
    ports:
      - "${BIND_PORT:-8642}:8642"
    environment:
      - BIND_PORT=8642
      - LOG_LEVEL=DEBUG
      - ANTHROPIC_API_KEY=${ANTHROPIC_API_KEY}
      - OPENAI_API_KEY=${OPENAI_API_KEY}
      - OPENROUTER_API_KEY=${OPENROUTER_API_KEY}
      - GOOGLE_API_KEY=${GOOGLE_API_KEY}
    volumes:
      - ~/.hermes:/home/hermes-agent/.hermes
      - ~/workspace:/workspace
    mem_limit: 2g
    networks:
      - hermes-net

  hermes-webui:
    image: ghcr.io/nesquena/hermes-webui:latest
    ports:
      - "${BIND_WEBSITE_PORT:-8787}:8787"
    volumes:
      - ~/.hermes:/home/hermeswebui/.hermes
      - ~/workspace:/workspace
    networks:
      - hermes-net

networks:
  hermes-net:
    name: hermes-net
```

**Start:**

```bash
docker compose up -d

# Logs folgen
docker compose logs -f

# Status
docker compose ps
```

### 🔧 Custom Dockerfile

```dockerfile
FROM nousresearch/hermes-agent:latest

# Copy custom environment
COPY .env /home/hermes-agent/.env

# Install additional tools
RUN uv pip install hermes-tools-extra

# Health Check
HEALTHCHECK --interval=5m --timeout=3m \
  CMD curl -f http://localhost:8642/health || exit 1
```

---

## 🌐 Remote Zugriff

### 🔗 SSH Tunnel

**Linux Server:**
```bash
ssh -N -L 8642:127.0.0.1:8642 user@your-server
# Visit: http://localhost:8642
```

**MacOS mit LocalTunnel:**
```bash
# Install LocalTunnel
npm install -g localtunnel

# Tunnel erstellen
lt --port 8642
```

**NAT mit Tailscale:**
```bash
# Tailscale IP ermitteln
tailscale ip -4

#访问
hermes gateway start
# Visit: http://tailscale-ip:8642
```

### 🌍 PaaS Optionen

| Platform | Kosten | Features |
|----------|--------|----------|
| **Railway** | $5-7/mo | Git-push deploy, auto HTTPS |
| **Render** | $7/mo | Unlimited bandwidth, Redis included |
| **Fly.io** | $25/mo | Global deployment, Serverless |
| **Coolify** | Custom | Self-hosted, Docker-friendly |

### 🔐 Password Protection

Web UI kann mit Passwort geschützt werden:

```bash
# .env
WEBUI_PASSWORD=mein-sicheres-passwort
HERMES_API_URL=http://localhost:8642

# Start
./start.sh
```

---

## 🔒 Sicherheit

### 🛡️ 7-Layer Defense

```
┌─────────────────────────────────────┐
│  1. Prompt Injection Scanning       │
├─────────────────────────────────────┤
│  2. Tool Allowlists (whitelist)     │
├─────────────────────────────────────┤
│  3. Docker Isolation / Sandbox      │
├─────────────────────────────────────┤
│  4. User Approval für Critical Ops  │
├─────────────────────────────────────┤
│  5. API Token Validation            │
├─────────────────────────────────────┤
│  6. Rate Limiting                   │
├─────────────────────────────────────┤
│  7. Audit Logging                  │
└─────────────────────────────────────┘
```

### 🔐 Best Practices

**API Keys:**
- Verwende `.env` für sensitive Daten
- Git ignorieren im `.gitignore`
- Regelmäßige Rotation (jeweils 90 Tage)
- Unterschiedliche Keys für Prod/Test

**Tool Allowlist:**
```bash
hermes tools set allowlist [tool1, tool2, ...]
# Nur zugelassene Tools aktivieren
```

**Audit Logs:**
```bash
# Logs aktivieren
hermes config set log_level DEBUG

# Logs ansehen
tail -f ~/.hermes/logs/*.log
```

**Docker Hardening:**
```bash
docker run -d \
  --security-opt no-new-privileges \
  --cap-drop=ALL \
  --cap-add=NET_BIND_SERVICE \
  ...
```

---

## ⚠️ Troubleshooting

### 🔍 Häufige Probleme

#### Problem: "Cannot connect to API"

**Symptome:**
```
hermes
> Error: API request failed: connection refused
```

**Lösung:**
```bash
# 1. API URL Check
hermes config get api_url

# 2. API Key testen
curl https://api.openai.com/v1/
```

#### Problem: "Token Limit Erreicht"

**Symptome:**
```
hermes
> Error: Context window nearly full (95%)
```

**Lösung:**
```bash
# 3. Kontext komprimieren
/ compress

# 4. Token Nutzung ansehen
/usage

# 5. Memory bereinigen
rm ~/.hermes/sessions/*.md
```

#### Problem: "Memory nicht gefunden"

**Symptome:**
```
hermes
> File not found: ~/.hermes/memory.md
```

**Lösung:**
```bash
# 1. Create memory.md
touch ~/.hermes/memory.md

# 2. Beispiel content
echo "# Memory
# User: Name
# Präferenzen: Liste
" > ~/.hermes/memory.md
```

---

## ❓ FAQ

**Q: Ist Hermes kostenlos?**

**A:** Ja, Hermes ist MIT lizensiert. Kosten entstehen nur:
- API-Abschaltungen (falls Cloud Models)
- Hardware-Kosten (falls lokal)
- Server-Renew (falls VPS)

**Q: Kann ich mit allen Modellen nutzen?**

**A:** Hermes unterstützt 200+ Modelle:
- OpenAI, Anthropic, Google
- OpenRouter (Pay-per-use)
- Ollama, vLLM (lokal, kostenlos)
- Custom Endpoints

**Q: Wie speichere ich Workflows als Skill?**

**A:** Nach einem Workaround:
```bash
hermes skill save --name mein-workflow
```
Hermes erstellt automatisch `SKILL.md` mit:
- User Profile
- Voice
- Persona
- Workaround steps

**Q: Läuft Hermes auf Windows?**

**A:** Native Windows nicht empfohlen. Verwende WSL2:
```bash
# WSL2 installieren
https://learn.microsoft.com/windows/wsl/install

# Dann in WSL installieren
curl ... | bash
```

**Q: Wie much kostet ein VPS?**

**A:** ~$4-8/Monat (Hetzner CX22):
- 4 GB RAM
- 2 vCPU
- 40 GB SSD
- Vollständig ausreichend

---

## 📖 Glossar

| Begriff | Beschreibung |
|---------|-------------|
| **Gateway** | Multi-Channel Routing System (Telegram, Discord, CLI) |
| **Memory** | Persistenter Speicher in `~/.hermes/memory.md` |
| **Skill** | Auto-generierter Workflow, aufgerufen via `/skill-name` |
| **Tool** | Eingebaute Fähigkeit (Search, Browser, Terminal, Files) |
| **Sub-Agent** | Isolierte Sub-Agent für parallele Workstreams |
| **Backend** | Execute Umgebung (Local, Docker, SSH, Modal) |
| **Context Window** | Wie viel Kontext das Model verarbeiten kann |
| **FTS5** | SQLite Full-Text Search für Session-Wiederherstellung |
| **Hooncho** | Dialekt für User Modeling |
| **MCP** | Model Context Protocol (Server Verbindung) |

---

## 🎯 Beispiel-Aufgaben

### 1️⃣ Daily News Briefing

```bash
hermes
> Schedule: News Briefing um 08:00
> Source: RSS Feeds, Search, Social Media
> Output: E-Mail an meine Adresse
```

**Automatisierung:**
```bash
hermes scheduler create --name morning-briefing \
  --schedule "0 8 * * *" \
  --task "news_briefing --format=mail --recipients=@me"
```

### 2️⃣ Code Review Automation

```bash
hermes
> Clone Pull Request
> Review Code Changes
> Write Comments
> Approve/Reject mit Begründung

hermes delegate_task tasks=[
  {goal: "PR #123 Review", context: "Repository URL"},
  {goal: "Generate Performance Analysis", context: "PR Diff"}
]
```

### 3️⃣ Blog Content Generator

```bash
hermes
> Analyze Top Blog
> Generate Similar Topic
> Research Sources
> Write Draft
> Edit mit Feedback

hermes skill save --name blog-writer
```

### 4️⃣ Test Suite Runner

```bash
hermes
> Review Git Repository
> Generate Unit Tests
> Generate Integration Tests
> Run Test Suite
> Report Ergebnisse

hermes delegate_task tasks=[
  {goal: "Generate Tests", context: "Project Structure"},
  {goal: "Run Test Suite", context: "Package Configuration"}
]
```

### 5️⃣ Email Cleanup

```bash
hermes
> Analyze Inbox
> Identify Low-Priority
> Generate Archive Strategy
> Implement mit Backup
```

### 6️⃣ Social Media Monitoring

```bash
hermes
> Track Keywords
> Analyze Sentiment
> Generate Reports
> Alert bei Issues

hermes skill save --name social-monitor
```

---

## 🔗 Weiterführende Ressourcen

### 📚 Offizielle Quellen

- **GitHub:** https://github.com/NousResearch/hermes-agent
- **Documentation:** https://hermes-agent.nousresearch.com/docs
- **Cheatsheet:** https://hermescheatsheet.com/

### 📖 Tutorials

- **Getting Started:** https://hermes-agent.nousresearch.com/docs/getting-started
- **CLI Guide:** https://hermes-agent.nousresearch.com/docs/user-guide/cli
- **Gateway Guide:** https://hermes-agent.nousresearch.com/docs/user-guide/messaging
- **Skills Guide:** https://hermes-agent.nousresearch.com/docs/user-guide/skills

### 🎤 Community

- **GitHub Stars:** 115.000+ Sterne (!!)
- **License:** MIT (Open Source)
- **Issues:** https://github.com/NousResearch/hermes-agent/issues
- **Discussions:** https://github.com/NousResearch/hermes-agent/discussions

### 🛠️ Docker Image

- **Registry:** ghcr.io/nousresearch/hermes-agent
- **Web UI:** ghcr.io/nesquena/hermes-webui
- **Tags:** latest, v1.0.0, v1.1.0

### 💰 Kosten

| Komponente | Kosten | Hinweise |
|------------|--------|----------|
| **Hardware** | $0-100 | Eigener Server |
| **VPS** | $4-8/Monat | Hetzner, AWS, DigitalOcean |
| **API Calls** | Pay-per-use | OpenRouter, OpenAI, Anthropic |
| **Serverless** | Pay-per-use | Modal, Daytona |
| **Docker** | Kostenlos | Self-Hosting |

### 📧 Support

Bei Problemen:
1. **GitHub Issues** [erstellen](https://github.com/NousResearch/hermes-agent/issues)
2. **Discussions** für Fragen nutzen
3. **Documentation** durchsuchen
4. **Community** Forums besuchen

---

## 📜 Lizensierung

```text
Copyright 2024-2026 Nous Research

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 📦 Changelog

### Version 1.0.0 (Aktuelle Version)
- ✅ Vollständiger Memory-System
- ✅ 47+ integrierte Tools
- ✅ Multi-Channel Support
- ✅ Auto-Skill Erzeugung
- ✅ Docker & K8s Support
- ✅ Mobile PWA Support

### Version 0.x.x
- ⚙️ Early Access Features
- 🚧 Experimental Skills
- 🔧 Developer-Tools

---

**Letzte Aktualisierung:** 2026 (aktuell)

**Dokumentiert von:** AI Assistant mit Hilfe offizeller Quellen

---

*📝 Diese Dokumention basiert auf:*
*   https://github.com/NousResearch/hermes-agent
*   https://hermes-agent.nousresearch.com/
*   https://hermescheatsheet.com/

*📖 Die offizielle Website https://get-hermes.ai ist ein Community-Portal für die Verwendung von Hermes Agent.*

*🌟 Join 115.000+ GitHub Stars!*

---

*🎉 Happy Agenting!*
