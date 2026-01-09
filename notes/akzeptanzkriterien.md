## Issue-Übersicht nach Entwicklungsphasen

### Phase P1: Visualization (MVP-Kernfeatures)

| Issue-ID | Page | Summary | Estimation (min) |
|----------|------|---------|------------------|
| ARC-24 | Quest Tracker | Kanban Board für Quest-Visualisierung | 960 |
| ARC-25 | Quest Tracker | Flow-/Metro Chart für Quest-Abhängigkeiten | 3360 |
| ARC-26 | Quest Tracker | Detaillierte Quest-Seiten | 1440 |
| ARC-29 | Item Database | Anzeige aller verfügbaren Items | 2400 |
| ARC-31 | Creature Database | Anzeige aller Kreaturen | - |
| ARC-32 | Workstation Planner | Einfache Workstation-Upgrades | 2880 |
| ARC-34 | Material Calculator | Berechnung benötigter Materialien | 2400 |
| ARC-37 | Interactive Maps | Basis-Implementierung interaktiver Karten | 1440 |

**Gesamt P1:** 14.880 Minuten ≈ 248 Stunden

### Phase P2: Progression (Nutzer-Fortschritt)

| Issue-ID | Page | Summary | Estimation (min) |
|----------|------|---------|------------------|
| ARC-20 | Dashboard | Fortschritt und Statistiken anzeigen | 960 |
| ARC-21 | Dashboard | Quick Access Cards für aktive Quests | 960 |
| ARC-22 | Dashboard | Quick Access Cards für Workstation-Upgrades | 960 |
| ARC-23 | Dashboard | Quick Access Cards für Wishlist | 960 |
| ARC-27 | Quest Tracker | Basis-Progression von Quests | 2400 |
| ARC-28 | Quest Tracker | Erweiterte Progression (Auth) | - |
| ARC-30 | Item Database | Erweiterte Filter- und Suchfunktionen | 1920 |
| ARC-33 | Workstation Planner | Erweiterte Workstation-Upgrades | 2400 |
| ARC-35 | Material Calculator | Wishlist für benötigte Items | 960 |

**Gesamt P2:** 11.520 Minuten ≈ 192 Stunden

### Phase P3: User Generated Content

| Issue-ID | Page | Summary |
|----------|------|---------|
| ARC-38 | Interactive Maps | Kooperative Karten (Squad-Feature) |
| ARC-41 | Community Guides | Basis-Post-System (Reddit-ähnlich) |
| ARC-42 | Community Guides | Erweitertes Post-System mit Moderation |

### Phase P4: Fancy Extensions

| Issue-ID | Page | Summary |
|----------|------|---------|
| ARC-36 | Material Calculator | Screenshot-Import via OCR |
| ARC-39 | Interactive Maps | Pathfinding-Algorithmen |
| ARC-40 | Long Term | Subscription-Modell |
| ARC-43 | Interactive Maps | Echtzeit-Routenplanung |

---

## User Stories nach Feature-Bereichen

### Format
```
Als [Rolle] möchte ich [Funktion], um [Nutzen] zu erreichen.
```

Die User Stories folgen den INVEST-Kriterien:
- **I**ndependent: Unabhängig voneinander umsetzbar
- **N**egotiable: Verhandelbar im Scope
- **V**aluable: Wert für den Nutzer
- **E**stimable: Schätzbar im Aufwand
- **S**mall: Klein genug für eine Iteration
- **T**estable: Durch Akzeptanzkriterien validierbar

---

### Feature-Bereich: Quest-Management-System

#### US-QM-01: Quest-Übersicht als Kanban-Board
**Quelle:** ARC-24 | **Phase:** P1-Visualization | **Priorität:** Must-Have

> Als Spieler möchte ich alle Quests in einem Kanban-Board mit den Spalten All, Active, Locked und Completed sehen, um meinen aktuellen Fortschritt auf einen Blick zu erfassen.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-QM-01.1 | Alle Quests werden in genau vier Spalten kategorisiert angezeigt | Spaltenanzahl = 4 | Bei Seitenladung |
| AC-QM-01.2 | Die Filterung nach Quest-Name liefert Ergebnisse in Echtzeit | Latenz < 100ms | Bei Tastatureingabe |
| AC-QM-01.3 | Die Quest-Anzahl pro Spalte wird numerisch angezeigt | Counter sichtbar | Permanent |

