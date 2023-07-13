# Presto Reconstruction Input Standards

## Paramaters

### File format
yaml (.yml)  
comments in document will be preserved, but not visible to GUI form users

see a complete example of the yaml input file here: [Holocene_DA_parameters.yml](https://github.com/DaveEdge1/prestoServer/blob/1e8b9bb4e6b3498fbb10154257c5c10fdb14e7c7/Holocene_DA_parameters.yml)

see the corresponding GUI form here: [Customize Holocene DA Parameters](http://68.183.108.187:85/holocene_da/username/dce725/domainname/gmail.com/configloc/manual)

### Parameter keys
Paramter keys follow a naming convention of underscore-separated lowercase terms with the first word being a grouping term and the second word being a specific, unique term as in: group_specific  
grouping terms come from a controlled set and include: recon, time, prior, proxy, geo, model, uncertainty  
verbose specific terms such as "range_to_reconstruct" are allowed and take the form: time_range_to_reconstruct  

#### PReSto grouping terms
* recon: parameters relating to the reconstruction broadly, eg. the climate variable to reconstruct  
* time: parameters relating to time, eg. temporal resolution and interval for reconstruction  
* prior: parameters relating to Bayesian priors, eg. percentage of the prior states to assimilate  
* proxy: parameters relating to proxies, eg. seasonality of proxies to assimilate  
* geo: parameters relating to geospatial, eg. coordinate bounds of proxy records to gather  
* model: paramters relating to climate models, eg. choice of linear_global or linear_spatial processing  
* uncertainty: paramters relating to error and confidence intervals, eg. choice of confidence interval width  

#### PReSto specific terms
Please make an effort to conform specific terms to those used in existing PReSto reconstructions. New terms may occassionaly be added due to novelty of specific parameters.  

### Parameter Values
Each paramter holds 10 key:value pairs  
values required by all data types denoted by **bold typescript**  
  
* **value**: the parameter input, to be adjusted as desired  
* **default**: the default parameter input, does not change  
* limits: upper and lower bounds (inclusive) for value key, required for numeric, lat-lon, and range data_type, eg. [0,12000]  
* options: list of valid choices for value key, required for character and list data types, eg. [linear_global, linear_spatial]  
* precision: minimum possible increment between valid options for value key, required for numeric, lat-lon and range data types, eg. 0.1  
* **long_name**: displayed parameter name for GUI, eg. time interval for reconstruction  
* **description**: notes for the user, eg. define a start and end year in units years BP  
* **data_type**: type of parameter, informs design of GUI form (see section below for deatils and options), eg. character  
* **complexity**: level of understanding required to make use of the parameter (details is section below), eg. experimental  
* URL: web page with additional information, eg. https://lipdverse.org/vocabulary/paleodata_proxy/  

### Parameter data type
The data type controls the strucure of the form element in the "Reconstruction Parameters" GUI, which is automatically generated from the yaml file. For instance, a "numeric" data type is given a range-slider form element.  
  
free-form:  
&nbsp;&nbsp;additonal requirement: none  
&nbsp;&nbsp;form element: text box  
&nbsp;&nbsp;example: experiment name
&nbsp;&nbsp;&nbsp;&nbsp;default: default
  
boolean:  
&nbsp;&nbsp;additonal requirement: none  
&nbsp;&nbsp;form element: radio buttons (true/false)  
&nbsp;&nbsp;example: Allow the mean of the prior to change through time  
&nbsp;&nbsp;&nbsp;&nbsp;default: false  
  
character:  
&nbsp;&nbsp;additional requirements: options  
&nbsp;&nbsp;form element: radio buttons allow user to select one from a list of options  
&nbsp;&nbsp;example: reconstruction in absolute or relative values 
&nbsp;&nbsp;&nbsp;&nbsp;default: relative  
&nbsp;&nbsp;&nbsp;&nbsp;options: [relative, absolute]  
  
list:  
&nbsp;&nbsp;additional requirements: options  
&nbsp;&nbsp;form element: check boxes allow user to select multiple from a list of options  
&nbsp;&nbsp;example: models used for prior   
&nbsp;&nbsp;&nbsp;&nbsp;default: ['hadcm3_regrid','trace_regrid']  
&nbsp;&nbsp;&nbsp;&nbsp;options: ['hadcm3_regrid','trace_regrid','famous_regrid']  
  
numeric:  
&nbsp;&nbsp;additional requirements: limits, precision  
&nbsp;&nbsp;form element: range slider and linked numeric input box  
&nbsp;&nbsp;example: minimum resolution of proxies  
&nbsp;&nbsp;&nbsp;&nbsp;default: 200  
&nbsp;&nbsp;&nbsp;&nbsp;limits:  [10, 1000]  
&nbsp;&nbsp;&nbsp;&nbsp;precision: 10  
  
range:  
&nbsp;&nbsp;additional requirements: limits, precision  
&nbsp;&nbsp;form element: dual range slider and linked numeric input boxes (min/max)  
&nbsp;&nbsp;example: minimum resolution of proxies
&nbsp;&nbsp;&nbsp;&nbsp;default: [3000,5000]  
&nbsp;&nbsp;&nbsp;&nbsp;limits:  [0,12000]  
&nbsp;&nbsp;&nbsp;&nbsp;precision: 1  
  
lat-lon:  
&nbsp;&nbsp;additional requirements: limits, precision  
&nbsp;&nbsp;form element: dual range slider and linked numeric input boxes (min/max)  
&nbsp;&nbsp;example: coordinate bounds for assimilating proxies  
&nbsp;&nbsp;&nbsp;&nbsp;default: [-90, 90, -180, 180]  
&nbsp;&nbsp;&nbsp;&nbsp;limits:  [-90, 90, -180, 180]  
&nbsp;&nbsp;&nbsp;&nbsp;precision: 0.001  

### Parameter complexity
Parameter complextity has three options: standard, advanced, experimental.
  
standard: displayed in GUI form by default, simplest parameters

advanced: displayed in GUI if "show advanced parameters" checkbox is selected, deeper understanding required

experimental: can not be adjusted through GUI form, exceedingly deep understanding necessary and/or may break code
  
## Data
Data should be pulled from a curated repository such as lipdverse.org each time the reconstruction is run rather than being saved in the container. This allows for newly generated data to be incorporated, and limits container size.  
