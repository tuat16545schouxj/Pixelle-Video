# Pixelle-Video

A fork of [AIDC-AI/Ovis](https://github.com/AIDC-AI/Pixelle-Video) focused on video understanding and generation with multimodal large language models.

## Features

- Video understanding with multimodal LLMs
- Frame-level visual tokenization
- Efficient video encoding pipeline
- Support for long-form video inference

## Installation

### From Source

```bash
git clone https://github.com/your-org/Pixelle-Video.git
cd Pixelle-Video
pip install -e .
```

### Using Docker

```bash
docker build -t pixelle-video .
docker run --gpus all -it pixelle-video
```

### Dev Container

Open in VS Code and select **Reopen in Container** to use the pre-configured development environment.

## Quick Start

```python
from pixelle_video import PixelleVideoModel, PixelleVideoProcessor

model = PixelleVideoModel.from_pretrained("pixelle-video-7b")
processor = PixelleVideoProcessor.from_pretrained("pixelle-video-7b")

# Video understanding
result = model.chat(
    video="path/to/video.mp4",
    query="Describe what is happening in this video.",
    processor=processor,
)
print(result)
```

## Requirements

- Python >= 3.10
- PyTorch >= 2.1
- CUDA 11.8+ (for GPU inference)
- See `pyproject.toml` for full dependency list

## Model Architecture

Pixelle-Video builds on top of a visual tokenizer and a causal language model backbone:

1. **Video Encoder** — Extracts per-frame visual features using a vision transformer.
2. **Visual Tokenizer** — Discretizes visual features into tokens compatible with the LLM vocabulary.
3. **LLM Backbone** — Processes interleaved video and text tokens for generation.

## Development

```bash
# Install with dev dependencies
pip install -e ".[dev]"

# Run tests
pytest tests/

# Build docs
mkdocs serve
```

## Citation

If you use Pixelle-Video in your research, please cite the original Ovis work:

```bibtex
@article{pixellevideo2024,
  title={Pixelle-Video: Multimodal LLM for Video Understanding},
  year={2024}
}
```

## License

This project is licensed under the Apache 2.0 License — see [LICENSE](LICENSE) for details.
