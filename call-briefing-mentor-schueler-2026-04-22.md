# DA Hotel App - Call Briefing (Mentor + Schüler)

Stand: 22.04.2026
Ziel: Schnelle, klare Antworten im Projektcall

## 1) Aktueller Ist-Stand (gesichert)

- Tooling-Basis steht: Vite, TypeScript, ESLint, Prettier, Vitest, Husky, lint-staged.
- Erster echter Service ist umgesetzt: HotelService mit In-Memory-Logik.
- Teststatus: 4 von 4 Tests grün (100 % Coverage für getesteten Code).
- Lintstatus: keine Errors, nur 2 Warnings im Vite-Template-Counter.
- Frontend UI ist noch größtenteils Vite-Starter und noch nicht auf CRM-Oberfläche umgestellt.

## 1b) Testing-Status im Detail (für Mentor-Fragen)

**Was wird getestet:**

- HotelService: Create, Validierung, Duplikat-Check, Deactivation
- TDD-Ansatz: Test vor Implementierung (Red → Green → Refactor Pattern)
- Vitest mit jsdom und V8 Coverage

**Testing-Pyramide geplant:**

- Unit Tests (viele): Services, Validatoren, Utils — aktuell aktiv
- Integration Tests (einige): Service + Supabase Mocks — geplant ab Sprint 2
- E2E Tests (wenige): komplette User Flows — geplant ab Woche

**Coverage-Schwelle:**

- Aktuell: 80 % für `src/services/**` (hart durchgesetzt, weich für UI)
- Plan: Ab Sprint 2 schrittweise erhöhen auf 85 %, später 90 %

**Nächste Test-Schritte:**

1. HotelService auf Supabase umstellen (Tests mit Mocks weiterführen)
2. CustomerService mit Tests bauen
3. Auth-Logik und Rollenprüfung mit Tests absichern
4. Integration Tests für kritische Flows schreiben

## 2) Was bereits vorbereitet ist (Dokumentation)

- Projektplan mit Phasen -1 bis 7 ist ausgearbeitet.
- 8-Wochen-Ausbildungsplan ist klar definiert.
- Datenmodell und Tech-Stack sind dokumentiert.
- Governance-Dokumente (Repository Policy, Workflow-Backlog, Contributing) sind vorhanden.

## 2b) Projektmanagement-Tool

- **ClickUp** — wird vom Mentor bereitgestellt und ist bereits verfügbar.
- Einsatz: Aufgaben, Sprint-Planung, Fortschrittsverfolgung für das gesamte Team.
- Offene Fragen für den Call:
  - Wie werden Tasks aus dem 8-Wochen-Plan in ClickUp abgebildet (Sprints, Lists, Boards)?
  - Welche Workflow-Stufen nutzen wir (z.B. To Do → In Progress → Review → Done)?
  - Werden GitHub-PRs mit ClickUp-Tasks verknüpft (Branch-Naming via ClickUp-ID)?

## 3) Offene Entscheidungen (Mentor-Blocker)

- Auth-Strategie:
  - Option A: Supabase Auth
  - Option B: Eigenes JWT-System
- Router-Strategie:
  - Option A: Eigener Mini-Router
  - Option B: Navigo

Empfehlung für schnellen Lernfortschritt:

- Auth: Supabase Auth
- Router: Navigo in früher Phase, später optional Mini-Router als Lernmodul

## 3b) Backend & Skalierbarkeit (vom Mentor erwähnt)

**Aktueller Ansatz:**

- Supabase als vollständiger Backend (DB + Auth + RLS + REST API).
- Kein separater Node.js/Express-Server nötig für MVP.
- Alle Business-Logik sitzt im Frontend (TypeScript Services).

**Skalierbarkeit später:**

- Wenn Business-Logik komplexer wird: ggf. Supabase Edge Functions oder eigener Backend.
- Vorerst nicht nötig — die Komplexität ist auf Bookings reduziert.
- RLS-Policies in Supabase ersetzen serverseitige Autorisierung.

**Konkrete Frage für Mentor:**

- Wollen wir vorerst ohne Backend arbeiten und ggf. später migrieren?
- Oder sollen wir schon die Backend-Struktur vorbereiten (auch wenn nicht genutzt)?

## 4) Saubere Aussage im Call (wichtig)

So formulieren:

- Setup und Qualitätsfundament sind produktiv startklar.
- Erste Domänenlogik wurde TDD-first umgesetzt und validiert.
- Der **erste Meilenstein ist konkret definiert: Buchungssystem für 1 Hotel** (Homepage + Back-Office).
- Wir starten sequenziell, nicht alles parallel — dadurch bleiben Qualität und Fokus erhalten.
- Mit Mentor-Entscheidung zu Auth und Router können wir ohne Reibungsverlust in die nächste Phase gehen.

## 5) Projektfokus & Scope (vom Mentor)

**Wichtig vs. Nicht-Wichtig:**

- Alles ist wichtig, aber **sequenziell** (eins nach dem anderen).
- Kein Scope-Drift — nicht alle Domains parallel starten.
- Fokus: Die meisten Use Cases abdecken, nicht 100 % Feature-Vollständigkeit.

**Was der Mentor NICHT will (Scope-Reduktion):**

- Nicht zu tief in Komplexität gehen.
- Design für Back-Office muss **nicht responsiv** sein.
- Backend-Infrastruktur: Supabase reicht, kein eigener API-Server nötig (vorerst).

---

## 5b) Erster Meilenstein — Buchungssystem (1 Hotel) [KONKRET]

**Definition of MVP:**

1. **Homepage (öffentlich, responsiv)**
   - Zimmer-Übersicht für 1 spezifisches Hotel
   - Buchungsformular: Datum + Zimmertyp + Kundendaten
   - Buchung anlegen → Bestätigung

