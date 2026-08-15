# Color Diffusion

A proof-of-concept diffusion model for colorizing black-and-white images.

<p align="center">
<img src="https://github.com/ErwannMillon/Color-diffusion/blob/main/visualization/inference/total_1.gif" width="128" height="128"/>
<img src="https://github.com/ErwannMillon/Color-diffusion/blob/main/visualization/inference/total_2.gif" width="128" height="128"/>
<img src="https://github.com/ErwannMillon/Color-diffusion/blob/main/visualization/inference/total_3.gif" width="128" height="128"/>
<img src="https://github.com/ErwannMillon/Color-diffusion/blob/main/visualization/inference/total_4.gif" width="128" height="128"/>
<img src="https://github.com/ErwannMillon/Color-diffusion/blob/main/visualization/inference/total_8.gif" width="128" height="128"/>
<img src="https://github.com/ErwannMillon/Color-diffusion/blob/main/visualization/inference/total_90.gif" width="128" height="128"/>
</p>

## Overview

This project explores how diffusion models can colorize grayscale images using the LAB color space. The model keeps the lightness channel fixed and learns to predict the color channels.

The core idea is simple:

- convert color images to LAB
- add noise to the AB channels
- feed the grayscale channel and noisy color channels into a UNet
- predict the color noise and denoise over time

The model is conditioned on features extracted from the grayscale channel, which helps it keep the colorization aligned with the input image.

## What’s Included

- Training code
- Inference scripts
- A Gradio demo
- Dataset utilities
- Visualization helpers
- Example notebooks

## Why It’s Interesting

This was intentionally scoped as a proof of concept, so the results are basic, but it captures the full shape of a diffusion pipeline: data preparation, noising, conditioning, denoising, and visual evaluation.

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
