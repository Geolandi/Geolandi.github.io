---
layout: splash
title: Cascadia
permalink: /research/sses/cascadia/
feature_row:
  - image_path: /assets/images/sse_cascadia.png
    alt: "Cascadia"
    title: "Cascadia"
    excerpt: ""
---

{% include feature_row %}

[Results with EarthScope time series for Cascadia](/research/sses/cascadia/es/)

The results are organized in chronological order, listing on top the most recent
folder. Each folder contains the following variables:

  - `X.mat`
  - `ICA.mat`
  - `ind_comps.mat`
  - `misfit_comps.mat`
  - `options.mat`

The file `X.mat` contains a structure named `Xd` with the following fields:
  - `name`: Cell of size equal to the number of time series containing the
    string name of each time series (first 4 characters of a string
    corresponding to the station name, fifth character is either "e" or "n" or
    "u" to indicate that it is the East, North or Up direction, respectively).
  - `type`: Cell of the same size as name, containing the type of data (in this
    case, they are GPS3 + the letter "e", "n" or "u" to indicate the direction).
  - `llh`: Matrix of size number of time series x 3, with longitude, latitude
    and height for each time series.
  - `timeline`: Vector of size number of epochs containing the timeline in
    decimal years.
  - `decmode`: String indicating the decomposition mode (always `T-mode` here).
  - `ts`: Matrix of size number of time series x number of epochs containing the
    detrended and offsets corrected position time series, used as input for
    vbICA.
  - `var_ts`: Same as `ts`, but containing the variance associated with the
    observations.
  - `data_mask`: Boolean matrix of the same size of `ts`, with a value of `0` if
    the data is missing and a value of `1` if the data is observed.
  - `unit`: String indicating the observation unit of the time series (mm).
  - `time_unit`: String indicating the observation unit of the timeline (yr).
  - `centering_offsets`: Vector containing the offset for each time series
    removed to make it zero-mean.

The file `ICA.mat` is a structure with the following fields:
  - `U`: Spatial distribution of the ICs
  - `S`: Weights of the ICs
  - `V`: Temporal functions of the ICs
  - `var_U`: variance associated with each element of U
  - `var_V`: variance associated with each element of V
  - `net`: Full network result as outputted by vbICA
  - `ind_sorting`: Indices to sort the ICs with descending weights

To reconstruct the original time series you can multiply `U`, `S` and
`V`<sup>`T`</sup>. Each component is stored in a different column of `U` and `V`.
`S` is a diagonal matrix. The columns of `U` and `V` have unit norm, but are not
orthogonal since they are the result of an ICA and not of a PCA.

Within the net structure you can find all the details about the mix of Gaussians
and the other parameters making up the mixing matrix and the sources. There you
can also find all the a priori hyperparameters and the negative free energy
evolution.
  
The file `ind_comps.mat` is a structure containing a single field:
  - `ind_comps`: A vector with the indices of the ICs selected for an inversion
    based on the analysis of the Power Spectral Density (PSD). A second
    selection is further performed with post-processing scripts, but I calculate
    the best inversion smoothing parameter for all these components.

The file `misfit_comps.mat` is a structure containing a single field:
  - `misfit_comps`: A matrix with the values of the misfit calculated with a
    leave-one-out procedure at the tested smoothing parameters. The size is
    number of tested smoothing parameters x number of inverted ICs.

The file `options.mat` is a structure containing a single field:
  - `options`: This is a structure containing all the options used in the
    analysis, from the download to the inversion. It is essential to reproduce
    the results.


The fault is taken from Hayes et al., 2017, Tectonic summaries of magnitude 7
and greater earthquakes from 2000 to 2015,
[https://doi.org/10.3133/ofr20161192](https://doi.org/10.3133/ofr20161192). It
is divided in triangular patches. The coordinates of the three vertices of each
patch can be found
[here](https://github.com/Geolandi/cex/blob/main/Data/Cascadia/SSE/Fault/fault_triangular.txt).
The coordinates are given in longitude (degrees), latitude (degrees) and height
(km, negative values to indicate depth). The position of the stations is
provided in the stored results, so that it is possible to calculate the Greens'
functions and quickly run the inversion with the optimal parameters. The
selected stations may differ from one day to another, and saving the Greens'
function for every day would be very space consuming. Calculating the Greens'
functions on-the-fly is quite quick (see also the `Julia` implementation for
post-processing).

<!-- [Nevada Geodetic Laboratory Cascadia](/research/sses/cascadia/ngl) -->

<!-- [2024-05-19](https://github.com/Geolandi/cex/blob/main/Scenarios/Cascadia/2024-05-19) -->


<!-- {% include feature_row id="intro" type="center" %}

{% include gallery caption="This is a sample gallery with **Markdown support**." %}


{% include feature_row id="feature_row2" type="left" %}

{% include feature_row id="feature_row3" type="right" %}

{% include feature_row id="feature_row4" type="center" %} -->