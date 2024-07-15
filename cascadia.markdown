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

The fault is taken from Hayes et al., 2017, Tectonic summaries of magnitude 7
and greater earthquakes from 2000 to 2015,
[https://doi.org/10.3133/ofr20161192](https://doi.org/10.3133/ofr20161192). It
is divided in triangular patches. The coordinates of the three vertices of each
patch can be found
[here](https://github.com/Geolandi/cex/blob/main/Data/Cascadia/SSE/Fault/fault_triangular.txt).
The coordinates are given in longitude (degrees), latitude (degrees) and height
(km, negative values to indicate depth).

The results are organized in chronological order, listing on top the most recent
folder. Each folder contains the following variables:

  - X.mat
  - ICA.mat
  - slip.mat
  - slip_rate.mat

The file X.mat is a structure with the following fields:
  - 

The file ICA.mat is a structure with the following fields:
  - U: Spatial distribution of the ICs
  - S: Weights of the ICs
  - V: Temporal functions of the ICs
  - var_U: variance associated with each element of U
  - var_V: variance associated with each element of V
  - net: Full network result as outputted by vbICA
  - ind_sorting: Indices to sort the ICs with descending weights
  - ind_comps: Indices of the ICs selected for an inversion

To reconstruct the original time series you can multiply U, S and V<sup>T</sup>.
Each component is stored in a different column of U and V. S is a diagonal
matrix. The columns of U and V have unit norm, but are not orthogonal since they
are the result of an ICA and not of a PCA.

Within the net structure you can find all the details about the mix of Gaussians
and the other parameters making up the mixing matrix and the sources. There you
can also find all the a priori hyperparameters and the negative free energy
evolution.

[EarthScope Cascadia](/research/sses/cascadia/es/)

[Nevada Geodetic Laboratory Cascadia](/research/sses/cascadia/ngl)

[2024-05-19](https://github.com/Geolandi/cex/blob/main/Scenarios/Cascadia/2024-05-19)


<!-- {% include feature_row id="intro" type="center" %}

{% include gallery caption="This is a sample gallery with **Markdown support**." %}


{% include feature_row id="feature_row2" type="left" %}

{% include feature_row id="feature_row3" type="right" %}

{% include feature_row id="feature_row4" type="center" %} -->