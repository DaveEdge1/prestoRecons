# Presto Reconstruction Input Standards

## Paramaters

### File format
yaml (.yml)

### Parameter keys
Paramter keys follow a naming convention of underscore-separated lowercase terms with the first word being a grouping term and the second word being a specific, unique term as in: group_specific
grouping terms come from a controlled set and include: recon, time, prior, proxy, geo, model, uncertainty
verbose specific terms such as "range_to_reconstruct" are allowed and take the form: time_range_to_reconstruct

#### PReSto grouping terms
recon: parameters relating to the reconstruction broadly, eg. the climate variable to reconstruct
time: parameters relating to time, eg. temporal resolution and interval for reconstruction
prior: parameters relating to Bayesian priors, eg. percentage of the prior states to assimilate
proxy: parameters relating to proxies, eg. seasonality of proxies to assimilate
geo: parameters relating to geospatial, eg. coordinate bounds of proxy records to gather
model: paramters relating to climate models, eg. choice of linear_global or linear_spatial processing
uncertainty: paramters relating to error and confidence intervals, eg. choice of confidence interval width

#### PReSto specific terms
Please make an effort to conform specific terms to those used in existing PReSto reconstructions. New terms may occassionaly be added due to novelty of specific parameters.

### Parameter Values
Each paramter key holds 10 key:value pairs
value: null
default: null
limits: null
options: [linear_global, linear_spatial]
precision: null
long_name: Processing the model prior
description: details at 
data_type: character
complexity: experimental
URL: null
Include bounds for numeric, list of possible values for strings (eg. bounds: [12000, 0])
Include description of each key (eg. description: “The start year of the reconstruction in yr BP”)
Include boolean flag for advanced-user parameters (eg. advanced: FALSE)


### Data
should be pulled rather than living in container
allows for new data, limits container size
