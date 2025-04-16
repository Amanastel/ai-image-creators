# AI Creative Pipeline

This application implements an end-to-end creative pipeline that:
1. Takes a text prompt
2. Expands it using a local LLM
3. Generates an image from the expanded prompt
4. Converts the image into a 3D model
5. Stores all interactions in memory

## Prerequisites

- Python 3.8 or higher
- Poetry for dependency management
- LLaMA 2 7B Chat model (GGUF format)

## Setup

1. Install dependencies:
```bash
poetry install
```

2. Download the LLaMA 2 7B Chat model:
```bash
mkdir -p models
# Download llama-2-7b-chat.gguf from Hugging Face and place it in the models directory
```

3. Create required directories:
```bash
mkdir -p outputs memory
```

## Running the Application

You can run the application in two ways:

1. Using the start script:
```bash
./start.sh
```

2. Using Docker:
```bash
docker build -t ai-creative-pipeline .
docker run -p 8888:8888 ai-creative-pipeline
```

The application will be available at http://localhost:8888/swagger-ui/#/App/post_execution

## Usage

1. Access the Swagger UI at http://localhost:8888/swagger-ui/#/App/post_execution
2. Click on the POST /execution endpoint
3. Click "Try it out"
4. Enter your prompt in the following format:
```json
{
  "prompt": "Make me a glowing dragon standing on a cliff at sunset"
}
```
5. Click "Execute"

The application will:
- Expand your prompt using the local LLM
- Generate an image from the expanded prompt
- Convert the image into a 3D model
- Save all outputs in the `outputs` directory
- Store the interaction in the `memory` directory

## Memory System

The application implements both short-term and long-term memory:

- Short-term memory: Maintains context during a single interaction
- Long-term memory: Stores all interactions in JSON files in the `memory` directory

Each memory entry contains:
- Timestamp
- Original prompt
- Expanded prompt
- Path to generated image
- Path to 3D model

## Output Structure

```
.
├── outputs/
│   ├── image_YYYYMMDD_HHMMSS.png
│   └── model_YYYYMMDD_HHMMSS.glb
├── memory/
│   └── memory_YYYYMMDD_HHMMSS.json
└── models/
    └── llama-2-7b-chat.gguf
```

## Error Handling

The application includes comprehensive error handling:
- Logs all errors with detailed messages
- Returns user-friendly error messages in the API response
- Maintains system stability even when errors occur

## Notes

- The application uses local LLM (LLaMA 2) to ensure privacy and avoid external API dependencies
- All generated assets are stored locally
- The memory system allows for future enhancements like similarity search 