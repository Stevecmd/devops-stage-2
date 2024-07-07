# # Use an official Python runtime as the base image
# FROM python:3.10-slim-buster

# ENV PYTHONDONTWRITEBYTECODE 1
# ENV PYTHONUNBUFFERED 1

# RUN apt-get update && apt-get install -y \
#     libpq-dev \
#     && apt-get clean

# WORKDIR /app

# # Set PYTHONPATH environment variable
# ENV PYTHONPATH=/app

# # Install Poetry
# RUN pip install poetry

# # Copy pyproject.toml and poetry.lock to the working directory
# COPY pyproject.toml poetry.lock ./

# # Install dependencies
# RUN poetry config virtualenvs.create false \
#     && poetry install --no-dev --no-interaction --no-ansi

# # Copy the rest of the application code to the working directory
# COPY . .

# # Make prestart.sh executable
# RUN chmod +x /app/prestart.sh

# # Expose backend port
# EXPOSE 8000

# # Run the backend server
# ENTRYPOINT ["bash", "/app/prestart.sh"]
# CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]

FROM python:3.10-slim

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
ENV PYTHONPATH "${PYTHONPATH}:/app"

RUN apt-get update && apt-get install -y \
    libpq-dev

WORKDIR /app

RUN pip install poetry
COPY pyproject.toml poetry.lock /app/
RUN poetry config virtualenvs.create true \
    && poetry install --no-dev --no-interaction --no-ansi

COPY . /app/

RUN chmod +x /app/prestart.sh

EXPOSE 8000

ENTRYPOINT ["poetry", "run", "bash", "-c", "/app/prestart.sh && uvicorn app.main:app --host 0.0.0.0 --port 8000"]
