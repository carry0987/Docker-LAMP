FROM arm64v8/mysql:latest

# Copy the shell script into the Docker container
COPY setup.sh /docker-entrypoint-initdb.d/setup.sh

# Make the script executable
RUN chmod +x /docker-entrypoint-initdb.d/setup.sh
