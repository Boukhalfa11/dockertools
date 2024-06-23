FROM postgres:14.1-alpine

# Environment variables
ENV POSTGRES_DB=db \
   POSTGRES_USER=boukha \
   POSTGRES_PASSWORD=root

# Copy the SQL files to the container
COPY ./createScheme.sql /docker-entrypoint-initdb.d/createScheme.sql

COPY ./insertData.sql /docker-entrypoint-initdb.d/insertData.sql