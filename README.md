# TIME SERIES CLASSIFICATION

All image processing, model training and inference were done using
[Orfeo ToolBox](orfeo-toolbox.org) 
[Monteverti Application](orfeo-toolbox.org/CookBook/Monteverdi.html)

## Image Preparation:
1. Images were masked using SCL for cloud and no data.
2. Vegetation Index (VI) NDVI, NDMI and SAVI were calculated.
3. VI's were stacked and missing data were gap-filled 
   using linear interpolation.
4. Images were rescaled based on histogram clipping 2% from upper and lower limit
and stretched between 0 and 1 for each date.
   


## Data Structure
Original Training polygons dataset were split into 3 set of train and validation 80/20 (using [QGIS](https://qgis.org/en/site/))

**1. [TRAINING_DATA](./TRAINING_DATA):** Contains zonal statistics (mean, max, min and std) for 
training and validation set from all images from Jan 2020 to Dec 2021 (142 Images)

**2. [TESTING DATA](./TESTING_DATA):** Contains zonal statistics (mean, max, min and std) for testing
set from images from Jan 2020 to Dec 2021 (142 Images) 

## Model Training

Random Forest model was trained using 4 variables (mean, std, max, min) from 
Dec 20 till May 21 (6 months) ('i.e., column value starting with value '_67' till '_101'). 
All the three set were used for training and validation

Total variables used for model training 
(variables * Time series data between Dec 2020 to May 2021) 
= 4 * 35 = 140

**[MODEL](./MODEL)**: Contains trained RF and confusion matrix from each training

Model Training was done using [Monteverti Application](orfeo-toolbox.org/CookBook/Monteverdi.html)'s
[TrainVectorClassifer](https://www.orfeo-toolbox.org/CookBook/Applications/app_TrainVectorClassifier.html#trainvectorclassifier)

## Model Prediction

**[PREDICT](./PREDICT)**: Prediction result for testing dataset

For running inference use [Monteverti Application](orfeo-toolbox.org/CookBook/Monteverdi.html)'s
[VectorClassifer](https://www.orfeo-toolbox.org/CookBook/Applications/app_VectorClassifier.html)

## Reference: 
- [Classification](https://www.orfeo-toolbox.org/CookBook/recipes/pbclassif.html)






