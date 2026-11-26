# Compatibility & Limitations

## Current state

**Texture Toolkit 0.1.0-backend-5.16 — Private Beta / In Validation**

| Item | Status |
| --- | --- |
| Unreal Engine release targets | **5.6, 5.7 and 5.8** (validation pending) |
| Operating system | **Windows x64** |
| Environment | **Unreal Editor only** |
| Asset type | **Texture2D** selected in the Content Browser |
| Core workflows | Export, Resize, Strip Alpha, Extract Channel, Channel Shuffle |
| Final packaged-build certification | **Pending** |
| Development baseline | **5.8.4**; this is not a public support certification |
| macOS / Linux | **Not advertised** |

The plugin descriptor marks this development line as Beta. This is **not** proof that a paid, publicly distributed build has passed full Editor regression tests.

## Unreal Engine support status

**UE 5.6, 5.7 and 5.8 are release targets, not yet advertised as supported.** UE 5.8.4 is the development baseline. Previous UE 5.0–5.5 versions are not in the current release plan. A successful C++ build alone does not prove that the plugin loads and works in the Editor.

| Version | Evidence to date | Status |
| --- | --- | --- |
| **5.8.4** | Local Win64 package build and Python tests; some historical commandlet checks | Interactive validation of the exact release package pending |
| **5.7.4** | Earlier local Win64 Development build and limited commandlet checks | Current release package and interactive validation pending |
| **5.6.1** | Local build attempts blocked by toolchain/engine-module issues | Build and Editor validation pending |

### Fab distribution checks

Fab **automatically compiles C++ Code Plugins for every selected Unreal Engine version**. A separate manual local build for each version is therefore **not required for Fab's build step**. Publishers must still upload an updated `.uplugin` project when adding a version, resolve Fab compilation errors, verify dependencies (including the Python runtime), and test the actual distributed package in the corresponding Editor. Only completed verification permits a support claim.

Official references: [Fab publishing and automated builds](https://dev.epicgames.com/documentation/en-us/fab/publishing-assets-for-sale-or-free-download-in-fab) and [Fab Code Plugin file requirements](https://dev.epicgames.com/documentation/en-us/fab/asset-file-format-and-structure-requirements-in-fab).

## Important limitations

- **Channel Shuffle:** one source texture only; no multi-source packing.
- **Extract Channel:** only supported 8-bit G8/BGRA8/RGBA8 Source Art, with actual available channels. G16/HDR/float extraction is not part of this version.
- **Export:** PNG/TGA, with source precision restrictions; G16 TGA is blocked.
- **Resize:** downscaling only, with optional **reimport into existing Unreal assets**. Reimport changes them and requires manual saving.
- **External originals:** only explicit Export overwrite or Resize/reimport options may change external files or Unreal import metadata. Read each operation's confirmation before proceeding.
- **GPU fidelity:** byte-identical source/output/import checks do not guarantee identical GPU-compressed appearance.

## Release verification

Final verification requires successful compilation **for each advertised UE version** (Fab's automated Code Plugin build, or a verified local build for non-Fab distribution) **and interactive Editor testing of the exact distributed package**. Test startup, Python/Pillow, Slate UI, all five operations, batch behavior, failed imports, stale previews, dirty packages, collisions, source precision and pixel/import fidelity.

The developer maintains separate engineering verification records for Unreal Editor regressions and source-to-import/display fidelity. The public compatibility status is updated only after the exact release package has been tested.

Until that evidence exists, this documentation is a **pre-release guide**, not a certified support matrix or a live purchase offer.
