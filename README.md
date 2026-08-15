# Color Diffusion

A proof-of-concept diffusion model for colorizing black-and-white images.

<p align="center">
  <img src="input_images/bwface.jpg" width="180" alt="Black and white input image" />
  <img src="visualization/forward_diff.gif" width="180" alt="Forward diffusion visualization" />
  <img src="visualization/denoising.gif" width="180" alt="Denoising visualization" />
</p>

## Snapshot

- LAB color space pipeline
- UNet-based denoising model
- Gradio demo
- Training, inference, and visualization scripts
- Example notebooks for experimentation

## Overview

This project explores how diffusion models can colorize grayscale images using the LAB color space. The model keeps the lightness channel fixed and learns to predict the color channels.

The core idea is simple:

- convert color images to LAB
- add noise to the AB channels
- feed the grayscale channel and noisy color channels into a UNet
- predict the color noise and denoise over time

The model is conditioned on features extracted from the grayscale channel, which helps it keep the colorization aligned with the input image.

## Repository Map

- `app.py` - Gradio demo entry point
- `train.py` - training script
- `inference.py` - image colorization inference
- `dataset.py` - dataset helpers
- `diffusion.py` and `denoising.py` - diffusion and denoising logic
- `visualization/` - generated examples and process visualizations
- `input_images/` - example grayscale inputs
- `configs/` - configuration files

## Usage

Download the dataset:

```bash
bash download_dataset.sh
```

Run inference from the command line:

```bash
python inference.py --image-path <IMG_PATH> --checkpoint <CKPT_PATH> --output <OUTPUT_PATH>
```

Or launch the Gradio app:

```bash
python app.py
```

## Notes

Some supporting code for the dataset, LAB conversions, and UNet setup was adapted from the projects linked in the original README. The repo also includes optional dynamic thresholding inspired by Assembly AI's Minimagen write-up.
