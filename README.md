# TSL Node Editor

[![WebGPU](https://img.shields.io/badge/WebGPU-Enabled-4285F4?style=flat-square&logo=googlechrome&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/API/WebGPU_API)
[![TSL](https://img.shields.io/badge/TSL-Three_Shading_Language-FF6B35?style=flat-square)](https://threejs.org/)
[![Three.js](https://img.shields.io/badge/Three.js-WebGPU-black?style=flat-square&logo=threedotjs)](https://threejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Fork](https://img.shields.io/badge/Fork-takahirox%2Ftsl--node--editor-lightgrey?style=flat-square&logo=github)](https://github.com/takahirox/tsl-node-editor)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)

> **⚠️ This is a fork of [takahirox/tsl-node-editor](https://github.com/takahirox/tsl-node-editor)** with additional contributions and experimental features added by [@yomero243](https://github.com/yomero243). All credit for the original editor goes to [@takahirox](https://github.com/takahirox).

A visual **node-based editor** for building Three.js TSL (Three Shading Language) materials, with real-time WebGPU preview and JS/TS export.

**Original Demo:** https://takahirox.github.io/tsl-node-editor/

---

## 🤔 Why TSL Matters

**TSL (Three Shading Language)** is replacing `ShaderMaterial` as the standard way to build materials in Three.js:

| Legacy `ShaderMaterial` | Modern TSL |
|---|---|
| Raw GLSL strings | Composable node graph |
| WebGL-only | WebGPU + WebGL backends |
| No type safety | TypeScript-friendly |
| Hard to serialize | JSON-serializable graph |
| Renderer-coupled | Backend-agnostic |

TSL is the material system Three.js is investing in for r180+. Learning it now puts you ahead of the curve.

---

## ✨ Features

- 🕸️ **Visual Node Graph** — drag-and-drop interface to wire TSL nodes into complex materials
- 👁️ **WebGPU Live Preview** — see your material update in real time on a 3D mesh
- 📤 **Code Export** — export the node graph as valid JS/TS code ready to use in your project
- 🔧 **Function Nodes** — define reusable TSL functions visually
- 📦 **GLTF Nodes** — load GLTF geometry, materials, and textures directly into the node graph
- 🔍 **Code Viewer** — inspect the generated TSL code alongside the visual editor

---

## 🔧 My Contributions (fork additions)

### `src/tslGltfExporter.ts`

The main addition in this fork is a **TSL GLTF Exporter** — a custom serializer that converts a TSL node graph back into GLTF-compatible material output.

Key implementation details:
- Walks the TSL node tree recursively to serialize each node into a typed `NodeExport` structure
- Handles shared/singleton TSL nodes (e.g., `positionWorld`, `normalView`) by name-mapping them from the TSL namespace
- Supports argument cleaning, link tracking between nodes, and property/index-based references
- Designed to be extensible via `overrides` — inject custom serialization logic for specific node types

This enables round-tripping: **build a material in the visual editor → export it as a GLTF-compatible TSL descriptor → reimport it in your Three.js scene**.

---

## ⚙️ Requirements

- Node.js 18+
- Browser with WebGPU support (Chrome 113+ / Edge 113+)

---

## 🚀 Getting Started

```bash
git clone https://github.com/yomero243/tsl-node-editor.git
cd tsl-node-editor
npm install
npm run dev
```

---

## 📁 Structure

```
tsl-node-editor/
├── src/
│   ├── App.tsx              # Main editor layout
│   ├── tslGltfExporter.ts  # ← Custom GLTF exporter (fork addition)
│   └── viewer.ts           # WebGPU preview renderer
├── viewer.html              # Preview iframe
└── index.html               # Main editor entry
```

---

## 🤝 Upstream

This fork tracks [takahirox/tsl-node-editor](https://github.com/takahirox/tsl-node-editor). Changes in this fork are experimental and may not be merged upstream (upstream does not accept PRs by policy).

If you find the GLTF exporter useful, feel free to open a discussion in the upstream repo.

---

## 👨‍💻 About

Fork maintained by **Gabriel** — Creative 3D Developer specializing in Three.js, React Three Fiber, WebGPU, and TSL material systems.

> 💼 **Available for freelance** — WebGL/WebGPU experiences, 3D tooling, shader development, and interactive web. [Let's connect →](https://github.com/yomero243)
