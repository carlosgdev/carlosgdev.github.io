# Models (GLB)

## david-bust.glb

Loaded by `src/scenes/layers/scene-2-persona.tsx` (capa 2 "persona" del canvas R3F).

### Source recomendada (CC0)

**SMK – Statens Museum for Kunst, "Head of Michelangelo's David"**

- Page: https://www.myminifactory.com/object/3d-print-head-of-michelangelo-s-david-52645
- License: **CC0 1.0 Universal** (Public Domain Dedication, no attribution required)
- Origin: scan from a 1899 plaster cast of the original Michelangelo David, captured by SMK with an Artec Eva
- Original format: STL (~100k triangles)

### Source alternativa (CC BY 4.0, GLB pre-optimized)

**Thomas Flynn (@nebulousflynn) — "Head Of Michelangelo's David, Optimised"**

- Page: https://sketchfab.com/3d-models/head-of-michelangelos-david-optimised-d29af50360624e5e9b1855666475380d
- License: CC BY 4.0 (requires attribution)
- Triangles: 100k, Vertices: 50k
- Derived from the same SMK CC0 scan, optimized with RapidCompact + provides direct GLB download
- If you use this version, add a credits line in the footer: "Head of David: Thomas Flynn (CC BY 4.0), based on SMK CC0 scan"

### Steps

1. Download from one of the sources above (CC0 from SMK is the cleanest).
2. If STL: convert to GLB. Easiest route:
   ```bash
   npx -y gltf-transform copy david.stl david-bust.glb
   npx -y gltf-transform draco david-bust.glb david-bust.glb --compression 7
   npx -y gltf-transform optimize david-bust.glb david-bust.glb
   ```
3. Place final file at: `app/public/models/david-bust.glb`
4. Rebuild: `npm run build`
5. The scene falls back to the previous primitive bust (sphere + cylinder) if the file is missing or fails to load, so the build never breaks.

### Material override

The scene applies the project's unified 3D language at runtime — replaces any embedded materials with `MeshStandardMaterial` using `PALETTE_3D.cream` + `UNIFIED_MATERIAL` (metalness 0.1, roughness 0.45). This keeps the bust coherent with the rest of the canvas (lessons-learned 2026-04-25 — "lenguaje 3D unificado").
