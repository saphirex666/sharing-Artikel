# 📚 Hermes Workspace - Umfassende Deutsch Dokumentation

> **Dein AI-Agentes Kommandozentralplatz** — Chat, Dateien, Speicher, Skills und Terminal an einem Ort  
> ⭐ 2.000+ Stars auf GitHub | 📦 Open Source (MIT)

---

## 📖 Inhaltsverzeichnis

1. [Einleitung](#-einleitung)
2. [Was ist Hermes Workspace?](#-was-ist-hermes-workspace)
3. [Systemanforderungen](#-systemanforderungen)
4. [Installation](#-installation)
5. [Setup-Anleitung](#-setupanleitung)
6. [Konfiguration](#-konfiguration)
7. [Gliederansicht](#-gliederansicht)
8. [Funktionen im Detail](#-funktionen-im-detail)
9. [Skills-Übersicht](#-skillsübersicht)
10. [Schriftauswahl-Einstellungen](#-schriftauswahleinstellungen)
11. [Berechtigungen & Sicherheit](#-berechtigungen--icherheit)
12. [Docker-Setup](#-docker-Setup)
13. [Lokale Modelle](#-lokale-modelle)
14. [Mobile Zugriff](#-mobile-zugriff)
15. [Faq & Troubleshooting](#-faq--troubleshooting)
16. [Glossar](#-glossar)
17. [Weiterführende Ressourcen](#-weiterfuhrende-ressourcen)

---

## 📝 Einleitung

Hermes Workspace ist eine **nativ webbasierte Kommandozentrale** für AI-Agenten, die alle Aspekte deiner automatisierten Workflows an einem einzigen Interface vereint. Es dient als Schicht über dem Hermes-Agent und bietet eine vollständige UI, um deine Agenten zu steuern, zu überwachen und zu verwalten.

### 🎯 Hauptziele

- **Unified Interface**: Alle Agentenfunktionen in einer einzigen Oberfläche
- **Real-time Monitoring**: Live-Anzeige der Agentenaktivitäten
- **Vollständiger Zugriff**: Chat, Terminal, Speicher, Skills und Dateien
- **Multi-Model Support**: Nahtlose Integration mit verschiedenen LLM-Anbietern
- **Mobile First**: Vollständige Funktionalität auf allen Geräten

---

## 🤖 Was ist Hermes Workspace?

Hermes Workspace ist eine **native Web-Workspace-Lösung** für den Hermes-Agent, der Agenten orchestriert, Speicher durchsucht, Skills verwaltet und alles von einer einzelnen Schnittstelle aus steuert.

### 🔑 Kernkonzept

Das Workspace läuft auf **vanilla Hermes Agent** (kein Fork), was bedeutet, dass:
- Keine Modifikationen am ursprünglichen Agenten
- Keine Drift von den Original-Features
- Vollständige Kompatibilität mit Updates
- Zero-maintenance Betrieb

### 🏗️ Architektur

```
┌─────────────────────────────────────────────────────────┐
│                    Hermes Workspace                      │
│  (Port 3000) UI Interface & Dashboard                    │
└────────────────────┬────────────────────────────────────┘
                     │
┌────────────────────▼────────────────────────────────────┐
│                  Hermes Gateway                          │
│  (Port 8642) API Layer & Session Management              │
│  - Model Management                                       │
│  - Memory Operations                                      │
│  - Skills Management                                      │
│  - Job Orchestration                                      │
└────────────────────┬────────────────────────────────────┘
                     │
┌────────────────────▼────────────────────────────────────┐
│              LLM Backend (optional)                      │
│  - Anthropic (Claude)                                     │
│  - OpenAI                                                  │
│  - OpenRouter                                              │
│  - Ollama (local)                                          │
│  - vLLM                                                    │
│  - LM Studio                                              │
└─────────────────────────────────────────────────────────┘
```

---

## 💻 Systemanforderungen

### ✅ Mindestanforderungen

| Komponente | Version | Anmerkung |
|-----------|---------|-----------|
| **Node.js** | 22+ | Für Frontend-Builds |
| **Python** | 3.11+ | Für Hermes Agent Backend |
| **pnpm** | Neueste | Paketmanager |
| **CPU** | 2+ Kerne | Empfohlen |
| **RAM** | 4GB+ | Minimale, 8GB+ empfohlen |
| **Speicher** | 10GB+ | Für Modelle und Caches |

### 🔧 Optionale Anforderungen

- **Docker** & **Docker Compose** (für Containerized Deployment)
- **Git** (für clonen des Repositories)
- **curl** (für Installation)

---

## 🚀 Installation

### ✅ Methode 1: One-Line Install (Empfohlen)

Die einfachste und schnellste Installationsmethode, die automatisch alles erkennt und installiert.

```bash
# Einzeiler - Installiert alles notwendige
curl -fsSL https://hermes-workspace.com/install.sh | bash
```

**Was dieser Befehl tut:**

1. **Erkennt vorhandene Dependencies:**
   - Prüft auf Node.js 22+
   - Prüft auf Python 3.11+
   - Prüft auf pnpm

2. **Installiert fehlende Komponenten:**
   - Installiert fehlende Paketmanager
   - Setzt `hermes-agent` von PyPI

3. **Klonet das Repository:**
   - Clont von GitHub
   - Erstellt Projektstruktur

4. **Konfiguriert `.env`:**
   - Erstellt Beispiel-Konfiguration
   - Promptet für LLM-Provider-Auswahl

5. **Idee: Wiederverwendbar**
   - Kann neu ausgeführt werden
   - Upgrades unterstützt

### 📋 Installation manuell (für Advanced Users)

```bash
# 1. Herunterladen des Repositories
git clone https://github.com/outsourc-e/hermes-workspace.git
cd hermes-workspace

# 2. Installieren von Abhängigkeiten
pnpm install

# 3. Kopieren der Beispiel-Konfiguration
cp .env.example .env

# 4. Konfigurieren des .env
nano .env  # Oder bevorzugter Editor verwenden

# 5. API-Token hinzufügen (falls authentication aktiviert ist)
echo 'HERMES_API_TOKEN=dein-token' >> .env

# 6. Workspace starten
pnpm dev
```

### 🔄 Upgrade von einer früheren Version

```bash
# Pull der neuesten Changes
git pull

# Upgrade der Abhängigkeiten
pnpm install

# Neustart
pnpm dev
```

---

## ⚙️ Setup-Anleitung

### ✈️ Schritt-für-Schritt Setup

#### **Schritt 1: One-Line Installation**

```bash
curl -fsSL https://hermes-workspace.com/install.sh | bash
```

**Nach dem Befehl:**

- System prüft Dependencies
- Fehltinstallationen durchführen
- Workspace klonen
- `.env` wire up

#### **Schritt 2: Gateway und UI starten**

Du hast **zwei Optionen**:

**Option A: Separate Terminale (Empfohlen für Debugging)**

```bash
# Terminal 1: Gateway starten (Port 8642)
hermes gateway run

# Terminal 2: Workspace starten (Port 3000)
cd ~/hermes-workspace && pnpm dev
```

**Option B: Alles auf einmal**

```bash
pnpm start:all
```

**Erster Lauf:** Fordert `hermes setup` auf, um einen Provider auszuwählen.

#### **Schritt 3: Browser öffnen**

Öffne **http://localhost:3000** im Browser.

### 🎯 Setup Checklist

- [ ] Node.js 22+ installiert
- [ ] Python 3.11+ installiert
- [ ] pnpm installiert
- [ ] `hermes-agent` von PyPI installiert
- [ ] Workspace Repository geklont
- [ ] `.env` Datei konfiguriert
- [ ] LLM-Provider API-Key hinzugefügt
- [ ] Gateway läuft (:8642)
- [ ] Workspace läuft (:3000)
- [ ] Browser Zugriff funktioniert

---

## ✍️ Konfiguration

### 📝 Grundlegende Konfiguration (.env)

```bash
# API URL zum Hermes Gateway
HERMES_API_URL=http://127.0.0.1:8642

# Dashboard API URL (optional)
HERMES_DASHBOARD_URL=http://127.0.0.1:9119

# API-Token (falls authentication aktiviert)
HERMES_API_TOKEN=dein-api-token

# Optional: Custom Port
PORT=3000

# LLM Provider Konfiguration
ANTHROPIC_API_KEY=sk-ant-...           # Claude
OPENAI_API_KEY=sk-...                  # OpenAI
OPENROUTER_API_KEY=sk-or-v1-...        # OpenRouter
GOOGLE_API_KEY=AIza...                 # Gemini

# Optional: API-Server Host (für remote access)
API_SERVER_HOST=0.0.0.0
```

### 🔐 Authentication Konfiguration

Falls dein Gateway mit `API_SERVER_KEY` gestartet wurde:

```bash
# In ~/.hermes/.env oder wherever der Gateway config liest:
API_SERVER_ENABLED=true
API_SERVER_KEY=dein-sicherer-schlussel
```

Dann im Workspace:

```bash
HERMES_API_TOKEN=dein-sicherer-schlussel
```

### 🌐 Remote Konfiguration (Tailscale / VPN / LAN)

Für Zugriff von anderen Geräten:

```bash
# Auf dem Server mit Workspace + Gateway:
HERMES_API_URL=http://100.x.y.z:8642
HERMES_DASHBOARD_URL=http://100.x.y.z:9119

# Gateway konfigurieren für alle Interfaces:
API_SERVER_HOST=0.0.0.0
```

**Schritte:**

1. **Tailscale installieren** auf Mac und Mobile Devices
2. **Einloggen** mit gleichem Account
3. **IP-Adresse ermitteln:**
   ```bash
   tailscale ip -4
   ```
4. **Access von Mobile:**
   ```
   http://100.x.x.x:3000
   ```

---

## 🖥️ Gliederansicht

Hermes Workspace bietet **6 Kern-Oberflächen**, die den typischen Workflow abdecken.

### 📊 Screen 01: Chat

**Multi-Model Conversations mit Real-time Tool Activity**

- **Unterstützte Modelle:**
  - Claude (Anthropic)
  - GPT (OpenAI / OpenRouter)
  - Gemini (Google)
  - Codex
  - Locale Modelle (Ollama, vLLM)

- **Features:**
  - Wechsle zwischen Modellen im Thread
  - Verliere keinen Kontext
  - Live-Tool-Aktivitätsanzeige
  - Tool-States Streaming in UI
  - Approve, abort, inspect Tool-Aufrufe

### 🎻 Screen 02: Conductor

**Mission Orchestrator — Spawn parallel Agents, watch them work**

- **Funktionen:**
  - Parallele Sub-Agenten erstellen
  - Live Worker Grid anzeigen
  - Mission-Orchestrierung
  - Worker Monitoring
  - Parallel Processing Visualisierung

- **Workflow:**
  1. Mission definieren
  2. Worker-Sub-Agenten spawnen
  3. Live Fortschritt überwachen
  4. Ergebniss aggregieren

### 📊 Screen 03: Dashboard

**At-a-glance metrics across sessions, messages, tools, tokens**

- **Metriken:**
  - Session Dumps
  - Nachrichten Statistiken
  - Tool-Aufrufe
  - Token-Nutzung
  - Kosten Tracking
  - Performance Metriken

- **Dashboards:**
  - Übersicht über alle Sessions
  - Token-Versuch Tracking
  - Kostenüberwachung
  - Tool-Effizienz

### 💾 Screen 04: Memory

**Browse and search what your agent remembers**

- **Funktionen:**
  - Browse durch agenten Speicher
  - Volltextsuche
  - Filterung nach Typ
  - Editieren von Speichereinträgen
  - Historie durchsuchen
  - Context Management

- **Speicher-Typen:**
  - Konversations-Historie
  - Fakten-Erinnerungen
  - Präferenzen
  - Session-Context
  - User Profiles

### 🖥️ Screen 05: Terminal

**Browser-native pty innerhalb des Workspaces**

- **Funktionen:**
  - Browser-basiertes Terminal
  - Full Color Support
  - Kommandozeilen-Befehle
  - Ausgabe-Streaming
  - Process Management
  - Dateioperationen

- **Use Cases:**
  - Remote Commands ausführen
  - Live Debugging
  - Script Execution
  - System-Information
  - Log-Inspektion

### ⚙️ Screen 06: Settings

**Themes, providers, accents — 8 paired light/dark themes**

- **Themen:**
  - 8 gepaarte light/dark Themen
  - Anpassbare Accents
  - Dark Mode Standard
  - System-Theme Erkennung

- **Einstellungen:**
  - API-Provider Selektoren
  - Modell Präferenzen
  - Interface Optionen
  - Benachrichtigungen
  - Sicherheitsoptionen

---

## 🎨 Funktionen im Detail

Hermes Workspace ist **für Agenten gebaut, die echte Arbeit leisten**.

### 📦 6 Kern-Features

#### 1️⃣ **Multi-Model Chat**

**Beschreibung:** Claude, GPT, Gemini, Codex und lokale Modelle in einem einzigen Chat-Flow. Wechsle mitten im Thread ohne Kontextverlust.

- **Cross-Model Conversations:**
  - Starte mit einem Modell
  - Wechsle für Teilaufgaben
  - Behalte einen gemeinsamen Thread
  - Kontext bleibt erhalten

- **Smart Model Routing:**
  - Automatic Provider Erkennung
  - Failover bei Ausfällen
  - Load balancing

#### 2️⃣ **Memory & Skills**

**Beschreibung:** Persistenter Speicher plus ein tiefes Katalog von 100+ Skills, die dein Agent nutzen kann. Durchsuchen und live editieren.

- **Speicher-Möglichkeiten:**
  - Conversational Memory
  - Factoid-Erinnerungen
  - User-Preferenzen
  - Session-Context
  - Tool-State-Persistierung

- **Skills-Management:**
  - 100+ integrierte Skills
  - Live-Browsing
  - Online-Editierung
  - Custom Skill Einbinden
  - Skill-Kategorisierung

- **Skill-Kategorien:**
  - `automation` - Automatisierungsaufgaben
  - `web_scraping` - Web-Data-Erfassung
  - `research` - Forschungs-Tools
  - `email` - E-Mail-Operations
  - `terminal` - Shell-Befehle
  - `browser` - Browser-Automation
  - `file` - Datei-Operationen
  - `mlops` - ML/Ops Tools
  - Und viele mehr (100+)!

#### 3️⃣ **Integrated Terminal**

**Beschreibung:** Befehle dort ausführen, wo dein Agent läuft — pty im Browser, volle Farben, ohne den Workspace zu verlassen.

- **Terminal-Funktionen:**
  - Browser-native pty
  - Echtzeit-Ausgabe
  - Error Logging
  - Process Management
  - Multi-line Input
  - Color-coded Output

- **Sicherheit:**
  - Sandbox-Environment
  - Permission Bounds
  - Audit Logging

#### 4️⃣ **Real-time Tool Cards**

**Beschreibung:** Beobachte den Agenten nachdenken und handeln mit Live Tool States in der UI. Approve, abort, inspect.

- **Live Monitoring:**
  - Tool-Aufrufe Streamen
  - Parameter-Echtzeit-Anzeige
  - Ergebnisse sofortig anzeigen
  - Error Tracking

- **Interaction:**
  - Approve Tool-Aufrufe
  - Abort bei Bedarf
  - Inspect Details
  - Batch-Operations

#### 5️⃣ **Mobile-first PWA**

**Beschreibung:** Vollständige Feature-Parität auf Desktop, Tablet oder Telefon. Installieren auf Home-Screen, offline funktionieren, push notifications.

- **PWA Features:**
  - Offline Support
  - Install to Home Screen
  - Push Notifications
  - Full Feature Parity
  - Responsive Design
  - Touch-optimized

- **Mobile-Support:**
  - iPhone/Android
  - Tablet views
  - Touch Gestures
  - Mobile Keyboard
  - Optimized Layout

#### 6️⃣ **Conductor + Operations**

**Beschreibung:** Mission Orchestrator mit parallelen Sub-Agenten, Live Worker Grid und Operations-Konsole für Management jedes laufenden Agenten.

- **Conductor Features:**
  - Parallel Sub-Agenten
  - Mission-Workflow
  - Progress Tracking
  - Result Aggregation

- **Operations Console:**
  - Agent Monitoring
  - Process Management
  - Resource Tracking
  - Performance Metrics
  - Error Alerts

---

## 🛠️ Skills-Übersicht

Hermes Workspace bietet Zugriff auf **100+ Skills**, kategorisiert nach Anwendungsbereich.

### 🔧 Automation Skills

```yaml
- auto-deduplicate-lists: Automatisches Deduplizieren von Listen-Daten
- proxy-auto-discovery: Proxy-Quellen automatisch entdecken, validieren, dok
- hermes-dashboard-scanner: Dashboards automatisch scannen
```

### 🤖 Autonomous AI Agents

```yaml
- claude-code: Task Delegierung an Claude Code CLI (PRs)
- codex: Task Delegierung an OpenAI Codex CLI
- hermes-agent: Hermes-Agent Konfigurieren, erweitern
- opencode: Task Delegierung an OpenCode CLI
- subagent-driven-development: Sub-Agent-basierte Entwicklung
```

### 🍺 Bier-Angebot Vergleich

```yaml
- bier-angebot-vergleich: Automatisierter Bier- und Getränkevergleich
```

### 🎨 Creative Skills

```yaml
- architecture-diagram: SVG-Architektur-Diagramme
- ascii-art: ASCII Art Generierung
- ascii-video: ASCII Video Konvertierung
- baoyu-comic: Wissens Comics (知识漫画)
- baoyu-infographic: Information Diagramme
- claude-design: Design HTML Artifacts
- design-md: DESIGN.md Token Spezifikationen
- excalidraw: Handgezeichnete Excalidraw Diagramme
- ideation: Projekt Ideen Generierung
- manim-video: Manim math/algo Animationen
- p5js: p5.js generative Kunst
- pixel-art: Pixel Art mit Retro-Paletten
- humanizer: Text humanisieren
- stable-diffusion: Text-zu-Bild Generierung
- clip: Vision-Language-Konnektions
- segment-anything-model: Zero-Shot Segmentierung
```

### 🏢 Dashboard Automation

```yaml
- dashboard-automation: Automatische Dashboard-Erstellung mit CI/CD
```

### 📊 Data Science

```yaml
- jupyter-live-kernel: Iterative Python via live Jupyter Kernel
- pandas-analysis: Pandas Datenanalyse
```

### 🚀 DevOps Skills

```yaml
- proxy-auto-search: Proxy-Github + API Quellen scouten
- proxy-scrape-system: Proxy-Scraping System
- webhook-subscriptions: Event-driven agent runs
```

### 🐕 Dogfood Testing

```yaml
- dogfood: Exploratory QA von Web Apps
```

### 📧 Email Skills

```yaml
- himalaya: IMAP/SMTP Email vom Terminal
- gmail-automation: Gmail API Automation
```

### 🔍 Expand Proxy Source Search

```yaml
- expand-proxy-source-search: Proxy-Quellen erweitern mit 20+ Suchbegriffen
- proxy-auto-scraping: Automatisiertes Proxy-Scraping
- proxy-auto-search-discovery: Proxy-Quellen automatisch entdecken
- proxy-source-discovery: Proxy-Quellen automatisch discoveren
```

### 🧩 GitHub Workflow

```yaml
- github-auth: Github auth setup mit SSH Keys, gh CLI
- github-code-review: PR Review: Diffs, Inline Comments
- github-repo-management: Repositories clonen/erstellen/managen
- github-issues: Issues erstellen, triage, label, assign
- github-pr-workflow: Pull Request Lebenszyklus
- github-repo-mgmt: Releases, Remotes verwalten
```

### 📦 Kleinanzeigen Scraping

```yaml
- kleinanzeigen-scraping: Automatisches Scraping kleinanzeigen
```

### 📍 Leisure Skills

```yaml
- find-nearby: Nahegelegene Orte finden (Restaurants, Apotheken)
```

### 💻 MCP Skills

```yaml
- native-mcp: MCP Client: Server verbinden, Tools registrieren
- mcporter: MCP CLI: Liste, konfigurieren, auth, call servers
```

### 📺 Media Skills

```yaml
- gif-search: GIFs von Tenor suchen/herunterladen
- songsee: Audio-Spektrogramme/features
- youtube-content: YouTube Transkripte zu Zusammenfassungen
- whatsapp-status: Instagram/WhatsApp Status automatisiert
```

### 🧠 Memory Stack Setup

```yaml
- memory-stack-setup: Hermes Memory Stack Setup auf Server mit Docker
```

### ☁️ MLOps (Cloud)

```yaml
- modal-serverless-gpu: Serverless GPU Cloud für ML Workloads
```

### 🏗️ MLOps (Evaluation)

```yaml
- evaluating-llms-harness: LM-Eval Harness Benchmarking
- weights-and-biases: W&B für ML Experimente
```

### 🏗️ MLOps (Inference)

```yaml
- gguf-quantization: GGUF Quantisierung für effiziente Inferenz
- guidance: LLM Ausgabe mit Regex/Grammaren kontrollieren
- llama-cpp: llama.cpp lokale GGUF Inferenz
- obliteratus: LLM Refusals abliterate
- outlines: Strukturierte JSON/Regex LLM Generierung
- serving-llms-vllm: vLLM High-Throughput Serving
```

### 🤖 MLOps (Models)

```yaml
- audiocraft-audio-generation: MusicGen/.AudioGen
- clip: Vision-Language Konnektions
- segment-anything-model: SAM zero-shot Segmentation
- stable-diffusion-image-generation: Text-zu-Bild Generierung
- whisper: OpenAI speech recognition
```

### 📚 MLOps (Research)

```yaml
- arxiv: arXiv Papers suchen
- blogwatcher: Blogs/RSS-Feeds überwachen
- llm-wiki: Karpathy LLM Wiki
- polymarket: Polymarket Queries
- sisa-agent-research: SISA-Agent Forschung automatisieren
- second-brain-automation: Second Brain MCP Skill
```

### 📧 Social Media

```yaml
- whatsapp-chat: Instagram/WhatsApp Chat automatisieren
- xitter: X/Twitter mit x-cli
- xurl: X/Twitter mit xurl CLI
- telegram-bot: Telegram Bot API
```

### 💻 Software Development

```yaml
- debugging-hermes-tui: Hermes TUI Befehle debuggen
- hermes-agent-skill-authoring: In-repo SKILL.md Autoring
- node-inspect-debugger: Node.js --inspect + Chrome DevTools
- plan: Plan mode: markdown zu .hermes/plans/
- python-debugpy: Python pdb REPL + debugpy remote
- requesting-code-review: Pre-commit review
- systematic-debugging: 4-Phase Root Cause Debugging
- test-driven-development: TDD RED-GREEN-REFACTOR
- writing-plans: Implementierungsplane schreiben
- subagent-driven-development: Plans via sub-agent ausführen
```

### 🔌 MCP Skills

```yaml
- native-mcp: MCP Client
- mcporter: MCP CLI Bridge
```

### 🏠 Smart Home

```yaml
- openhue: Philips Hue Lights, scenes, rooms control
```

### 🧪 Red Teaming

```yaml
- godmode: Jailbreak LLMs: Parseltongue, GODMODE, ULTRAPLINIAN
```

### 📜 Second Brain

```yaml
- second-brain-automation: Second Brain MCP Skill
- llm-wiki: Interlinker markdown KB
- github-wiki: WIKI Management
```

### 🔄 Workspace Dispatch

```yaml
- workspace-dispatch: Mission Orchestrator
- cronjob: Cron Job Management
- delegation: Sub-Agent Orchestrierung
```

### 🌐 Yuanbao

```yaml
- yuanbao: Yuanbao (元宝) Groups: @mention, query
```

---

## 💡 Schriftauswahl-Einstellungen

### 🎨 Themen

Hermes Workspace bietet **8 gepaarte light/dark Themen**:

1. **Zen Light / Zen Dark** - Minimalistisch
2. **Grayscale Light / Grayscale Dark** - Schwarz-Weiß
3. **Nordic Light / Nordic Dark** - Kühle Töne
4. **Dracula / Dracula** - Beliebtes Theme
5. **Catppuccin / Catppuccin** - Modern
6. **One Dark / One Dark** - Classic
7. **Gruvbox / Gruvbox** - Retro
8. **Monokai / Monokai** - Professionell

### 🌈 Akzente

Jedes Hauptthema kann mit akzent-Farben angepasst werden:
- 🟢 Greenscale-Akkzente
- 🔵 Bluescale-Akkzente
- 🟣 Purplescale-Akkzente
- 🧡 Orangescale-Akkzente
- 🔴 Reds
- 🟡 Yellows
- 🩶 Grayscales
- 🌈 Rainbowscale-Akkzente

---

## 🔐 Berechtigungen & Sicherheit

### 🔑 API Token Management

**Token-Konfiguration:**

```bash
# Im .env
HERMES_API_TOKEN=dein-secure-schlüssel
```

**Best Practices:**

- Tokens NICHT in Public Repositories commiten
- `.env` zu `.gitignore` hinzufügen
- Tokens regelmäßig rotieren
- Environment-Variablen bevorzugen
- Token-Revoke bei verdächtigem Zugriff

### 🛡️ Authentication

Falls der Gateway mit `API_SERVER_KEY` gestartet wurde:

```bash
# Beide müssen übereinstimmen:
HERMES_API_TOKEN=<gleicher-token-wie-API_SERVER_KEY>
```

**Secure Key Generieren:**

```bash
# Mit openssl
openssl rand -base64 32

# Oder mit pwgen
pwgen 64 1
```

---

## 🐳 Docker Setup

### 📦 Voraussetzungen für Docker

- **Docker Engine** installiert
- **Docker Compose** installiert
- **Anthropic API Key** — [Einen hier erhalten](https://console.anthropic.com/settings/keys)
- **Optional:** Andere LLM API Keys

### 🚀 Schritt 1: Environment Konfigurieren

```bash
# Repository klonen
git clone https://github.com/outsourc-e/hermes-workspace.git
cd hermes-workspace

# Beispiel-Konfiguration kopieren
cp .env.example .env

# .env editieren
nano .env
```

**Mindestens einen LLM-Provider hinzufügen:**

```bash
# Wähle mindestens einen:
ANTHROPIC_API_KEY=sk-ant-...           # Empfehlung: Claude
# OPENAI_API_KEY=sk-...                # GPT / o-series
# OPENROUTER_API_KEY=sk-or-v1-...      # OpenRouter (kostenlose Modelle verfügbar)
# GOOGLE_API_KEY=AIza...               # Gemini
```

### 🏃 Schritt 2: Services Starten

```bash
docker compose up
```

**Dies zieht zwei prepared Images und startet sie:**

- **hermes-agent** → `nousresearch/hermes-agent:latest` auf Port **8642**
- **hermes-workspace** → `ghcr.io/outsourc-e/hermes-workspace:latest` auf Port **3000**

#### ✅ Verifizieren

Prüfe die Docker Logs für `[gateway] Connected to Hermes` — dies bestätigt die erfolgreiche Verbindung.

```bash
docker compose logs -f
```

### 📦 Schritt 3: Vom Source Bauen

Für benutzer_definierte Builds:

```bash
docker compose -f docker-compose.yml -f docker-compose.dev.yml up --build
```

### 📜 Schritt 4: Pre-Built Image (Coolify / Easypanel / Dokploy / Unraid)

```yaml
service: hermes-workspace
image: ghcr.io/outsourc-e/hermes-workspace:latest
ports:
  - 3000:3000
env:
  HERMES_API_URL: http://hermes-agent:8642
  HERMES_API_TOKEN: ${API_SERVER_KEY}  # Falls gateway auth aktiviert
  ANTHROPIC_API_KEY: ${ANTHROPIC_API_KEY}
command: >-
  sh -c "sleep 10 && hermes dashboard && pnpm start:all"
```

---

## 🧠 Lokale Modelle

Hermes Workspace unterstützt **zwei Modi** mit lokalen Modellen:

### 🎯 Portable Mode (Easily)

Kein Hermes Gateway benötigt — direkt auf deinen local Server zeigen.

**Ollama Beispiel:**

```bash
# Ollama starten
OLLAMA_ORIGINS=* ollama serve

# Workspace Ollama zeigen
HERMES_API_URL=http://127.0.0.1:11434 pnpm dev
```

**vLLM Beispiel:**

```bash
# vLLM starten
vllm serve your-model \
  --host 127.0.0.1 \
  --port 8000

# Workspace vLLM zeigen
HERMES_API_URL=http://127.0.0.1:8000/v1/chat/completions pnpm dev
```

### 🔧 Enhanced Mode (Voll Features)

Leite durch das Hermes Gateway für Sitzungen, Speicher, Skills, Jobs und Tools.

```bash
# 1. Gateway activation aktivieren in ~/.hermes/.env:
API_SERVER_ENABLED=true

# 2. Everything starten together:
hermes gateway run          # Kern-APIs auf :8642
hermes dashboard            # Dashboard-APIs auf :9119
hermes workspace dev        # Workspace auf :3000
```

---

## 📱 Mobile Zugriff

### 🔗 Zugriff über Tailscale

Access Hermes Workspace von überall auf deinen Devices — kein port forwarding, keine VPN-Verwicklung.

**Setup:**

1. **Tailscale installieren** auf Mac und mobilem Device
2. **Einloggen** mit gleichem Tailscale Account
3. **Mac Tailscale IP ermitteln:**
   ```bash
   tailscale ip -4
   # Beispiel-Ausgabe: 100.x.y.z
   ```
4. **Hermes Workspace auf deinem Phone öffnen:**
   ```
   http://100.x.y.z:3000
   ```

### 📲 PWA Features

Auf Mobile:

- **Install to Home Screen:** Ein-Klick-Installation
- **Offline Support:** Funktionsfähig ohne Internet
- **Push Notifications:** Alerts für Agenten-Aktivitäten
- **Touch-Optimized:** Große Buttons, klare Navigation
- **Full Feature Parity:** Alle Funktionen verfügbar

---

## ❓ FAQ & Troubleshooting

### 🔍 Häufige Fragen

**Q: Welches ist das beste LLM-Modell für Hermes?**

**A:** Claude 3.5 Sonnet ist empfohlen, aber alle OpenAI-kompatiblen Endpunkte funktionieren. OpenRouter bietet kostenlose Modelle für Testing.

**Q: Kann ich mit mehreren Modellen gleichzeitig arbeiten?**

**A:** Ja! Hermes Workspace ermöglicht Multi-Model Conversations. Wechsle mitten im Thread zwischen Claude, GPT, Gemini ohne Kontextverlust.

**Q: Wie verwalte ich API Costs?**

**A:** Nutze das Dashboard für:
- Token-Versuch Tracking
- Kostenüberwachung
- Model Switching für günstigere Optionen
- Batch Processing mit optimierten Modellen

**Q: Wie starte ich den Agenten im Hintergrund?**

**A:** 
```bash
hermes gateway run --daemon
# Oder
systemctl enable hermes
systemctl start hermes
```

**Q: Was tun bei Verbindungsfehlern?**

**A:**
1. Prüfe `.env` Konfiguration
2. Verifiziere API-URL ist korrekt
3. Stelle sicher, dass API-Tokens gültig sind
4. Prüfe Firewall-Einstellungen
5. Starte Services neu: `pnpm restart`

**Q: Wie updatte ich auf eine neuere Version?**

**A:**
```bash
git pull
pnpm install
pnpm dev
```

### ⚠️ Bekannte Probleme

**Problem:** "Cannot connect to Camofox"

**Lösung:** Camofox Browser Server benötigt. Starte mit:
```bash
npm start  # in camofox-browser
# Oder
docker run -p 9377:9377 -e CAMOFOX_PORT=9377 jo-inc/camofox-browser
```

**Problem:** "HERMES_API_URL unreachable"

**Lösung:** Stelle sicher, dass:
- Der Gateway läuft (`hermes gateway run`)
- Die API-URL in `.env` korrekt ist
- Port 8642 verfügbar ist, dass nicht belegt ist
- Firewall-Regeln erlauben den Zugriff

**Problem:** "Token Invalid"

**Lösung:**
1. Re-gegenerieren des API-Tokens
2. `.env` Neustart
3. Gateway Neustart
4. Workspace Cache löschen: `rm -rf node_modules/.cache`

---

## 📖 Glossar

| Begriff | Beschreibung |
|---------|--------------|
| **Gateway** | API Layer (Port 8642) der Hermes-Agent mit Models, Memory, Skills |
| **Workspace** | UI Interface (Port 3000) für Interaktion mit dem Agenten |
| **Conductor** | Mission Orchestrator für parralele Sub-Agenten |
| **Skill** | Ein modulare Fähigkeit, die dein Agent nutzen kann |
| **Memory** | Speicher für Agenten-Kontext, Fakten, Präferenzen |
| **PWA** | Progressive Web App mit Offline-Funktionen |
| **pty** | Pseudo-Terminal für Terminal-Simulation im Browser |
| **SSE** | Server-Sent Events für Real-Time Updates |
| **Token** | Einheit zur Messung von LLM-Ausgaben |
| **Sub-Agent** | Ein Parallele Worker-Agent, der eine Teil-Mission bearbeitet |

---

## 🔗 Weiterführende Ressourcen

### 📚 Offizielle Quellen

- **GitHub Repository:** https://github.com/outsourc-e/hermes-workspace
- **Hermes Agent Docs:** https://hermes-agent.nousresearch.com/docs
- **Hermes Atlas:** https://hermesatlas.com/projects/outsourc-e/hermes-workspace

### 📖 Community

- **GitHub Stars:** 2.000+ Sterne
- **MIT License:** Open Source, kommerziell erlaubt
- **Discussions:** [GitHub Discussions](https://github.com/outsourc-e/hermes-workspace/discussions)

### 🎓 Tutorial

- **HerMES Agent Workspace V2: Complete 2026 Guide**
- **Blog Post:** https://aisuccesslabjuliangoldie.com/blog/hermes-agent-workspace/
- **Demo Videos:** [YouTube Playlist](link-zu-Demo-VIDEOS)

### 🛠️ Docker

- **Docker Hub:** `nousresearch/hermes-agent:latest`
- **Container Registry:** `ghcr.io/outsourc-e/hermes-workspace:latest`
- **Compose:** docker-compose.yml + docker-compose.dev.yml

### 📧 Support

Bei Problemen:
1. **GitHub Issues** [erstellen](https://github.com/outsourc-e/hermes-workspace/issues)
2. **Discussions** für Fragen nutzen
3. **Wiki** durchsuchen
4. **Community** beitreten

---

## 🎯 Checkliste für Erste Installierung

```yaml
Erste-Installierung:
  installieren:
    - [x] curl -fsSL https://hermes-workspace.com/install.sh | bash
    - [x] hermes gateway run
    - [x] cd ~/hermes-workspace && pnpm dev
    - [x] http://localhost:3000 im Browser öffnen
  
  konfigurieren:
    - [x] LLM API-Keys hinzufügen
    - [x] .env überprüfen
    - [x] Modelle testen
    - [x] Skills durchsuchen
  
  erkunden:
    - [x] Chat-Funktionen
    - [x] Terminal ausprobieren
    - [x] Memory durchsuchen
    - [x] Dashboard metrics
    - [x] Settings anpassen
```

---

## 📜 Lizensierung

```text
Copyright 2025 outsource-something

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
- ✅ Vollständige UI für Hermes-Agent
- ✅ Multi-Model Support
- ✅ 100+ Skills integriert
- ✅ Docker Support
- ✅ Mobile PWA
- ✅ Docker Compose
- ✅ Offline Support

### Version 0.x.x
- ⚙️ Early Access Features
- 🚧 Experimental Skills
- 🔧 Developer-Tools

---

**Letzte Aktualisierung:** 2026 (aktuell)

**Dokumentiert von:** AI Assistant mit Hilfe der offiziellen Quellen

---

*📝 Diese Dokumention basiert auf https://hermes-workspace.com*

*ℹ️ Für Updates, bitte GitHub Repository überprüfen:*

```bash
git remote -v
git fetch
git checkout main
git pull
```

*🎉 Happy Agenting!*
