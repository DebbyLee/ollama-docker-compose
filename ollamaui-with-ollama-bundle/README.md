# Docker Compose Setup for Ollama-WebUI with Ollama bundle
This repository provides a Docker Compose setup for running Ollama-webui. Ollama-webui provides a web user interface for the application and come with Ollama bundle

### Prerequisites
Make sure you have Docker and Docker Compose installed on your machine.

[Docker Installation Guide](https://docs.docker.com/engine/install/)
[Docker Compose Installation Guide](https://docs.docker.com/compose/reference/)

### Getting Started
Follow these steps to get the services up and running:

1. Clone the Repository
```
git clone <repository-url>
cd <repository-directory>
```
2. Start the Services
Use Docker Compose to start the services:

```
docker-compose up -d
```
This command will start both ollama and ollama-webui services in detached mode.

### Services
Ollama
- Image: ollama/ollama
- Ports: 11434:11434
- Volumes: ollama:/root/.ollama
- Restart Policy: Always
Ollama-WebUI
- Image: ghcr.io/ollama-webui/ollama-webui:main
- Ports: 3000:8080
- Extra Hosts: host.docker.internal:host-gateway
- Volumes: ollama-webui:/app/backend/data
- Restart Policy: Always


### Pull the images
Find the libray that you would like to pull from [Ollama library](https://ollama.com/library)
Assuming that you would like to pull llama3.1
1. Pull from Ollama UI via http://localhost:3000
2. Using docker exec to pull the image
```
docker exec -it ollama-docker-compose-ollama-1 ollama pull llama3.1
```
3. Using docker compose exec to pull the image
```
docker compose exec ollama ollama pull llama3.1
```

### Stop the services
```
docker-compose down
```
