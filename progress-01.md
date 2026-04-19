---
theme: default
title: DA Hotel CRM - Fortschritt 01
titleTemplate: "%s"
info: |
  Sprint Update - Setup + erster TDD Service
highlighter: shiki
transition: fade-out
mdc: true
---

# 📈 DA Hotel CRM - Fortschritt 01

Setup abgeschlossen, erste echte Domänen-Logik gestartet.

- Stand: Ende Day-0 Engineering Setup
- Fokus heute: Tooling + Qualitätsfundament
- Ziel: ab morgen Feature-Slices pro Domain

---

# ✅ Was wir umgesetzt haben

- Vite + Vanilla TypeScript Frontend aufgesetzt
- ESLint + Prettier eingerichtet
- Vitest mit jsdom und Coverage-Basis eingerichtet
- Husky + lint-staged Git-Hooks aktiviert
- Erste HotelService-Logik implementiert
- Ersten echten Test-Block geschrieben (4 Tests grün)

---

# 🧱 Technisches Fundament (Jetzt live)

| Bereich    | Status | Ergebnis                    |
| ---------- | ------ | --------------------------- |
| Build/Dev  | ✅     | Vite läuft lokal            |
| Linting    | ✅     | ESLint Regeln aktiv         |
| Formatting | ✅     | Prettier im Workflow        |
| Testing    | ✅     | Vitest ausführbar           |
| Git Hooks  | ✅     | pre-commit + pre-push aktiv |

---

# 🧪 TDD-Start: HotelService

Erste fachliche Regeln sind umgesetzt und getestet:

- Name ist Pflicht
- City ist Pflicht
- Keine Duplikate (name + city)
- Hotels können deaktiviert werden

```ts
expect(() => service.create({ name: "city inn", city: "berlin" })).toThrow(
  "Hotel already exists: city inn (berlin)",
);
```

---

# 🐙 Git-Workflow (sauber in Schritten)

Heute wurde bewusst in kleinen Commits gearbeitet:

1. Setup: Vite + TypeScript
2. Setup: ESLint + Prettier
3. Setup: Vitest
4. Setup: Husky + lint-staged
5. Feature-Start: HotelService + Tests

Warum wichtig: Jede Änderung bleibt einzeln reviewbar.

---

# 🎯 Nächste Schritte (Sprint 01)

- Supabase Client sauber anbinden
- HotelService von In-Memory auf Supabase umstellen
- shared/types für Hotel-Domäne aufbauen
- Erste Hotel-List View an Service koppeln
- RLS-Policy für hotels Tabelle vorbereiten

---

# ❓Feedback an Mentor & Team

- Ist der Setup-Standard so für das Hauptrepo passend?
- Wollen wir Coverage-Grenzen sofort erzwingen oder ab Sprint 2?
- Auth zuerst (Woche 1) oder parallel mit Hotels starten?

Vielen Dank - wir sind jetzt bereit für echte Feature-Entwicklung.
