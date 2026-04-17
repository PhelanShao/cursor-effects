# Cursor Effects

My cursor trail/smear effect configurations for VS Code and Ghostty terminal.

## VS Code - Neovide Cursor Effect

Simulates [Neovide](https://neovide.dev/) editor's cursor trail animation in VS Code.

Based on [vscode-neovide-cursor](https://github.com/LengineerC/vscode-neovide-cursor) by LengineerC.

### Setup

1. Install the [Custom CSS and JS Loader](https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css) extension:

   ```
   ext install be5invis.vscode-custom-css
   ```

2. Copy the script to a stable location:

   ```bash
   mkdir -p ~/.config/vscode
   cp vscode/neovide-cursor.js ~/.config/vscode/
   ```

3. Add to VS Code `settings.json`:

   ```json
   {
     "vscode_custom_css.imports": [
       "file:///Users/<your-username>/.config/vscode/neovide-cursor.js"
     ]
   }
   ```

4. Open Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`) and run **Enable Custom CSS and JS**, then restart VS Code.

> **Note:** Every time VS Code updates, the custom CSS injection may be reset. Re-run **Enable Custom CSS and JS** to restore the effect.

### Parameters

Edit `neovide-cursor.js` to customize:

| Parameter | Default | Description |
|-----------|---------|-------------|
| `cursorColor` | `"#C8D3F5"` | Cursor color |
| `useShadow` | `true` | Enable cursor shadow |
| `shadowColor` | same as cursorColor | Shadow color |
| `shadowBlur` | `10` | Shadow blur radius |
| `animationLength` | `0.10` | Animation duration for line jumps (seconds) |
| `shortAnimationLength` | `0.04` | Animation duration for short movements (seconds) |
| `trailSize` | `1` | Trail density (0-1, higher = longer trail) |
| `cursorUpdatePollingRate` | `500` | DOM polling interval for cursor detection (ms) |

---

## Ghostty - Cursor Smear Shader

A GLSL shader that creates a cursor smear/trail effect in the [Ghostty](https://ghostty.org/) terminal.

### Setup

1. Copy the config and shader files:

   ```bash
   mkdir -p ~/.config/ghostty/shaders
   cp ghostty/config ~/.config/ghostty/config
   cp ghostty/cursor_smear.glsl ~/.config/ghostty/shaders/
   ```

2. Restart Ghostty.

### Config Overview

The included `config` file contains:

- **Font**: ComicShannsMono Nerd Font (English) + LXGW WenKai GB Screen (Chinese)
- **Font size**: 14.6
- **Theme**: Dracula-based color palette
- **Background opacity**: 0.75 (translucent)
- **Cursor effect**: cursor_smear.glsl shader
- **Keybindings**: `Ctrl+J` scroll up, `Ctrl+K` scroll down
- **Other**: auto-copy selection, hide mouse while typing

### Parameters

Edit `cursor_smear.glsl` to customize:

| Parameter | Default | Description |
|-----------|---------|-------------|
| `OPACITY` | `0.6` | Trail opacity |
| `DURATION` | `0.3` | Trail fade duration in seconds |
