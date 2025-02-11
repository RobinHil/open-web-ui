# 🌐 OpenWebUI Docker Configurations

This repository contains different Docker Compose configurations for deploying OpenWebUI with LocalAI and/or Ollama.

## 🌟 Features

- 🚀 Three deployment options:
  - OpenWebUI + LocalAI
  - OpenWebUI + Ollama
  - OpenWebUI + LocalAI + Ollama
- 🎮 GPU support with NVIDIA CUDA
- 🔄 Automatic container orchestration
- 🔌 Isolated network configuration
- 💾 Persistent data storage

## 🏗️ Project Structure

```
.
├── localai/
│   └── docker-compose.yml  # OpenWebUI + LocalAI configuration
├── ollama+localai/
│   └── docker-compose.yml  # OpenWebUI + LocalAI + Ollama configuration
├── ollama/
│   └── docker-compose.yml  # OpenWebUI + Ollama configuration
├── LICENSE
└── README.md
```

## 📋 Prerequisites

- Docker and Docker Compose installed
- NVIDIA GPU with CUDA support
- NVIDIA Container Toolkit installed

## 🚀 Getting Started

1. Clone this repository:
```bash
git clone https://github.com/RobinHil/open-web-ui.git
cd open-web-ui
```

2. Choose your preferred configuration and navigate to the corresponding directory:
```bash
cd localai         # For LocalAI setup
# or
cd ollama          # For Ollama setup
# or
cd ollama+localai  # For combined setup
```

3. Start the services:
```bash
docker compose -p [compose_alias] up -d
```

## 🔌 Service Configurations

### LocalAI Setup
- OpenWebUI: `http://localhost:3000`
- LocalAI API: `http://localhost:3100`
- Environment Variables:
  - `USE_CUDA_DOCKER: true`
  - `OPENAI_API_BASE_URLS: http://localai:8080/v1`

### Ollama Setup
- OpenWebUI: `http://localhost:3000`
- Environment Variables:
  - `USE_CUDA_DOCKER: true`
  - `OLLAMA_BASE_URLS: http://ollama:11434`

### Combined Setup
- OpenWebUI: `http://localhost:3000`
- LocalAI API: `http://localhost:3100`
- Environment Variables:
  - `USE_CUDA_DOCKER: true`
  - `OLLAMA_BASE_URLS: http://ollama:11434`
  - `OPENAI_API_BASE_URLS: http://localai:8080/v1`

## 💾 Persistent Storage

Each configuration includes the following volumes:
- `open-webui_data`: OpenWebUI data storage
- `localai_models`: LocalAI models storage (when applicable)
- `ollama_data`: Ollama data storage (when applicable)

## 🔧 Technical Details

All services are configured with:
- Automatic restart capability
- GPU access through NVIDIA Container Toolkit
- Bridged network configuration
- Inter-service dependencies
