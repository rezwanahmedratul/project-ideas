# NixOS Configuration Visualizer

## Overview
A visual editor and documentation generator for NixOS flake configurations. It parsesflake files and renders an interactive dependency graph showing module relationships, option hierarchies, and override chains — making Nix's declarative complexity more approachable.

## Architecture / Structure
- **Parser**: Nix language parser (or nixpkgs lib.import) to extract module dependencies
- **Graph Builder**: Constructs DAG of options, modules, and their inheritance
- **Renderer**: D3.js or Cytoscape.js force-directed graph for interactive exploration
- **Documentation Generator**: Produces Markdown or HTML reference docs from parsed config

## Workflow
1. Point tool at a flake.nix or configuration.nix file
2. Parse all imported modules and resolve option declarations
3. Build dependency graph showing which modules override what
4. Render interactive visualization with zoom/pan and filtering
5. Generate clickable documentation with search and navigation

## Tools
- Node.js + nix language bindings (or JSON output via `nix eval --json`)
- D3.js for visualization
- React for UI components
- Tree-sitter-nix for syntax highlighting
- Markdown / HTML export

## Learning Goals
- Nix expression language and flake system internals
- Declarative configuration management
- Graph theory applied to dependency resolution
- Documentation-as-code workflows

## Build Milestones
1. Week 1: Nix eval to JSON bridge + basic AST parser
2. Week 2: Module dependency extraction from flake outputs
3. Week 3: Graph data structure and D3.js rendering
4. Week 4: Interactive features (click, filter, zoom)
5. Week 5: Markdown documentation generator
6. Week 6: VS Code extension or CLI wrapper for adoption
