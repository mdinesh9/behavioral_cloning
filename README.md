[//]: # (Image References)

[video1]: ./output_videos/output.mp4 "Video"

# Behavioral Cloning

1. Submission includes all required files and can be used to run the simulator in autonomous mode

    - My submission includes the following codes
        - model.py containing the script to create and train the model
        - drive.py for driving the car in autonomous mode
        - model.h5 containing a trained convolution neural network

2. Submission includes functional code

    - Using the Udacity provided simulator and my drive.py file, the car can be driven autonomously around the track by executing
        - python drive.py model.h5

3. Submission code is usable and readable

    - Submission code is usable and readable
        - Code is available in simulator_model.ipynb

### Model Architecture and Training Strategy

1. An appropriate model architecture has been employed



_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
lambda_1 (Lambda)            (None, 160, 320, 3)       0         
_________________________________________________________________
cropping2d_1 (Cropping2D)    (None, 65, 318, 3)        0         
_________________________________________________________________
conv2d_1 (Conv2D)            (None, 31, 157, 24)       1824      
_________________________________________________________________
conv2d_2 (Conv2D)            (None, 14, 77, 36)        21636     
_________________________________________________________________
conv2d_3 (Conv2D)            (None, 5, 37, 48)         43248     
_________________________________________________________________
conv2d_4 (Conv2D)            (None, 3, 35, 64)         27712     
_________________________________________________________________
conv2d_5 (Conv2D)            (None, 1, 33, 64)         36928     
_________________________________________________________________
flatten_1 (Flatten)          (None, 2112)              0         
_________________________________________________________________
dense_1 (Dense)              (None, 100)               211300    
_________________________________________________________________
dropout_1 (Dropout)          (None, 100)               0         
_________________________________________________________________
dense_2 (Dense)              (None, 50)                5050      
_________________________________________________________________
dense_3 (Dense)              (None, 10)                510       
_________________________________________________________________
dense_4 (Dense)              (None, 1)                 11        
=================================================================
Total params: 348,219
Trainable params: 348,219
Non-trainable params: 0


2. Attempts to reduce overfitting in the model

    - I added a dropout layer which is one of the regularization technique to reduce overfitting and tested it on the similator.

3. Model parameter tuning

    - I used Adam optimizer with 0.001 learning rate

4. Appropriate training data

    - I collected the following types of training data by using simulator in training mode

        - Driving front - center of the track
        - Driving front - left of the track
        - Driving front - right of the track
        - Driving front - recovering from side lanes
        - Driving back of the track - left and right of the track

### Model Architecture and Training Strategy

1. Solution Design Approach

    - Training and Validation data
        - Once I collected the raw data from simulation, I divided the data into 70% for training and 30% for testing.

    - Directory structure:
        - I did not include the raw data in the git because of the size. The directory structure is:
            - data
                - IMG
                - driving_log.csv
                    - This file consists of data points related to:
                        - images - center, left, right
                        - steering angle, throttle, brake, and speed


    - Data preprocessing
        - I cropped the bottom and top part of the image because, its just noise for the neural network because of the presence of many unnecessary objects.
    
    - Data Augmentation
        - In order to increase the amount of training data and help the neural network learn from different angle, I am flipping all the images.

### Videos

Behavioral cloning output - [click here][video1]