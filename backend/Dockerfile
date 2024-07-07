# Use the official Python image as a base image
FROM python:3.12.3

# Set the working directory
WORKDIR /app

# Copy the requirements file into the container
COPY pyproject.toml poetry.lock* /app/

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 - && \
    poetry config virtualenvs.create false && \
    poetry install --no-dev

# Copy the rest of the application code
COPY . /app

# Expose the backend port
EXPOSE 8000

# Run the application
CMD ["poetry", "run", "uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
