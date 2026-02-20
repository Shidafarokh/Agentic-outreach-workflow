# Email Project - Streamlit Dashboard + LangGraph Multi-Agent

A multi-agent email generation system with LangChain, LangGraph, and Streamlit dashboard.

## Setup Instructions

### 1. Prerequisites
- Python 3.10+
- [uv](https://github.com/astral-sh/uv) package manager (install globally first)

### 2. Initialize the Project with uv

Run these commands in the project root directory:

```bash
# Create a virtual environment and install dependencies
uv venv

# Activate the virtual environment
# On Windows:
.venv\Scripts\activate
# On macOS/Linux:
source .venv/bin/activate

# Install dependencies from pyproject.toml
uv pip install -e .

# (Optional) Install dev dependencies
uv pip install -e ".[dev]"
```

### 3. Environment Setup

Create a `.env` file in the project root:

```
OPENAI_API_KEY=your_key_here
# Add other API keys as needed
```

### 4. Project Structure

```
EMAIL-PROJECT/
├── src/
│   ├── app.py              # Main Streamlit application
│   ├── agents/
│   │   ├── __init__.py
│   │   └── agent_graph.py  # LangGraph multi-agent system
│   ├── storage/
│   │   ├── __init__.py
│   │   └── application_storage.py  # JSON tracker
│   ├── ui/
│   │   ├── __init__.py
│   │   ├── dashboard_tab.py
│   │   ├── email_generator_tab.py
│   │   └── about_tab.py
│   └── utils/
│       ├── __init__.py
│       └── config.py
├── data/
│   └── applications.json   # JSON storage with tracked applications
├── pyproject.toml          # uv project configuration
├── .env                    # Environment variables (not committed)
└── README.md
```

### 5. Run the Application

```bash
streamlit run src/app.py
```

## Dependencies

- **Streamlit**: Web UI framework
- **LangChain**: >=1.2.0 for agent framework
- **LangGraph**: Multi-agent orchestration
- **Requests**: HTTP client
- **Selenium**: Optional web scraping
- **python-dotenv**: Environment variable management

## Storage Schema

All applications are stored in `data/applications.json` with the following structure:

```json
{
  "applications": [
    {
      "id": "uuid",
      "person_name": "string",
      "university_name": "string",
      "status": "draft|sent|error",
      "created_at": "ISO 8601 timestamp",
      "sent_at": "ISO 8601 timestamp or null",
      "tone_choice": "professional|casual|formal",
      "drafts": ["draft1", "draft2", "draft3"],
      "selected_draft_index": 0,
      "final_email_text": "string or null",
      "last_error": "string or null"
    }
  ]
}
```

## Development

### Run tests
```bash
pytest
```

### Format code
```bash
black src/
```

### Lint code
```bash
ruff check src/
`
