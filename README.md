# Udacity-FB-Flowers-CNN

Udacity PyTorch Deep Learning Scholarship Challenge final project.

## Background

The project was part of the requirements for the completion of Facebook and Udacity's PyTorch Deep Learning Scholarship Challenge. This project will be used to determine acceptance into the next phase of the scholarship which is the PyTorch Nanodegree from Udacity.

The goal of this project is to showcase what we have learned in the first phase of the challenge which covered an introduction to PyTorch, PyTorch basics and the different deep learning models with coding in PyTorch. For this project we are asked to create a classifier model that would be able to output the predicted category of a flower among 102 categories. 

## Methodology

For this project I was decided to approach it via transfer learning (fixed feature extractor) from a pre-trained model. The first few models trained for this project were based on the VGG architecture with a rewritten classifier layer to classify 102 categories of flowers instead of the 1000 categories of ImageNet. The results were okay with the validation accuracy reaching 83-85%. The problem with the initial model, or VGG models to be specific, is that they are huge in size. The VGG model I trained had a `.pth` file on the 500MB+ size which does not fit into the workspace for the submission of the notebook.

To solve the model size issue, I checked on the documentation again for the different pre-trained models available on torchvision and settled on he Densenet169 model as the basis since it had, for me, a good balance of size and Top 1 and Top 5 accuracy values. Again the classifier was rewritten for the model since this was a fixed feature extraction approach. I also change the hyperparameters for training as well, learning rate and the scheduler. The final submitted model had a validation accuracy of 93-94% at 55MB. This was a considerable improvement from the initial model of 83-85% at 500MB+.

## Results

To see how the model is doing on the test data we made a function to visualize both the actual image with the label and the resulting top 5 predictions of our model. The results are below.

<p align="center"><img src='.\images\2019-01-17 01_40_46-Image Classifier Project.ipynb - Colaboratory.png' width=500px alt = "results-Stemless_Gentian"></p>

<p align="center"><img src='.\images\2019-01-17 01_41_03-Image Classifier Project.ipynb - Colaboratory.png' width=500px alt = "poinsettia"></p>

There are categories where the model is almost certain of the category as seen in the Stemless Gentian example with a predicted probability of almost 1.0. On some categories where the data are much more limited the model still had a good top 1 prediction which is correct but only with a 0.38 probability while the rest of the predictions are scattered among the top 5.

## Possible Improvements

All in all this was a great project and challenge to be part of. The community of scholars were very accommodating and varied and the experience levels and nationalities so diverese that there is always someone in the community willing to answer or help another for issues on the lessons.

In terms of the project this was another eye opening project personally. I learned more about hyperparameter tuning, although I admit that I still have a lot to learn and will check out more possible iterations of this model. Another thing that I liked was that the model saved on the project can actually be deployed to a website or an app which was a good next step.

I was able to talk to another scholar regarding this project and he mentioned that he was able to achieve a high validation accuracy result by fine tuning the model instead of using it simply as a feature extractor. This would be my next objective for the next iteration of this project.