# Installation

Texture Toolkit is an **Editor-only plugin**, not a runtime component for packaged games.

## Requirements

- **Unreal Engine 5.6, 5.7 and 5.8** are the planned Windows release targets. **None is currently certified for release**; UE 5.8.4 is the development baseline.
- **Windows x64**.
- An Unreal-compatible **C++ build toolchain** only when installing/compiling from source; installing a matching precompiled Fab release package should not require compiling the plugin locally.
- Unreal's **PythonScriptPlugin** and **EditorScriptingUtilities** plugins enabled.
- A project in which you can install a project-level Editor plugin.

Texture Toolkit bundles **Pillow 9.5.0**. Development checks have exercised Python 3.11.8 on UE 5.7.4/5.8.4; UE 5.6 dependency compatibility remains unverified. You do not need a separate standalone image-processing application.

## Fab packages versus manual source installation

When a verified Fab Code Plugin release becomes available, Fab handles compilation for its selected UE versions. The publisher still validates the exact distributed package separately in every engine version claimed as compatible. **Do not treat a successful Fab build as proof of functional compatibility.** Consult [Compatibility & Limitations](compatibility.md) for current verification status.

The steps below describe the **manual project-level installation** of a plugin package and are not a statement that a Fab release is already available.

## Install in a project

1. Close Unreal Editor.
2. Copy the complete plugin directory to `<YourProject>/Plugins/TextureToolkit`.
3. Reopen the project. Allow the Editor module to compile if prompted.
4. In **Edit → Plugins**, enable **Texture Toolkit for Unreal Artists** and its Editor dependencies.
5. Restart the Editor if prompted.
6. In the Content Browser, select one or more **Texture2D** assets, right-click and open **Texture Toolkit**.

The context submenu is available only when every selected asset is a `Texture2D`. A mixed selection with another asset type does not show it.

## After installation

Read [Getting Started](getting-started.md) for a first export. **Settings** and **About** are available from the main Unreal Editor **Texture Toolkit** menu.

For confirmed engine support and known limitations of a distributable package, consult the release-specific compatibility information. **Do not assume support for other Unreal Engine versions.**

[Compatibility & Limitations](compatibility.md) · [Troubleshooting](troubleshooting.md)
