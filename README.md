# MSc_Dissertation_DroughtAnalysis
This repository shows the code used to plot the figures for the dissertation: "How Climate Change affects Droughts in South America – Copula-Based Drought Analysis with an Event Attribution Case Study".

In order for the code to work properly, it is important that the directory structure is the same as in this repository. This is necessary because the code builds on each other and values are stored and loaded in specific directories. This is done to be able to do the analysis on the data, as some of the calculations, for example the SPEI values, take hours to days depending on the resolution of the model. The structure must be as follows:
```
\data:
  \AR6_regions:
    \obs:
      \era5:
        \eff_precip #stores the values for the evaluation
        \model data #contains t2m, tmax, tmin, pr data
        \model_data_attr #contains t2m, tmax, tmin, pr data containing the time period of the extreme drought event
        \nSPEI_HG85_cal1980_2010 #contains the calculated SPEI values for all regions and aggregation times
        \extended_nSPEI_HG85_cal1980_2010 #contains the calculated SPEI values for all regions and aggregation times containing the time period of the extreme drought event
      \mswep_mswx:
        \eff_precip #stores the values for the evaluation
        \nSPEI_HG85_cal1980_2010 #contains the calculated SPEI values for all regions and aggregation times
        \extended_nSPEI_HG85_cal1980_2010 #contains the calculated SPEI values for all regions and aggregation times containing the time period of the extreme drought event
        \mswep_pr # contains the preciptation data
        \mswep_tmax # contains the tmax data
        \mswep_tmin # contains the tmin data
        \mswep_pr_nrt # contains the preciptation data containing the time period of the extreme drought event
        \mswep_tmax_nrt # contains the tmax data containing the time period of the extreme drought event
        \mswep_tmin_nrt # contains the tmin data containing the time period of the extreme drought event
```
In order to use this framework, it is necessary to run the code in a certain order, as some of the code uses data stored in the above structure. This enumeration should be seen as a sort of recipe for how to use what is provided.

```
1. Run the code for SPEI_obs_era5.ipynb and SPEI_obs_mswep.ipynb to test the different marginal distributions for each region. This code must be run 3 times for the different aggregation periods (1, 6 and 12) in order to store the necessary values and to check the distrbutions each time. The place to change the aggregation is indicated in the code under "Define aggregation time".

2.  
```
