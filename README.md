# Fawkes' Tracker

In this repository I'm going to test the Fawkes (https://github.com/Shawn-Shan/fawkes) software to see how it protects user's privacy against Facial Recogntion (FR) system. Microsoft Azure Cognitive Service will be used as FR. This is a service package including many other sub-services, I will use the face service in this case (https://docs.microsoft.com/en-us/azure/cognitive-services/face/).

From left-to-right: Original train image - cloak with min mode - cloak with high mode - test image 
<p align='center'>
  <img src='https://github.com/minha12/test_fawkes/blob/master/imm/train/01-1m.jpg' width='200'>
  <img src='https://github.com/minha12/test_fawkes/blob/master/imm/train_min/01-1m_min_cloaked.png' width='200'>
  <img src='https://github.com/minha12/test_fawkes/blob/master/imm/train_high/01-1m_high_cloaked.png' width='200'>
  <img src='https://github.com/minha12/test_fawkes/blob/master/imm/test/01-6m.jpg' width='200'>
</p> 

## Dataset

IMM dataset (https://www2.imm.dtu.dk/~aam/datasets/datasets.html) will be used. This dataset includes:
- 40 identities 
- Each identity has 6 images on different poses, emotions and light condition.
- There are 240 images in total. Train/Test set ratio will be 5/1 meaning that for each identity, 5 images will be used for training (these 5 image will be 'cloaked' by Fawkes software before using for training) 1 remaining image (uncloaked) will be used for testing.

## Step-by-step:
- Step1: Split train/test dataset (200/50 images)
- Step2: Generate cloaked images from the train set. These cloaked images can be found in folder 'imm/train_min' or 'imm/train_high' depending on the '-mode' set to 'min' or 'high' while cloaking.
- Step3: Train FR model using Microsoft Azure Cognitive Service
- Step4: Using test images to test the identitification capability. 

## Quick view of result with '-mode min'

```
Identifying faces in 01-6m.jpg
Succesfull identifed with confidence:  0.83565
Identifying faces in 02-6m.jpg
Succesfull identifed with confidence:  0.78883
Identifying faces in 03-6m.jpg
Succesfull identifed with confidence:  0.79678
Identifying faces in 04-6m.jpg
Succesfull identifed with confidence:  0.7752
Identifying faces in 05-6m.jpg
Succesfull identifed with confidence:  0.76879
Identifying faces in 06-6m.jpg
Succesfull identifed with confidence:  0.86857
Identifying faces in 07-6m.jpg
Succesfull identifed with confidence:  0.7365
Identifying faces in 08-6f.jpg
Succesfull identifed with confidence:  0.73986
Identifying faces in 09-6m.jpg
Succesfull identifed with confidence:  0.79151
Identifying faces in 10-6m.jpg
Succesfull identifed with confidence:  0.7982
```

## What the numbers said
The result showed that cloaking 100% of training images can reduce identification capability of FR, however, with ```-mode=min```, 100% identities have been re-indentified with confidence in range [0.55272, 0.87816]. 

<p align='center'>
  <img src='https://github.com/minha12/test_fawkes/blob/master/confidence_hist.png' width='400'>
</p> 

Turining into ```-mode=high```, 47,5% of identities has not been re-identified while the remaining can still be re-indentified with confidence ranging in [0.51044, 0.63938].


