---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Tiny-Imagenet Challenge"
summary: "Modified version of DenseNet architecture to train on tiny-ImageNet dataset."
authors: []
tags: []
categories: []
date: 2019-10-22T21:21:50+05:30

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
### EIP phase-1 Project  
**Goal**: Achieve atleast 60% validation accuracy on Tiny-Imagenet Dataset in less than 200 epochs.  

**Challenges**:  

* Due to lack of infrastructure, google colab was the only option available.  

**Approach**:  

* Trained a custom made DenseNet Model (21 layers) after taking receptive field and object size into consideration.  
* The model has 5 DenseBlocks each with 3 convolution layers and 4 transition blocks in between. There is no 5th transition block. 
* Substitued Flattern + Dense with Global Average Pooling layer to enable progeressive resizing.  
* Trained the model on scaled down images (16x16 and 32x32) for initial few epochs to extract the essential features and later on original size to improve the further accuracy.  
* Train additionally on poorly performing classes identified using F1 score.  
* Triangular Cyclic LR for faster convergence.  
* 14 different type of image augmentation techniques.  

**Details**:  

* Batch size: 320  
* Total Parameters: 8.9M  
* Learning Rate: MaxLR = 0.05, MinLR=0.001 and StepSize=2000  

**Results**:

* Validation Accuracy 62.95%
* Epochs 95

You can find the notebook [here](https://colab.research.google.com/drive/1INaQhqN5ZlQZMkldE_MC3nK69Ty5RCuh#scrollTo=LJE5n5pJRgMP)
 