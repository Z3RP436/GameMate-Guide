# GameMate - Discord Shared Event Guide

GameMate ermöglicht die serverübergreifende Koordination von Events. Diese Anleitung richtet sich an **Sub-Server Administratoren**, **Event-Ersteller** und **Spieler**.

---

## 🛠️ Für Sub-Server Administratoren

Um deinen Server mit dem Netzwerk zu verbinden und Events vom Main-Server zu empfangen, folge diesen Schritten:

### Den Server einrichten
Nutze den Befehl `/setup`, um die Grundkonfiguration vorzunehmen oder bestehende Einstellungen zu aktualisieren. Du benötigst hierfür einen **Registrierungs-Token**, den du von einem Administrator des Main-Servers erhältst.

**Befehl:** `/setup`
**Parameter:**
*   `token` (Pflicht): Der Registrierungs-Token des Main-Servers.
*   `events-channel` (Pflicht): Der Kanal, in dem alle neuen Shared Events automatisch angekündigt werden.
*   `creator-role` (Pflicht): Die Rolle auf deinem Server, die berechtigt ist, Shared Events zu verwalten (neben Administratoren).
*   `language` (Optional): Die bevorzugte Sprache für Bot-Antworten auf diesem Server (z. B. `de` für Deutsch).

### Einzelne Einstellungen anpassen
Falls du später nur einzelne Teile der Konfiguration ändern möchtest, kannst du folgende Befehle nutzen:

*   **`/event-channel set`**: Ändert den Kanal für Event-Ankündigungen.
    *   `channel`: Der neue Zielkanal.
*   **`/role set`**: Ändert die berechtigte Rolle für Event-Ersteller.
    *   `type`: Wähle `event_creator`.
    *   `role`: Die neue Rolle.
*   **`/language server-locale`**: Ändert die Sprache des Bots für diesen Server.
    *   `locale`: Wähle die gewünschte Sprache (z. B. `Deutsch` oder `English`).

---

## 📝 Für Event-Ersteller

Nutzer mit Administrator-Rechten oder der konfigurierten `creator-role` können Shared Events verwalten.

### Shared Event Befehle
Alle Event-Aktionen werden über den Hauptbefehl `/shared-event` gesteuert:

*   **`/shared-event create`**: Erstellt ein neues Event, das auf allen verbundenen Servern veröffentlicht wird.
    *   `name`: Titel des Events.
    *   `description`: Kurze Beschreibung.
    *   `date`: Datum im Format `TT.MM.JJJJ`.
    *   `time`: Uhrzeit im Format `HH:mm`.
    *   `member_limit` (Optional): Maximale Teilnehmeranzahl.
    *   `game` (Optional): Das Spiel, das gespielt wird.
*   **`/shared-event edit`**: Bearbeitet ein bestehendes Event (nur für den Besitzer).
    *   `id`: Die ID des Events.
    *   Optionale Felder: `name`, `description`, `date`, `time`, `member_limit`, `game`.
*   **`/shared-event remove`**: Löscht ein Event (ID erforderlich).
*   **`/shared-event list`**: Zeigt eine Übersicht aller aktuell geplanten Shared Events.
*   **`/shared-event info`**: Zeigt detaillierte Informationen zu einem spezifischen Event (ID erforderlich).
*   **`/shared-event start`**: Startet das Event manuell (nur Besitzer).
*   **`/shared-event stop`**: Beendet das Event manuell (nur Besitzer).

---

## 🎮 Für Spieler

Als Spieler kannst du einfach an Events teilnehmen, egal auf welchem Server sie ursprünglich erstellt wurden.

*   **Beitreten:** Klicke auf das ✅-Emoji unter einer Event-Ankündigung oder tritt direkt über das von Discord erstellte **Scheduled Event** bei.
*   **Warteliste:** Sollte ein Event voll sein, wirst du automatisch auf die Warteliste gesetzt. Du rückst nach, sobald ein Platz frei wird.
*   **Kanäle:** Sobald du einem Event beigetreten bist, erhältst du Zugriff auf die entsprechenden Event-Kanäle (Text/Voice), sofern diese eingerichtet wurden.
*   **Erinnerungen:** Der Bot sendet dir kurz vor Start des Events eine Benachrichtigung.

---

## 🔄 Workflow: So funktioniert ein Shared Event

