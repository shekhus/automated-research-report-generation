**AI-powered system for automated collection, analysis, and generation of structured research reports**

This project implements an automated pipeline that leverages large language models (LLMs) to perform in-depth research on a given topic 
and produce comprehensive, well-structured reports. It is designed to reduce manual effort in literature review, data synthesis, and report
drafting phases commonly required in academic, professional, or industry research workflows.

## Key Features (Inferred & Planned)

- Topic-based research initiation via command-line or configuration
- Multi-agent architecture for task decomposition (researcher, analyst, writer, reviewer, etc.)
- Web search integration, content extraction, and synthesis using LLMs
- Structured report generation (introduction, methodology, findings, conclusions, references)
- Support for iterative refinement and quality control steps
- Modular design allowing easy swapping of LLM providers and tools
- Environment variable configuration for API keys and model selection
- Jupyter Notebook support for experimentation and result visualization

## Tech Stack

| Layer                | Technology                          |
|----------------------|-------------------------------------|
| Language             | Python 3.10+                        |
| Project Management   | pyproject.toml (likely Hatch/PDM/Poetry) |
| Dependencies         | requirements.txt                    |
| LLM Orchestration    | Likely LangChain, CrewAI, AutoGen, or custom agents (see `research_and_analyst/`) |
| Environment          | .env file for secrets               |
| Experimentation      | Jupyter Notebooks (~93% of codebase) |
| Entry Point          | main.py                             |
| Utilities            | get_lib_versions.py (dependency diagnostics) |

## Quick Start

### Prerequisites

- Python 3.10 or higher (see `.python-version`)
- Git
- API key(s) for at least one LLM provider (Groq, OpenAI, Anthropic, Google Gemini, etc.)

### Local Setup

```bash
# 1. Clone the repository
git clone https://github.com/shekhus/automated-research-report-generation.git
cd automated-research-report-generation

# 2. (Recommended) Create virtual environment
python -m venv .venv
source .venv/bin/activate    # Linux/macOS
# or .venv\Scripts\activate   # Windows

# 3. Install dependencies
pip install -r requirements.txt

# Alternative: if using Poetry / PDM / Hatch (check pyproject.toml)
# poetry install
# pdm install
# hatch env create

# 4. Configure environment variables
cp .env.copy .env
# Edit .env and add required keys, for example:
# GROQ_API_KEY=gsk_...
# OPENAI_API_KEY=sk-...
# ANTHROPIC_API_KEY=sk-ant-...
# GOOGLE_API_KEY=...
# DEFAULT_LLM_PROVIDER=groq
# DEFAULT_MODEL=gemma2-9b-it   (or llama3-70b-8192, claude-3-5-sonnet, etc.)

# 5. Run the main pipeline
python main.py --topic "Impact of large language models on scientific publishing" --output-dir ./reports
# → Adjust flags/parameters according to actual implementation in main.py
Development & Experimentation
Many core experiments and prototypes are implemented in Jupyter Notebooks (located in the repository root or subfolders). To explore:
Bashjupyter notebook
# or
jupyter lab
Open notebooks to inspect agent definitions, prompt chains, tool usage, and intermediate outputs.
Project Structure
textautomated-research-report-generation/
├── research_and_analyst/       Core logic: agents, tools, workflows, prompts
├── .env.copy                   Environment variable template
├── .gitignore
├── .python-version             Python version pin
├── README.md
├── get_lib_versions.py         Utility to print installed package versions
├── main.py                     Primary entry point / CLI runner
├── pyproject.toml              Project metadata & modern dependency config
├── requirements.txt            Pin-compatible dependencies
└── *.ipynb                     Jupyter notebooks for research & prototyping (majority of code)
Configuration (.env)
env# LLM configuration (at least one required)
GROQ_API_KEY=your_groq_key_here
# OPENAI_API_KEY=sk-...
# ANTHROPIC_API_KEY=...
# GOOGLE_API_KEY=...

# Optional / defaults
DEFAULT_LLM_PROVIDER=groq
DEFAULT_MODEL=gemma2-9b-it
TEMPERATURE=0.3
MAX_TOKENS=8192
OUTPUT_FORMAT=markdown     # or pdf, docx, html (if implemented)
Current Status

Repository is under active development.
No released versions or packages yet.
Primarily Python with heavy Jupyter usage for iterative experimentation.

Contributing
Contributions are welcome.

Fork the repository
Create a feature branch (git checkout -b feature/report-section-reviewer)
Commit changes (git commit -m 'Add critic agent for report coherence')
Push to the branch (git push origin feature/report-section-reviewer)
Open a Pull Request

License
MIT License (recommended — add a LICENSE file if not already present)

This project aims to accelerate high-quality research output by automating tedious synthesis and writing tasks while preserving human oversight for final validation. Adjustments to this README should be made as implementation details (agent roles, supported output formats, CLI arguments, etc.) become more explicit in the codebase.
