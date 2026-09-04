# Interactive Algorithm Visualizer with Performance Comparison

## Overview
A web-based interactive visualizer for common algorithms (sorting, searching, graph traversal) with side-by-side performance comparison across implementations and data sizes.

## Architecture/Structure
```
┌─────────────────────────────────────────────────────────┐
│            Algorithm Visualizer                          │
├─────────────┬──────────────┬──────────────┬─────────────┤
│  Algorithm  │  Visualization│  Benchmark  │  Export     │
│  Selector   │    Engine    │    Engine    │  Generator  │
├─────────────┴──────────────┴──────────────┴─────────────┤
│              Frontend (React + D3.js)                    │
└─────────────────────────────────────────────────────────┘
```

## Workflow
1. User selects algorithm and implementation variant
2. Visualizer renders step-by-step execution with animations
3. Side-by-side comparison shows multiple algorithms simultaneously
4. Benchmark engine runs timing tests across input sizes
5. Results export to CSV/JSON for analysis

## Tools
- React + TypeScript
- D3.js for visualizations
- Web Workers for benchmark execution
- Canvas API for animations
- Chart.js for result visualization

## Learning Goals
- Algorithm complexity analysis
- Interactive visualization techniques
- Web Workers for parallel execution
- Benchmark methodology

## Build Milestones
1. **M1**: Sorting algorithms visualizer (bubble, merge, quick)
2. **M2**: Search algorithms (binary, DFS, BFS)
3. **M3**: Side-by-side comparison mode
4. **M4**: Real-time benchmarking with timing
5. **M5**: Graph algorithm visualization (Dijkstra, A*)
6. **M6**: Export and sharing functionality
