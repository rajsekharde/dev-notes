
Running using Docker Compose:


Define new service in docker-compose.yml:

services:
  database:
    image: postgres:15 # Use an older, stable base image
    container_name: postgres_db
    ports:
      - "5432:5432"
    environment:
      POSTGRES_USER: ${POSTGRES_USER} # Automatically imported from .env file in same directory
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
      POSTGRES_DB: ${POSTGRES_DB}
    volumes:
      - pgdata:/var/lib/postgresql/data # Volume mount for persistent storage
    networks:
      - app-network # Use the custom network app-network
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U ${POSTGRES_USER} -d ${POSTGRES_DB}"] # Checks if db is ready to accept connections
      interval: 10s # Performed every 10 seconds
      timeout: 5s # Command has a 5-sec timeout to complete
      retries: 5 # Healthcheck will be considered failed after 5 unsuccessful attempts
      start_period: 5s # Gives the container 5 secs before the healthcheck starts running

volumes:
  pgdata: # Define a volume

networks:
  app-network:
    driver: bridge # Define a custom network with the bridge network driver


Run: docker compose up --build -d

** Only defining POSTGRES_PASSWORD in environment is enough to run postgres on docker


Access PostgreSQL inside Docker: docker exec -it <container_name> psql -U <username> -d <db_name>

Exit psql: \q

List tables: \dt

Describe a table (view columns and types): \d table_name
