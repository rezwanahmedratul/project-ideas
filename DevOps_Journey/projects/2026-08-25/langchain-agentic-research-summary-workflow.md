# Project: LangChain Agentic Workflow for Automated Research Summaries

## Overview
Build a Python-based AI agent using LangChain that autonomously searches the web for research papers on a given topic, extracts key findings, and generates a structured markdown report. Includes tool-use (search, read), memory, and configurable output templates.

## Architecture / Structure
```
┌─────────────────────────────────────────────────────┐
│  User Prompt                                        │
│  "Research: latest advances in reinforcement        │
│   learning for robotics, 2026"                      │
├─────────────────────────────────────────────────────┤
│  LangChain Agent (OpenAI Functions)                 │
│  ┌───────────────────────────────────────────────┐  │
│  │  Tools:                                       │  │
│  │  ├── web_search    (Tavily / Serper API)      │  │
│  │  ├── fetch_url     (read_page content)        │  │
│  │  └── write_report  (save .md file)            │  │
│  └───────────────────────────────────────────────┘  │
│       │    │    │                                  │
│       ▼    ▼    ▼                                   │
│  [Search] → [Fetch] → [Synthesize] → [Output]       │
│       │                                         │
│  ┌────▼────────────────────────────────────┐     │
│  │  Memory: ConversationBufferWindow       │     │
│  │  (last N interactions for context)      │     │
│  └─────────────────────────────────────────┘     │
├─────────────────────────────────────────────────────┤
│  Output                                             │
│  └── research_summary_<topic>.md                   │
│      ├── Executive Summary                          │
│      ├── Key Papers (with links)                    │
│      ├── Methodology Highlights                     │
│      └── Open Questions                             │
└─────────────────────────────────────────────────────┘
```

## Workflow
1. Install LangChain, langchain-openai, tavily-python, beautifulsoup4
2. Define agent tools: `web_search` (returns snippet results), `fetch_url` (extracts page text), `write_report` (saves to file)
3. Set up LLM chain with `ChatOpenAI` and function-calling agents
4. Configure system prompt with role: "expert research analyst"
5. Add conversation memory (`ConversationBufferMemory`) to maintain context
6. Test with a topic; iterate until output quality meets standards
7. Wrap in a CLI: `python research_agent.py --topic "quantum error correction"`
8. Add optional: parse PDF URLs and extract arxiv abstracts

## Tools
- **Python 3.12**
- **LangChain** + **langchain-openai**
- **Tavily API** or **Serper.dev** (web search)
- **BeautifulSoup4** (HTML parsing)
- **tiktoken** (token counting / cost estimation)
- **typer** or **click** (CLI framework)

## Learning Goals
- LangChain agent architectures (ReAct, OpenAI Functions)
- Tool definition and function calling with LLMs
- Conversation memory patterns
- Structured output generation from unstructured web data
- CLI design for AI-powered workflows
- Token cost estimation and budget tracking

## Build Milestones
1. [ ] Set up Python project with Poetry; install LangChain deps
2. [ ] Implement `web_search` and `fetch_url` tools
3. [ ] Build agent loop with ReAct pattern; test on simple topic
4. [ ] Add memory to track conversation history
5. [ ] Create structured output template (markdown sections)
6. [ ] Build CLI with `typer`; accept `--topic` and `--output-dir`
7. [ ] Add PDF/arxiv handling for paper-focused topics
8. [ ] Implement token usage logging and cost reporting

## References
- https://python.langchain.com/docs/agents/
- https://python.langchain.com/docs/integrations/tools/tavily_search
