# Configuration Management System

## Overview

This FastAPI application provides a robust and scalable system to manage configuration requirements for onboarding organizations from various countries. It supports CRUD (Create, Read, Update, Delete) operations for managing these configurations, ensuring flexibility to handle country-specific onboarding requirements.

## Features

- Create Configuration: Define and store onboarding requirements for a country.
- Get Configuration: Retrieve the onboarding requirements for a specific country.
- Update Configuration: Modify the onboarding requirements for a country.
- Delete Configuration: Remove the onboarding requirements for a country.
- Database Interaction: Uses PostgreSQL with SQLAlchemy ORM for database interactions.
- API Documentation: Automatically generated interactive API documentation.
- Error Handling: Comprehensive error handling using FastAPI's built-in exception mechanisms.

## Advanced Features

- Duplicate Configuration Handling:
  Add error handling to detect and handle duplicate configurations gracefully, providing informative error messages to the user.

- Partial Update:
  Modify the update endpoint to support partial updates, allowing users to update only the fields they specify.

- Validation Errors:
  Implement data validation using Pydantic models to ensure that input data conforms to expected formats and constraints, providing informative error messages for validation failures.

- Concurrency Control:
  Implement concurrency control mechanisms such as optimistic locking or versioning to prevent conflicts and ensure data consistency.

- Logging and Monitoring:
  Integrate logging frameworks (e.g., Python's logging module) to log important events and errors, and set up monitoring tools to track application performance and health metrics.

## Getting Started

## Prerequisites

- Python 3.8+
- PostgreSQL
- pip (Python package installer)

## Installation

    1. Clone the repository:

```bash
  git clone https://github.com/yourusername/config_management.git
cd config_management
```

    2. Create and activate a virtual environment:

```bash
  python -m venv env
source env/bin/activate  # On Windows use `env\Scripts\activate`
```

    3. Install the dependencies:

```bash
  pip install -r requirements.txt
```

    4. Configure the environment variables:

```bash
DATABASE_URL=postgresql://user:password@localhost/dbname
pip install -r requirements.txt
```

    5. Initialize the database:

```bash
 alembic upgrade head
```

## Running the Application

Use Uvicorn to run the FastAPI application:

```bash
 alembic upgrade head
```

The application will be available at http://127.0.0.1:8000.

## API Reference

#### Create Configuration

```http
  POST /create_configuration
```

| Parameter      | Type     | Description                                        |
| :------------- | :------- | :------------------------------------------------- |
| `country_code` | `string` | **Required**.Country code (ISO 3166-1 alpha-2)     |
| `Requirements` | `List  ` | **Required**. List of requirements for the country |

#### Get Configuration

```http
  GET /get_configuration/{country_code}
```

| Parameter      | Type     | Description                         |
| :------------- | :------- | :---------------------------------- |
| `country_code` | `string` | **Required**. Country code to fetch |

#### Update Configuration

```http
  POST /update_configuration

```

| Parameter      | Type     | Description                          |
| :------------- | :------- | :----------------------------------- |
| `country_code` | `string` | **Required**. Country code to update |
| `Requirements` | `List  ` | **Required**. Updated requirements   |

### Delete Configuration

```http
  DELETE /delete_configuration/{country_code}
```

| Parameter      | Type     | Description                          |
| :------------- | :------- | :----------------------------------- |
| `country_code` | `string` | **Required**. Country code to delete |

## Tech Stack

**Client:** None specified (the application is server-side only)

**Server:**

- FastAPI: A modern, fast (high-performance), web framework for building APIs with Python 3.7+ based on standard Python type hints.
- SQLAlchemy: SQL toolkit and Object-Relational Mapping (ORM) library for Python.
- PostgreSQL: A powerful, open source object-relational database system.
- Pydantic: Data validation and settings management using Python type annotations.
- Uvicorn: A lightning-fast ASGI server implementation, using `uvloop` and `httptools`.

**Additional Tools:**

- Alembic: A lightweight database migration tool for use with SQLAlchemy.
- Python Logging: Standard Python module for logging application events and errors.
- dotenv: Loads environment variables from a .env file.
