# Swing or Take? *Predicting MLB Strikes*

[Michael Jordan](https://www.linkedin.com/in/michaeljoshuajordan/)  
February 2020 

![cover image](images/coverimage.png)

## Table of Contents
* [Overview and Motivation](#overview-and-motivation)
* [Methodology](#methodology)
* [Tools and Technologies](#tools-and-technologies)
* [Acknowledgments](#acknowledgments)

## Overview and Motivation
Making solid contact with a pitch thrown in Major League Baseball (MLB) is one of the hardest things to do in professional sports.
- **Problem**: *How can a batter optimize their chance of making solid contact during an at bat?*

Arguably, one of the most important variables that makes hitting a pitch difficult is not knowing whether the pitch will be thrown within the strike zone (be called a strike) or outside of it (be called a ball). Generally, a pitch thrown within the strike zone is easier to hit than one one that is thrown outside the strike zone.
- **Goal:** *Predict whether a major league pitch will be a called strike or not in order to recommend whether a batter should swing or take the pitch with less than 2 strikes in the count.*


## Methodology 
Implementation of this project involved: 

1. Obtain pitch-level data for every pitch thrown during the 2015-2018 MLB regular seasons, where each row represents a single pitch. Datasets were procured from [Kaggle](https://www.kaggle.com/pschale/mlb-pitch-data-20152018#games.csv) as the following 3 csv files:  
      a. **atbats.csv**  
      b. **pitches.csv**  
      c. **games.csv** 

2. Create a single master dataframe containing the metadata from the images scraped from both The Met and MoMA. [Code found here.](https://github.com/jordanm3/street-art-to-fine-art/blob/master/data_collection/metadata_final.ipynb)

3. Train a convolutional neural network autoencoder. Perform dimensionality reduction by taking the images of my corpus and passing them through 3 convolutional and pooling layers that learn the image’s features. Produce a narrow encoded layer that contains the lowest possible dimensions of the input data, allowing comparison between images to be computationally feasible. [Code found here.](https://github.com/jordanm3/street-art-to-fine-art/blob/master/models/autoencoder_model.ipynb)

4. Use the narrow encoded layer to encode the corpus of fine art images and a test street art image, resulting in a set of feature tensors. Use cosine similarity to compare the street art image to every fine art image in the corpus to find the most visually similar matches. [Code found here.](https://github.com/jordanm3/street-art-to-fine-art/blob/master/models/image_comparison.ipynb) 

5. Develop a Flask web application that allows a user to upload an image of street art from their computer. Return the top 3 pieces of fine art that the autoencoder model determines are the best matches. Files used in the app include:  
      a. [Flask python code](https://github.com/jordanm3/street-art-to-fine-art/blob/master/flask_files/imagecomparison.py)  
      b. [Home page](https://github.com/jordanm3/street-art-to-fine-art/blob/master/flask_files/index.html)  
      c. [Results page](https://github.com/jordanm3/street-art-to-fine-art/blob/master/flask_files/results.html)

## Tools and Technologies


## Acknowledgments
