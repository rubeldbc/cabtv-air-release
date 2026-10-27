# CabTV Air — Windows setup

**CabTV Air** is a broadcast playout and on-air graphics system for TV channels, built on OBS Studio. This repository
publishes its **Windows installer only** — one `setup.exe` that installs OBS Studio together with CabTV Air, ready to
start. The source code is not published here.

> **Download:** [**cabtv-air-1.0.0-windows-x64-setup.exe**](https://github.com/rubeldbc/cabtv-air-release/releases/latest)
> from the **[Releases](https://github.com/rubeldbc/cabtv-air-release/releases)** page.

---

## Contents

1. [What CabTV Air does](#1-what-cabtv-air-does)
2. [What the setup installs](#2-what-the-setup-installs)
3. [System requirements](#3-system-requirements)
4. [Download and check the file](#4-download-and-check-the-file)
5. [Install, step by step](#5-install-step-by-step)
6. [First start](#6-first-start)
7. [Donation (the licence of CabTV Air)](#7-donation-the-licence-of-cabtv-air)
8. [Update to a newer setup](#8-update-to-a-newer-setup)
9. [Uninstall](#9-uninstall)
10. [Where everything is](#10-where-everything-is)
11. [Troubleshooting](#11-troubleshooting)
12. [What's new](#12-whats-new)
13. [Third-party software](#13-third-party-software)
14. [About this repository](#14-about-this-repository)

---

## 1. What CabTV Air does

CabTV Air adds its own sources to OBS Studio. Each one is added from OBS's **Sources → +** list:

| Source in OBS | What it is for |
| --- | --- |
| **CabTV AirList** | The playlist and playout: clips played back to back without a gap, cue and jump, live feeds, schedules, the as-run log, a clip library with its own database, a clip editor (frame, in and out points), the **Auto Playlist** that builds a day's rundown from chunks, movies, fillers and commercials, and the **CountDown** window for any row. |
| **CabTV AirGFX** | A graphics designer for on-air graphics: shapes, texts, clocks, countdowns, pictures, videos and web pages in groups that come and go by their own animations, bound to the clips they belong to — with a *Lead* to start before their clip. |
| **CabTV AirPGM** | A full-screen programme card (for example *Coming up next*), placed in the playlist before a movie. Its texts and thumbnails read the next movies from the playlist. |
| **CabTV AirURW** | The *You are watching* card: the movie's own clip in a box, with its name, prefix and thumbnail over it. |
| **CabTV AirTicker** | A news ticker: a header and a crawl, fed from a text file, a Google Sheet or its own web page. |
| **CabTV AirLshape** | An L-shaped frame (DownStream) that squeezes the programme picture to make room for graphics. |

It also brings:

- **Web pages** for the newsroom and the control room — the ticker's news page, the log, and the control page — opened
  from the buttons in CabTV Air's windows, in the PC's own browser.
- **One database for every record** (clips, playlists, schedules, rundowns, graphics' presets), installed with it —
  nothing to set up.
- **Media found wherever it stands**: a design's pictures and videos are found again if the install moves; a file
  found nowhere is asked for once (*Locate…*), and until then drawn as a plain colour — never an error on air.

## 2. What the setup installs

One `setup.exe` does everything a PC needs. You are never asked to type a command.

- **OBS Studio 32.2.2**, portable, in its own folder — separate from any other OBS on the PC. CabTV Air is inside it.
- **CabTV Air** — the plugin, its data and its designs.
- **The database** — empty at the first install; **never written over** by a later setup.
- **Microsoft Visual C++ runtime** (needed by OBS and the database), installed only if the PC does not have it.
- **A *CabTV Air* shortcut** on the desktop and in the Start menu.
- **Its uninstaller**, listed in Windows' *Installed apps*.

**The folder:** `D:\CabTV Air` by default (when the PC has a fixed D: drive formatted NTFS; otherwise `C:\CabTV Air`).
**You can choose any other folder** on the setup's *Select Destination Location* page.

OBS's own update check is turned off in this install: a newer OBS comes with a newer CabTV Air setup, tested with it.

## 3. System requirements

| | |
| --- | --- |
| Windows | Windows 10 or Windows 11, 64-bit |
| Processor | 64-bit (x64) |
| Graphics | A DirectX 11 graphics card (as OBS Studio needs) |
| Disk | About **1 GB** free on an **NTFS** drive (the database needs NTFS), plus room for your clips |
| Rights | An administrator account to run the setup, once |
| Network | Needed for the *Donation* (licence) check and for a Google Sheet feed; the web pages work on the PC itself |

## 4. Download and check the file

1. Open the **[Releases](https://github.com/rubeldbc/cabtv-air-release/releases)** page.
2. Under the newest release, click **cabtv-air-1.0.0-windows-x64-setup.exe** to download it.
3. Each release lists the file's **SHA-256** fingerprint (and `SHA256SUMS.txt` beside it).

<details>
<summary>For IT staff: checking the download's fingerprint</summary>

In PowerShell, in the folder you downloaded to:

```powershell
Get-FileHash .\cabtv-air-1.0.0-windows-x64-setup.exe -Algorithm SHA256
```

The *Hash* shown must match the release's SHA-256 exactly. If it does not, delete the file and download it again.
</details>

**Windows SmartScreen** may show *"Windows protected your PC"*, because the setup is not code-signed. Click
**More info**, check that the publisher's file is the one you downloaded from this page, then **Run anyway**.

## 5. Install, step by step

1. **Close OBS Studio** if it is open — any OBS on the PC. The setup will not continue while OBS runs; it asks you to
   close it and press **Retry**. (It never closes OBS for you: an OBS may be on air.)
2. **Run** `cabtv-air-1.0.0-windows-x64-setup.exe` and allow it to make changes (**Yes**).
3. **Select Destination Location** — `D:\CabTV Air` is proposed. Keep it, or click **Browse…** and choose another
   folder. A drive that is not NTFS is refused, with a message saying so.
4. **Select Additional Tasks** —
   - *Create a desktop shortcut* (ticked).
   - *Remove the older OBS AirList and CabTV AirTicker plugins* — shown only where they are installed; CabTV Air
     replaces both.
5. **Install.** The setup lays OBS, CabTV Air and the database, installs the Microsoft runtime if needed, and sets the
   database's rights for every user of the PC.
6. **Finish** — leave *Start CabTV Air* ticked to start it straight away.

An earlier install of CabTV Air in OBS's own plugins folder is moved into the new folder by the setup, its records with
it (the old records are also kept where they were).

## 6. First start

1. Start **CabTV Air** from its desktop shortcut or the Start menu. This is OBS Studio with CabTV Air inside it.
2. OBS's first-run wizard may appear — you can cancel it.
3. In OBS's **Sources** box, click **+** and add **CabTV AirList**. Double-click it to open the **AirList** window:
   your playlist, its transport (Play, Stop, Cue, Next), and its menus.
4. Add your clips: **Add from disk…** opens the preliminary list, where each clip is named and typed before it enters
   the playlist; **Add from database…** adds clips you have used before.
5. Add graphics the same way — **CabTV AirGFX**, **CabTV AirPGM**, **CabTV AirURW**, **CabTV AirTicker** — and
   double-click one to open its designer. A new AirPGM and a new AirURW start with a ready design.
6. Bind graphics to clips with a row's **Source binding…** (its right-click menu), or a type's default graphics in
   **Settings › Types**: a graphic is on screen with the clips that bind it, and off with the others.

## 7. Donation (the licence of CabTV Air)

CabTV Air plays by an active **Donation**. Open the **AirList** window → **Settings** → the **Donation** tab:

- **Donation ID** — this PC's own ID. Send it to your CabTV Air provider to activate the PC.
- **Status** — whether this PC's donation is active, and what is left of it.

Without an active donation CabTV Air plays only a short round of clips — none on a PC that never had a donation — and
its graphics stay hidden. Reinstalling, updating or uninstalling
CabTV Air **never removes** this PC's donation data.

## 8. Update to a newer setup

1. Download the newer setup from the [Releases](https://github.com/rubeldbc/cabtv-air-release/releases) page.
2. **Close CabTV Air (OBS).**
3. Run the new setup. It finds your install and keeps its folder.

What an update **keeps**: your database (clips, playlists, schedules, rundowns, presets), OBS's settings, your scene
collections and profiles, and the donation. What it **replaces**: OBS's program files and CabTV Air's own files. Running
the same setup again is always safe — it also mends an install whose database rights went wrong.

## 9. Uninstall

Open Windows **Settings → Apps → Installed apps**, find **CabTV Air**, and choose **Uninstall** (or use *Uninstall CabTV
Air* in the Start menu). Close CabTV Air first.

The uninstaller asks: ***Delete CabTV Air's database and its OBS settings too?***

- **No** (the default) — OBS and CabTV Air are removed; your **database and OBS settings are kept** in the install
  folder, for a later install to find.
- **Yes** — they are removed too.

The donation data is never removed.

## 10. Where everything is

Inside the install folder (`D:\CabTV Air` by default):

| Folder | What it holds |
| --- | --- |
| `bin\64bit\obs64.exe` | OBS Studio — what the *CabTV Air* shortcut starts |
| `obs-plugins\64bit\` | OBS's plugins, CabTV Air's among them |
| `data\obs-plugins\cabtv-air\` | CabTV Air's data: its words, effects, designs, web pages |
| `config\` | OBS's settings, profiles and scene collections — **yours** |
| `pg\` | The database server |
| `pgdata\` | The database — **your records** |
| `uninstall\` | The uninstaller |
| `data\obs-studio\license\`, `OBS-SOURCE.txt` | OBS Studio's licence and where its source is |

The setup's own log (what it did, step by step) is written to Windows' temporary folder as *Setup Log ….txt*.

## 11. Troubleshooting

| What you see | What to do |
| --- | --- |
| The setup says **OBS is running** | Close every OBS on the PC, then press **Retry**. |
| The setup refuses the folder's drive | Choose a folder on an **NTFS** drive (most fixed drives are). |
| The setup says the **database is not ready** | Restart Windows and run the same setup again — your records are kept. |
| *"Windows protected your PC"* | **More info → Run anyway** (the setup is not code-signed; see §4). |
| A clip or a design says *not saved: the database is not open* | Run the setup again over the install (it repairs the database's rights), then start CabTV Air. |
| A design's picture or video is missing | A window asks for it once: **Locate…** the folder where it now is (every other missing file of that folder is found too), or **Use a colour** for now. |
| A graphic does not appear with its clip | Check that the clip's row binds it (the row's **Source binding…**), and its *Lead* in the designer's ⚙ settings. |
| Something else | Send your CabTV Air provider OBS's log: in CabTV Air, **Help → Log Files → Upload Current Log File** (or *Show Log Files*). |

## 12. What's new

### 1.0.0 — 27 October 2026

The first public setup. Highlights of this build:

- **Installer** — OBS Studio 32.2.2 included, portable; `D:\CabTV Air` by default, any folder you choose; the
  database ready for every user; an earlier install moved in with its records.
- **AirGFX** — a graphic's **Lead** now works however long it is: a graphic set to start two minutes before its movie
  stays ready through every clip of the break and starts on time. Drawing a **Countdown** sets its group to show for
  two minutes and the project's Lead to two minutes; drawing a **Clock** makes its group endless.
- **AirPGM** — a new AirPGM starts with a ready *Coming up* card: the next five movies, each row with its air time,
  thumbnail, prefix and name, coming in one after another and going out in the same order; 10 seconds long.
- **AirURW** — a new AirURW starts with a ready lower third: the movie's thumbnail, *Watching*, its prefix and its name;
  10 seconds long.
- **AirPGM and AirURW** — a text or thumbnail that finds no movie is hidden on its own; the rest of the card still
  plays.
- **AirList** — the **CountDown** window: a much larger time, the serial and the movie's name on one line, a smaller
  window. **Settings › General › Maintenance › Remove Unwanted Sources**: names of sources that no longer exist, found
  and removed or replaced — with *Include past days*. A renamed source is followed everywhere it is used.
- **Auto Playlist** — a chunk is never filled with the same card over and over when no filler or commercial list
  exists.

## 13. Third-party software

The setup includes, unchanged, each under its own licence:

| Software | Version | Licence | Source |
| --- | --- | --- | --- |
| OBS Studio | 32.2.2 | GNU GPL v2 or later | <https://github.com/obsproject/obs-studio> (also `OBS-SOURCE.txt` in the install) |
| PostgreSQL | 18.1 | PostgreSQL Licence | <https://www.postgresql.org/> |
| Node.js | 24.21.0 | MIT | <https://nodejs.org/> |
| Microsoft Visual C++ Redistributable | 2015–2022 | Microsoft's licence | <https://learn.microsoft.com/cpp/windows/latest-supported-vc-redist> |
| GNU FriBidi | — | GNU LGPL v2.1 or later | <https://github.com/fribidi/fribidi> |

OBS Studio is the work of the OBS Project and is not part of CabTV Air; CabTV Air is a plugin that runs inside it.

## 14. About this repository

- This repository holds **only this README**. Each setup is published as a file of a
  **[Release](https://github.com/rubeldbc/cabtv-air-release/releases)** (GitHub keeps files of that size there, not
  in the repository itself), with its SHA-256 beside it.
- **No source code is published here.** Please do not open pull requests.
- Questions and support: your CabTV Air provider.

© 2026 Kamrul Islam Rubel. CabTV Air.
