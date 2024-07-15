---
layout: splash
title: Slow Slip Events
permalink: /research/sses/
feature_row:
  - image_path: /assets/images/sse_cascadia.png
    alt: "Real-time slow slip events spatio-temporal history"
    title: "Cascadia"
    excerpt: "[Results](/research/sses/cascadia/)"
---

{% include feature_row %}


The general goal of the analyses here presented is to provide a near real-time
slow slip spatio-temporal history. The results are not fully real-time because
they depend on the available GNSS data products (i.e., position time series
processed by other institutes). The spatio-temporal history includes not only
the times of slip, but every epoch available in the surface position time
series.

Currently, the analysis is performed based on data from the [Nevada Geodetic
Laboratory](http://geodesy.unr.edu) (NGL) or
[Earthscope](https://www.earthscope.org) (ES). The list of times at which
instrumental or tectonic offsets may have affected a station is taken from the
NGL's [Master Steps Database](http://geodesy.unr.edu/NGLStationPages/steps.txt).

In this page you can find the various scenarios (e.g., Cascadia) that I am
currently running. For each scenario you will find a description of the files.

The analysis involves three steps.

  - Time series correction
  - Time series decomposition
  - Inversion of selected components


**Time series correction**

The GNSS position time series are corrected for:
  - blunders
  - outliers
  - offsets
  - linear trend

Offsets and linear trend are estimated with an iterative trajectory model
approach. The model includes also seasonal terms (annual and semi-annual) as
well as post-seismic terms (exponential relaxation), but these are not corrected
from the time series because their actual temporal evolution is likely very
different from the idealized aforementioned functions.

<!-- {% include feature_row id="intro" type="center" %}

{% include gallery caption="This is a sample gallery with **Markdown support**." %}


{% include feature_row id="feature_row2" type="left" %}

{% include feature_row id="feature_row3" type="right" %}

{% include feature_row id="feature_row4" type="center" %} -->