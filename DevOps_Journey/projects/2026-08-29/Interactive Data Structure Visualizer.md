# Interactive Data Structure Visualizer

## Overview
A browser-based interactive visualizer for common data structures (arrays, linked lists, trees, graphs, hash tables, heaps) and their operations. Students and developers can step through insertions, deletions, traversals, and sorts with animated visual feedback.

## Architecture / Structure
- **Frontend**: React + Canvas/SVG for rendering data structures
- **Step Engine**: Controls animation playback (play, pause, step forward/back)
- **Operation Library**: Implementations of common DS operations with trace output
- **Export**: Ability to save visualizations as GIF or shareable links

## Workflow
1. User selects a data structure type from sidebar
2. Chooses an operation (insert, delete, sort, search, traverse)
3. Inputs values and clicks "Run" to start animation
4. Steps through each iteration with visual highlight of active elements
5. Exports animation or copies code snippet showing the implementation

## Tools
- React + TypeScript
- Canvas API or SVG for rendering
- GSAP or Framer Motion for animations
- CodeMirror for code display
- React Spring for layout transitions

## Learning Goals
- Deep understanding of data structure internals and performance trade-offs
- Algorithm visualization techniques
- Frontend animation and state management
- Educational tool design principles

## Build Milestones
1. Week 1: Array and linked list visualizations with insertion/deletion
2. Week 2: Binary search tree with rotations and traversal animations
3. Week 3: Hash table with collision handling visualization
4. Week 4: Heap and priority queue with heapify/sort animations
5. Week 5: Sorting algorithm comparison (bubble, merge, quick, heap sort)
6. Week 6: Shareable URLs, GIF export, and responsive design
