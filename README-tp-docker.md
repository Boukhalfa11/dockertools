# Requirements to run the project:

- Have Docker and docker-compose installed.

# Build the project:
- Clone the repository.
- Run `docker-compose up -d` to launch the 3 services as follow:

```
184503366bde   dockertools_httpd      "httpd-foreground"       5 seconds ago        Up 4 seconds    0.0.0.0:8000->80/tcp, :::8000->80/tcp       dockertools_httpd_1
ef6ff9ce2a04   dockertools_backend    "java -jar simple-ap…"   6 seconds ago        Up 4 seconds    0.0.0.0:8080->8080/tcp, :::8080->8080/tcp   backendapi
328fd52c2872   dockertools_database   "docker-entrypoint.s…"   About a minute ago   Up 32 seconds   0.0.0.0:5432->5432/tcp, :::5432->5432/tcp   dockertools_database_1
```

To access the server, navigate to `http://localhost:8000` 

# Content of the project

This project contains three services:

- **Backend Service:** This service manages the backend logic of the application. Built using Spring Boot and Java, it handles API requests and interacts with the database.
- **Database Service:** Responsible for database operations, this service utilizes the PostgreSQL relational database.
- **Reverse Proxy Service:** This service routes requests to the appropriate service and is implemented using Apache Server.


# Answering questions
1.Why should we run the container with a flag -e to give the environment variables?

--> We need to use the -e flag to pass environment variables to the container because these variables are used to configure the container at runtime. By using the -e flag, we can ensure the container is set up with the correct settings for the application.

2. When we talk about /docker-entrypoint-initdb.d it means inside the container, so you have to copy your directory's content and the container’s directory.

--> The docker-entrypoint-initdb.d directory is used to initialize the database when the container starts. The scripts in this directory are executed at container startup and are used to create the database schema and populate the database with data.

3. Why do we need a volume to be attached to our postgres container?

--> We need to attach a volume to the PostgreSQL container to persist the data. Without a volume, the data stored in the container is lost when the container is stopped or removed. By attaching a volume, we can store the data on the host machine, ensuring it persists even if the container is stopped or removed.

4. Why do we need a multistage build?

--> We need a multistage build to reduce the size of the final image. In a multistage build, multiple stages are used to build the application, and only the necessary files from the previous stages are copied to the final stage. This approach allows us to minimize the final image size by including only the essential files and dependencies.

5. Why do we need a reverse proxy?

--> We need a reverse proxy to route requests to the appropriate service. A reverse proxy can load balance requests across multiple instances of a service, route requests to different services based on the request path, and provide SSL termination. Additionally, it can offer enhanced security features such as rate limiting, request filtering, and authentication.

6. Why is docker-compose so important?

--> Docker-compose simplifies the deployment of multi-container Docker applications by defining services, networks, and volumes in a single file. It allows easy management of application lifecycle tasks like building, starting, stopping, and scaling containers, providing a consistent and efficient way to work with Docker.

7. What ```mvn clean verify```is it supposed to do?

--> mvn clean verify is a Maven command that cleans the project by removing the target directory, compiles the source code, runs tests to validate functionality, and packages the application into a JAR file. It's typically used to ensure the application is built correctly and passes tests before deployment to production.

8. Unit tests? Component tests? Integration tests?

- Unit tests: Test individual units or components in isolation, fast and focused on specific functionality.
- Component tests: Test interactions between components, ensuring integration and cooperation.
- Integration tests: Test end-to-end functionality and interactions with external systems, validating application behavior in a real-world scenario.

9. What are testcontainers?

--> Testcontainers is a Java library that simplifies testing by enabling developers to create and manage lightweight Docker containers seamlessly within their tests. It offers a straightforward and unified method to test applications interacting with external systems or services. This capability is particularly beneficial for testing databases, message brokers, web services, and other external dependencies, ensuring thorough testing in environments closely resembling production setups.

10. Secured Variables in Github, why?

--> Securing variables in GitHub is crucial to prevent sensitive information like API keys and passwords from being exposed to unauthorized access, ensuring the application's security and integrity.