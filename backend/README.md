# Backend - FastAPI with PostgreSQL

This directory contains the backend of the application built with FastAPI and a PostgreSQL database.

## Prerequisites

- Python 3.8 or higher
- Poetry (for dependency management)
- PostgreSQL (ensure the database server is running)

### Installing Poetry

To install Poetry, follow these steps:

```sh
curl -sSL https://install.python-poetry.org | python3 -
```

Add Poetry to your PATH (if not automatically added):

## Setup Instructions

1. **Navigate to the backend directory**:
    ```sh
    cd backend
    ```

2. **Install dependencies using Poetry**:
    ```sh
    poetry install
    ```

3. **Set up the database with the necessary tables**:
    ```sh
    poetry run bash ./prestart.sh
    ```

4. **Run the backend server**:
    ```sh
    poetry run uvicorn app.main:app --reload
    ```

5. **Update configuration**:
   Ensure you update the necessary configurations in the `.env` file, particularly the database configuration.

## Extra

6. **Convert Bash files to CRLF to fix line endings**:
```sh
dos2unix *.sh
```

7. Reduce use of resources
Once Docker has been setup, you might use `docker-compose build --no-cache` followed by `docker-compose up` when you've made <br />
significant changes to your Docker images or configurations and want to ensure that you're starting <br />
fresh without any cached layers affecting the build process. <br />
`--no-cache:` - This flag tells Docker Compose to build the images without using any cached layers.
```sh

docker-compose build --no-cache
docker-compose up

```