1.  **Erstellung:** Ein Ersteller nutzt `/shared-event create` auf einem beliebigen Server (meist Main-Server).
2.  **Verteilung:** Der Bot sendet die Ankündigung sofort in die `events-channel` aller registrierten Sub-Server.
3.  **Anmeldung:** Spieler auf allen Servern können via Reaktion (✅) oder über das integrierte Discord Event teilnehmen. Die Teilnehmerliste wird global synchronisiert.
4.  **Vorbereitung:** Kurz vor dem Termin erhalten alle Teilnehmer eine Erinnerung.
5.  **Durchführung:** Zum Startzeitpunkt wird das Event aktiv. Teilnehmer nutzen die bereitgestellten Kanäle.
6.  **Abschluss:** Das Event wird beendet, Kanäle werden für die Teilnehmer wieder ausgeblendet.

---

## 🏆 Ranking & Warteliste

GameMate nutzt ein Ranking-System, um die Zuverlässigkeit und das Engagement der Spieler zu fördern.

### Ranking-Einfluss
Das Ranking hat einen direkten Einfluss auf die **Warteliste**:
*   Spieler mit einem höheren Ranking werden auf der Warteliste priorisiert.

### Ranking Befehle
Mit dem Befehl `/ranking` kannst du verschiedene Informationen abrufen:
*   **`/ranking own`**: Zeigt dein eigenes aktuelles Ranking an.
*   **`/ranking member`**: Zeigt das Ranking eines anderen Mitglieds (User-Auswahl erforderlich).
*   **`/ranking shared-event`**: Zeigt eine Übersicht der Rankings aller Teilnehmer eines spezifischen Events (Event-ID erforderlich).

---

## 🔒 Berechtigungsmatrix
| Befehl                    | Admin | Event-Ersteller Rolle | Event-Besitzer | Spieler | Parameter                                                                                                                                         |
|---------------------------|:-----:|:---------------------:|:--------------:|:-------:|---------------------------------------------------------------------------------------------------------------------------------------------------|
| `/setup`                  |   ✅   |           ❌           |       ❌        |    ❌    | `token`, `events-channel`, `creator-role`, `language` *(optional)*                                                                                |
| `/event-channel set`      |   ✅   |           ❌           |       ❌        |    ❌    | `channel`                                                                                                                                         |
| `/role set`               |   ✅   |           ❌           |       ❌        |    ❌    | `type`, `role`                                                                                                                                    |
| `/language server-locale` |   ✅   |           ❌           |       ❌        |    ❌    | `locale`                                                                                                                                          |
| `/language user-locale`   |   ✅   |           ✅           |       ✅        |    ✅    | `locale`                                                                                                                                          |
| `/shared-event create`    |   ✅   |           ✅           |       ❌        |    ❌    | `name`, `description`, `date`, `time`, `member_limit` *(optional)*, `game` *(optional)*                                                           |
| `/shared-event edit`      |   ❌   |           ❌           |       ✅        |    ❌    | `id`, `name` *(optional)*, `description` *(optional)*, `date` *(optional)*, `time` *(optional)*, `member_limit` *(optional)*, `game` *(optional)* |
| `/shared-event remove`    |   ❌   |           ❌           |       ✅        |    ❌    | `id`                                                                                                                                              |
| `/shared-event list`      |   ✅   |           ✅           |       ✅        |    ✅    | `-`                                                                                                                                               |
| `/shared-event info`      |   ✅   |           ✅           |       ✅        |    ✅    | `id`                                                                                                                                              |
| `/shared-event start`     |   ❌   |           ❌           |       ✅        |    ❌    | `id`                                                                                                                                              |
| `/shared-event stop`      |   ❌   |           ❌           |       ✅        |    ❌    | `id`                                                                                                                                              |
| `/ranking own`            |   ✅   |           ✅           |       ✅        |    ✅    | `–`                                                                                                                                               |
| `/ranking member`         |   ❌   |           ❌           |       ❌        |    ❌    | `member`                                                                                                                                          |
| `/ranking shared-event`   |   ❌   |           ❌           |       ✅        |    ❌    | `id`                                                                                                                                              |

---

## 📖 Glossar

* **`Shared-Event`**: Ein Event, welches Nutzer serverübergreifend veranstalten.
* **`Main-Server`**: Der Haupt-Server [GameMateHUB](https://discord.gg/QKx2Y2kH5N). In den Sprach- und Textkanälen dieses Servers finden die Events statt. Hier erfährst du außerdem alle Neuigkeiten und kannst dich mit anderen Mitgliedern vernetzen!
* **`Sub-Server`**: Jeder Server der den GameMate Bot installiert ist ein Sub-Server. Er kann Events erstellen und seine Nutzer über geteilte Events von anderen Communitys informieren.
* **`Administrator`**: Mit Administratoren sind immer die Administratoren der jeweiligen Sub-Server gemeint.

🚀 Viel Erfolg bei deinem nächsten Event!
