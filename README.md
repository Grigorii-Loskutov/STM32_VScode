# H757_for_UIM — build presets and quick guide

This repository contains a dual-core STM32H757 project with separate subprojects for CM7 and CM4. Use CMake presets to configure and build the cores.

Available configure presets (root):

- `Root-Debug` — configure the whole project in `${sourceDir}/build/Root-Debug`
- `Root-Release` — release build in `${sourceDir}/build/Root-Release`
- `CM7-Debug` — configure CM7 only in `${sourceDir}/CM7/build`
- `CM4-Debug` — configure CM4 only in `${sourceDir}/CM4/build` (present but unused by default)

Available build presets:

- `CM7-Build` — builds using `CM7-Debug` configure preset
- `CM4-Build` — builds using `CM4-Debug` configure preset
- `Root-Build-Debug` — builds using `Root-Debug`

Quick commands (PowerShell)

Configure project root (Debug):

```powershell
C:/ST/STM32CubeCLT_1.19.0/CMake/bin/cmake.exe -S . -B build/Root-Debug -G Ninja -DCMAKE_BUILD_TYPE=Debug
```

Configure CM7 only:

```powershell
C:/ST/STM32CubeCLT_1.19.0/CMake/bin/cmake.exe --preset CM7-Debug
```

Build CM7 (from repo root):

```powershell
C:/ST/STM32CubeCLT_1.19.0/CMake/bin/cmake.exe --build "CM7/build" --config Debug
# or use build preset
C:/ST/STM32CubeCLT_1.19.0/CMake/bin/cmake.exe --build --preset CM7-Build
```

List available presets:

```powershell
C:/ST/STM32CubeCLT_1.19.0/CMake/bin/cmake.exe --list-presets
```

Notes
- The project intentionally keeps a `CM4` subproject (but you mentioned CM4 is not used) — presets for CM4 are present but you can ignore them.
- Presets live in `CMakePresets.json` at repository root; keep them unique (no duplicate `name` values) so CMake can read them.

If you want, I can also make the root preset build both cores with a single command or remove the `CM4` preset — tell me which you prefer.

---
Generated/edited by automation during maintenance.
