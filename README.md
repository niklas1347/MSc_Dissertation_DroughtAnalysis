# MSc_Dissertation_DroughtAnalysis
This repository shows the code used to plot the figures for the dissertation: "How Climate Change affects Droughts in South America – Copula-Based Drought Analysis with an Event Attribution Case Study".

Here is an overview of the provided codes with a short descibtion:
* mscthesis_nm_drought.yml - This is the working environment which can be used to run the code.
* Im_Methods.ipynb - Creates the figures used in the shown in the methodology section.
* calc_SPEI_obs_era5.ipynb - Calculates the SPEI values for ERA5.
* calc_SPEI_obs_mswep.ipnb - Calculates the SPEI values for MSWEP/MSWX.
* calc_SPEI_CMIP6.ipnb - Calculates the SPEI values for the CMIP6 models.
* Im_SPEI6_era5_MarginalCheck.ipynb - Creates the figure visualising the marginal distribution fitting.
* Im_Eval_Spatial_Seasonal.ipynb - Creates the figure visualising the spatial and seasonal evaluation for all 7 IPCC AR6 regions.
* Im_Eval_Distribution.ipynb - Creates the figure visualising the distributional evaluation for all 7 IPCC AR6 regions.
* Im_Res1_SPEI_AR6regions_Era5.ipynb - Creates the figure visualising the SPEI time series for the three aggregation periods and the 7 IPCC AR6 regions.
* Im_Res1_CMIP6_SDF.ipynb - Creates the figure visualising the SDF curves for the Drought Analysis.
* Im_Res1_CMIP6_DA.ipynb - Creates the figure visualising the Drought Atlas for South America.
* Im_Attr_SPEI_SpatialExtent_obs_era5.ipynb - Creates the figure visualising the spatial extent of the drought event for SPEI-6 and SPEI-12. It also determines the specific drought charactersitics (duration, severity, beginning, end) of the drought event according to ERA5.
* Attr_SPEI_obs_mswep.ipynb - Determines the specific drought charactersitics (duration, severity, beginning, end) of the drought event according to MSWEP/MSWX.
* Im_Attr_SDF_obs_era5_mswep.ipynb - Creates the figure visualsing the SDF curves of the observational model and determines the return period of the Extreme Drought Event according to the observational model
* Im_Attr_CMIP_SDF.ipynb - Creates the figure visualsing the SDF curves of the CMIP6 model for the Extreme Event Attribution. It also calculates the return period for the analysed Extreme Event based on the drought charactersitics obtained through the two observational models.
* Attr_SPEI6_PR.ipynb - Calculates the Probability Ratios for the CMIP6 models based on SPEI-6. Provides the mean, upper and lower values for each scenario and each model. The results can then be used to calculate the model-ensemble using the "https://climexp.knmi.nl/synthesis.cgi" website.
* Attr_SPEI12_PR.ipynb  - Calculates the Probability Ratios for the CMIP6 models based on SPEI-12. Provides the mean, upper and lower values for each scenario and each model. The results can then be used to calculate the model-ensemble using the "https://climexp.knmi.nl/synthesis.cgi" website.
* Im_Attr_probRatios.ipynb - Creates the figures visualises the Probability Ratio. This code uses the result files from the "https://climexp.knmi.nl/synthesis.cgi" website.

In order to use this framework, it is necessary to run the code in a certain order, as some of the code uses data stored in the structure described below. This enumeration should be seen as a sort of "recipe":

1. Run the code calc_SPEI_obs_era5.ipynb and calc_SPEI_obs_mswep.ipynb to test the different marginal distributions for each region. This code must be run 3 times for the different aggregation periods (1, 6 and 12) in order to store the necessary values (SPEI Timeseries) and to check the distrbutions each time. The place to change the aggregation is indicated in the code under "Define aggregation time".

2. Run the code calc_SPEI_CMIP6.ipynb to calculate and safe the SPEI values for the CMIP6 models. This code must be run 3 times for the different aggregation periods (1, 6 and 12) and also for all 8 CMIP6 in order to store the necessary values (SPEI timeseries and Severity for a drought of a given return period and duration). The place where to change the model and the aggregation period is indicatd in the code. It is also possible to just safe the code 8 times, each time with a different chosen model to have a better overview.

3. For the Attribtutin codes the (indicated by Attr) it is important to run IM_Attr_SpatialExtent_obs_era5_nSPEI.ipynb and Attr_SPEI_obs_mswep.ipynb first to get the drought characteristics (duration and severity) based on the observation models. In addition, Attr_SPEI6_PR.ipynb and Attr_SPEI12_PR.ipynb must be run before Im_Attr_probRatios.ipynb, using the "https://climexp.knmi.nl/synthesis.cgi" website in between to obtain the required input files.

4. For the other codes there is no specifc order as long as the steps 1. and 2. are performed before.

Also, for the code to work properly, it is important that the directory structure is the same as described below. This is necessary because the code builds upon on each other and values are stored and loaded in specific directories. This is done in order to be able to perform analysis on the data, as some of the calculations, such as the SPEI values, take hours to days depending on the resolution of the model. The structure must be as follows:
```
\data:
  \AR6_regions:
    \shapefiles # here the IPCC AR6 reference regions needs to be stored as a shapefile. These are given in the repository as well.
    \obs:
      \era5:
        \eff_precip # stores the values for the evaluation
        \model data # contains t2m, tmax, tmin, pr data
        \model_data_attr # contains t2m, tmax, tmin, pr data including the time period of the extreme drought event
        \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
        \extended_nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times including the time period of the extreme drought event
      \mswep_mswx:
        \eff_precip # stores the values for the evaluation
        \nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times
        \extended_nSPEI_HG85_cal1980_2010 # contains the calculated SPEI values for all regions and aggregation times including the time period of the extreme drought event
        \mswep_pr # contains the preciptation data
        \mswep_tmax # contains the tmax data
        \mswep_tmin # contains the tmin data
        \mswep_pr_nrt # contains the preciptation data including the time period of the extreme drought event
        \mswep_tmax_nrt # contains the tmax data including the time period of the extreme drought event
        \mswep_tmin_nrt # contains the tmin data including the time period of the extreme drought event
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

The necessary data (tas, tasmin, tasmax and pr) can be downloaded from the following sides:
* ERA5: https://climexp.knmi.nl/
* MSWEP/MSWX: https://www.gloh2o.org/
* CMIP6:  https://aims2.llnl.gov/search/, recommended tool: sydna package (https://docs.nesi.org.nz/Scientific_Computing/Supported_Applications/Synda/)

