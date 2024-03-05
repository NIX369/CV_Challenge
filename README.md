# CV_Challenge

Dataset Used: https://www.kaggle.com/datasets/kaustubhdikshit/neu-surface-defect-database

Observations about the dataset:

While, processing the data to create the tfrecords, I observed multiple issues with the dataset:

- There are missing xml annotation files for the respective image. (Ex: The image crazing_240.jpg is rpesent, but it's xml file is missing).
  
- Inconsistent file names in the xml annotations (Ex: patches_231 has the attribute file name specified as "patches_231.jpg", pitted_surface_125 has the attributed file name specified as "pitted_surface_125" with     no .jpg extension). While reading the images and their respective annotations while creating tf records, this costed more time for debugging the issue.
  
- The feature definition mentioned by you has some features such as: source_id, format, text, view and while parsing through the dataset, I observed that there were no such attributes in the xml annotations.
  
- Some xml annotations had missing labels and after generating the tf records, while passing these records as input to the Xception model, I faced some challenges as they were returing None (Empty values).

# Task 1: Generating tf records

Approaches to solve task1 (creating the tf records):
Multpile approaches were used to generate the tf records for each image file becuase of the above observations made to the dataset. 

Approach 1: Directly converting the xml annotations to tf records with help of the feature description.
    The code for this is mentioned in the notebook titled: XML_tfrecords.ipynb

Approach 2: Loading the xml annotations data to a CSV file then converting to tf records
    The code for this is mentioned in the notebook titled: XML_CSV_tfrecords.ipynb

Approach 3: Loading the xml annotations data to JSON format and then converting this to tf records
    The code for this is specified in the notebook titled: XML_JSON_tfrecords.ipynb

The tf records were generated in all 3 approaches. According to me, the right ones were generated from Approach 3.

# Task 2: Training the Xcpetion Model

I build the Xception model as specified and one major observation initially was, the DNN uses RGB input images of size (224x224). 
The dataset provided has the following size (200x200) & color_channel = 1; because of black and white images.

The neural network with the mentioned parameters are in the notebook: XML_tfrecords.ipynb

# Final Remarks:

It was an interesting challenge to detect defects on the stell surface using computer vision.

I am currently in the middle of the final exams of my Master's degree and I was not able to put in the full time to create a new dataset and fix the issues as mentioned above.
I learnt a lot through this challenge and would like to discuss more about this in the further rounds. :)
