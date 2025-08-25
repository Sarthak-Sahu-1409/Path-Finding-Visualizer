## Pathfinding Visualizer (React + TypeScript + Vite)

An interactive pathfinding and maze-generation visualizer built with React, TypeScript, Vite, and Tailwind CSS.

- Live Demo: `https://final-path-finding-visualizer.vercel.app/`

### Features
- Visualize classic pathfinding algorithms: Dijkstra, A*, Breadth-First Search (BFS), Depth-First Search (DFS)
- Generate mazes: Binary Tree, Recursive Division
- Adjustable animation speed (Slow, Medium, Fast)
- Click-and-drag to draw or erase walls
- Reset/Replay visualization easily

### Tech Stack
- React 18, TypeScript
- Vite
- Tailwind CSS, tailwind-merge
- react-icons

### Getting Started
Prerequisites: Node.js 18+ and npm or pnpm/yarn.

1) Install dependencies
```
npm install
```

2) Start the dev server
```
npm run dev
```

3) Open the app
Vite will print a local URL (typically `http://localhost:5173`).

4) Build for production
```
npm run build
```

5) Preview the production build
```
npm run preview
```

### Usage
1) Choose a Maze from the "Maze" dropdown (or "No Maze").
2) Choose a Graph algorithm (Dijkstra, A*, BFS, DFS).
3) Select animation Speed.
4) Optionally draw walls by clicking and dragging on the grid.
5) Press Play to visualize. When finished, the button becomes Reset to clear and try again.

### Algorithms Overview
- Dijkstra (`src/lib/algorithms/pathfinding/dijkstra.ts`): Uniform-cost shortest path in unweighted grids.
- A* (`src/lib/algorithms/pathfinding/aStar.ts`): Informed search using heuristic + distance.
- BFS (`src/lib/algorithms/pathfinding/bfs.ts`): Explores neighbors level-by-level (shortest path in unweighted grids).
- DFS (`src/lib/algorithms/pathfinding/dfs.ts`): Depth-first exploration (not guaranteed shortest path).

Maze Generation:
- Binary Tree (`src/lib/algorithms/maze/binaryTree.ts`)
- Recursive Division (`src/lib/algorithms/maze/recursiveDivision.ts` with `horizontalDivision.ts` and `verticalDivision.ts`)

### High-Level Architecture
- `src/App.tsx`: Wraps providers and renders `Nav` and `Grid`.
- Context
  - `PathfindingContext`: algorithm, maze, grid state, visualization flag
  - `SpeedContext`: selected animation speed
  - `TileContext`: start and end tiles
- Hooks: simple accessors around the above contexts (`usePathfinding`, `useSpeed`, `useTile`).
- Components
  - `Nav`: controls for maze, algorithm, speed, and play/reset
  - `Grid`: renders the grid and handles wall drawing
  - `Tile`: individual cell rendering
  - `PlayButton`: play/reset button
- Utils
  - `runPathfindingAlgorithm.ts` and `runMazeAlgorithm.ts` orchestrate algorithms
  - `animatePath.ts` animates traversed tiles and final path
  - `helpers.ts`, `heuristics.ts`, `getUntraversedNeighbors.ts`, `constructBorder.ts`, etc.
- Styling: Tailwind via `src/index.css`

### Configuration
- Grid size: `MAX_ROWS`, `MAX_COLS` in `src/utils/constants.ts`
- Speed options and timing constants: `SPEEDS`, `SLEEP_TIME`, `EXTENDED_SLEEP_TIME`
- Start/End tile defaults: `START_TILE_CONFIGURATION`, `END_TILE_CONFIGURATION`

### Scripts
```
npm run dev       # Start Vite dev server
npm run build     # Type-check and build for production
npm run preview   # Preview production build
npm run lint      # ESLint (TypeScript + React)
```

### Deployment
The project is Vercel-ready. A typical deployment uses the Vite static output produced by `npm run build`.

- Live Demo: `https://final-path-finding-visualizer.vercel.app/`

### Screenshots / Media
- GIF: `src/assets/pathfinding-visualizer.gif`

### License
This project is open-source under the MIT License. See `LICENSE` for details.

### Acknowledgements
Inspired by common visualizers for pathfinding and maze algorithms and implemented with a focus on clarity and educational value.