---

#### US-QM-02: Quest-Abhängigkeiten als Flow-Chart
**Quelle:** ARC-25 | **Phase:** P1-Visualization | **Priorität:** Must-Have

> Als Spieler möchte ich die Abhängigkeiten zwischen Quests als interaktives Flussdiagramm visualisieren, um Quest-Ketten und Voraussetzungen zu verstehen.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-QM-02.1 | Quest-Abhängigkeiten werden als gerichteter Graph mit Kanten dargestellt | Kantendarstellung korrekt | Bei Rendering |
| AC-QM-02.2 | Das Layout wird automatisch durch den Dagre-Algorithmus berechnet | Keine Überlappungen | Initial |
| AC-QM-02.3 | Zoom und Pan sind via Maus/Touch möglich | Zoom-Range 0.5x–2x | Bei Interaktion |
| AC-QM-02.4 | Klick auf einen Quest-Node öffnet die Detail-Ansicht | Navigation funktional | < 300ms |
| AC-QM-02.5 | Farbcodierung zeigt Quest-Status | 3 distinkte Farben | Permanent |

---

#### US-QM-03: Detaillierte Quest-Informationen
**Quelle:** ARC-26 | **Phase:** P1-Visualization | **Priorität:** Must-Have

> Als Spieler möchte ich auf einer Detail-Seite alle Informationen zu einer Quest einsehen, um die Anforderungen und Belohnungen vollständig zu verstehen.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-QM-03.1 | Die Detail-Seite zeigt Quest-Name, Beschreibung, Ziele und Belohnungen | Alle 4 Felder vorhanden | Bei Seitenladung |
| AC-QM-03.2 | Voraussetzungs-Quests sind als klickbare Links dargestellt | Links navigieren korrekt | Bei Klick |
| AC-QM-03.3 | Nachfolgende Quests sind als klickbare Links dargestellt | Links navigieren korrekt | Bei Klick |
| AC-QM-03.4 | Die Seite ist über dynamische Route `/quests/[slug]` erreichbar | URL-Routing funktional | Direkt |
| AC-QM-03.5 | Benötigte Items zeigen Menge und sind mit Item-Datenbank verlinkt | Verlinkung funktional | Bei Klick |

---

#### US-QM-04: Quest-Fortschritt speichern
**Quelle:** ARC-27 | **Phase:** P2-Progression | **Priorität:** Must-Have

> Als Spieler möchte ich meinen Quest-Fortschritt markieren und persistent speichern, um meinen Spielfortschritt über Sessions hinweg zu verfolgen.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-QM-04.1 | Ein Klick markiert die Quest als abgeschlossen | Status-Toggle funktional | < 100ms |
| AC-QM-04.2 | Alle vorherigen Quests einer Quest-Kette werden automatisch als complete markiert | Kaskadierung korrekt | < 500ms |
| AC-QM-04.3 | Der Fortschritt wird im localStorage persistiert | Daten nach Reload vorhanden | Sofort |
| AC-QM-04.4 | Der Fortschritt kann zurückgesetzt werden (einzeln oder komplett) | Reset-Funktion verfügbar | Bei Bestätigung |

---

### Feature-Bereich: Item-Datenbank

#### US-ID-01: Item-Katalog anzeigen
**Quelle:** ARC-29 | **Phase:** P1-Visualization | **Priorität:** Must-Have

> Als Spieler möchte ich alle im Spiel verfügbaren Items in einer übersichtlichen Card-Grid-Ansicht sehen, um schnell das gesuchte Item zu finden.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-ID-01.1 | Alle Items werden als Cards in einem responsiven Grid dargestellt | Grid-Layout auf allen Viewports | Bei Seitenladung |
| AC-ID-01.2 | Jede Card zeigt Icon, Name, Typ und Seltenheit | Vollständige Informationen pro Card | Permanent |
| AC-ID-01.3 | Filterung nach Typ/Kategorie ist möglich | Filter liefert korrekte Subset | < 200ms |
| AC-ID-01.4 | Filterung nach Seltenheit ist möglich | Filter liefert korrekte Subset | < 200ms |
| AC-ID-01.5 | Sortierung nach Name, Gewicht, Wert ist möglich | Sortierreihenfolge korrekt | < 200ms |
| AC-ID-01.6 | Textsuche nach Item-Name liefert Ergebnisse in Echtzeit | Ergebnisse bei Eingabe | < 300ms |


