# Use the official Python image as a base image
FROM python:3.12.3

# Set the working directory
WORKDIR /app

# Install Poetry
ENV POETRY_HOME=/opt/poetry
RUN curl -sSL https://install.python-poetry.org | python3 - && \
    $POETRY_HOME/bin/pip install poetry && \
    ln -s $POETRY_HOME/bin/poetry /usr/local/bin/poetry

# Add Poetry to PATH
ENV PATH="${POETRY_HOME}/bin:$PATH"

# Copy the requirements file into the container
COPY pyproject.toml poetry.lock* /app/

# Install dependencies
RUN poetry config virtualenvs.create false && poetry install --no-dev

# Copy the rest of the application code
COPY . /app

# Expose the backend port
EXPOSE 8000

# Run the application
CMD ["poetry", "run", "uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
