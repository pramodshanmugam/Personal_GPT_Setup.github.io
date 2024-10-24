---
layout: default
title: Setting Up GPT Locally
---

# Worried About Your GPT Search Becoming Public? Here's How to Set Up Your Personal GPT

In an era where privacy concerns around AI usage are increasing, many are looking for ways to keep their AI conversations private. This guide will walk you through setting up your **Personal GPT** locally, keeping all interactions secure and private. By leveraging Docker and **Ollama** for LLM inference, you can ensure that your GPT stays entirely under your control.

Follow the steps below to create a personalized GPT environment right on your machine, with easy-to-manage Docker containers. You can clone the full setup from my [GitHub repository Frontend:](https://github.com/pramodshanmugam/chatbot-frontend-react.git) [Github repository Backend:](https://github.com/pramodshanmugam/chatbot-frontend-react.git).

![Pramod's GPT](./images/gptpramod.gif)

---

## Prerequisites

Before we begin, ensure you have the following installed:

1. **Docker**: [Install Docker](https://docs.docker.com/get-docker/)
2. **Docker Compose**: [Install Docker Compose](https://docs.docker.com/compose/install/)

---

## Step 1: Clone the Repository

First, grab the repository which contains everything you need to get started:

```bash
git clone https://github.com/pramodshanmugam/personal-gpt-docker.git
cd personal-gpt-docker
```

![Git Clone Screenshot](./images/gitclone.png)

---

## Step 2: Set Up Ollama Locally for LLM Inference

Ollama powers the GPT behind the scenes, allowing for fast local inference. Let’s get it running in a Docker container.

### 1. Pull Ollama Docker Image

Start by pulling the Ollama Docker image:

```bash
docker pull ollama/ollama
```

![Ollama Pull Screenshot](./images/ollamapull.png)

### 2. Run Ollama Docker Container

Next, run the container on port 11434:

```bash
docker run -d --name ollama-container -p 11434:11434 ollama/ollama:latest
```

### 3. Pull the Llama Model

Once the container is running, pull the desired Llama model:

```bash
docker exec -it ollama-container ollama pull llama3.2
```

When the pull is complete, your setup should resemble the following screenshot:

![Ollama Successfully Installed](./images/ollamasuccess.png)

---

## Step 3: Running the Backend and Frontend

With Ollama ready, it's time to spin up both the backend and frontend services.

### 1. Optional: Update the GPT Name

If you’d like to personalize your GPT instance, open the `docker-compose.yml` file and modify the `REACT_APP_CHAT_NAME` environment variable:

```yaml
chatbot_frontend:
  environment:
    - REACT_APP_CHAT_NAME="Pramod's GPT"  # Change this to personalize
```

![Updating GPT Name](./images/changingname.png)

### 2. Run Docker Compose

Start both the backend and frontend by running Docker Compose:

```bash
docker-compose up --build
```

![Docker Compose Success](./images/dockercompose.png)

---

## Step 4: Access the Application

Once all the containers are up, visit your personalized GPT at:

- http://localhost:3000

![Successfully Ran the GPT](./images/gpt.gif)

---

## Conclusion

Congratulations! You’ve successfully set up your own local GPT using Docker and Ollama. With this setup, you can ensure that all your AI interactions remain private and fully under your control.

If you encounter any issues, feel free to open an issue on the GitHub repository or reach out to me.