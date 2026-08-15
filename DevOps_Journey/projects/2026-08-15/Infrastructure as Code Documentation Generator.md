# Infrastructure as Code Documentation Generator

## Overview
A tool that automatically generates documentation from Terraform, Pulumi, or CDK infrastructure code using AI.

## Architecture
```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  IaC Code   │     │  Parser     │     │  Documentation│
│  (TF, Pulumi│────▶│  (AST/JSON) │────▶│  Generator  │
│   , CDK)    │     └─────────────┘     └─────────────┘
└─────────────┘            │                    │
        │           ┌───────────┐       ┌───────────┐
        │           │  AI       │       │  Template │
        │           │  Enhancer │       │  Engine   │
        └───────────▶│           │──────▶│           │
                    └───────────┘       └───────────┘
```

## Workflow
1. **Parse**: Extract infrastructure components from code
2. **Analyze**: Understand dependencies and relationships
3. **Enrich**: Use LLM to add context and explanations
4. **Generate**: Create documentation in multiple formats
5. **Publish**: Output to Markdown, HTML, or Confluence

## Tools
- Terraform / Pulumi / CDK
- Python with LLM integration
- Markdown / HTML generators
- Git for version control
- ReadTheDocs or Docusaurus for hosting

## Learning Goals
- Master IaC documentation practices
- Learn code parsing and AST manipulation
- Practice AI-assisted documentation
- Understand infrastructure architecture

## Build Milestones
1. **M1**: Basic Terraform documentation generator
2. **M2**: Add Pulumi and CDK support
3. **M3**: Integrate AI for contextual enrichment
4. **M4**: Support multiple output formats
5. **M5**: Add dependency visualization
6. **M6**: Implement auto-update on code changes
