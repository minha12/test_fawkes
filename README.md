# Test fawkes

In this repository I'm going to test the Fawkes (https://github.com/Shawn-Shan/fawkes) software to see how it protects user's privacy against Facial Recogntion (FR) system. Microsoft Azure Cognitive Service will be used as FR. This is a service package including many other sub-services, I will use the face service in this case (https://docs.microsoft.com/en-us/azure/cognitive-services/face/).

## Dataset

IMM dataset (https://www2.imm.dtu.dk/~aam/datasets/datasets.html) will be used. This dataset includes:
- 40 identities 
- Each identity has 6 images on different poses, emotions and light condition.
- There are 240 images in total. Train/Test set ratio will be 5/1 meaning that for each identity, 5 images will be used for training (these 5 image will be 'cloaked' by Fawkes software before using for training) 1 remaining image (uncloaked) will be used for testing.

## Step-by-step:
- Step1: Split train/test dataset (200/50 images)
- Step2: Generate cloaked image from the train set. There cloaked images can be found in folder 'imm/train_min' or 'imm/train_high' depending on the '-mode' set to 'min' or 'high' while cloaking.
- Step3: Train FR model using Microsoft Azure Cognitive Service
- Step4: Using test images to test the identitification capability. 

## Quick view of result with '-mode min'
```
Identifying faces in 17-6m.jpg
Succesfull identifed with confidence:  0.70441
Identifying faces in 35-6f.jpg
Succesfull identifed with confidence:  0.71688
Identifying faces in 05-6m.jpg
Succesfull identifed with confidence:  0.76879
Identifying faces in 22-6f.jpg
Succesfull identifed with confidence:  0.69649
Identifying faces in 26-6m.jpg
Succesfull identifed with confidence:  0.87816
Identifying faces in 34-6m.jpg
Succesfull identifed with confidence:  0.78223
Identifying faces in 31-6m.jpg
Succesfull identifed with confidence:  0.74775
Identifying faces in 38-6m.jpg
Succesfull identifed with confidence:  0.71601
Identifying faces in 02-6m.jpg
Succesfull identifed with confidence:  0.78883
Identifying faces in 06-6m.jpg
Succesfull identifed with confidence:  0.86857
Identifying faces in 07-6m.jpg
Succesfull identifed with confidence:  0.7365
Identifying faces in 11-6m.jpg
Succesfull identifed with confidence:  0.79475
Identifying faces in 32-6m.jpg
Succesfull identifed with confidence:  0.7848
Identifying faces in 30-6f.jpg
Succesfull identifed with confidence:  0.8192
Identifying faces in 39-6m.jpg
Succesfull identifed with confidence:  0.68639
Identifying faces in 20-6m.jpg
Succesfull identifed with confidence:  0.7155
Identifying faces in 16-6m.jpg
Succesfull identifed with confidence:  0.55272
Identifying faces in 18-6m.jpg
Succesfull identifed with confidence:  0.86173
Identifying faces in 36-6m.jpg
Succesfull identifed with confidence:  0.73877
Identifying faces in 37-6m.jpg
Succesfull identifed with confidence:  0.74653
Identifying faces in 12-6f.jpg
Succesfull identifed with confidence:  0.70208
Identifying faces in 21-6m.jpg
Succesfull identifed with confidence:  0.73285
Identifying faces in 14-6f.jpg
Succesfull identifed with confidence:  0.79513
Identifying faces in 23-6m.jpg
Succesfull identifed with confidence:  0.76362
Identifying faces in 19-6m.jpg
Succesfull identifed with confidence:  0.7652
Identifying faces in 28-6m.jpg
Succesfull identifed with confidence:  0.75379
Identifying faces in 15-6f.jpg
Succesfull identifed with confidence:  0.72639
Identifying faces in 33-6m.jpg
Succesfull identifed with confidence:  0.71798
Identifying faces in 24-6m.jpg
Succesfull identifed with confidence:  0.78832
Identifying faces in 25-6m.jpg
Succesfull identifed with confidence:  0.73501
Identifying faces in 29-6m.jpg
Succesfull identifed with confidence:  0.82223
Identifying faces in 03-6m.jpg
Succesfull identifed with confidence:  0.79678
Identifying faces in 04-6m.jpg
Succesfull identifed with confidence:  0.7752
Identifying faces in 40-6m.jpg
Succesfull identifed with confidence:  0.81176
Identifying faces in 13-6m.jpg
Succesfull identifed with confidence:  0.74826
Identifying faces in 08-6f.jpg
Succesfull identifed with confidence:  0.73986
Identifying faces in 01-6m.jpg
Succesfull identifed with confidence:  0.83565
Identifying faces in 27-6m.jpg
Succesfull identifed with confidence:  0.6546
Identifying faces in 10-6m.jpg
Succesfull identifed with confidence:  0.7982
Identifying faces in 09-6m.jpg
Succesfull identifed with confidence:  0.79151
```
