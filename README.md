# Localization of Fetal Head in Ultrasound Images



### Background

During pregnancy, ultrasound imaging is  used to measure fetal biometrics. One of these measurements is the fetal head circumference (HC). The HC can be used to estimate the gestational age and monitor growth of the fetus. The HC is measured in a specific  cross section of the fetal head, which is called the standard  plane.

### Data Description

The dataset a total of 1334 two-dimensional  (2D) ultrasound images of the standard plane that can be used to measure the HC.

The data for this challenge can be downloaded from Zenodo, [DOI 10.5281/zenodo.1322001](https://doi.org/10.5281/zenodo.1322000) 

The data is divided into a training set of  999 images and a test set of 335 images. The size of each 2D ultrasound  image is 800 by 540 pixels with a pixel size ranging from 0.052 to 0.326 mm. The pixel size for each image can be found in the csv files:  ‘training_set_pixel_size_and_HC.csv’ and ‘test_set_pixel_size.csv’. The  training set also includes an image with the manual annotation of the  head circumference for each HC, which was made by a trained sonographer. The csv file 'training_set_pixel_size_and_HC.csv ' includes the head  circumference measurement (in millimeters) for each annotated HC in the  training set. All filenames start with a number. There are 999 images in the trainingset, but the filenames only go to 805. Some ultrasound  images were made during the same echoscopic examination and have  therefore a very similar appearance. These images have an additional  number in the filename in between "_" and "HC" (for example 010_HC.png  and 010_2HC.png).

Source: https://hc18.grand-challenge.org/

![sample](/static/fc_region.png)

*Samples from Dataset, first row showing Ultrasound images and second row showing the Fetal Head region*

### Network Archiecture

![network](/static/network.png)

Z. Sobhaninia, A. Emami, N. Karimi and S. Samavi, "Localization of Fetal Head in Ultrasound Images by Multiscale View and Deep Neural Networks," *2020 25th International Computer Conference, Computer Society of Iran (CSICC)*, 2020, pp. 1-5, doi: 10.1109/CSICC49403.2020.9050094.

### Loss Function
w(x) * BCE + DiceLoss

*where*

w(x) is weighting representation, which will enlarge gradient loss on boundaries of  fetal  head  regions.

### Data Preprocessing

1. Data Augmentation
   1. Vertical Flipping
   2. Horizontal Flipping
   3. Rotation, Range (-30, 30)
   4. Resize to 240 x 240
2. MinMax Scaling

### Prediction

![sampleprediction](/static/sample_prediction.png)

### TODO

1. Train on orginal resolution
2. Compute the following
   1. Dice Score
   2. Absolute Difference (ADS)
   3. Hausdorff Distance (HD)

### References

https://ieeexplore.ieee.org/document/9050094

https://github.com/e-lab/pytorch-linknet

http://jaidevd.com/posts/weighted-loss-functions-for-instance-segmentation/

https://zenodo.org/record/1327317

https://hc18.grand-challenge.org/

