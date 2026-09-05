# Once Human — Linux / Steam / Proton Test Report
## Environment
- Distro: Garuda Linux (Arch-based)
- Kernel: linux-zen 7.2.3.zen1-2
- Desktop: KDE Plasma (`org.kde.breezedark.desktop`)
- Steam: `/home/sin/.local/share/Steam`
- Proton: Proton Experimental
- Game: Once Human

## Steam Config Fixes Applied
1. **libraryfolders.vdf** — ensured Steam library path uses Linux native path (`/home/sin/.local/share/Steam`) instead of Windows-style `S:\`. Files corrected:
   - `/home/sin/.local/share/Steam/config/libraryfolders.vdf`
   - `/home/sin/.local/share/Steam/steamapps/libraryfolders.vdf`

2. **LD_PRELOAD cleanup** — removed stale `gameoverlayrenderer.so` LD_PRELOAD entries. No leftover overlay hook files found in env at runtime.

## Runtime Results
- Game launched via Steam using Proton Experimental.
- No fatal crash, no Wine crash dump, no abnormal exit.
- Main process and xalia wrapper active.

### Non-Fatal Warnings Observed
- `LD_PRELOAD` `gameoverlayrenderer.so` ELFCLASS mismatch (32/64-bit). Known Steam overlay artifact; does not block gameplay.
- `XOpenIM()` failed. Cosmetic input-method warning.
- GTK theme rc warnings. Cosmetic.

## Verdict
Once Human runs on this configuration without required runtime patches. If future crashes occur, collect `/tmp/dumps/*.dmp` and Proton logs for diagnosis.

## How To Reproduce
1. Install Steam on Arch/Garuda.
2. Install Once Human via Steam library.
3. Ensure `libraryfolders.vdf` paths use Linux style.
4. Launch → Proton Experimental recommended.
