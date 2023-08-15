# Image Processing and Classification - Ripe Mango Detector
Processing and classifying images of mangos to determine if it is ripe or not ripe based on red-color distribution

<p align="center">
  <img src="https://github.com/leeharry709/about-me/blob/main/media/download.png?raw=true"><img src="https://github.com/leeharry709/about-me/blob/main/media/download%20(1).png?raw=true"><img src="https://github.com/leeharry709/about-me/blob/main/media/download%20(2).png?raw=true"><img src="https://github.com/leeharry709/about-me/blob/main/media/download%20(3).png?raw=true"><img src="https://github.com/leeharry709/about-me/blob/main/media/download%20(4).png?raw=true">
</p>

# Introduction
This project was to create a program that could intake a user submitted image of a mangoe and classify whether it is ripe or not. I once got confused whether mangos were ripe or not at the supermarket, so I thought it would be a fun project and challenge to create this. This would require a large dataset of mangos with varying ripeness as well as some machine learning. This project was done in two steps - using a premade dataset of mangos to train a model that will help detect mango ripeness and generating mangos and artificially generated ripeness. I'll explain that in Part 2 below.

## Part 1
### Using a pre-made dataset
I trained a model with tensorflow using a premade set of images from Kaggle that had 427 ripe mangos and 1003 unripe mangos. By training the model to differentiate between what is a "green mango" versus what is a "ripe mango", the user can input a filepath to their mango image and it will predict whether or not it is or is not a ripe mango based on its red-yellow-green color distribution. Based on how much green is missing and red is showing, the program will tell if a mango is ripe or not. 

The major limiting factor is how much yellow is showing. For mangos, yellow can swing between both ripe and unripe depending on how much green or red is showing. If too much yellow is showing, the program will classify it as unripe. Another big challenge was that the database of ripe and green mangos was not very useful. The colors were inconsistent due to lighting and utilizing real-life images with stock images which greately affected saturation and color distribution. It also had a few different varieties of mangos, and this color detection method is primary useful for identifying ripeness in kent mangos. In part 2, I attempt to control this issue.

## Part 2
### Artificially generating a dataset
I wanted to create a dataset that could alleviate my dataset issues from part 1, so I thought to generate images of mangos of different color distributions. For this part, I went with the theory that mangos that are at least 50% red are considered ripe regardless of yellow and green color distribution. Using this as my definition, I created a program that could take 1 image of a mango and make X number of images with incrementally smaller amounts of red-color distribution. Since the only color I really needed was red, I calculated the Euclidian distance from the color red (RGB: 255, 0, 0) and incrementally blacked-out the colors farthest from red.

<p align="center">
<img src="https://raw.githubusercontent.com/leeharry709/about-me/main/media/download%20(5).png">
<br>Distribution of Euclidian distance (excluding pure-white pixels) in input image
</p>

By doing it this way, I could create my own dataset of mangoes from a small number of mangoes with an even number of ripe vs unripe mangos, alleviating the dataset issue from step one. One thing to note is that this could introduce heavy bias into the image set since it is based on what the person generating the dataset considers to be ripe or not. Theorhetically, one could say that ripe mangoes are just mangoes with no green, regardless of red-yellow color distribution. This is by no means a perfect way to handle the dataset issue in part 1, but it offers a start to a solution.

## Conclusion
Training the model on a premade dataset was a great entrypoint into understanding machine learning. Processing and generating images of mangos of different color distribution offers a solution, but is by no means the best answer. Somewhere in the middle lies a good way to creating a final product that could classify images of user sent mangos as ripe or not ripe regardless of lighting or variety. Potentially, even asking the user to input 2 sides of the mango would allow the program to give the best answer since one side could be more red then the other, and the program would average the color distribution from the 2 images to give the final answer.

## Image Classification - Real World Use Case
Binary image classification can find use in a lot of fields. One use case I've seen extensively is the detection of AI-generate images vs human-created images. Sites like isitai.com work by using machine learning models to examine various features of the image, such as color patterns, shapes, and textures, and then compares them to patterns typically found in human-generated images or AI-generated images. Image classification can also be used in the medical field to diagnose patioents such as with xrays, MRIs, and CT scans.

<p align="center">
  <img src="https://raw.githubusercontent.com/leeharry709/Image-Processing-and-Classification/main/ai_detection.PNG" width = 50%>
</p>
