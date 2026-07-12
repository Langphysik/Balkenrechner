# Balken-Rechner als Handy-App (Android)

Dieser Ordner enthält alles, was nötig ist. Die App braucht **keinen Server mit Programmlogik** —
nur einen Ort, von dem die Dateien per **https** ausgeliefert werden. Das ist die einzige
Bedingung, die Android für die Installation stellt.

## Inhalt

| Datei | Zweck |
|---|---|
| `index.html` | die komplette App (Rechenkern, Zeichnung, Diagramme, Ausdrucke) |
| `manifest.webmanifest` | Name, Farben, Icon, Startverhalten (Vollbild ohne Browserleiste) |
| `sw.js` | Service Worker — legt die App im Gerät ab, damit sie **offline** läuft |
| `icons/` | App-Symbol in drei Größen (auch „maskable" für runde Android-Symbole) |

## Weg A — GitHub Pages (kostenlos, ca. 10 Minuten)

1. Auf github.com anmelden, oben rechts **New repository**, Name z. B. `balken-rechner`,
   auf **Public** stellen, anlegen.
2. Im neuen Repository **Add file → Upload files**, alle Dateien dieses Ordners hineinziehen
   (den Ordner `icons` mit hochladen, die Struktur muss erhalten bleiben). **Commit changes**.
3. **Settings → Pages**: unter *Branch* `main` und `/ (root)` wählen, **Save**.
4. Nach ein bis zwei Minuten steht dort die Adresse, etwa
   `https://deinname.github.io/balken-rechner/`.

## Auf dem Handy installieren

1. Adresse in **Chrome** auf dem Android-Handy öffnen.
2. Chrome bietet **„App installieren"** an (sonst: Menü ⋮ → *Zum Startbildschirm hinzufügen*).
3. Fertig — das Symbol liegt auf dem Startbildschirm, die App öffnet sich im Vollbild ohne
   Adressleiste und funktioniert danach **auch ohne Internetverbindung**.

Android baut daraus im Hintergrund ein echtes Paket (WebAPK); die App erscheint in der
App-Liste und in den Einstellungen wie jede andere App.

Auf dem iPhone geht es ebenso, dort über *Teilen → Zum Home-Bildschirm*.

## Weg B — echtes APK zum Weitergeben

Wenn du eine Datei brauchst, die du Kollegen schicken kannst:
**pwabuilder.com** aufrufen, die Adresse aus Weg A eintragen, Android-Paket erzeugen lassen.
Das Ergebnis ist ein APK mit demselben Inhalt. Zur Installation müssen die Empfänger
„Installation aus unbekannten Quellen" erlauben; für den Play Store wäre ein
Entwicklerkonto nötig (einmalig 25 $).

## Nach Änderungen

Wird `index.html` geändert, in `sw.js` die Zeile

```js
const CACHE = "balken-rechner-v1";
```

auf `-v2` usw. hochzählen. Sonst behalten bereits installierte Geräte die alte Fassung im Cache.

## Hinweise

- Der PowerPoint-Export ist in dieser Fassung **nicht** enthalten — die App läuft dadurch
  vollständig offline. Die drei Ausdrucke (Lösung, Schülerversion, Momente zeichnen) sind
  weiterhin da und lassen sich vom Handy aus drucken oder als PDF speichern.
- Am Handy ist die Zeichnung oben angeheftet und bleibt beim Scrollen durch die Regler sichtbar.
