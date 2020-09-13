# Flipkart-GRID
Object Localization Problem

### Problem Statement -

Participants were supposed to draw a box around objects in images, separating them from the background of the image. In technical terms, we were supposed to train models which would draw bounding boxes around objects in the images.

Here is an example of the bounding boxes we were expected to draw using the ML models - 

![Image](https://i.ibb.co/dP6JvtZ/1-FAk-Tit-ZCvm-Z2xd-M8o-FF2ng.png)  ![Image](https://i.ibb.co/XXWryJg/bounded.png)

### Metric -
-> IoU Metric

![Image](https://i.ibb.co/XXSNKdb/IOU.png)

# PS: Pre-Trained Models were not allowed.

## Approach

- Started off with segregating the images into 2 categories: images which had the ground truth labels available and boxes which did not have them.
- Applied Sobel Filter and Canny Filter on the 14000 images, whose bounding box coordinates were given.
- Used Keras for the purpose, and it does not contain support for IoU metric, so had to manually define the metric. 
- Trained a number of models, that had approaches ranging from simple stacked convolutional layer models to Models having skip connections to models inspired from Fractal Architectures. 
- Due to less number of images available, usage of deep models was not possible, and hence only shallower architectures  were used.

- After experimenting with a lot of architectures, 2 models were finalised. 
- The first Model was a 3-layer convolutional layer model, followed by a Fully Connected layer.  This model was trained on first 128 by 128 pixels Sobel images, 256 by 256 pixels Sobel images and finally on 128 by 128 pixeled Canny images.
- Got 3 predictions using this model. 
- The other model was a Skip Connection model, that had mild residual connections, apart from having stacked Convolutions and FC layers. Predictions on this model was done using  128 by 128 pixeled Sobel images.
- Finally the predictions were ensembled in a slightly complex manner, ensembling the first 3 predictions first using a specific set of weights, and then ensembled the resulting predictions with predictions obtained from the skip connection model. 
-This prediction recorded an IoU of 0.826 on the unseen test dataset.


### Rank - 80th  (out of around 2200 participating teams)
