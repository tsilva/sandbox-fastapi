# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A simple REST API demonstrating CRUD operations using FastAPI and SQLModel with SQLite persistence. The entire application is contained in a single `main.py` file with an `Item` model.

## Environment Setup

The project uses Conda for environment management:

```bash
source activate-env.sh
```

This script:
- Detects if Miniconda is installed
- Creates the conda environment from `environment.yml` if it doesn't exist
- Activates the `sandbox-fastapi` environment

Dependencies are managed via `environment.yml` which includes:
- Python 3.11
- FastAPI with standard extras
- SQLModel for database ORM
- python-dotenv and asyncer

## Running the Application

Start the development server:

```bash
fastapi dev main.py
```

The API will be available at:
- Base URL: `http://localhost:8000`
- Interactive docs (Swagger): `http://localhost:8000/docs`
- Alternative docs (ReDoc): `http://localhost:8000/redoc`

## Architecture

**Single-file application** (`main.py`):
- `Item` model: SQLModel class with `id`, `name`, `price`, and `is_offer` fields
- Database: SQLite (`items.db`) with SQLModel/SQLAlchemy
- Session management: `get_session()` dependency provides database sessions
- Database initialization: Tables created on app startup via `on_startup` event

**Endpoints**:
- `GET /` - Root endpoint
- `POST /items/` - Create item
- `GET /items/` - List all items
- `GET /items/{item_id}` - Get specific item
- `PUT /items/{item_id}` - Update item (partial updates supported)
- `DELETE /items/{item_id}` - Delete item

All endpoints use dependency injection (`Depends(get_session)`) for database access.

## Important Notes

- README.md must be kept up to date with any significant project changes
- The SQLite database file (`items.db`) is created automatically on first run
- The application uses FastAPI's dependency injection system for database session management
