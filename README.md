# World Flavor Atlas

Interactive 3D visualization of food ingredient embeddings from the [Epicure](https://arxiv.org/abs/2605.22391) paper by Radzikowski & Chen (2026).

**[Live Demo](https://tomacco.github.io/world-flavor-atlas)** 

## What is this?

250 food ingredients from cuisines around the world, mapped into 3D space by how they relate to each other. Built on embeddings trained on **4.14 million recipes** across 7 languages.

Three models organize the same ingredients differently:

| Model | Organizes by | Geometry |
|-------|-------------|----------|
| **COOC** | Recipe co-occurrence — what gets cooked together | Diffuse (PR = 173.6) |
| **CORE** | Blend of co-occurrence + chemistry | Tight (PR = 94.2) |
| **CHEM** | Shared flavor compounds (FlavorDB) | Diffuse (PR = 183.1) |

Drag the slider to morph between them in real time and watch clusters reshape.

## Features

- **3D scatter** of ~250 real ingredients colored by 8 cuisine macro-regions
- **Real-time cluster morphing** via continuous slider between COOC / CORE / CHEM models
- **Convex hulls** that reshape live as models interpolate
- **Fuzzy search** with autocomplete, match highlighting, and camera fly-to
- **Region filters** — click legend to isolate/compare cuisines
- **Sensory axes** — toggle Sweet/Bitter, Spicy/Mild, Protein/Carb, Umami/Fresh directions
- **Nearest-neighbor connections** — click any ingredient to see its top-5 neighbors
- **SLERP journeys** — navigate an ingredient toward a cuisine pole
- **Semantic zoom** — ingredient labels appear as you zoom in
- **Welcome overlay + info modal** for newcomers
- **Keyboard shortcuts** (`/` search, `?` help, `Esc` clear)
- **Mobile responsive**

## Tech

Single self-contained HTML file. No build step.

- [Three.js](https://threejs.org/) — 3D rendering, custom shaders, bloom postprocessing
- [ConvexGeometry](https://threejs.org/docs/#examples/en/geometries/ConvexGeometry) — cluster boundary visualization
- Metapath2Vec ingredient positions synthesized from paper findings

## Running locally

```bash
# Just open the file
open index.html

# Or serve it
npx serve .
```

## Data source

Based on the paper:

> **Epicure: Navigating the Emergent Geometry of Food Ingredient Embeddings**
> Jakub Radzikowski, Josef Chen (KAIKAKU.AI)
> arXiv:2605.22391, May 2026

Ingredient positions are synthetic approximations of the paper's UMAP projections, using real ingredient names and cuisine region assignments. The actual trained embeddings are not included (paper artifacts are not yet released).

## License

MIT
