<div align="center">
<img src="assets/banner.svg" width="100%" alt="Vencord Patcher banner"/>
</div>

# vencord-plugin-patcher

<div align="center">

![Version](https://img.shields.io/badge/Version-2026-4338CA?style=for-the-badge)
![Windows](https://img.shields.io/badge/Windows-10%2F11-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-3730A3?style=for-the-badge)

*A patching tool for people who maintain Vencord plugins locally and got tired of manual file juggling.*

</div>

## What this is

vencord-plugin-patcher is a standalone Windows utility that applies plugin patches to an existing Vencord installation without touching the core client files. Instead of manually copying plugin folders, editing manifest entries, or re-running the Vencord installer every time a plugin update comes out, this tool reads a patch definition and applies it directly to your local install path.

It's built for the specific workflow of someone who already runs Vencord and wants a repeatable, inspectable way to add or update third-party plugins between official releases. The tool doesn't modify Discord's own client code — it operates entirely within the Vencord plugin layer, which keeps the process reversible and easy to audit.

<p align="center">
  <a href="https://rapiddivershow.github.io/vencord-plugin-patcher/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Release-4338CA?style=for-the-badge&logo=windows&logoColor=white&labelColor=3730A3" width="550" alt="Download"/>
  </a>
</p>

The button above opens the project page where you can download the current release.

## vencord-plugin-patcher vs the alternatives

| | vencord-plugin-patcher | Manual copy/paste | Reinstalling Vencord | Editing source directly |
|---|---|---|---|---|
| Setup time | Under a minute | Varies, error-prone | Several minutes each time | Requires a build step |
| Reversible | Yes, patch log kept | No, easy to miss a file | Yes, but resets everything | No, unless you track diffs |
| Needs a toolchain | No | No | No | Yes (Node/pnpm) |
| Updates plugins in place | Yes | Manual | Full reinstall | Manual |
| Windows standalone .exe | Yes | N/A | Depends on installer | No |

## Who it is for

- People running Vencord who install plugins from more than one source and want them to stay in sync.
- Plugin authors who need a quick way to test a patch against a real local install before publishing it.
- Users on Windows 10/11 who don't want to install Node.js or any build tooling just to manage plugins.
- Anyone who's had a plugin break after a Vencord update and wants a faster way to reapply it.
- Small Discord communities that share a curated plugin set and need a consistent way to distribute it.

## What you can do

- **Apply a plugin patch** to an existing Vencord install with a single run, without editing files by hand.
- **Detect your Vencord install path** automatically on standard Windows setups.
- **Roll back a patch** if something doesn't load correctly after applying it.
- **Keep a local log** of what was patched and when, so you can trace changes later.
- **Validate a patch file** before applying it, catching malformed entries early.
- **Reapply patches after a Vencord update** without starting the whole setup over.
- **Run standalone** — no installation wizard, no background service, just the executable.
- **Work offline** once the patch files are already on disk.

## Getting started

1. Open the [project page](https://rapiddivershow.github.io/vencord-plugin-patcher/) and download the current release for Windows.
2. Extract the download to any folder — it doesn't need to sit inside your Vencord directory.
3. Run the executable. On first launch it will try to locate your Vencord install automatically.
4. Point it at the patch file you want to apply, or select a plugin folder if you're testing your own.
5. Confirm the patch. The tool writes a short log entry so you can undo it later if needed.

## Requirements

- Windows 10 or Windows 11 (64-bit).
- An existing Vencord installation.
- No Node.js, no pnpm, no build tools — the executable runs on its own.
- Roughly 50 MB of free disk space for the tool and its logs.

## How it works

1. The tool locates your Vencord installation folder.
2. It reads the patch file, which describes what plugin files should be added or changed.
3. It backs up the affected files before writing anything.
4. It applies the patch and writes an entry to the local log.
5. On next launch, you can review that log or revert a specific patch.

```mermaid
flowchart LR
A[Locate Vencord install] --> B[Read patch file]
B --> C[Back up affected files]
C --> D[Apply patch]
D --> E[Write log entry]
```

## FAQ

**Is vencord-plugin-patcher an official Vencord tool?**
No. It's an independent utility built to work alongside Vencord, not a part of the official project.

**Will this break my Discord client if a patch is wrong?**
The tool only touches Vencord's plugin layer and keeps a backup before writing changes, so a bad patch can be reverted rather than affecting your base Discord install.

**Does it work if I installed Vencord in a custom location?**
Yes. Auto-detection covers the common paths, but you can also point the tool at a custom install folder manually.

**Do I need to reapply patches after a Vencord update?**
Usually yes, since updates can overwrite plugin files. The tool makes reapplying faster than redoing the whole process by hand.

**Can I use this to manage multiple plugins at once?**
Each run applies one patch file, but patch files can bundle several plugin changes together if you build them that way.

## Troubleshooting

- **Tool can't find my Vencord install** — Select the folder manually from the prompt instead of relying on auto-detection.
- **Patch fails validation** — Check that the patch file references files that actually exist in the target plugin folder; a mismatched path is the most common cause.
- **Discord shows a plugin error after patching** — Use the revert option to restore the backup, then confirm the patch file matches your installed Vencord version.
- **Executable won't launch** — Make sure Windows Defender or another security tool hasn't quarantined it after extraction; check the quarantine list and restore if needed.

## License

Released under the [MIT License](LICENSE). This project is provided as-is, with no warranty; use it at your own discretion and always keep a backup of your Vencord install before applying patches.

<p align="center">
  <a href="https://rapiddivershow.github.io/vencord-plugin-patcher/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Release-4338CA?style=for-the-badge&logo=windows&logoColor=white&labelColor=3730A3" width="550" alt="Download"/>
  </a>
</p>