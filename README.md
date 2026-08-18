# Spotify - The Train Car Teleporter

A Railroader utility mod for FUSE users.

## Commands

- `/spotify check` - non-destructive scan. Shows which cars are eligible and why cars are skipped.
- `/spotify` - asks Railroader's own `OpsController.Sweep("*")` routine to spot all open-waybill cars, then verifies where each car ended up.
- `/spotify help` - command help.

Spotify deliberately delegates the actual movement to Railroader's native sweep/open-space logic instead of manually changing transforms.

## Build

1. Copy your local reference DLLs into `Spotify/Libs/`:
   - `Assembly-CSharp.dll`
   - `FUSE.dll`
   - `UnityEngine.dll`
   - `UnityEngine.CoreModule.dll`
   - `UnityEngine.UI.dll`
   - `Newtonsoft.Json.dll`
2. Do **not** commit those DLLs. They are ignored by `.gitignore`.
3. Open `Spotify.sln` in Visual Studio 2022.
4. Select **Release**.
5. Choose **Build -> Build Solution**.
6. The install-ready folder is created at:
   `Spotify/bin/Release/Spotify/`
7. Copy that `Spotify` folder into Railroader's `Mods` folder.

## FUSE / Railloader note

Spotify does not require a separate Railloader installation.

FUSE 1.0.3 provides a compatibility shim for the old `Railloader.PluginBase` / `IModdingContext` assembly-plugin shape. Spotify uses that shim only so FUSE can discover the DLL and register `/spotify`.

## First test

Run:

`/spotify check`

before running `/spotify`.

If the project does not compile, send the full Visual Studio **Build Output** back to ChatGPT. If it compiles but the command fails in game, send the Spotify/FUSE lines from `Player.log`.
