# An Analysis of Bike Safety in London
by AJ Bishop, Ben Cote, Jacob Freyermuth, Greg McCracken, and Daniel Tuthill (Bristlecone Team)
This project was completed for the Erdos Institute Data Science Bootcamp, Fall 2022.

We built a comprehensive dataset of bike accidents and safety features in Greater London, United Kingdom. We then used this dataset to determine whether shared bus and bike lanes were as safe as segregrated bus lanes.

---

This README covers the dataset creation, clustering analysis on shared bus and bike lanes, and initial regressive and classification analyses.

## Table of contents
1. [Dataset Creation](#dataset)
    1. [Public Dataset Sourcing](#sourcing)
    2. [Dataset Matching](#matching)
2. [Clustering](#clustering)
3. [Additional Analyses](#additional)
    1. [Regression](#regression)
    2. [Classification](#classification)

## Dataset Creation <a name="dataset"></a>

### Public Dataset Sourcing <a name="sourcing"></a>

The dataset is created from three publically accessible datasets. **Due to their large size, these datasets are not stored in this repository**:
1. [cycling_safety_uk_gov.csv](https://zenodo.org/record/5603036#.Y49yTXbMJD9)<br/>
This dataset contains all accidents in the United Kingdom involving bikes from 2005-2018. This is a processed version of [Road Safety Data](https://www.data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data) produced for the [CYCLANDS](https://www.nature.com/articles/s41597-022-01333-2) collection.
![collisions](/Dataframe_creation/Plots/collisions.png)

2. [dft_traffic_counts_aadf.csv](https://roadtraffic.dft.gov.uk/downloads)<br/>
This dataset contains the traffic annual average daily flows (aadf) for most roads in the United Kingdom from 2000-2021. More information on the dataset can be found [here](https://storage.googleapis.com/dft-statistics/road-traffic/all-traffic-data-metadata.pdf).
![traffic_counters](/Dataframe_creation/Plots/traffic_counters.png)

3. [cycle_lane_track.json](https://cycling.data.tfl.gov.uk/)
This dataset contains the location and classification of all bike lanes in Greater London. More information on the dataset can be found [here](https://cycling.data.tfl.gov.uk/CyclingInfrastructure/documentation/asset_information_guide.pdf).
![bike_lanes](/Dataframe_creation/Plots/bike_lanes.png)

### Dataset Matching <a name="matching"></a>

The three public datasets are geographically matched using two nearest neighbor algorithms in [geomatch.ipnyb](/Dataframe_creation/geomatch.ipynb). First all bike lanes features within 0.1 miles of an aadf countint point are matched. Then all collisions in Greater London are matched to counting points. Road names are used as a threshold for accident matching, checking aadf counter points nearest neighbors by increasing distance from the accident until a successful match is found. This notebook outputs two new datasets:
1. combined_collisions_v3.csv: All collisions in Greater London from 2005-2018 with an associated aadf count (if matched) and bike lanes.
2. aadf_features_london_colyears.csv: All aadf counting points in Greater London with associated bike lanes.

Using these two new datasets, accident counts at each aadf counter point are aggregrated, and a final dataset which lists all aadf counter points in Greater London, their associated bike lanes, and the number of collisions and severity information at each counter point from 2005-2018 is created in [BuildRoadDataframe_v3p1.ipynb](/Dataframe_creation/BuildRoadDataframe_v3p1.ipynb). This dataset is output as df_road_v3p1_zeros.csv.

Other datasets found in /Dataframe_creation are:
1. aadf_year_meta.csv: Meta data for dft_traffic_counts_aadf.csv
2. longs_lats.npz: All features extracted from cycle_lane_track.json stored as .npz for ease of access

## Clustering <a name="clustering"></a>
k-means clustering analysis is performed in [kmeans_SharedBusLanes.ipynb](erdos_AU22_bristlecone/Analysis/Clustering/kmeans_SharedBusLanes.ipynb). This notebook shows the clustering implementation, k selection, interpretation of resulting clusters, and example application using the "urban-bikeways" cluster to study the safety of shared bus/bike lanes in Greater London.

## Additional Analyses <a name="additional"></a>

