# MAM – Asset Manager

MAM is a desktop app to browse and tag your 3D asset library and send assets straight to **Houdini, Blender and
Maya** (and to **Unreal, Unity and Godot**). The library lives in a local folder or on a NAS: models, textures,
HDRIs, gobos, HDAs and sounds. Megascans, Fab and Poly Haven sit next to it in sections of their own. MAM runs on
Windows, macOS and Linux.

This repository holds the downloads only. The source code is not published here.

## Download

The newest version is under **[Releases](https://github.com/arunosaru/mam/releases/latest)**:

| System | File |
|---|---|
| Windows (installer, recommended) | `MAM-<version>-windows-setup.exe` |
| Windows (portable) | `MAM-<version>-windows-x64.zip` |
| Mac (Apple Silicon) | `MAM-<version>-macos-arm64.dmg` |
| Linux | `MAM-<version>-linux-x64.tar.gz` |

Not every release has a file for every system. If yours is missing, take the latest release that has one.

## Install

- **Windows:** Run the setup. It needs no admin rights and installs into `%LOCALAPPDATA%\Programs\MAM`, so MAM can
  update itself later. Or unpack the .zip anywhere and start `MAM.exe`. If SmartScreen warns, click
  *More info → Run anyway*. MAM needs the *Microsoft Edge WebView2 Runtime*, which Windows 10/11 usually has already.
- **Mac:** Open the .dmg and drag *MAM* onto *Applications*. If macOS says on the first start that it cannot check
  the app: *System Settings → Privacy & Security → Open Anyway*.
- **Linux:** Unpack and start `MAM/MAM`. MAM needs WebKitGTK (Ubuntu/Debian: `sudo apt install gir1.2-webkit2-4.1`).

On its first start MAM asks for your library folder. If it finds a Megascans library, it suggests that one too.
Everything else can be set later in the settings (Ctrl+, or ⌘,).

## Updates

MAM looks for a new version when it starts. *Update* downloads and checks it, *Restart now* swaps it in and starts
again. Settings, library and projects stay as they are. If the Houdini, Blender or Maya addon changed, install it
again in *Settings → Programs*.

## Features

### Library

- **Folders stay as they are:** Every asset is a folder in your library, organised in categories and
  subcategories. MAM only adds a small `metadata.json` with the tags.
- **Several paths:** The same library can be entered under different drive letters or mounts (e.g. `Z:\01_Assets`
  and `/Volumes/nas/01_Assets`). MAM uses the first path that is reachable on this computer.
- **Fast on a NAS too:** The window opens at once, the library is brought up to date in the background. What has
  been read shows while the scan goes on. If the NAS is not reachable, the last known state stays visible.
- **Search:** Ctrl+K searches everything (assets, categories, commands), Ctrl+F filters the view by name and tags.
  The colour wheel next to the search field filters by the main colour of the thumbnail.
- **Tags, favourites, rename, move, delete** – also for many assets at once. Deleted assets go to the trash, and
  Ctrl+Z undoes deleting, renaming and moving.
- **Import** by drag and drop or Ctrl+I: folders, zip files (unpacked), HDR/EXR files and whole HDRI folders.
  Assets already in the library are recognised and not imported twice.
- **Unregistered folders:** *Import → Unregistered folders* finds folders in the categories that are no asset yet
  and adds them with one click.
- **Needs attention** lists assets without a thumbnail or without tags.
- **Source and license** can be noted per asset. For restrictive licenses MAM gives a hint as soon as you add the
  asset to a project.

### Thumbnails

- **Paste a picture:** A screenshot in the clipboard becomes the thumbnail with Ctrl+V.
- **Videos and image sequences** as previews: the tile plays them while the mouse is on it. *Set thumbnail …*
  turns a video or a sequence into a small looping preview.
- **Without a picture:** MAM shows the preview stored in the .blend file. *Render thumbnail* renders a proper
  thumbnail with Blender in the background, also for many assets at once.
- **HDRIs** are rendered by MAM itself when they have no thumbnail of their own.

### Send to Houdini, Blender and Maya

- **One click:** Send a model, maps or an HDRI from the details panel into the open program.
  Install the addons in *Settings → Programs*.
- **A finished material:** The maps become a material that is already on the model. MAM recognises the role of
  each map by its file name (albedo, normal, roughness, metallic, displacement, opacity, AO …).
- **Choice of renderer:**
  - Houdini: Karma (MaterialX) or Redshift
  - Maya: Arnold or Redshift
  - Blender: Cycles / EEVEE
- **Several materials:** If a model comes with several texture sets, each becomes a material of its own on its
  material slot.
- **Packed maps** (ORM, ARM, MRAO, Unity mask map, base color with alpha) are read. *Pack channels* packs single
  maps into such files.
- **LODs, resolutions and UDIMs:** LOD and resolution can be switched in the panel. UDIM tiles count as one map.
- **Several instances:** If two Houdinis (or Mayas, Blenders) are open, MAM asks which scene to send to.
- **HDAs:** Houdini Digital Assets show their type, context and version and are installed and created as a node
  when sent. On request, every HDA of the library is right in Houdini's Tab menu.
- **Gobos:** Light templates are sent as a projecting spotlight, also as an animated image sequence.
- **USD assets:** *Files → USD asset* turns an asset into a self-contained USD with a MaterialX material, LOD and
  variant sets and a light proxy for the viewport.

### Megascans, Fab and Poly Haven

- **Megascans:** Bridge's Megascans library is a section of its own, sorted by type and category like in Bridge.
  Nothing is copied.
- **Fab:** Downloads from Fab are in the same section. Megascans assets from Fab are sorted in like those from
  Bridge, assets of other sellers are under *Fab*. The grey background of Fab pictures is cut out.
- **Poly Haven:** The whole free catalogue (HDRIs, textures, models, all CC0) can be browsed. *Download* saves into
  a folder of its own, and further resolutions are added instead of replacing the one before.
- **Take over:** *Copy to my library* copies an asset from these sections into your own library.

### Projects

- **Nested:** Projects can be nested as deep as you like (e.g. studies → semester → course → assignment), with a
  due date and countdown, notes, a cover and a project folder of their own.
- **Add assets** with Ctrl+P. They stay where they are in the library.
- **Scenes:** All scenes in the project folder (Blender, Houdini, Maya, C4D, 3ds Max, Nuke, Substance Painter,
  ZBrush) show grouped by program, with their versions together.
- **Renders:** Pictures, playblasts and image sequences play as a flipbook. *Compare* puts two versions side by
  side with a slider.
- **Reference board:** A free pin board per project like PureRef, for pictures by drag and drop or Ctrl+V, and
  for notes.
- **Hand-in:** *Credits* lists every asset with its source and license. *Zip* packs the project for handing it
  in, optionally with the assets used and a `CREDITS.txt`.

### Sounds

- **Sound library:** A category *Sounds* (or *Audio*, *SFX*) is shown as a sound library (WAV, AIFF, FLAC, MP3,
  OGG), grouped by UCS category and pack, with waveform and player.
- **Save a part:** Mark a range of the waveform, listen to it and save it as a WAV.

### Order and safety

- **Storage:** Shows what the library, Megascans, projects and the cache take.
- **Clean up:** Suggests old scene versions, backup files and old sim caches. Everything goes to a trash first.
- **Backup:** Copies new and changed files of the library and the projects to another drive. Nothing is ever
  deleted in the backup.

## Shortcuts

Ctrl on Windows and Linux, ⌘ on the Mac. `?` shows every shortcut in the app.

| Shortcut | Action |
|---|---|
| Click / ↩ | Open the details panel |
| Space | Quick preview |
| Ctrl+K | Search everything |
| Ctrl+F | Filter the view |
| Ctrl+D | Favourite on/off |
| Ctrl+P | Add to a project |
| Ctrl+V | Paste a picture as thumbnail |
| F2 | Rename |
| Del / ⌫ | Move to trash |
| Ctrl+Z | Undo |
| Ctrl+I | Import |
| Ctrl+R | Read the library again |
| Ctrl+ + / – | Tile size |
| Ctrl+, | Settings |

## Help with problems

*Settings → Programs → Show log file* opens the app's log. Please attach it to every bug report.

## License

See [LICENSE.txt](LICENSE.txt).
