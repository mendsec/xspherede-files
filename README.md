# Spheradian Files

**A spatial file manager concept for [Spheradian](https://github.com/mendsec/spheradian): your folders as a city, and a Metroid-style sector map that shows where you are, where you are going, and what you are carrying.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Status: prototype](https://img.shields.io/badge/status-concept%20prototype-yellow.svg)](#project-status)

---

## The idea

Most file managers show a flat list and leave you to keep the shape of your file system in your head. Spheradian Files makes that shape visible in two stages.

### 1. The city (overview)

Before the familiar flat view, you see your file system from above. Every folder is a structure, and every top-level folder is a district:

| Visual property | Meaning |
|---|---|
| Height | Total size of the folder, including subfolders |
| Footprint | Number of files directly inside it |
| Density (opacity and glow) | Average weight of those files |

Two styles are available:

- **Metropolis**: solid towers with lit windows, like a skyline.
- **Monoliths**: columns of stacked translucent cubes; heavy folders look dense and massive, light ones look almost hollow.

Click any structure and the camera dives into it, landing you in the flat view at that folder.

### 2. The flat view with a sector map

The main area works like a conventional file manager: breadcrumbs, back, forward, up, copy, cut, paste, new folder, and the usual keyboard shortcuts.

The difference is a 3D sector map on the right edge, inspired by the map screens of exploration games:

- **Rooms are folders**, connected by corridors and shafts that follow the folder tree.
- **Unexplored rooms** are dim blue wireframes; **explored rooms** turn amber; **your room** carries a floating marker.
- **Changing folders draws the route** you take: up to the common ancestor and down to the destination, with the marker travelling along it.
- **Copy and cut change the room itself.** A copied item makes its room glow cyan with a duplicated echo; a cut item makes it red, dashed, and unstable.
- **While something is on the clipboard, every move draws a pending route** from its origin to where you are, with data packets flowing along it and a drop ring on your current room. You can see where the action is headed before you commit to it.
- **Paste sends a cube along the route.** Copied folders spawn at the origin and fly to their new place in the map; cut folders physically relocate.

## Running the prototype

**Try it online:** https://mendsec.github.io/spheradian-files/

To run it locally, note that the prototype is a single HTML file with no build step. Open it in a modern browser with WebGL 2:

```bash
xdg-open prototype/cube-explorer/index.html
```

It loads [three.js](https://threejs.org) 0.160.0 from jsDelivr, so the first load needs network access. The file system is **simulated**: a deterministic, generated tree. The prototype never reads your disk.

### Controls

| Context | Input | Action |
|---|---|---|
| City | Click a structure | Dive into that folder |
| City | Drag / wheel | Orbit / zoom |
| City | `M` | Toggle Metropolis and Monoliths |
| City | `Enter` | Enter `/home` |
| Flat view | Double-click / `Enter` | Open folder |
| Flat view | `Backspace`, `Alt+Left`, `Alt+Right` | Up, back, forward |
| Flat view | `Ctrl+C`, `Ctrl+X`, `Ctrl+V` | Copy, cut, paste |
| Flat view | `Ctrl+Shift+N` | New folder |
| Flat view | `Esc` | Back to the city |
| Map | Drag / wheel / click a room | Rotate / zoom / travel there |

Press **▶ Demo** in the flat view for a scripted tour of copy, cut, and paste across the map.

## Project status

**Concept prototype.** This repository currently holds a browser simulation used to explore the interaction design. It is not a working file manager and does not touch real files.

## Roadmap

- [x] Browser simulation of the city overview and the sector map
- [ ] Interaction refinements: label collision handling, multi-selection, drag and drop onto map rooms
- [ ] Native implementation in Rust and `wgpu`, sharing conventions with Spheradian
- [ ] Read-only access to a real directory tree, then real file operations
- [ ] Integration as a component of the Spheradian session, with trust-domain colours on rooms

## Relationship to Spheradian

Spheradian is a spherical 3D desktop environment prototype. Like the file managers of other desktop environments, Spheradian Files lives in its own repository so it can evolve, be released, and be reviewed independently of the compositor.

## Contributing

Ideas and feedback on the interaction design are welcome through issues. All code, comments, documentation, and commit messages are written in English. See [AGENTS.md](AGENTS.md) for the rules that apply to automated contributors as well.

## License

[MIT](LICENSE)