---

### Feature-Bereich: Workstation-Planner

#### US-WP-01: Workstation-Übersicht
**Quelle:** ARC-32 | **Phase:** P1-Visualization | **Priorität:** Must-Have

> Als Spieler möchte ich alle Workstations mit ihren Upgrade-Leveln und Anforderungen sehen, um meine Hideout-Entwicklung zu planen.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-WP-01.1 | Alle Workstations werden mit aktuellem (X) und maximalem Level (Y) angezeigt | Level-Anzeige X/Y | Bei Seitenladung |
| AC-WP-01.2 | Upgrade-Requirements (Items + Mengen) sind pro Level einsehbar | Anzeige expandierbar | Bei Klick < 200ms |
| AC-WP-01.3 | Workstation-Icons werden korrekt zugeordnet angezeigt | Icon-Mapping vollständig | Permanent |

---

#### US-WP-02: Workstation-Fortschritt speichern
**Quelle:** ARC-33 | **Phase:** P2-Progression | **Priorität:** Should-Have

> Als Spieler möchte ich meinen Workstation-Level speichern, um meinen Hideout-Fortschritt zu tracken und für den Material-Calculator zu nutzen.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-WP-02.1 | Klick erhöht das gespeicherte Level um 1 | Level-Inkrement korrekt | < 100ms |
| AC-WP-02.2 | Der Fortschritt wird im Game-Store (Zustand) persistiert | State nach Reload vorhanden | Sofort |
| AC-WP-02.3 | Option des Material-Calculator bezieht nur nicht-abgeschlossene Upgrades ein | Filter funktional | Bei Berechnung |

---

### Feature-Bereich: Material-Calculator

#### US-MC-01: Material-Aggregation
**Quelle:** ARC-34 | **Phase:** P1-Visualization | **Priorität:** Must-Have

> Als Spieler möchte ich basierend auf ausgewählten Quests und Workstation-Upgrades die Gesamtmenge benötigter Materialien berechnen, um mein Inventar optimal zu nutzen.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-MC-01.1 | Quests sind per Multi-Select auswählbar | Mehrfachauswahl funktional | Bei Interaktion |
| AC-MC-01.2 | Workstation-Upgrades sind per Multi-Select auswählbar | Mehrfachauswahl funktional | Bei Interaktion |
| AC-MC-01.3 | Eine " Select All"-Option ist verfügbar | Bulk-Selection funktional | Bei Klick |
| AC-MC-01.4 | Die aggregierten Materialien werden mit Gesamtmenge angezeigt | Summierung korrekt | < 500ms |
| AC-MC-01.5 | Materialien sind nach Typ gruppiert darstellbar | Gruppierung toggle-bar | Bei Klick |

---

#### US-MC-02: Wishlist-Integration
**Quelle:** ARC-35 | **Phase:** P2-Progression | **Priorität:** Should-Have

> Als Spieler möchte ich die berechneten Materialien in eine Wishlist speichern

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-MC-02.1 | Ein "Save"-Button speichert die aktuelle Berechnung | Persistierung erfolgreich | Bei Klick |
| AC-MC-02.2 | Ein "Load"-Button lädt eine gespeicherte Wishlist | Anwenden der Wishlist | Bei Klick|
| AC-MC-02.3 | Export als Text/Bild ist möglich | Export-Format korrekt | Bei Klick |

---

### Feature-Bereich: Recycling-Kalkulator (Nachträglich identifiziert)

> **Hinweis zur Anforderungsquelle:** Dieses Feature wurde nicht im initialen Backlog erfasst, sondern während eines Stakeholder-Interviews in Phase P2 als hochpriorisierter Bedarf identifiziert. Ein erfahrener Spieler beschrieb das Problem der ineffizienten Ressourcennutzung durch fehlendes Verständnis der Recycling-Ketten. Aufgrund des hohen Nutzenwerts wurde das Feature über die geplanten Interaktiven Karten (ARC-37) priorisiert. Dies demonstriert die Adaptivität des agilen Anforderungsmanagements gemäß Abschnitt 2.2.1.

#### US-RC-01: Recycling-Datenbank
**Quelle:** Stakeholder-Interview | **Phase:** P1-Visualization (repriorisiert) | **Priorität:** Must-Have

