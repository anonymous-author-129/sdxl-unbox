# Unpacking SDXL Turbo: Interpreting Text-to-Image Models with Sparse Autoencoders

![modification demostration](resources/image.png)

This repository contains code to reproduce results from our paper on using sparse autoencoders (SAEs) to analyze and interpret the internal representations of text-to-image diffusion models, specifically SDXL Turbo.

## Repository Structure

```
|-- SAE/                    # Core sparse autoencoder implementation
|-- SDLens/                 # Tools for analyzing diffusion models
|   `-- hooked_sd_pipeline.py   # Modified stable diffusion pipeline
|-- scripts/
|   |-- collect_latents_dataset.py  # Generate training data
|   `-- train_sae.py                    # Train SAE models
|-- utils/
|   `-- hooks.py           # Hook utility functions
|-- checkpoints/           # Pretrained SAE model checkpoints
|-- app.py                # Demo application
|-- app.ipynb             # Interactive notebook demo
|-- example.ipynb         # Usage examples
`-- requirements.txt      # Python dependencies
```

## Installation

```bash
pip install -r requirements.txt
```

## Demo Application

You can try our gradio demo application (`app.ipynb`) to browse and experiment with 20K+ features of our trained SAEs out-of-the-box. 

## Usage

1. Collect latent data from SDXL Turbo:
```bash
python scripts/collect_latents_dataset.py --save_path={your_save_path}
```

2. Train sparse autoencoders:

    2.1. Insert the path of stored latents and directory to store checkpoints in `SAE/config.json`

    2.2. Run the training script:

```bash
python scripts/train_sae.py
```

## Pretrained Models

We provide pretrained SAE checkpoints for 4 key transformer blocks in SDXL Turbo's U-Net. See `example.ipynb` for analysis examples and visualization of learned features.


## Acknowledgements

The SAE component was implemented based on [`openai/sparse_autoencoder`](https://github.com/openai/sparse_autoencoder) repository.
