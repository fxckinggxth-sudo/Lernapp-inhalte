# Lernapp-Inhalte

Diese Dateien werden von der App beim Start aus dem Internet geladen.
Wenn du hier etwas änderst, hat die App den neuen Stand beim nächsten Öffnen. Neu installieren musst du nicht.

## Einrichten (einmalig)
1. Auf GitHub ein neues Repository anlegen, z. B. `lernapp-inhalte`. Es muss **Public** sein, damit die App es ohne Login lesen kann.
2. Die Dateien dieses Ordners hochladen (Add file → Upload files). Die Ordnerstruktur muss bleiben: `themen.json` im Hauptordner, die Themen im Ordner `themen/`.
3. In der App-Datei `Content.kt` oben die Adresse eintragen:
   `https://raw.githubusercontent.com/DEIN-NAME/DEIN-REPO/main/`
   (`DEIN-NAME` = dein GitHub-Benutzername, `DEIN-REPO` = Name des Repositorys, `main` = Name des Branches)
4. Zum Test im Browser `…/main/themen.json` aufrufen. Wenn dort der Text erscheint, passt die Adresse.

## Neues Thema hinzufügen
1. `themen/vorlage.json` kopieren und umbenennen, z. B. `themen/pharmakologie.json`. Karten eintragen.
2. In `themen.json` einen Eintrag ergänzen:
   `{ "id": "pharmakologie", "titel": "Pharmakologie", "beschreibung": "…", "datei": "themen/pharmakologie.json" }`
   Einträge werden durch Kommas getrennt.
3. Speichern (Commit). Nach spätestens ein paar Minuten ist es in der App (GitHub hält Dateien kurz zwischen).
4. In der App oben auf „Themen aktualisieren“ tippen.

## Aufbau einer Karte
| Feld | Pflicht | Bedeutung |
|---|---|---|
| `frage` | ja | Frage oder Begriff |
| `antwort` | ja | Richtige Antwort (kurz halten, sie wird bei Multiple Choice als Option angezeigt) |
| `kategorie` | nein | Unterbereich im Thema, z. B. Kapitel. Erscheint als Auswahl vor der Runde |
| `gruppe` | nein | Falsche Antworten bei Multiple Choice kommen aus derselben Gruppe. Gleichartige Karten in dieselbe Gruppe legen |
| `hinweis` | nein | Kleiner Zusatz unter der Frage |
| `erklaerung` | nein | Text, der nach der Antwort angezeigt wird |
| `prompt` | nein | Kurze Aufgabenstellung über der Frage, z. B. „Was heißt das auf Deutsch?“ |
| `umkehrbar` | nein | `true` = die Karte wird auch umgekehrt gefragt (Antwort → Frage) |
| `prompt_rueck` | nein | Aufgabenstellung für die umgekehrte Frage |
| `tippen` | nein | `false` = nur Multiple Choice, nicht zum Eintippen (für lange Antworten) |

Tipp: Pro Gruppe sollten mindestens 4 Karten mit unterschiedlichen Antworten vorhanden sein. Sonst mischt die App Antworten aus anderen Gruppen als falsche Optionen dazu.
Die Dateien müssen gültiges JSON sein (Anführungszeichen, Kommas). Bei einem Fehler nutzt die App weiter den zuletzt gespeicherten Stand.
