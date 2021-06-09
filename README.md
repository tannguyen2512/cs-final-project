# Resized 2015 & 2019 Diabetic Retinopathy Detection

## About the dataset
The dataset includes images from the 2015 Diabetic Retinopathy Detection and APTOS 2019 Blindness Detection competitions. 



Each image has been resized and cropped to have a maximum size of 1024px. The code for resizing & cropping can be found here, and is based off of ilovescience's code.

For the 2015 images, a left and right field is provided for every subject. Images are labeled with a subject id as well as either left or right (e.g. 1_left.jpeg is the left eye of patient id 1). The 2019 images do not specify a subject or eye.

A clinician has rated each image for the severity of diabetic retinopathy on a scale of 0 to 4:

0 - No DR

1 - Mild

2 - Moderate

3 - Severe

4 - Proliferative DR
## Why I choose this topic ?

## Challenges of the dataset
### 1. Imbalance dataset
- **What is an imbalance dataset ?**

    A classification dataset is imbalance when the number of samples of classification classes are significantly different from each other.

    Imbalance dataset is usually encountered in medical (e.g. cancer, diabetes) or fraud detection.

- **How to deal with imbalance dataset ?**

    - Under sampling:
        
        ```Python
        from imblearn.under_sampling import NearMiss
        ```

        - Randomly remove a certain number of samples from majority classes, so that classes are more balanced

        - **Disadvantage**: under sampling should only be done when majority classes have a lot of samples to remove.

        - Most of the time, people do not prefer undersampling ????
    
    - Over sampling:

        ```python
        from imblearn.combine import SMOTETomek
        ```
        OR
        ```python
        from imblearn. over_sampling import RandomOverSampler
        ```
        - The opposite of under sampling: increase the number of samples in minority classes by creating more data points that are close to 

        - More efficient than under sampling, as we don't lose any data that we already have
        

### 2. Noise
Like any real-world data set, you will encounter noise in both the images and labels. Images may contain artifacts, be out of focus, underexposed, or overexposed. The images were gathered from multiple clinics using a variety of cameras over an extended period of time, which will introduce further variation.