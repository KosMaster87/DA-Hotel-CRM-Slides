---
theme: default
title: DA Hotel CRM — Projektvorstellung
titleTemplate: '%s'
info: |
  DA Hotel CRM — Präsentation für Developer-Akademie Schüler & Mentor
highlighter: shiki
transition: slide-left
mdc: true
---

# 🏨 DA Hotel CRM

**Ein echtes Projekt. Echte Tools. Echte Teamarbeit.**

Projektvorstellung im Rahmen der Developer-Akademie Weiterbildung

<div class="pt-12">
  <span class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Let's go 🚀
  </span>
</div>

---

# 🗺️ Was wir heute bauen

Eine vollständige **Hotel-CRM Web-App** — von der Datenbank bis zum Browser.

- 🏨 **Hotels** verwalten — Stammdaten, Zimmer, Kategorien
- 👤 **Kunden** anlegen und pflegen
- 📅 **Buchungen** — von Pending bis Checked-Out
- 🚚 **Lieferanten** und Verträge verwalten
- 🧾 **Rechnungen** aus Buchungen generieren
- 📊 **Dashboard** mit KPIs und offenen Aufgaben
- 🔐 **Rollen** — Admin, Manager, Viewer

> Kein Toy-Projekt. Ein echtes System, das ein Hotel wirklich nutzen könnte.

---

# 🤔 Warum kein React oder Angular?

Das ist die wichtigste Entscheidung im Projekt.

- **Frameworks verstecken** wie das Web wirklich funktioniert
- Wir wollen zuerst verstehen: DOM, Events, State, Routing — von Hand
- Dann macht ein Framework **plötzlich Sinn** — statt Magie

```typescript
// Das schreiben wir selbst — kein Magic Binding
document.getElementById('hotel-list')!.innerHTML = hotels
  .map(h => `<li>${h.name}</li>`)
  .join('');
```

> React-Entwickler die Vanilla JS können sind **deutlich bessere** React-Entwickler.

---

# 🛠️ Unser Tech-Stack

Bewusste Entscheidungen — mit Begründung.

| Was | Womit | Warum |
|---|---|---|
| Frontend | **Vanilla TypeScript + Vite** | Kein Framework-Overhead, wir verstehen alles |
| Datenbank | **Supabase** (PostgreSQL) | Echte DB + Auth + Security in einem |
| Tests | **Vitest** | Schnell, Modern, TypeScript-nativ |
| Qualität | **ESLint + Prettier + Husky** | Wie in echten Teams |
| Struktur | **Monorepo** | frontend / shared / supabase |

> Jede Technologie haben wir bewusst gewählt — nicht zufällig installiert.

---

# 🔐 Security by Design — Supabase RLS

Jede Tabelle hat von Anfang an Zugriffsregeln.

```sql
-- Jeder authentifizierte User darf lesen
CREATE POLICY "hotels_select"
  ON hotels FOR SELECT TO authenticated
  USING (true);

-- Nur Manager und Admin dürfen schreiben
CREATE POLICY "hotels_insert"
  ON hotels FOR INSERT TO authenticated
  WITH CHECK (
    (auth.jwt() ->> 'role')::text IN ('admin', 'manager')
  );
```

- Viewer sieht alles — kann nichts ändern
- Manager verwaltet Hotels, Buchungen, Kunden
- Admin hat vollen Zugriff + kann löschen

> Security nicht nachträglich — sondern von Tag 1.

---

# 🧪 TDD-First — Tests vor dem Code

Wir schreiben Tests **bevor** der Code existiert.

```
Red  🔴 → Test schreiben (schlägt fehl, Code existiert nicht)
Green 🟢 → minimalen Code schreiben (Test wird grün)
Refactor 🔵 → Code aufräumen (Tests bleiben grün)
```

```typescript
// Erst der Test:
it('should throw when hotel not found', async () => {
  mockSupabase.single.mockResolvedValue({ data: null, error: { message: 'Not found' } });
  await expect(hotelService.getById('999')).rejects.toThrow('Not found');
});

// Dann die Implementierung.
```

> TDD zwingt uns, vorher zu **denken** bevor wir tippen.

---

# 🤖 AI-Unterstützung mit Copilot

Wir nutzen GitHub Copilot **strukturiert** — nicht blind.

Projekt-spezifische Prompts in `.github/prompts/`:

| Prompt | Wann nutzen |
|---|---|
| `new-feature-slice` | Neues Feature end-to-end anlegen |
| `add-migration` | Supabase Tabelle + RLS |
| `code-review` | Code gegen unsere Standards prüfen |
| `debug` | Bug systematisch analysieren |
| `deploy-check` | Vor jedem PR-Merge |

> Copilot als Junior im Team — wir geben Anweisungen, wir reviewen den Output.

---

# 📅 8-Wochen-Plan

Von Null zur fertigen App.

| Woche | Fokus |
|---|---|
| **0** | Setup: Supabase, Vite, ESLint, Git, erster Commit |
| **1** | Auth: Login, Rollen, geschützte Routen |
| **2** | Hotels: CRUD, Service, View, Tests |
| **3** | Kunden: CRUD + Validierung |
| **4** | Buchungen: Statusmaschine, Business Rules |
| **5** | Lieferanten + Verträge |
| **6** | Rechnungen aus Buchungen |
| **7** | Dashboard + KPIs + Polish |
| **8** | Präsentation 🎉 |

---

# 🐙 GitHub — So arbeiten wir

Professioneller Git-Workflow von Tag 1.

```bash
# Feature-Branch erstellen
git checkout -b feature/hotel-list

# Commit mit Conventional Commits
git commit -m "feat(hotels): add hotel list view with pagination"

# Pull Request öffnen → Review → Merge
gh pr create --title "feat(hotels): ..."
```

**Und nebenbei:** GitHub Achievements sammeln 🏆
- **Pair Extraordinaire** — Co-Authored Commits
- **Pull Shark** — PRs mergen
- **Galaxy Brain** — Discussions beantworten

> Unser Repo: [github.com/KosMaster87/da-hotel-crm](https://github.com/KosMaster87/da-hotel-crm)

---

# ❓ Offene Fragen an den Mentor

Zwei Entscheidungen brauchen deinen Input, bevor wir starten:

### Auth-Strategie
- **Option A:** Supabase Auth komplett (einfacher, integriert)
- **Option B:** Eigenes JWT + Supabase als DB (mehr Kontrolle, mehr Aufwand)

### Client-Side Router
- **Option A:** Eigener Mini-Router (lernen wie es funktioniert)
- **Option B:** `navigo`-Bibliothek (produktionsnäher, weniger Boilerplate)

---
layout: center
---

# 🚀 Let's build something real.

**Repo:** [github.com/KosMaster87/da-hotel-crm](https://github.com/KosMaster87/da-hotel-crm)

Fragen? Ideen? Verbesserungsvorschläge?

_Wir freuen uns auf euer Feedback_ 🙌
