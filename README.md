<div align="center">
  <img src="logo.png" alt="sandbox-fastapi" width="512"/>

  [![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/)
  [![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-00a393.svg)](https://fastapi.tiangolo.com/)
  [![SQLModel](https://img.shields.io/badge/SQLModel-ORM-orange.svg)](https://sqlmodel.tiangolo.com/)
  [![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

  **⚡ A simple REST API demonstrating CRUD operations using FastAPI and SQLModel with SQLite persistence 🗃️**

  [API Docs](http://localhost:8000/docs) · [ReDoc](http://localhost:8000/redoc)
</div>

## Overview

sandbox-fastapi is a minimal, single-file REST API that showcases how to build CRUD operations with FastAPI and SQLModel. It uses SQLite for persistence, making it perfect for learning, prototyping, or as a starting point for larger projects.

## Features

- **Complete CRUD operations** - Create, read, update, and delete items via REST endpoints
- **SQLModel ORM** - Type-safe database models that work seamlessly with FastAPI
- **SQLite persistence** - Zero-configuration database that stores data in a local file
- **Auto-generated docs** - Interactive Swagger UI and ReDoc documentation out of the box
- **Dependency injection** - Clean database session management using FastAPI's DI system

## Quick Start

```bash
# Activate the conda environment
source activate-env.sh

# Start the development server
fastapi dev main.py
```

The API will be available at `http://localhost:8000`

## Installation

### Prerequisites

- [Miniconda](https://docs.conda.io/en/latest/miniconda.html) or [Anaconda](https://www.anaconda.com/)

### Setup

```bash
# Clone the repository
git clone https://github.com/tsilva/sandbox-fastapi.git
cd sandbox-fastapi

# Run the environment setup script
source activate-env.sh
```

The setup script automatically:
- Detects if Miniconda is installed
- Creates the conda environment from `environment.yml` if needed
- Activates the `sandbox-fastapi` environment

## API Reference

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | Root endpoint, returns hello world |
| `POST` | `/items/` | Create a new item |
| `GET` | `/items/` | List all items |
| `GET` | `/items/{item_id}` | Get a specific item by ID |
| `PUT` | `/items/{item_id}` | Update an existing item |
| `DELETE` | `/items/{item_id}` | Delete an item |

### Item Schema

```json
{
  "id": 1,
  "name": "Example Item",
  "price": 9.99,
  "is_offer": false
}
```

## Usage Examples

### Create an Item

```bash
curl -X POST "http://localhost:8000/items/" \
  -H "Content-Type: application/json" \
  -d '{"name": "Widget", "price": 19.99, "is_offer": true}'
```

### List All Items

```bash
curl "http://localhost:8000/items/"
```

### Get a Specific Item

```bash
curl "http://localhost:8000/items/1"
```

### Update an Item

```bash
curl -X PUT "http://localhost:8000/items/1" \
  -H "Content-Type: application/json" \
  -d '{"name": "Updated Widget", "price": 24.99}'
```

### Delete an Item

```bash
curl -X DELETE "http://localhost:8000/items/1"
```

## Project Structure

```
sandbox-fastapi/
├── main.py           # FastAPI application with all endpoints
├── environment.yml   # Conda environment dependencies
├── activate-env.sh   # Environment setup script
├── items.db          # SQLite database (created on first run)
└── README.md
```

## Dependencies

- **Python 3.11**
- **FastAPI** - Modern web framework for building APIs
- **SQLModel** - SQL databases in Python with type hints
- **python-dotenv** - Environment variable management
- **asyncer** - Async utilities

## License

MIT
