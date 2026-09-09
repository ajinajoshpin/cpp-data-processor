# GPU Image Stylization Pipeline

## Overview
This project processes 100 unique images using GPU-accelerated CUDA kernels to apply four artistic filters: Oil Paint, Pencil Sketch, Cartoon Effect, and Vintage Film. The images are generated from a single input image with random variations in brightness, contrast, color, and noise.

## Dataset
- **Total Images Processed:** 100 unique variations
- **Image Size:** 791 x 1000 pixels
- **Source:** Single input image (sweet.jpg) with generated variations

## Full Dataset
The complete dataset (100 input images + sample outputs from all filters) is available for download:
📦 **[Download project_artifacts.zip](https://we.tl/t-6Opis6RCfwnNT6Lq)**

## Filters Implemented

| Filter | Description |
|--------|-------------|
| Oil Paint | Smooths colors while preserving edges using neighborhood averaging |
| Pencil Sketch | Converts to grayscale with edge enhancement using Sobel operator |
| Cartoon Effect | Color quantization for cartoon look (32 levels per channel) |
| Vintage Film | Warm tones with color transformation (red boost, blue reduction) |

## Performance Results (100 images)

| Filter | GPU Avg Time (s) | CPU Avg Time (s) | Speedup |
|--------|------------------|------------------|---------|
| Oil Paint | 0.0026 | 0.0018 | 0.68x |
| Pencil Sketch | 0.0080 | 0.0077 | 0.97x |
| Cartoon Effect | 0.0025 | 0.0012 | 0.47x |
| Vintage Film | 0.0022 | 0.0106 | **4.75x** |

## One Image, Four Filters

| Original | Oil Paint | Pencil Sketch | Cartoon | Vintage |
|----------|-----------|---------------|---------|---------|
| ![original]<img width="557" height="452" alt="image" src="https://github.com/user-attachments/assets/4b90ba68-a515-4177-b7b3-e0272a9f66dd" />
 | ![oilpaint](output_oilpaint/output_000.png) | ![sketch]<img width="533" height="425" alt="image" src="https://github.com/user-attachments/assets/9438f71a-a7e3-40d0-ad80-8f3b5118a095" />
 | ![cartoon]<img width="567" height="455" alt="image" src="https://github.com/user-attachments/assets/42eff79e-c099-47fa-928b-70ad501dd09b" />
 | ![vintage]<img width="561" height="445" alt="image" src="https://github.com/user-attachments/assets/06b5a38e-d4b8-4db0-b604-65297f363806" />



### Key Observation
GPU was **4.75x faster** for the Vintage filter, which involves complex floating-point color transformations. For simpler operations on small images (791×1000), CPU was faster due to GPU overhead. This demonstrates that GPU acceleration is most beneficial for complex operations.

## Repository Contents
- `GPU_Image_Stylization.ipynb` - Complete Colab notebook
- `performance_data.txt` - Detailed performance metrics
- `project_artifacts.zip` - 100 input images + sample outputs
- `sweet.jpg` - Original input image

## How to Run
1. Open the notebook in Google Colab
2. Enable GPU: Runtime → Change runtime type → GPU
3. Run all cells sequentially
4. 100 images will be generated and processed with 4 filters

## Requirements
- Google Colab with GPU runtime
- PyCUDA
- OpenCV
- NumPy

## Author
AJINA JOSHPIN A
## License
This project is submitted as part of the CUDA at Scale Independent Project.
