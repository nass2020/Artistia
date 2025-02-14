# Artistia

<center><img src="assets/logo.png" alt="logo" height="200px" width="200px"></center>
A website made using HTML, CSS, Bootstrap and Flask to perform computer vision related tasks like style transfer, image colorization, sketching and pixelating. Style transfer was made using transfer learning(vgg16) and tensorflow framework in Python and for image colorization we trained an autoencoder and the u-net model on images obtained from Flickr dataset. For, Image Sketching we trained the u-net model on images obtained from the APDrawingDB dataset.

## Setting up and running the project

1. Fork the repo and clone it
```
git clone https://github.com/EnigmAI/Artistia.git
cd Artistia
```
2. Activate your conda or virtual Python environment
3. To download the required packages run the commands below
```
pip install -r requirements.txt
```
4. To start the backend server run the following command
```
python main.py
```
5. Open your browser and navigate to the url below
```
http://localhost:5000
```

## Deep Learning Models

- <strong>Style Transfer</strong> - We used two different implementations of style transfer. One is for low resolution images and the other one for high resolution images, both made using Tensorflow framework. The difference between the two is only the optimizer, we used fmin_l_bfgs_b optimizer from scipy for low resolution image style transfer and SGD optimizer from tensorflow for high resolution image style transfer. We got better results in fewer epochs using fmin_l_bfgs_b but it was unable to handle higher resolution images so we used SGD for those. Both the implementations use transfer learning(pretrained vgg16 on imagenet dataset) and optimizes the image. Content optimization is done by reducing loss between convolutional outputs of content image and current image obtained from VGG while style optimization is done by reducing loss between gram matrices of convolutional outputs of current image and style image obtained at five different points from the VGG model. To understand style transfer more in-depth go through the OptimizingContent.ipynb, OptimizingStyle.ipynb, StyleTransfer.ipynb inside NeuralStyleTransfer directory.

- <strong>Image Colorization</strong> - For image colorization we made an autoencoder and u-net model using tensorflow framework that we trained on images obtained from Flickr dataset. Instead of using RGB image format we converted images to LAB format(L channel is basically grayscale and AB channel contains information regarding colour of the image). The models take in the L channel(grayscaled image) as input then predicts AB channel, then we combine all the channels to get the final coloured image. To understand it better go through the jupyter notebooks provided inside the ImageColorization directory.

- <strong>Image Sketching</strong> - For image sketching we made the u-net model using tensorflow framework and it was trained on images obtained from the APDrawingDB dataset. To view the code, go through the jupyter notebook provided inside the ImageSketching directory.

## Preview

Disclaimer - Loading time to get the results were skipped in this preview for convenience but it might take upto 1 minute to get the actual results.

![](assets/preview.gif)
