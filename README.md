# MSc_Dissertation_DroughtAnalysis
This repository shows the code used to plot the figures for the dissertation: "How Climate Change affects Droughts in South America – Copula-Based Drought Analysis with an Event Attribution Case Study".

In order for the code to funciton properly it is important the structure of the directories is the same than in this repository. This is necessary the code build up on each other and values are stored and loaded in specified directories. This is done in order to do the analysis with the data as some of the calculations, for example of the SPEI values, need hours to days depending on the resolution of the model. The structure needs to be as follows:
```
\data:
  \AR6_regions:
    \obs:
      \era5:
        \eff_precip #stores the values for the evaluation
        \model data #contains t2m, tmax, tmin, pr data
        \nSPEI_HG85_Clair_cal1980_2010 #contains the calculated SPEI values for all regions and aggregation times
        \model_data_attr #contains t2m, tmax, tmin, pr data containing the time period of the extreme drought event
```
