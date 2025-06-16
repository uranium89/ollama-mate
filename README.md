# OllaMate - Technical Documentation

OllaMate is a containerized AI orchestration platform that integrates Ollama with various services for a complete AI development and deployment environment.

## System Architecture

OllaMate consists of the following core components:

- **Ollama**: AI model serving and inference
- **n8n**: Workflow automation and orchestration
- **PostgreSQL**: Database for workflow and configuration storage
- **Qdrant**: Vector database for embeddings and semantic search
- **AnythingLLM**: UI interface for LLM interactions

## Technical Requirements

### Hardware Requirements
- **CPU**: Multi-core processor (4+ cores recommended)
- **RAM**: Minimum 8GB (16GB+ recommended for larger models)
- **Storage**: 20GB+ free space (varies based on models)
- **GPU (Optional)**: 
  - NVIDIA GPU with CUDA support (8GB+ VRAM recommended)
  - AMD GPU with ROCm support

### Software Requirements
- Docker Engine 20.10.0+
- Docker Compose v2.0.0+
- For GPU support:
  - NVIDIA: CUDA 11.4+ and nvidia-container-toolkit
  - AMD: ROCm 5.0+ and relevant container runtime

## Installation and Deployment

### 1. Repository Setup
```bash
git clone https://github.com/uranium89/ollama-mate
cd ollama-mate
```

### 2. Configuration

#### Environment Variables
Create a `.env` file in the root directory:
```env
POSTGRES_USER=your_username
POSTGRES_PASSWORD=your_secure_password
# Additional environment variables as needed
```

#### Volume Configuration
OllaMate uses Docker volumes for persistent storage:
- `n8n_storage`: Workflow data
- `postgres_storage`: Database files
- `ollama_storage`: AI model weights
- `qdrant_storage`: Vector embeddings
- `anyllm_storage`: UI configurations

### 3. Deployment Options

docker-compose up -d

## Component Configuration

### Ollama Configuration
- Default port: 11434
- Model storage location: `/ollama_storage`
- Supported formats: GGUF, GGML

### n8n Workflow Engine
- Access URL: http://localhost:5678
- Authentication: Enabled by default
- Database: PostgreSQL

### Qdrant Vector Database
- Access port: 6333
- Storage type: Persistent
- Index format: HNSW
### AnythingLM
- Access URL: http://localhost:3001
- Model storage location: `/anyllm_storage`
- Database: PostgreSQL
## Security Considerations

1. **Network Security**
   - All services are containerized
   - Inter-service communication via Docker network
   - External access controlled via ports

2. **Data Security**
   - Persistent volume encryption recommended
   - Environment variable protection
   - Regular backup procedures recommended

## Performance Optimization

### CPU Deployment
- Set appropriate resource limits in docker-compose.yml
- Monitor memory usage for large models
- Consider model quantization for efficiency

### GPU Deployment
- CUDA/ROCm optimization settings available
- Monitor GPU memory usage
- Enable hardware-specific optimizations

## Troubleshooting

### Common Issues
1. **Insufficient Memory**
   - Check container logs
   - Adjust Docker memory limits
   - Consider using smaller models

2. **GPU Access Issues**
   - Verify driver installation
   - Check container runtime configuration
   - Ensure proper device permissions

3. **Service Communication**
   - Check network configuration
   - Verify service health status
   - Review container logs

## Contributing

1. Fork the repository
2. Create a feature branch
3. Submit a pull request with detailed description
4. Follow code style and documentation guidelines

## License
MIT 
