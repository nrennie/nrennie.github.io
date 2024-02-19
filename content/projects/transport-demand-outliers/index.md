---
title: "Transport demand outliers"
subtitle: ""
excerpt: ""
date: 2024-02-01
weight: 8
author: "Nicola Rennie"
draft: false
categories:
  - Research
  - Statistics
layout: single
image: featured.png
---

My research interests lie in statistics, data science, and operational research - with a focus on applications to health data. I'm also interested in research into the way we teach statistics and data science, particularly on aspects related to accessibility and reproducibility of teaching materials.

My previous research focused on the development and use of functional analysis for detecting outliers in time series data. We have performed case studies on multiple empirical data sets including railway booking data and bike-sharing usage data. 

A blog post giving an overview of my PhD thesis is available on [my website](https://nrennie.rbind.io/blog/2021-10-06-detecting-demand-outliers-in-transport-systems/).

### Overview of PhD project

- borrow from blogpost
- link to GitHub
- link to relevant pubs
- add quarto report on bikehsaring here
- add data vis bike sharing

I recently completed my PhD at STOR-i CDT at Lancaster University. My thesis was titled "Detecting demand outliers in transport systems" and here I'll (try to) give a brief overview of the work I've done in the last three years. The final version of my thesis can be found [here](https://eprints.lancs.ac.uk/id/eprint/160845/1/2021renniephd.pdf).

### What are demand outliers?

An outlier is generally considered an abnormal event that doesn't fit with the pattern of events normally observed. In the transport setting, demand outliers might mean that there are a lot more (or less) passengers than normal, or that they book earlier than normal, or that passengers are willing to pay more than they normally would for the same ticket. There are many things that can cause these changes in demand such as, football matches, weather, or public holidays. Some of these events e.g. Christmas, are known about in advance and can be accounted for in the planning process. Others are not known about. And it's these changes in demand that we want to identify. Ideally, they'd be identified as early as possible, in order for the transport company to take action. 

It's important to detect changes in demand for multiple reasons. Transport companies set prices and ticket availability based on forecasts of demand. If the demand no longer matches the forecasts, then the prices that have been set are no longer optimal. Then transport companies lose revenue. It could also result in transport services being busier than expected. If you've ever gotten on a packed train and been unable to get a seat, you know that incorrectly managed demand isn't desirable for passengers either.

At the moment, many transport companies employ analysts to monitor the number of bookings. However, as human beings, we're not very good at spotting things by eye, and we tend to see patterns that don't exist. My research develops a statistical method to identify demand outliers and send alerts to analysts.

### So, how do we find the outliers?

Most transport providers store information about bookings as a time series. For example, for train ABC departing on January 31 at 10:00, there is a series of observations of how many passengers had booked tickets by 3 months per departure, 1 month before departure, 1 week before departure ... You get the idea. *Note: I'll mainly be talking about trains here, but it's all generalisable to other types of transport systems.

So for a set of departures, we would have a collection of time series that might look a bit like this:
<p align="center">
<img src="bookings.jpg?raw=true">
</p>

To detect outliers within this set of time series, we use *functional analysis*. Functional analysis treats each time series of bookings as an observation of a continuous function. We calculate the *functional depth* of the time series of bookings for each train. I won’t go into all of the details about the equations for calculating the functional depth because they’re not very nice. But generally, depth measures provide us with an ordering of the time series -- where the time series closest to the centre i.e., the median, has the highest depth, and that in the tails of the distribution i.e. outliers, have low depth. This allows to consider both changes in magnitude (e.g. a big increase in bookings), and shape of booking patterns (e.g. passengers booking earlier than normal). Outliers are detected by setting a threshold for the functional depth. Any time series with a functional depth below that threshold is classified as an outlier.

Of course, we don't just want to identify demand outliers in historic data (although this can still be beneficial on its own). We want to identify these outliers as they are happening, so that an analyst can make an adjustment. We found that forecasting the bookings still to come in, and performing the outlier detection on the forecasted bookings, helped us to identify the outliers earlier. 

### Thinking about transport systems

The vast majority of, if not all, transport systems do not simply consist of a single journey from A to B. There are often many places where passengers can start and end their journey, and multiple combinations to get between the two. It's quite unlikely that any demand changes will only affect one single part of the transport network e.g. a single leg of a train journey. It's also quite unlikely that the entire network will be affected by demand changes in the same way at the same time. Before even thinking about demand outliers, we developed a method split up the network into clusters that experience demand in similar ways. Our outlier detection method could then be applied jointly to legs in the same cluster which are likely to share common outliers. 

<p align="center">
<img src="featured.png?raw=true">
</p>

During my PhD, I collaborated with Deutsche Bahn, the German rail provider, and was able to test the methods developed on their data. We tested our methodology on a section of the Deutsche Bahn network consisting of two train lines - (i) from Munich to Hamburg and (ii) from Basel in Switzerland to Berlin. Generally, legs in the same train line were clustered together, and the edges of the clusters coincided with major train stations.

### A venture into bike-sharing

Of course, it's not all about trains. There are many other industries where detecting and accounting for systematic changes of demand is of interest. One of those industries is bike-sharing -- where members of the public can pick-up a bike at a terminal and return it to any other terminal. Most bike-sharing systems are located in cities. Since some areas of a city are more populous than others, the bikes must be redistributed from the terminals that are commonly used as drop-offs to those that are commonly used for pick-ups. Although, a responsive approach could be taken to redistributing bikes i.e. only sending drivers to a terminal when it is full or empty, this isn't very efficient. 

<p align="center">
<img src="bikes.png?raw=true">
</p>

If we are able to identify and predict when unusual demand patterns occur, bike-sharing companies can better organise their resources. A case study of the Capital Bikeshare system in Washington D.C. finds that there are spatial and temporal patterns to the outliers that occur. 

### Final Thoughts

Overall, a key finding of my thesis is that functional data analysis is a very powerful tool for identifying demand outliers. However, features of the data such as network effects or seasonal patterns need to be taken into account first. More research into how an outlier-based alert system could be implemented in an automated way is still needed.

## Related publications

**Outlier detection in network revenue management.** <br>
**N. Rennie**, C. Cleophas, A. M. Syksulski, F. Dost. *OR Spectrum*. 2023. doi: [doi.org/10.1007/s00291-023-00714-2](https://doi.org/10.1007/s00291-023-00714-2).

**Analysing and visualising bike sharing demand with outliers.** <br>
**N. Rennie**, C. Cleophas, A. M. Syksulski, F. Dost. *Discover Data*. Volume 1, Issue 1. March 2023. doi: [doi.org/10.1007/s44248-023-00001-z](https://doi.org/10.1007/s44248-023-00001-z)

**Identifying and responding to outlier demand in revenue management.** <br>
**N. Rennie**, C. Cleophas, A. M. Syksulski, F. Dost. *European Journal of Operational Research*. Volume 293, Issue 3, 16 September 2021, 1015-1030. doi: [doi.org/10.1016/j.ejor.2021.01.002](https://doi.org/10.1016/j.ejor.2021.01.002).

**Detecting demand outliers in transport systems** <br>
**N. Rennie**. *PhD Thesis*. 2021. doi: [doi.org/10.17635/lancaster/thesis/1448](https://doi.org/10.17635/lancaster/thesis/1448).


