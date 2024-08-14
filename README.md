# MSc_Dissertation_DroughtAnalysis
This repository shows the code used to plot the figures for the dissertation: "How Climate Change affects Droughts in South America – Copula-Based Drought Analysis with an Event Attribution Case Study".

Here is an overview of the provided codes with a short descibtion:
* calc_SPEI_obs_era5.ipynb - Calculates the SPEI values for ERA5
* calc_SPEI_obs_mswep.ipnb - Calculates the SPEI values for MSWEP/MSWX
* calc_SPEI_CMIP6.ipnb - Calculates the SPEI values for the CMIP6 models
* Im_Methods.ipynb - Creates the figures used in the shown in the methodology section
* Im_SPEI6_era5_MarginalCheck.ipynb - Creates the figure visualising the marginal distribution fitting

In order to use this framework, it is necessary to run the code in a certain order, as some of the code uses data stored in the above structure. This enumeration should be seen as a sort of recipe for how to use what is provided.

1. Run the code calc_SPEI_obs_era5.ipynb and calc_SPEI_obs_mswep.ipynb to test the different marginal distributions for each region. This code must be run 3 times for the different aggregation periods (1, 6 and 12) in order to store the necessary values and to check the distrbutions each time. The place to change the aggregation is indicated in the code under "Define aggregation time".

2. Run the code calc_SPEI_CMIP6.ipynb to calculate and safe the SPEI values for the CMIP6 models. This code must be run 3 times for the different aggregation periods (1, 6 and 12) and also for all 8 CMIP6 in order to store the necessary values. The place where to change the model and the aggregation period is indicatd in the code. It is also possible to just safe the code 8 times, each time with a different chosen model to have a better overview.

3. Now the other codes can be run in any order.

Furthermore, in order for the code to work properly, it is important that the directory structure is the same described below. This is necessary because the code builds on each other and values are stored and loaded in specific directories. This is done to be able to do the analysis on the data, as some of the calculations, for example the SPEI values, take hours to days depending on the resolution of the model. The structure must be as follows:
```
\data:
  \AR6_regions:
    \shapefiles # here the IPCC AR6 reference regions needs to be stored as a shapefile. These are given in the repository as well.
    \obs:
      \era5:
        \eff_precip # stores the values for the evaluation
        \model data # contains t2m, tmax, tmin, pr data
        \model_data_attr # contains t2m, tmax, tmin, pr data containing the time period of the extreme drought event
        \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
        \extended_nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times containing the time period of the extreme drought event
      \mswep_mswx:
        \eff_precip # stores the values for the evaluation
        \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
        \extended_nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times containing the time period of the extreme drought event
        \mswep_pr # contains the preciptation data
        \mswep_tmax # contains the tmax data
        \mswep_tmin # contains the tmin data
        \mswep_pr_nrt # contains the preciptation data containing the time period of the extreme drought event
        \mswep_tmax_nrt # contains the tmax data containing the time period of the extreme drought event
        \mswep_tmin_nrt # contains the tmin data containing the time period of the extreme drought event
  \CMIP6:
    \ACCESS-CM2:
      \eff_precip # stores the values for the evaluation
      \model_data # contains t2m, tmax, tmin, pr data
      \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
      \results_sev_given_T_D # contains the severity values for a drought of a given return period and a given Duration, necessary in order to plot the SDF curves
    \ACCESS-ESM1-5:
      \eff_precip # stores the values for the evaluation
      \model_data # contains t2m, tmax, tmin, pr data
      \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
      \results_sev_given_T_D # contains the severity values for a drought of a given return period and a given Duration, necessary in order to plot the SDF curves
    \CanESM5:
      \eff_precip # stores the values for the evaluation
      \model_data # contains t2m, tmax, tmin, pr data
      \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
      \results_sev_given_T_D # contains the severity values for a drought of a given return period and a given Duration, necessary in order to plot the SDF curves
    \FGOALS-g3:
      \eff_precip # stores the values for the evaluation
      \model_data # contains t2m, tmax, tmin, pr data
      \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
      \results_sev_given_T_D # contains the severity values for a drought of a given return period and a given Duration, necessary in order to plot the SDF curves
    \IPSL-CM6A-LR:
      \eff_precip # stores the values for the evaluation
      \model_data # contains t2m, tmax, tmin, pr data
      \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
      \results_sev_given_T_D # contains the severity values for a drought of a given return period and a given Duration, necessary in order to plot the SDF curves
    \MIROC6:
      \eff_precip # stores the values for the evaluation
      \model_data # contains t2m, tmax, tmin, pr data
      \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
      \results_sev_given_T_D # contains the severity values for a drought of a given return period and a given Duration, necessary in order to plot the SDF curves
    \MRI-ESM2-0:
      \eff_precip # stores the values for the evaluation
      \model_data # contains t2m, tmax, tmin, pr data
      \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
      \results_sev_given_T_D # contains the severity values for a drought of a given return period and a given Duration, necessary in order to plot the SDF curves
    \NorESM2-LM:
      \eff_precip # stores the values for the evaluation
      \model_data # contains t2m, tmax, tmin, pr data
      \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
      \results_sev_given_T_D # contains the severity values for a drought of a given return period and a given Duration, necessary in order to plot the SDF curves
  \attribution:
    \synthesis_files_climate_explorer # contains the synthesis files which contain the calculated model-ensemble and intermodel spread, the file is downloaded from the "https://climexp.knmi.nl/synthesis.cgi" website

```

