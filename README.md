# VGG-CDM (VGG-19 Guided Colour Distribution Matching)
### A bachelor's thesis project that implements VGG-19 for photorealistic colour transfer
| Source    | Reference | VGG-CDM |
| --------- | ------- | ------- |
|  <img src = 'https://github.com/cristian20021/gifs/blob/main/MaleVideo.gif' >          |   <img src = 'https://github.com/cristian20021/gifs/blob/main/Blade.jpg' height = '500'>    |  <img src = 'https://github.com/cristian20021/gifs/blob/main/MaleVideo_Blade.gif' >   |
|           |      <img src = 'https://github.com/cristian20021/gifs/blob/main/Blade2.jpg' height = '500'>     |<img src = 'https://github.com/cristian20021/gifs/blob/main/MaleVideo_Blade2.gif' >     |
|           |      <img src = 'https://github.com/cristian20021/gifs/blob/main/Moonlight.jpg' height = '500'>   |<img src = 'https://github.com/cristian20021/gifs/blob/main/MaleVideo_Moonlight.gif' >      |
## Contents  
- **OneFrameOriginals/** — source images (add your source images here).  
- **OneFrameIntermediate/** — intermediate processing results (VGG-CDM Intermediate).  
- **OneFrameFinal/** — final result (VGG-CDM).  
- **AlgorithmicModelsOutput/** — outputs from algorithm runs (LHM, PCCM, Reinhard).  
- **References/** — reference materials (add your style images here).  
- **Videos/** — source videos (add your videos here).
- **Videos/VideosFinal** — processed videos.
- **Videos/{source_video}_{reference_image}_Frames/** — all the frames of the source video are located here.
- **Videos/{source_video}_{reference_image}_FramesIntermediate/** — all the intermediate processed frames of the source video are located here.
- **Videos/{source_video}_{reference_image}_FramesFinal/** — all the final processed frames of the source video are located here.
- **OneFrameProcessing.py** — core processing script for single frame processing.  
- **main.py** — main entry point to run the full pipeline.

  
## Features  
- Processes an image using a modified version of VGG-19 for a photorealistic colour transfer between the source image and reference image.
- Processes a video in the style of a reference
- Computes 3 benchmarks for evaluation purposes (SSIM, PSNR, Delta-E)

## Architecture
- The deep layers of VGG-19 are frozen to capture only the colour of the reference image
- A colour-related loss function is injected into the CNN
- The image is passed through the modified CNN for 200 iterations, optimizing the pixels every time (if it is possible)
- A soft blur filter is applied on the intermediate result to get rid of any unwanted textures inherited from the reference image
- The intermediate and source images are merged using a hard filter
  ![Untitled (3)](https://github.com/user-attachments/assets/dddc3618-80e8-4af9-a223-540641e2f2d2)
## Add your own media and files
- All the source images are located in the OneFrameOriginals/ folder. If you want to add your own source images, make sure to put them here
- All the reference images are located in the References/ folder. If you want to add your own reference images, make sure to put them here
- All the videos are located in the Videos/ folder. If you want to add your own videos, make sure to put them here
## Prerequisites
- Python 3.13
- Libraries: torch, torchvision, opencv-python, numpy, Pillow, scikit-image, moviepy, colortrans\
## Installation & Setup 
Clone the repo
```bash
git clone https://github.com/cristian20021/VGG-CDM.git  
cd VGG-CDM
```
Install the dependencies
```bash
pip install -r requirements.txt    
```
## Run
Run main.py file and choose which file you would like to process (image, video) or benchmark generation
For the inputs just type the name of the file with the extension included (do not put the full path), e.g. Batman.jpg

## Acknowledgement
This work was inspired by the PyTorch's implementation of [neural style transfer](https://docs.pytorch.org/tutorials/advanced/neural_style_tutorial.html)