2. **Back-Office (intern, Login erforderlich)**
   - Mitarbeiter-Login (einfach, Supabase Auth)
   - Buchungsübersicht für sein Hotel
   - Buchungen anpassen / bestätigen / stornieren
   - Design: **nicht responsiv** (Desktop/Tablet only)

**Erfolgskriterien für Meilenstein:**

- [ ] Homepage zeigt Zimmer für 1 Hotel
- [ ] Buchungsformular ist funktionsfähig
- [ ] Back-Office-Login funktioniert
- [ ] Mitarbeiter sieht alle Buchungen seines Hotels
- [ ] Buchungen können bearbeitet werden
- [ ] 100 % der Tests grün
- [ ] Keine ESLint-Fehler
- [ ] PR-Workflow erfolgreich durchlaufen

**Timeline für diesen Meilenstein:** 2–3 Wochen (nach Mentor-Entscheidungen Auth/Router)

---

## 5c) Spike Projects (Lernthemen, noch nicht bekannt)

Diese Themen werden parallel recherchiert und später gemeinsam besprochen:

1. **Supabase Row Level Security (RLS)** — wie Mitarbeiter nur ihre eigenen Daten sehen
2. **Client-Side Routing** — wie Links im Vanilla TS funktionieren (Basis für Navigo oder Mini-Router)
3. **Responsive Design Patterns** — Mobile-first CSS für die Homepage
4. **State Management ohne Framework** — wie State zwischen Services und Views gekoppelt wird
5. **PDF-Export** — für Rechnungen / Buchungsbestätigungen (später)

**Prozess:** Jeder recherchiert ein Spike einzeln, notiert Erkenntnisse, Team tauscht sich aus.

---

## 5d) Team-Prozesse

### Information Beschaffung

- Jeder sammelt selbstständig Material / Erkenntnisse zu seinem Bereich.
- Austausch: Wöchentliches Sync (Montag oder Freitag, 15 Min).
- Ziel: Redundanz vermeiden, Best Practices schnell teilen.

### Sprint-Reflexion

- Rhythmus: **1–2 Wochen pro Sprint** (meist Mo–Fr).
- Freitag: Kurze Retro — "Was lief gut? Was lief schlecht? Was lernen wir?"
- Gute Features (schnell gemacht, sauberer Code) und schlechte Features (technische Schulden, Frustrationen) notieren.
- Lernziel aus Frontendkurs anwenden: Was haben wir dort gelernt, was hilft hier?

### Feedback-Quellen

- **Mentor:** Hotel-Management-Hintergrund, kennt noch mehr Praktiker.
- **Externe Feedback-Geber:** Mentor vermittelt Kontakte aus der Branche.
- **Schüler:** Gegenseitiges Code-Review in PRs, Fehler früh erkennen.

---

## 5e) Nächste 5 konkreten Schritte

1. Mentor entscheidet Auth und Router final.
2. Supabase Migrationen + RLS Baseline für Bookings-Domäne.
3. BookingService mit Tests bauen (fokus: 1 Hotel).
4. Homepage-Wireframe für Zimmer + Buchungsformular.
5. Back-Office-Wireframe für Buchungsverwaltung (nicht responsiv).

## 6) Typische Fragen und kurze Antworten

Frage: Ist das Projekt schon feature-fertig?
Antwort: Noch nicht. Das Fundament ist fertig. Der erste Meilenstein ist konkret: Buchungssystem für 1 Hotel mit Homepage und Back-Office.

Frage: Wann ist dieser erste Meilenstein fertig?
Antwort: 2–3 Wochen nach Mentor-Entscheidungen zu Auth und Router.

Frage: Ist die Codequalität schon abgesichert?
Antwort: Ja, über Linting, Tests, Git-Hooks und klaren PR-Workflow. Aktuell nur zwei unkritische Lint-Warnungen im Starter-Code.

Frage: Warum kein Backend?
Antwort: Supabase ersetzt den Backend (DB + Auth + RLS). Wenn später die Komplexität steigt, können wir Edge Functions oder einen Backend hinzufügen.

Frage: Warum kein Framework wie Angular oder React?
Antwort: Bewusste Ausbildungsentscheidung. Erst Web-Grundlagen mit Vanilla TypeScript, dann Framework-Abstraktion bewusst einsetzen.

Frage: Wo liegen aktuell die größten Risiken?
Antwort: Verzögerung durch offene Auth/Router-Entscheidungen. Scope-Drift vermeiden durch strikte Fokussierung auf 1 Hotel im MVP.

Frage: Was ist das Lernziel für Schüler im nächsten Abschnitt?
Antwort: TDD-first in echtem Feature-Slice, saubere Service-Grenzen, RLS-Verständnis, responsives Design (Homepage) und disziplinierter PR-Workflow.

## 7) Gesprächsstruktur für 10 Minuten

- Minute 1-2: Zielbild und Projektkontext
- Minute 3-4: Was bereits solide steht
- Minute 5-6: Offene Entscheidungen mit Vorschlag
- Minute 7-8: Nächste Sprintschritte
- Minute 9-10: Q&A und Rollenklärung Mentor/Schüler

## 8) Roter Faden für den Abschluss im Call

- Wir haben Stabilität im Fundament.
- Der erste Meilenstein ist konkret: **Buchungssystem für 1 Hotel** (Homepage responsiv + Back-Office).
- Wir starten sequenziell — nicht alles parallel — dadurch bleibt Qualität und Lernerfolg erhalten.
- Mit Mentor-Entscheidung zu Auth und Router können wir ohne Reibungsverlust starten.
- Feedback vom Mentor und seinen Kontakten aus der Branche hilft uns, nah an der Realität zu bleiben.
