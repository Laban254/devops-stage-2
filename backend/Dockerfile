# Use the latest official Python image as a base
FROM python:latest

# Install Poetry using pip
RUN pip install poetry uvicorn

# Set the working directory
WORKDIR /app

# Copy the application files
COPY . .

# Install dependencies using Poetry
RUN poetry install

# Expose the port FastAPI runs on
EXPOSE 80

# Run the prestart script and start the server
CMD ["sh", "-c", "poetry run bash ./prestart.sh && poetry run uvicorn app.main:app --host 0.0.0.0 --port 80 --reload"]