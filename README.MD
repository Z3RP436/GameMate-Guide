# GameMate - Discord Shared Event Guide

GameMate ermöglicht die serverübergreifende Koordination von Events. Diese Anleitung richtet sich an **Sub-Server Administratoren**, **Event-Ersteller** und **Spieler**.

---

## 🛠️ Für Sub-Server Administratoren

Um deinen Server mit dem Netzwerk zu verbinden und Events vom Main-Server zu empfangen, folge diesen Schritten:

### Den Server einrichten
Nutze den Befehl `/setup`, um die Grundkonfiguration vorzunehmen. Du benötigst hierfür einen **Registrierungs-Token**, den du von einem Administrator des Main-Servers erhältst.

**Befehl:** `/setup`
**Parameter:**
*   `token` (Pflicht): Der Registrierungs-Token des Main-Servers.
*   `events-channel` (Pflicht): Der Kanal, in dem alle neuen Shared Events automatisch angekündigt werden.
*   `creator-role` (Pflicht): Die Rolle auf deinem Server, die berechtigt ist, Shared Events zu verwalten (neben Administratoren).
*   `language` (Optional): Die bevorzugte Sprache für Bot-Antworten auf diesem Server (z. B. `de` für Deutsch).

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

*   **Beitreten:** Klicke auf das ✅-Emoji unter einer Event-Ankündigung.
*   **Warteliste:** Sollte ein Event voll sein, wirst du automatisch auf die Warteliste gesetzt. Du rückst nach, sobald ein Platz frei wird.
*   **Kanäle:** Sobald du einem Event beigetreten bist, erhältst du Zugriff auf die entsprechenden Event-Kanäle (Text/Voice), sofern diese eingerichtet wurden.
*   **Erinnerungen:** Der Bot sendet dir kurz vor Start des Events eine Benachrichtigung.

---

## 🔄 Workflow: So funktioniert ein Shared Event

1.  **Erstellung:** Ein Ersteller nutzt `/shared-event create` auf einem beliebigen Server (meist Main-Server).
2.  **Verteilung:** Der Bot sendet die Ankündigung sofort in die `events-channel` aller registrierten Sub-Server.
3.  **Anmeldung:** Spieler auf allen Servern können via Reaktion (✅) teilnehmen. Die Teilnehmerliste wird global synchronisiert.
4.  **Vorbereitung:** Kurz vor dem Termin erhalten alle Teilnehmer eine Erinnerung.
5.  **Durchführung:** Zum Startzeitpunkt wird das Event aktiv. Teilnehmer nutzen die bereitgestellten Kanäle.
6.  **Abschluss:** Das Event wird beendet, Kanäle werden für die Teilnehmer wieder ausgeblendet.

🚀 Viel Erfolg bei deinem nächsten Event!
