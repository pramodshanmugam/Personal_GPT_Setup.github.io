---
layout: default
title: Setting Up Pramod's GPT Locally
---

# Setting Up Pramod's GPT Locally

This guide will walk you through setting up your **Personal GPT** locally using Docker. The project includes a backend, frontend, and uses **Ollama** for LLM inference. You can clone the Docker Compose setup from my [GitHub repository](https://github.com/pramodshanmugam/personal-gpt-docker.git).

## Prerequisites

Before starting, make sure you have the following installed:

1. **Docker**: [Install Docker](https://docs.docker.com/get-docker/)
2. **Docker Compose**: [Install Docker Compose](https://docs.docker.com/compose/install/)

---

## Step 1: Clone the Repository

Clone the GitHub repository which contains the Docker Compose setup for the backend and frontend:

```bash
git clone https://github.com/pramodshanmugam/personal-gpt-docker.git
cd personal-gpt-docker
```
![Git Clone Screenshot](./assets/gitclone.png)

## Step 2: Set Up Ollama Locally

To use Ollama locally for inference, you need to run Ollama in a Docker container. Follow the steps below:

1. **Pull Ollama Docker Image:**

Pull Ollama Docker image into your local:

```bash
docker pull ollama/ollama
```
![Ollama Pull Screenshot](./assets/ollamapull.png)

2. **Run Ollama Docker Container:**

Run Ollama on port 11434 by using the following command:

```bash
docker run -d --name ollama-container -p 11434:11434 ollama/ollama:latest
```

2. **Pull the Llama Model:**

Once the container is running, execute this command to pull the Llama model (version 3.2):

```bash
docker exec -it ollama-container ollama pull llama3.2
```
After you successfully pull ollama and run it on your look it should look something like this.

![Ollama Sucessfull Installed](./assets/ollamasuccess.png)

## Step 3: Running the Backend and Frontend

Now that Ollama is set up, let's run the backend and frontend services using Docker Compose.

1. **Update the GPT's name (Optional)**

In the docker-compose.yml file, I've set up environment variables for naming the GPT. You can customize the REACT_APP_CHAT_NAME value if needed.

```yaml
chatbot_frontend:
  environment:
    - REACT_APP_CHAT_NAME="Pramod's"  # Modify this if you'd like
```

![Adding your name to the GPT](./assets/chaningname.png)
2. **Run Docker Cmpose**

```bash 
docker-compose up --build
```
![Docker Compose Success](./assets/dockercompose.png)

## Step 4: Access the Application

Once the containers are up, you can access the services via:

- http://localhost:3000

![Successfully Ran the GPT](./_site/assets/changingname.png)
## Conclusion 

You have successfully set up Pramod's GPT locally with Docker for both the backend and frontend, and connected it to Ollama for LLM inference. If you run into any issues, feel free to raise an issue on the GitHub repository or contact me.


