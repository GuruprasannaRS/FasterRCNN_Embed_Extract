# FasterRCNN_Embed_Extract

A Python project for extracting embeddings from images using the Faster R-CNN model. This project processes images to extract feature embeddings from detected objects before the classification layers, which can be used for downstream tasks like training custom classifiers.

## Overview

This project demonstrates how to:
- Load a pre-trained Faster R-CNN ResNet-50 FPN model
- Extract feature embeddings from detected objects in images
- Process multiple images and save embeddings as NumPy arrays
- Generate a summary report of the extraction process

## Project Structure

```
FasterRCNN_Embed_Extract/
├── Notebook/
│   └── fasterrcnn-embed-extract.ipynb    # Main Jupyter notebook with implementation
├── Results/                               # Output directory containing extracted embeddings
│   ├── *.npy                             # NumPy files containing embeddings for each image
│   └── data_emebeddings.xlsx             # Summary Excel file with extraction metadata
└── README.md                             # This file
```

## Features

- **Pre-trained Model**: Uses `fasterrcnn_resnet50_fpn` from torchvision with COCO weights
- **Embedding Extraction**: Extracts features from the ROI (Region of Interest) pooling layer
- **Batch Processing**: Processes multiple images and saves individual embeddings
- **Metadata Tracking**: Records number of bounding boxes and embedding dimensions for each image
- **Output Formats**: Saves embeddings as `.npy` files and summary as Excel spreadsheet

## How It Works

1. **Image Processing**: Converts PIL images to PyTorch tensors
2. **Feature Extraction**: Passes images through the backbone network to get feature maps
3. **RPN Processing**: Uses Region Proposal Network to generate object proposals
4. **ROI Pooling**: Applies Region of Interest pooling to extract region-specific features
5. **Embedding Generation**: Passes pooled features through the box head to get final embeddings
6. **Output Generation**: Saves embeddings and creates metadata summary

## Key Functions

- `get_embeddings(model, image)`: Extracts embeddings from a single image
- `process_images(model, image_paths)`: Processes multiple images and saves results
- `get_image_paths(image_folder, limit=10)`: Retrieves image paths from a directory

## Dependencies

- PyTorch
- torchvision
- PIL (Pillow)
- NumPy
- pandas
- openpyxl (for Excel output)

## Usage

1. Open the Jupyter notebook: `Notebook/fasterrcnn-embed-extract.ipynb`
2. Update the `image_folder` path to point to your image directory
3. Run all cells to process images and extract embeddings
4. Check the `Results/` folder for extracted embeddings and summary data

## Output

- **Embedding Files**: Each processed image generates a `.npy` file containing the extracted embeddings
- **Summary Excel**: Contains metadata including image name, number of bounding boxes, embedding size, and corresponding file names
- **Console Output**: Displays the number of detected objects for each image during processing

## Notes

- The model automatically downloads pre-trained weights on first run
- Supports common image formats (tested with .jpg files)
- Embeddings are extracted before the final classification layer
- Each bounding box detection generates a separate embedding vector
