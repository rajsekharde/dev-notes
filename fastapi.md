### Running using docker compose

**Dockerfile**:

FROM python:3.11-slim # Start from the official Python base image

WORKDIR /code # Set the current working directory to /code. This is where we'll put the requirements.txt file and the app directory

COPY . . # Copy full backend root directory

RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt # Install dependencies without storing them locally

COPY ./src /code/src # Copy the ./src directory inside the /code directory

EXPOSE 8000 # Container will listen on port 8000

CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"] # Command to run the fastapi app


Project structure:

backend/

-src/

--__init__.py

--main.py

-Dockerfile

-requirements.txt

docker-compose.yml


Running app without docker compose:

Build the container:

docker build -t app . # In the same directory as the Dockerfile

Run the container:

docker run -p 8000:8000 app

Stop the container:

docker stop <container-id>


**docker-compose.yml**:

services:
  api:
    build:
      context: ./backend # directory where the Dockerfile is located
      dockerfile: Dockerfile # Explicitly specify the Dockerfile (Optional if named Dockerfile)
    ports:
      - "8000:8000" # port mapping: host_port:container_port
    volumes:
      - ./backend/src:/code/src # sync local and container code
    environment:
      - ENV=development # sets environment variables

Running the app:

docker compose up --build -d

Stopping the app:

docker compose down

