# Diabetic Retinopathy Detection on color fundus image 

[Link to dataset](https://www.kaggle.com/c7934597/resized-2015-2019-diabetic-retinopathy-detection)

## Motivation
- Diabetes is a chronic disease that occurs when human body cannot produce or effectively use insulin to regulate a proper level of blood sugar.
- In 2014, there are 422 million adults get diabetes. Prevalence has been rising more rapidly in low- and middle-income countries than in high-income countries. [(WHO)](https://www.who.int/news-room/fact-sheets/detail/diabetes).
- Overtime, diabetes can result in several complications, such as heart attack, kidney failure, amputation and blindness
- Diabetic Retinopathy (DR) is one of the global leading causes of blindness. It is a condition caused by diabetes, that damages the eye's retina gradually, and can lead to permanent blindness if left untreated.
- Put it simple, among 3 people have diabetes, one can get DR. And among 10 people with DR, 1 can vision-threatening DR [(source)](https://www.youtube.com/watch?v=EnmbYbGxyuc&list=PL0kc7lQdKnHp_dBNgwSCxi3Vrvrms1k4B&index=3&ab_channel=Docplexus)
- Get diagnosed and treated in early stages of DR can significantly reduce the risk of vision loss.
- Diagnosis process usually acquires specialized machine to capture the image of the retina and a trained doctor to diagnosis the photo [(link)](https://www.youtube.com/watch?v=M6IlOKXlCqs&list=PL0kc7lQdKnHp_dBNgwSCxi3Vrvrms1k4B&index=5&ab_channel=NationalEyeInstitute%2CNIHNationalEyeInstitute%2CNIH), which is not always accessible for the many, especially in low and middle-income countries.
- Applying machine learning to detect DR helps reduce significantly time, cost, and requirements in diagnosing DR
- Beside, I simply wanna try something in the medical domain

## Use case in a general: 
- After the fundus color image is taken by a technician with a specialized machine, the image can be croped and resize, then put in the model. The model will predict if the patient has DR or not, and which stage it is.

## About the dataset
The dataset includes images from the [2015 Diabetic Retinopathy Detection](https://www.kaggle.com/c/diabetic-retinopathy-detection) and [APTOS 2019 Blindness Detection competitions](https://www.kaggle.com/c/aptos2019-blindness-detection).
Each image has been resized and cropped to have a maximum size of 1024px. The data can be downloaded directly from Kaggle, but will requires some organizing to unify the 2 datasets into one.

For the 2015 images, a left and right field is provided for every subject. Images are labeled with a subject id as well as either left or right (e.g. 1_left.jpeg is the left eye of patient id 1). The 2019 images do not specify a subject or eye.

A clinician has rated each image for the severity of diabetic retinopathy on a scale of 0 to 4:

0. No DR
1. Mild non-proliferative DR (NPDR)
2. Moderate NPDR
3. Severe NPDR
4. Proliferative DR

## Some challenges of the dataset and solutions in mind
### 1. Imbalance dataset
Class 0 accounts for the majority of data, which the typical case of medical data.

Possible solutions:
    - Over sampling: increase the number of samples in minority classes by creating more data points (e.g. SMOTE technique)
    - Choosing performance metrics:
        - Accuracy is not suitable for imbalance dataset. 
        - False negative can be more costly than false positive, as we don't want DR patient left unchecked => probably consider recall as metrics
        - Some papers use "quadratic weighted kappa"
    - Image augmentation


### 2. Noise
Noise and variation are introduced in various ways: 
- Data comes from 2 different datasets. 
- Dataset was gathered from a variety of clinical cameras
- Image may contain artifacts, be out of focus, underexposed, or overexposed

Possible solutions:
- Enhance constrast: histogram equalizer
- Counter inherent background noise: min-max normalization
- Other noise reducing technique, but meanwhile, maintain the detail to detect DR
- Image augmentation

## Model selection:
- AlexNet
- ResNet
- GoogleNet
- Inception
- PCA 

## Demo expectation:
- Model with at least 90 accuracy / recall
- Probably have a streamlit to upload a fundus image and predict it

## Timeline:
Done:
- Understand DR.
- Understand the traditional process of DR diagnose
- Find references
First week:
- Ready some well-cited papers on the topic, identify pros and cons
- Build the pipeline
- Try with some transfer learning
Second week:
- Pick up one to fine tune, augmenting
- Streamlit
