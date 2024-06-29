# A Global Open-Source Dataset of Monthly Irrigated and Rainfed Cropped Areas (MIRCA-OS) for the 21st Century
This dataset is an update of MIRCA2000. Utilizing a data library of subnational crop-specific irrigated and rainfed harvested area statistics combined with global gridded land cover products, we developed a global gridded (5-arcminute) irrigated and rainfed cropped area (MIRCA-OS) dataset for the years 2000 to 2015 for 23 crop classes.

This repository provides all the necessary code to downscale subnational harvested area statistics to 5-arcminute resolution grid cell areas.

## Repository Structure
The repository has two main components:

data/ - Includes all the input datasets used to generate the MIRCA-OS dataset.

code/ - Includes the Jupyter notebooks used to generate and validate the MIRCA-OS dataset. The code has four main components: preprocessing, downscaling, mosaicking, and validation.

## Preprocessing

We used several gridded input datasets, including the GAEZ annual harvested area gridded map (HA), the area equipped for irrigation (AEI), the HYDE cropland extent (CE), crop calendar, and the area of each grid cell. In this part of the code:

-We generated a five arcminute grid cell area in hectares.
-Clipped and reprojected all input datasets according to the target area.
-Extracted the planting and maturity month of each spatial unit from the gridded crop calendar.

## Downscaling
This part of the code provides detailed Python-based language code used to downscale national/subnational statistics to 5-arcminute resolution grid cells. The procedure includes:

-Uploading the crop calendar.

-Sorting the areas based on ranking priority.

-Following seven distinct iterative and sequential steps: four to allocate irrigated areas and three for rainfed areas.

While downscaling, the highest priority was given to ensure the sum of crop-specific irrigated area at each grid cell is lower than or equal to the AEI. For any amounts of harvested area that remained to be allocated within the administration unit after meeting this highest priority, we then spatially distributed these harvested areas to maximize the consistency of each grid's crop-specific irrigated and rainfed areas with CE and HA.

## Mosaicking
The downscaling code will generate a TIFF file for each spatial unit according to their unit code. This part of the code enables the mosaicking of the rasters to generate a global map. Besides, the code that is used to convert the monthly aggregated TIFF files into annual TIFF files is also included in this section.

## Validation
The MIRCA-OS dataset has been validated against all available global and regional crop-specific irrigation area datasets. Global validation was done against the MIRCA2000 dataset and the GloRice (I) dataset, while regional validation was performed against EIM2010, and national level validation was done against MIRAD-CropScape and GLAD datasets. Details of the validation codes are summarized in this section.

Contributors

Endalkachew Abebe Kebede

Kevin Ong’are Oluoch

Dr. Kyle Frankel Davis 

## Contact

Please contact Endalkachew Kebede (endiabe@udel.edu) or Kyle Davis (kfdavis@udel.edu) for any questions.
