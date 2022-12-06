# An Analysis of Bike Safety in London
by AJ Bishop, Ben Cote, Jacob Freyermuth, Greg McCracken, and Daniel Tuthill (Bristlecone Team)
This project was completed for the Erdos Institute Data Science Bootcamp, Fall 2022.

We built a comprehensive dataset of bike accidents and safety features in Greater London, United Kingdom. We then used this dataset to determine whether shared bus and bike lanes were as safe as segregrated bus lanes.

---

This README covers the dataset creation, clustering analysis on shared bus and bike lanes, and initial regressive analyses.

## Table of contents
1. [Dataset Creation](#dataset)
2. [Clustering](#paragraph1)
    1. [Sub paragraph](#subparagraph1)
3. [Regression](#paragraph2)

## Dataset Creation <a name="dataset"></a>

### Public Dataset Sourcing

The dataset is created from three publically accessible datasets:
1. [cycling_safety_uk_gov.csv](https://zenodo.org/record/5603036#.Y49yTXbMJD9)<br/>
This dataset contains all accidents in the United Kingdom involving bikes from 2005-2018. This is a processed version of [Road Safety Data](https://www.data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data) produced for the [CYCLANDS](https://www.nature.com/articles/s41597-022-01333-2) collection. Contained information can be found at the dataset source or within the [geomatch.ipnyb](erdos_AU22_bristlecone/Dataframe_creation/geomatch.ipynb) notebook.

2. [dft_traffic_counts_aadf.csv](https://roadtraffic.dft.gov.uk/downloads)<br/>


3. [cycle_lane_track.json](https://cycling.data.tfl.gov.uk/)
