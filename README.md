# Central Memory App and MCP Server

## Problem

Let's face the harsh truth. Prompts, instructions, and AI-related memory were scattered everywhere. Some lived in notebooks, some in random documents, and others were tucked away in code comments. Every time we wanted to evaluate or reuse a prompt, it felt like searching for a needle in a haystack. Even worse, different projects and different AI providers used slightly different versions of the same instruction — creating inconsistencies and frustration. What should have been a shared knowledge base was instead fragmented across silos.

## Solution

The idea was simple: what if there was **one central place** where all prompts, instructions, and memories lived? A system where each memory could be stored, read, updated, or deleted, and where the structure was clear and transparent. Thus, the **Central Memory App** was born. Built on **FastAPI** and designed to also serve as an **MCP server**, it would act as both a storage hub and a distribution center for AI knowledge.

Instead of being buried in code or hidden in notebooks, memories would live in `app/data/<dir>`, saved in markdown format. Easy to filter, easy to validate. And because the system runs in Docker with volume binding, users could manage the files directly — or through clean, well-defined API endpoints.

## Key Features

* CRUD endpoints to manage prompts and memories.
* Hierarchical storage in markdown for human readability.
* Docker volume binding for flexible file management.
* MCP server integration to expose instructions globally across AI assistants.
* Designed for consistency, transparency, and reusability.

## Value Proposition

This app is more than just a memory bank — it’s about **restoring order to chaos**. By centralizing prompts and instructions:

* Developers and AI engineers gain a **single source of truth**.
* Prompts can be **validated and tested** without guesswork.
* Knowledge can be **reused across projects** and even across different AI coding providers.
* Custom instructions (e.g., telling an AI coding assistant what to do when a user types `/draft-release`) can be **defined once and reused across different codebases**, thanks to MCP server integration.
* Markdown’s simple, hierarchical nature makes it easy for humans to read and for LLMs to consume.

It’s not a heavy enterprise knowledge system. It’s lightweight, pragmatic, and focused: a tool for today’s needs.

## Target Users

* **AI engineers** looking for consistency in experiments.
* **Developers** tired of chasing scattered prompts.
* **Organizations** seeking lightweight knowledge management.
* **AI toolchains** that benefit from MCP-exposed memories.

## Differentiation

This isn’t about building the next massive platform. Instead, it’s about **making the simple powerful**:

* Unlike random prompt files, this system enforces structure.
* Unlike complex knowledge bases, it stays markdown-simple.
* Unlike embedding-only stores, it keeps content human-readable and auditable.

## Architecture in Story

Think of the Central Memory App as a **library**. Each markdown file is a book, carefully placed on the right shelf (`app/data/<dir>`). FastAPI is the **librarian**, handling requests to borrow, update, or add new books. Docker ensures the library is portable but permanent — the shelves come with the building. And the MCP server acts like a **loudspeaker**, broadcasting instructions to every assistant in the building, so no matter where you are, you can access the same reliable knowledge.

## Why Now

Because the more we build with AI, the more we realize that **context is everything**. Without structure, we waste time reinventing the same instructions, debugging the same inconsistencies, and duplicating knowledge that should have been shared. The Central Memory App is a step toward making AI development not just smarter, but more **organized, consistent, and collaborative**.


## Technologies Used
- **Programming Language**: Python 3.11+
- **Web Framework**: FastAPI (for API development, asynchronous handling, and Pydantic for data validation)
- **ASGI Server**: Hypercorn
- **Dependency Management**: `uv`
- **Configuration**: `pydantic-settings` for `.env` file parsing.

## Development Setup

### Prerequisites
- Python 3.11 or higher
- Docker and Docker Compose (for containerized development)

### Local Development (without Docker)
1.  **Clone the repository**:
    ```bash
    git clone https://github.com/mta-tech/central-memory.git -b main
    cd central-memory
    ```
2.  **Initialize Python environment with `uv`**:
    ```bash
    uv venv .venv
    ```
3.  **Install dependencies**:
    ```bash
    uv sync
    ```
4.  **Create environment file**:
    Copy `.env.example` to `.env` and configure your LLM API keys and other settings.
    ```bash
    cp .env.example .env
    ```
5.  **Run the application**:
    ```bash
    python manage.py
    ```
    The application will be accessible at `http://localhost:8000`.

### Docker Setup (Recommended)
For a consistent development environment, use Docker Compose.

1.  **Build the Docker image**:
    ```bash
    docker-compose build
    ```
2.  **Create environment file**:
    Copy `.env.example` to `.env` in the root directory and configure your LLM API keys and other settings.
    ```bash
    cp .env.example .env
    ```
3.  **Run the application using Docker Compose**:
    ```bash
    docker-compose up
    ```
    This will start the FastAPI application in a container. The application will be accessible at `http://localhost:8000`. Changes to the codebase will be reflected automatically due to volume mounting.

## API Endpoints


## Contributing
Contributions are welcome! Please refer to the project's guidelines for more information.
