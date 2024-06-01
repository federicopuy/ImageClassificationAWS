# ImageClassificationAWS
Image Classification Workflow using AWS Sagemaker, Lambda and Step functions.

## Description
This project provides a step-by-step guide to classify a set of images obtained from the CIFAR dataset into their respective labels. In this case, it classifies whether the image is a bicycle or motorcycle. 

The notebook is divided into the following sections:

- Data Loading: Load the inference data from a JSON file.
- Data Processing: Extract and process the inference data and timestamps.
- Visualization: Create visualizations to monitor the model's performance.

## Data Staging
We obtain the data from the CIFAR dataset and transform it into a usable shape and format. We then upload the images into an S3 bucket.

## Model Training
Using the already labelled and loaded images, we train the model using sagemakers `Estimator`.

## Workflow creation
The inferences are saved into S3, and then are fed into a Step Function Workflow with the following AWS Lambdas:
A) Image Serializer
B) Image Classifier
C) Filter for low confidence scores

The definitions for these can be found in `lamba.py`. One is invoked as part of the Step Function:

<img width="1100" alt="Success Step function" src="https://github.com/federicopuy/ImageClassificationAWS/assets/12384264/4c8eb112-780a-420c-8bcc-4c28a6805df6">

## Visualizations
The outputs of the workflow are then extracted and visualized in a series of plots.

<img width="638" alt="Screenshot 2024-06-01 at 7 00 16 PM" src="https://github.com/federicopuy/ImageClassificationAWS/assets/12384264/07dbcd5a-5b4c-4137-9588-fe0118f385a7">
