# GameMate - Dein Discord Shared Event Bot

GameMate ist ein Discord-Bot, der speziell dafür entwickelt wurde, Events über mehrere Server hinweg zu koordinieren. Mit einer Architektur aus einem **Main-Server** (Zentrale) und mehreren **Sub-Servern** (Partner-Servern) ermöglicht er eine nahtlose Organisation von Gaming-Sessions und Community-Events.

## 🚀 Den Bot hinzufügen & Einrichten

Um GameMate zu nutzen, muss der Bot auf den beteiligten Servern vorhanden sein.

### 1. Main-Server festlegen (Zentraler Server)
Der Main-Server ist der Ort, an dem Events erstellt und verwaltet werden.
*   Füge den Bot deinem Server hinzu.
*   Nutze den Befehl `/main-guild set`, um diesen Server als Hauptserver zu registrieren.
*   Nur Administratoren können diesen Befehl ausführen.

### 2. Sub-Server verbinden (Partner-Server)
Sub-Server sind Server, auf denen die Events des Main-Servers veröffentlicht werden.
*   **Token generieren:** Auf dem **Main-Server** muss ein Admin mit `/token-generation` einen Einladungstoken erstellen.
    *   `usage-count`: Wie viele Server diesen Token nutzen können.
    *   `expiration-date`: Wie lange der Token gültig ist.
*   **Setup auf dem Sub-Server:** Auf dem Partner-Server nutzt ein Admin den Befehl `/setup`:
    *   `token`: Der auf dem Main-Server generierte Token.
    *   `creator-role`: Eine Rolle auf dem Sub-Server, deren Mitglieder ebenfalls Events erstellen dürfen (optional, falls Berechtigung gewünscht).
    *   `events-channel`: Der Kanal, in dem die Event-Ankündigungen erscheinen sollen.
    *   `language`: Die Sprache für diesen Server (z.B. `de`).

---

## 🎮 Was man als Spieler machen kann

Als Mitglied auf einem der verbundenen Server stehen dir folgende Funktionen zur Verfügung:

*   **Events beitreten:** Klicke einfach auf das ✅ unter einer Event-Ankündigung.
*   **Automatische Kanäle:** Sobald du einem Event beitrittst, erhältst du Zugriff auf die entsprechenden Event-Kanäle (Text & Voice), sofern diese für das Event konfiguriert wurden.
*   **Warteliste:** Wenn ein Event voll ist, wirst du automatisch auf die Warteliste gesetzt und rückst nach, falls jemand absagt.
*   **Benachrichtigungen:** Du erhältst automatische Erinnerungen kurz vor Start des Events.
*   **Feedback:** Nach dem Event kannst du Feedback geben (sofern aktiviert), um dein Erlebnis zu bewerten.

---

## 🛠️ Was man als Admin machen kann

Admins (oder Nutzer mit der konfigurierten Creator-Rolle) haben volle Kontrolle über die Events:

*   **Event-Management:** Über `/shared-event` können Events erstellt, bearbeitet, gelöscht oder aufgelistet werden.
*   **Server-Verknüpfung:** Verwaltung der Token-Generierung und der Server-Hierarchie.
*   **Status-Kontrolle:** Events manuell starten (`/shared-event start`) oder stoppen (`/shared-event stop`).
*   **Übersicht:** Mit `/shared-event list` behältst du den Überblick über alle geplanten Aktivitäten.

---

## 🔄 Workflow: Ein neues Shared Event erstellen

Hier ist der Schritt-für-Schritt Prozess, wie ein Event über alle Server verteilt wird:

1.  **Erstellung:** Ein Admin auf dem **Main-Server** nutzt den Befehl `/shared-event create`.
    *   Gib Name, Beschreibung, Datum (`TT.MM.JJJJ`), Uhrzeit (`HH:mm`) und optional ein Mitgliedslimit oder das Spiel an.
2.  **Veröffentlichung:** Sobald das Event erstellt wurde, sendet der Bot automatisch eine Ankündigung in die konfigurierten `events-channel` aller verbundenen **Sub-Server**.
3.  **Synchronisierung:** Alle Informationen (Teilnehmerliste, Details) werden in Echtzeit über alle Server hinweg synchron gehalten. Wenn jemand auf Server A beitritt, wird die Teilnehmerzahl auch auf Server B aktualisiert.
4.  **Erinnerung:** Kurz vor dem Startzeitpunkt sendet der Bot Erinnerungen an alle angemeldeten Teilnehmer.
5.  **Start:** Zum geplanten Zeitpunkt (oder manuell via `/shared-event start`) wird das Event als "Aktiv" markiert. Die Teilnehmer werden informiert und können direkt in die Kanäle springen.
6.  **Abschluss:** Nach Ende des Events wird es archiviert und die temporären Berechtigungen für Kanäle werden wieder entfernt.

---

Viel Spaß beim Organisieren deiner nächsten Gaming-Session mit **GameMate**! 🚀
