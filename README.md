# Fechtschritt

Minimalistische Begleit-App zum Fechtkurs. Die App sagt Fußarbeit-Kommandos auf Deutsch an, du führst sie aus.

## Benutzung

`index.html` im Browser öffnen (am Handy oder Laptop). Keine Installation, kein Server nötig.

1. **Kurswoche** wählen. Aktionen, Waffe und Tempo werden passend eingestellt.
2. Bei Bedarf **Waffe**, **Tempo**, **Dauer** und **Platz** anpassen.
3. **Start** drücken. Tippen pausiert, „Beenden“ bricht ab.

Die App merkt sich, wo du stehst, und sagt nie „Vor“, wenn vorn kein Platz mehr ist.

## Kommandos

| Kommando | Bedeutung |
|---|---|
| Vor | Schritt vor |
| Zurück | Schritt zurück |
| Stoß | Stoß aus dem Stand |
| Angriff | Stoß mit Schritt vor |
| Konter | Stoß mit Schritt zurück |

Alle 30 Sekunden kommt ein Haltungshinweis mit etwas längerer Pause. Etwa jede vierte Ansage ist ein Angriff, nie zwei direkt hintereinander.

## Eigene Sprachaufnahmen

Lege MP3-Dateien in den Ordner `sounds/`. Fehlt eine Datei, spricht die Browserstimme.

`vor.mp3`, `zurueck.mp3`, `stoss.mp3`, `angriff.mp3`, `konter.mp3`, `haltung.mp3`, `fertig.mp3`

Wichtig: keine Stille am Anfang der Aufnahme, sonst kommt das Kommando verzögert. Eigene Dateien funktionieren nur, wenn die App über einen Webserver läuft (z. B. GitHub Pages), nicht beim direkten Öffnen der Datei.

## Neue Kurswoche hinzufügen

In `index.html` das Objekt `WEEKS` erweitern. Pro Woche stehen nur die **neuen** Aktionen drin; alles aus früheren Wochen gilt automatisch weiter.

```js
var WEEKS = {
  1:{neu:["vor","zurueck"], waffe:"ohne", tempo:"langsam"},
  2:{neu:["vorStoss"], waffe:"mit", tempo:"langsam"},
  3:{neu:["stoss"], waffe:"mit", tempo:"mittel"}   // Beispiel
};
```

Mögliche Aktionen: `vor`, `zurueck`, `stoss`, `vorStoss` (Angriff), `zurueckStoss` (Konter). Neue Aktionen kommen in das Objekt `ACTIONS`.

Wochen ohne Eintrag erscheinen in der App gesperrt.

## Hinweis

Die Sprachausgabe nutzt die eingebaute Stimme des Browsers. Ohne Sprachausgabe spielt die App unterschiedliche Signaltöne.

Idee nach der App „Fencing Footwork“ (Version 0.8.2).
