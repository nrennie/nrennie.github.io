---
title: "Dashboards"
subtitle: ""
excerpt: "A selection of interactive applications and dashboards developed using R and Python."
date: 2024-03-28
weight: 8
author: "Nicola Rennie"
draft: false
categories:
  - Dashboards
  - Shiny
layout: single
image: featured.png
---

## Project description

I have developed several dashboards and applications, covering a variety of topics and uses.

{{< dashboard-section "/projects/dashboards/tidytuesday.png" >}}
### [#TidyTuesday](https://nrennie.rbind.io/tidytuesday-shiny-app/)
An app that displays every [#TidyTuesday](https://github.com/rfordatascience/tidytuesday) plot I’ve created, with functionality to search by packages used in creating the plots and links to the original code and data, that updates by itself whenever I create a new plot. This app is deployed using Shinylive for R, meaning it runs in the user's web browser and does not require an R server. Read my [blog post](https://nrennie.rbind.io/blog/webr-shiny-tidytuesday/) describing the process of building and deploying this Shiny app.
{{< /dashboard-section >}}



{{< dashboard-section "/projects/dashboards/shinytweet.png" >}}
### [Outlier Detection](https://github.com/nrennie/OutlierApp)

An R shiny dashboard based on my PhD research to detect outliers in functional time series data occurring in a network in an online setting. Accompanies the paper titled ["Detecting outlying demand in multi-leg bookings for transportation networks"](https://arxiv.org/abs/2104.04157).
{{< /dashboard-section >}}



{{< dashboard-section "/projects/dashboards/shinytweet.png" >}}
### [Life Expectancy](https://github.com/nrennie/Significance/tree/main/Were_not_getting_any_younger_Or_should_that_be_older)
An R shiny dashboard to accompany my Significance article [We’re not getting any younger! Or should that be older?](https://www.significancemagazine.com/science/723-we-re-not-getting-any-younger-or-should-that-be-older) which investigates trends in life expectancy.
{{< /dashboard-section >}}



{{< dashboard-section "/projects/dashboards/shinytweet.png" >}}
### [aRt](https://github.com/nrennie/nrennie_aRt)
An R shiny application to generate and download generative art created in R.
{{< /dashboard-section >}}



{{< dashboard-section "/projects/dashboards/shinytweet.png" >}}
### [shinytweet](https://github.com/nrennie/shinytweet)
A simple R shiny application to browse tweets related to R, Python, and data science. This app uses GitHub actions to automatically update data and redeploy the shiny app.

Read my [blog post](https://nrennie.rbind.io/blog/automatically-deploying-a-shiny-app-for-browsing-rstats-tweets-with-github-actions/) about creating, deploying, and updating this Shiny app for more information.
{{< /dashboard-section >}}
