# 🎨 AI Creative Pipeline

An advanced AI-powered creative pipeline that transforms text descriptions into stunning images and 3D models, powered by local LLM technology and the Openfabric SDK.

## ✨ Features

- 🤖 **Local LLM Integration**: Uses LLaMA 2 for intelligent prompt expansion
- 🎨 **Text-to-Image Generation**: Creates high-quality images from text descriptions
- 🌟 **Image-to-3D Conversion**: Transforms 2D images into interactive 3D models
- 💾 **Smart Memory System**: Maintains context and history across sessions
- 🔒 **Privacy-Focused**: All processing happens locally
- 🎯 **Multiple Artistic Styles**: Supports realistic, artistic, minimalist, and fantasy styles
- 📊 **Comprehensive Logging**: Detailed execution logs and error tracking

## 🚀 Prerequisites

- Python 3.8 or higher
- Poetry for dependency management
- LLaMA 2 7B Chat model (GGUF format)
- 8GB+ RAM recommended
- NVIDIA GPU (optional, for faster processing)

## 📦 Installation

1. Clone the repository:
```bash
git clone https://github.com/Amanastel/ai-image-creator.git
cd ai-image-creator
```

2. Install dependencies:
```bash
poetry install
```

3. Download the LLaMA 2 7B Chat model:
```bash
mkdir -p models
# Download llama-2-7b-chat.gguf from Hugging Face
# Place it in the models directory
```

4. Create required directories:
```bash
mkdir -p outputs memory
```

## 🛠️ Configuration

1. Environment Setup:
   - Copy `.env.example` to `.env`
   - Adjust memory settings if needed
   - Configure GPU settings (optional)

2. Model Configuration:
   - Default model: LLaMA 2 7B Chat
   - Supports other GGUF format models
   - Configurable inference parameters

## 🖥️ Running the Application

### Method 1: Using Start Script
```bash
./start.sh
```

### Method 2: Using Docker
```bash
docker build -t ai-creative-pipeline .
docker run -p 8888:8888 -v $(pwd)/outputs:/app/outputs -v $(pwd)/memory:/app/memory ai-creative-pipeline
```

Access the application at: http://localhost:8888/swagger-ui/#/App/post_execution

## 📝 Usage Guide

### Basic Usage

1. Access the Swagger UI
2. Navigate to POST /execution endpoint
3. Click "Try it out"
4. Submit a prompt:
```json
{
  "prompt": "Make me a glowing dragon standing on a cliff at sunset",
  "style": "fantasy",
  "dimensions": {
    "width": 1024,
    "height": 768
  },
  "quality": 95
}
```

### Advanced Options

- **Styles**: 
  - `realistic`: Photo-realistic images
  - `artistic`: Creative interpretations
  - `minimalist`: Clean, simple designs
  - `fantasy`: Magical and otherworldly scenes

- **Quality Settings**:
  - Resolution: Up to 2048x2048
  - Quality: 1-100 scale
  - Format: PNG/JPG/JPEG

## 🧠 Memory System

### Short-Term Memory
- Maintains context during interactions
- Enables coherent conversation flow
- Temporary storage in Redis (optional)

### Long-Term Memory
- JSON-based persistent storage
- Searchable history
- Entry format:
```json
{
  "timestamp": "2025-04-16T23:33:12.341825",
  "original_prompt": "glowing dragon on cliff",
  "expanded_prompt": "A majestic dragon...",
  "image_path": "outputs/image_20250416_233312.png",
  "model_path": "outputs/model_20250416_233312.glb"
}
```

## 📁 Project Structure

```
ai-creative-pipeline/
├── app/
│   ├── core/           # Core application logic
│   ├── models/         # AI models and weights
│   └── utils/          # Utility functions
├── outputs/            # Generated content
│   ├── images/         # 2D image outputs
│   └── models/         # 3D model outputs
├── memory/             # Persistent storage
├── config/            # Configuration files
├── tests/            # Test suite
└── docker/           # Docker configuration
```

## 🐛 Error Handling

- Comprehensive error logging
- Graceful failure recovery
- User-friendly error messages
- Automatic retry mechanism

## 🔒 Security Notes

- Local processing ensures data privacy
- No external API dependencies
- Secure file handling
- Resource usage limits

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) for details on:
- Code style
- Development process
- Pull request procedure

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Authors

- **Aman Kumar** - *Initial work* - [Amanastel](https://github.com/Amanastel)

## 🙏 Acknowledgments

- OpenFabric team for the SDK
- LLaMA team for the language model
- Contributors and testers 
