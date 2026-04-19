---
theme: default
title: DA Hotel CRM - Slides Hub
titleTemplate: "%s"
info: |
  Zentrale Startfolie für Intro- und Fortschritts-Präsentationen
highlighter: shiki
transition: fade
mdc: true
---

# 🎞️ DA Hotel CRM - Slides Hub

Zentrale Einstiegsfolie für alle Präsentationen rund um das Projekt.

- Intro und Projektpitch
- Fortschritts-Updates pro Sprint
- Später: Demo-, Architektur- und Abschluss-Decks

---

# 🗂️ Verfügbare Decks

## 00 - Projektvorstellung

Datei: `progress-00-day-0-engineering-setup.md`

Inhalt:

- Projektidee
- Tech-Stack
- Lernansatz ohne Framework
- 8-Wochen-Plan
- offene Mentor-Fragen

Starten:

```bash
npm run dev:intro
```

---

# 📈 Fortschrittsdecks

## 01 - Setup + erster TDD Service

Datei: `progress-01.md`

Inhalt:

- abgeschlossenes Day-0 Setup
- CI, Hooks, Linting, Tests
- erster HotelService
- erste grüne Tests
- nächste Schritte für Sprint 01

Starten:

```bash
npm run dev:progress
```

---

# 🧭 Empfohlene Struktur für die Zukunft

Für spätere Präsentationen dieses Schema nutzen:

- `progress-00-day-0-engineering-setup.md`
- `progress-01.md`
- `progress-02.md`
- `progress-03.md`
- `architecture-deep-dive.md`
- `demo-bookings.md`
- `final-presentation.md`

So bleibt `slides.md` immer nur der Hub.

---

# ⚙️ Nützliche Commands

```bash
# Hub anzeigen
npm run dev

# Intro-Deck
npm run dev:intro

# aktuelles Progress-Deck
npm run dev:progress
```

Builds:

```bash
npm run build
npm run build:intro
npm run build:progress
```

---

---
layout: center
---

# 🚀 Einstieg wählen

Intro für neue Zuschauer:
`progress-00-day-0-engineering-setup.md`

Aktueller Projektstand:
`progress-01.md`