> Als Spieler möchte ich alle recycelbaren Items mit ihren Output-Materialien und Effizienzwerten sehen, um fundierte Recycling-Entscheidungen zu treffen.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-RC-01.1 | Alle recycelbaren Items werden tabellarisch mit Input und Output angezeigt | Vollständigkeit der Daten | Bei Seitenladung |
| AC-RC-01.2 | Die Recycling-Effizienz (Werterhalt) wird pro Item berechnet und angezeigt | Prozentwert vorhanden | Bei Rendering |
| AC-RC-01.3 | Sortierung nach Effizienz, Name ist möglich | Sortierung funktional | < 200ms |

---

#### US-RC-02: Reverse-Engineering von Materialien
**Quelle:** Stakeholder-Interview | **Phase:** P1-Visualization (repriorisiert) | **Priorität:** Must-Have

> Als Spieler möchte ich für ein Zielmaterial alle möglichen Recycling-Pfade sehen, um zu verstehen, welche Items ich recyceln kann, um das Material zu erhalten.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-RC-02.1 | Nach Auswahl eines Zielmaterials werden alle Quell-Items angezeigt | Liste vollständig | < 1s |
| AC-RC-02.2 | Rekursive Pfade (Item A → Item B → Zielmaterial) werden aufgelöst | Tiefe ≥ 3 Ebenen | < 2s |
| AC-RC-02.3 | Die Pfade sind nach Effizienz sortierbar | Sortierung funktional | < 200ms |

---

#### US-RC-03: Recycling-Ketten-Visualisierung
**Quelle:** Stakeholder-Interview | **Phase:** P1-Visualization (repriorisiert) | **Priorität:** Should-Have

> Als Spieler möchte ich komplette Recycling-Ketten als Baum oder Graph visualisieren, um die Transformationspfade visuell nachzuvollziehen.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-RC-03.1 | Recycling-Ketten werden als interaktiver Baum mit React Flow dargestellt | Graph-Rendering funktional | < 2s |
| AC-RC-03.2 | Nodes sind farbcodiert nach Item-Seltenheit | Farbzuordnung korrekt | Permanent |
| AC-RC-03.3 | Kanten zeigen die Output-Menge an | Label vorhanden | Permanent |
| AC-RC-03.4 | Terminal-Materialien (nicht weiter zerlegbar) sind visuell markiert | Distinkte Darstellung | Permanent |

---

### Feature-Bereich: Dashboard

#### US-DB-01: Fortschritts-Übersicht
**Quelle:** ARC-20 | **Phase:** P2-Progression | **Priorität:** Should-Have

> Als Spieler möchte ich auf dem Dashboard meinen Gesamtfortschritt in Zahlen und Prozenten sehen, um meine Spielerfolge zu quantifizieren.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-DB-01.1 | Die absolute Quest-Completion wird als X/Y angezeigt | Zahlen korrekt | Bei Seitenladung |
| AC-DB-01.2 | Die prozentuale Quest-Completion wird angezeigt | Prozentwert korrekt | Bei Seitenladung |
| AC-DB-01.3 | Die Daten werden korrekt aus dem Game-Store bezogen | Store-Integration | Real-time |

---

#### US-DB-02: Quick-Access-Cards
**Quelle:** ARC-21, ARC-22, ARC-23 | **Phase:** P2-Progression | **Priorität:** Should-Have

> Als Spieler möchte ich auf dem Dashboard schnellen Zugriff auf aktive Quests, aktuelle Workstation-Upgrades und meine Wishlist haben, um die wichtigsten Informationen sofort zu sehen.

**SMART-Akzeptanzkriterien:**

| ID | Kriterium | Messbar | Zeitgebunden |
|----|-----------|---------|--------------|
| AC-DB-02.1 | Bis zu 6 aktive Quests werden als Cards angezeigt | Maximal 6 Cards | Bei Seitenladung |
| AC-DB-02.2 | Klick auf eine Quest-Card navigiert zur Detail-Seite | Navigation funktional | Bei Klick |
| AC-DB-02.3 | Aktuelle Workstation-Upgrades zeigen nächstes Level + Requirements | Daten korrekt | Bei Seitenladung |
| AC-DB-02.4 | Wishlist-Items werden mit fehlender Menge angezeigt | Owned vs. Required | Bei Seitenladung |

---
