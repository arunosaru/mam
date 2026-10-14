# MAM – Asset Manager

MAM ist eine Desktop-App, mit der du deine 3D-Asset-Bibliothek durchsuchst, verschlagwortest und direkt an
**Houdini, Blender und Maya** schickst (dazu **Unreal, Unity und Godot**). Die Bibliothek liegt in einem
lokalen Ordner oder auf einem NAS: Modelle, Texturen, HDRIs, Gobos, HDAs und Sounds. Megascans, Fab und Poly
Haven stehen in eigenen Bereichen daneben. MAM läuft unter Windows, macOS und Linux.

Dieses Repository enthält nur die Downloads. Den Quellcode gibt es hier nicht.

## Download

Die neueste Version steht unter **[Releases](https://github.com/arunosaru/mam/releases/latest)**:

| System | Datei |
|---|---|
| Windows (Installer, empfohlen) | `MAM-<Version>-windows-setup.exe` |
| Windows (portabel) | `MAM-<Version>-windows-x64.zip` |
| Mac (Apple Silicon) | `MAM-<Version>-macos-arm64.dmg` |
| Linux | `MAM-<Version>-linux-x64.tar.gz` |

Nicht jedes Release bringt eine Datei für jedes System mit. Steht dein System nicht dabei, nimm das letzte
Release, in dem es eine gibt.

## Installieren

- **Windows:** Den Setup ausführen. Er braucht keine Adminrechte und installiert nach
  `%LOCALAPPDATA%\Programs\MAM`, sodass MAM sich danach selbst aktualisieren kann. Alternativ die .zip irgendwo
  entpacken und `MAM.exe` starten. Warnt SmartScreen, auf *Weitere Informationen → Trotzdem ausführen* klicken.
  Gebraucht wird die *Microsoft Edge WebView2 Runtime*, die bei Windows 10/11 meist schon installiert ist.
- **Mac:** Die .dmg öffnen und *MAM* auf *Programme* ziehen. Meldet macOS beim ersten Start, dass es die App
  nicht prüfen kann: *Systemeinstellungen → Datenschutz & Sicherheit → Trotzdem öffnen*.
- **Linux:** Entpacken und `MAM/MAM` starten. Gebraucht wird WebKitGTK
  (Ubuntu/Debian: `sudo apt install gir1.2-webkit2-4.1`).

Beim ersten Start fragt MAM nach dem Bibliotheksordner. Wird eine Megascans-Library gefunden, schlägt MAM auch
diese vor. Alles andere lässt sich später in den Einstellungen setzen (Strg+, bzw. ⌘,).

## Updates

MAM sucht beim Start nach einer neuen Version. *Update* lädt sie herunter, prüft sie, und *Restart now*
tauscht sie aus und startet neu. Einstellungen, Bibliothek und Projekte bleiben dabei erhalten. Hat sich das
Houdini-, Blender- oder Maya-Addon geändert, installiere es unter *Settings → Programs* erneut.

## Funktionen

### Bibliothek

- **Ordner bleiben, wie sie sind:** Jedes Asset ist ein Ordner in deiner Bibliothek, gegliedert nach Kategorien
  und Unterkategorien. MAM legt nur eine kleine `metadata.json` mit den Tags dazu.
- **Mehrere Pfade:** Dieselbe Bibliothek lässt sich unter verschiedenen Laufwerksbuchstaben oder Mounts eintragen
  (z. B. `Z:\01_Assets` und `/Volumes/nas/01_Assets`). MAM nimmt den ersten Pfad, der auf diesem Rechner erreichbar ist.
- **Schnell auch auf dem NAS:** Das Fenster öffnet sofort, die Bibliothek wird im Hintergrund abgeglichen.
  Während des Scans erscheint schon, was gelesen ist. Ist das NAS nicht erreichbar, bleibt der letzte Stand sichtbar.
- **Suche:** Strg+K durchsucht alles (Assets, Kategorien, Befehle), Strg+F filtert die Ansicht nach Name und Tags.
  Der Farbkreis neben dem Suchfeld filtert nach der Hauptfarbe des Vorschaubilds.
- **Tags, Favoriten, Umbenennen, Verschieben, Löschen**, auch für mehrere Assets auf einmal. Gelöschtes landet im
  Papierkorb, und Strg+Z macht Löschen, Umbenennen und Verschieben rückgängig.
- **Import** per Drag & Drop oder Strg+I: Ordner, Zip-Dateien (werden entpackt), HDR/EXR-Dateien und ganze
  HDRI-Ordner. Was schon in der Bibliothek liegt, wird erkannt und nicht doppelt importiert.
- **Nicht erfasste Ordner:** *Import → Unregistered folders* findet Ordner in den Kategorien, die noch kein Asset
  sind, und nimmt sie mit einem Klick auf.
- **Needs attention** listet Assets ohne Vorschaubild oder ohne Tags.
- **Quelle und Lizenz** lassen sich pro Asset festhalten. Bei einschränkenden Lizenzen weist MAM darauf hin,
  sobald du das Asset einem Projekt zuordnest.

### Vorschaubilder

- **Bild einfügen:** Ein Screenshot in der Zwischenablage wird mit Strg+V zum Vorschaubild.
- **Videos und Bildsequenzen** als Vorschau: Die Kachel spielt sie ab, solange die Maus darauf liegt.
  *Set thumbnail …* macht aus einem Video oder einer Sequenz eine kleine, loopende Vorschau.
- **Ohne Bild:** MAM zeigt das Vorschaubild aus der .blend-Datei. *Render thumbnail* rendert mit Blender
  im Hintergrund ein richtiges Vorschaubild, auch für mehrere Assets auf einmal.
- **HDRIs** werden selbst gerendert, wenn sie kein eigenes Vorschaubild haben.

### Senden an Houdini, Blender und Maya

- **Ein Klick:** Modell, Maps oder HDRI aus dem Detail-Panel ins offene Programm schicken.
  Die Addons installierst du unter *Settings → Programs*.
- **Fertiges Material:** Aus den Maps wird automatisch ein Material, das gleich auf dem Modell liegt.
  Die Rolle jeder Map erkennt MAM am Dateinamen (Albedo, Normal, Roughness, Metallic, Displacement, Opacity, AO …).
- **Renderer wählbar:**
  - Houdini: Karma (MaterialX) oder Redshift
  - Maya: Arnold oder Redshift
  - Blender: Cycles / EEVEE
- **Mehrere Materialien:** Bringt ein Modell mehrere Texture-Sets mit, wird jedes ein eigenes Material auf seinem
  Material-Slot.
- **Gepackte Maps** (ORM, ARM, MRAO, Unity Mask Map, Base Color mit Alpha) werden gelesen. *Pack channels* packt
  einzelne Maps zu solchen Dateien zusammen.
- **LODs, Auflösungen und UDIMs:** LOD und Auflösung lassen sich im Panel umschalten. UDIM-Kacheln sind eine Map.
- **Mehrere Instanzen:** Sind zwei Houdinis (oder Mayas, Blenders) offen, fragt MAM, an welche Szene es gehen soll.
- **HDAs:** Houdini Digital Assets zeigen Typ, Kontext und Version und werden beim Senden installiert und als Node
  angelegt. Alle HDAs der Bibliothek stehen auf Wunsch direkt in Houdinis Tab-Menü.
- **Gobos:** Licht-Schablonen werden als projizierendes Spotlight gesendet, auch als animierte Bildsequenz.
- **USD-Assets:** *Files → USD asset* macht aus einem Asset ein eigenständiges USD mit MaterialX-Material,
  LOD- und Varianten-Sets und leichtem Proxy für den Viewport.

### Megascans, Fab und Poly Haven

- **Megascans:** Die Megascans-Library von Bridge erscheint als eigener Bereich, sortiert nach Typ und Kategorie
  wie in Bridge. Nichts wird kopiert.
- **Fab:** Downloads aus Fab stehen im selben Bereich. Megascans-Assets aus Fab werden einsortiert wie die aus Bridge,
  Assets anderer Verkäufer stehen unter *Fab*. Der graue Hintergrund der Fab-Bilder wird freigestellt.
- **Poly Haven:** Der ganze freie Katalog (HDRIs, Texturen, Modelle, alle CC0) ist durchsuchbar.
  *Download* lädt in einen eigenen Ordner, und weitere Auflösungen kommen dazu, statt die vorige zu ersetzen.
- **Übernehmen:** *Copy to my library* übernimmt ein Asset aus diesen Bereichen in die eigene Bibliothek.

### Projekte

- **Verschachtelt:** Projekte lassen sich beliebig verschachteln (z. B. Studium → Semester → Fach → Abgabe),
  mit Frist und Countdown, Notizen, Cover und eigenem Projektordner.
- **Assets zuordnen** mit Strg+P. Sie bleiben dabei an ihrem Platz in der Bibliothek.
- **Szenen:** Alle Szenen aus dem Projektordner (Blender, Houdini, Maya, C4D, 3ds Max, Nuke, Substance Painter,
  ZBrush) erscheinen nach Programm gruppiert, mit zusammengefassten Versionen.
- **Renders:** Bilder, Playblasts und Bildsequenzen laufen als Flipbook. *Compare* stellt zwei Versionen mit
  Schieberegler nebeneinander.
- **Referenz-Board:** Eine freie Pinnwand pro Projekt wie PureRef, für Bilder per Drag & Drop oder Strg+V
  und für Notizen.
- **Abgabe:** *Credits* listet alle Assets mit Quelle und Lizenz. *Zip* packt das Projekt für die Abgabe,
  wahlweise mit den verwendeten Assets und einer `CREDITS.txt`.

### Sounds

- **Sound-Bibliothek:** Eine Kategorie *Sounds* (oder *Audio*, *SFX*) wird als Sound-Bibliothek gezeigt
  (WAV, AIFF, FLAC, MP3, OGG). Gruppiert wird nach UCS-Kategorie und Pack, mit Wellenform und Player.
- **Ausschnitt speichern:** Einen Bereich der Wellenform markieren, anhören und als WAV speichern.

### Ordnung und Sicherheit

- **Speicherplatz:** Zeigt, was Bibliothek, Megascans, Projekte und Cache belegen.
- **Aufräumen:** Schlägt alte Szenenversionen, Backup-Dateien und alte Sim-Caches vor.
  Alles wandert erst in einen Papierkorb.
- **Backup:** Kopiert neue und geänderte Dateien aus Bibliothek und Projekten auf eine andere Platte.
  Im Backup wird nie etwas gelöscht.

## Tastenkürzel

Unter Windows und Linux Strg, auf dem Mac ⌘. `?` zeigt alle Kürzel in der App.

| Kürzel | Aktion |
|---|---|
| Klick / ↩ | Detail-Panel öffnen |
| Leertaste | Schnellvorschau |
| Strg+K | Alles durchsuchen |
| Strg+F | Ansicht filtern |
| Strg+D | Favorit an/aus |
| Strg+P | Zu einem Projekt hinzufügen |
| Strg+V | Bild als Vorschaubild einfügen |
| F2 | Umbenennen |
| Entf / ⌫ | In den Papierkorb |
| Strg+Z | Rückgängig |
| Strg+I | Import |
| Strg+R | Bibliothek neu einlesen |
| Strg+ + / – | Kachelgröße |
| Strg+, | Einstellungen |

## Hilfe bei Problemen

*Settings → Programs → Show log file* öffnet das Protokoll der App. Häng es an jede Fehlermeldung an.

## Lizenz

Siehe [LICENSE.txt](LICENSE.txt).
