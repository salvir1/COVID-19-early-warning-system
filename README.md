# COVID Early Warning System Project Overview

This project is an attempt to define a good early warning indicator for COVID outbreaks. States and public health agencies have a difficult job to keep COVID transmission under control. One of the keys to control is a system that provides them an early and accurate warning of an increase in new COVIC infections in their jurisdiction. How good is the data that they are currently using at providing that early indiactor? Is there a way to improve upon the timeliness and accuracy of the warning?

This project grew out of an interest to compare the available data from states that had experienced an outbreak vs. states that hadn't experienced an outbreak. As the analysis progressed it became clear that the common statistical measures of COVID-19 infection spread that are utilized today--total cases, case rates, and positive test rates--all have their shortcomings. The first part of this project explores the shortcomings with the measures that are currently available. Not all 
of the shortcomings are equal. The study identifies the one metric that most clearly and consistently correlates with outbreaks-albeit not as quickly or definitively as desired.

## Part 2: An Alternative COVID Early Warning System

The first part of this project (described [here](https://github.com/salvir1/part-1-covid-outbreak-analysis)) informs this second part--a proposed alternative regional COVID-19 early warning system. This second part addresses some of the shortcomings of the currently available tools to provide an earlier and more certain warning of an increase in new COVID infections. Simulations of these alternative concepts are modeled to compare its theoretical improvement in performance over current options. Ideally, a system like this could ultimately allow state governments and public health agencies a more accurate picture of COVID prevalence in their jurisdictions so that they know when they need to respond to keep an uptick from turning into an outbreak. That is the focus of this repo.

## Goals

The high level goals of this project are:
- To characterize the difference at the regional level between an uptick and an outbreak in COVID case rates (described [here](https://github.com/salvir1/part-1-covid-outbreak-analysis))
- To develop statistics that could become the foundation of a COVID-19 earling warning system
- To work with various EDA and data visualization tools and techniques

## Tools and techniques used in this project

**Tools**
- Python, Jupyter Lab, SciKitLearn, Pandas, Numpy

**Visualization**
- Plotly, Matplotlib

**Techniques**
- Time series, clustering, spatial mapping, simple moving average, linear regression, simulation

## Raw data sourced from COVID Tracking Project

- Terms of use: The COVID Tracking Project at The Atlantic’s data and website content is published under a Creative Commons CC BY 4.0 license, which requires users to attribute the source and license type (CC BY 4.0) when sharing our data or website content.
- Citation: [the COVID Tracking Project](https://www.covidtrackingproject.com), Creative Commons CC BY 4.0 license

# Can we create a better COVID Early Warning System?

This notebook proposes variations of a COVID Early Warning System meant to address the shortcomings in current approaches.These variations are designed to create a *surveillance* system that measures the prevalence of undiagnosed COVID infections as opposed to statistics that rely on a haphazard mix of tests from confirmatory diagnoses of symptomatic people and screening tests from asymptomatic people. The statistics for these models are also designed using common statistical process techniques to allow for more certain decision-making.

## A quick review

The first section of this project highlighted a number of shortcomings with the current methods used to monitor COVID infections in the general population ([click here](https://github.com/salvir1/part-1-covid-outbreak-analysis) for details).

- Perhaps the most common statistic quoted by the popular press is the sum of positive tests. This statistic is a poor signal for what is going on. Case rate is a more accurate measure. Positive test rate has a high rate of variability and isn't as good as case rate.
- When an outbreak occurs, new active infections increase faster than what the data shows. Current positive diagnoses only capture a portion of all infections. The actual number of new infections is 2.5 times or more larger. The slope of the actual outbreak curve compared to the observed curve is that much steeper. 
- Old news is not good news. It can be many days from the time someone infected with COVID develops symptoms and when a positive test enters a tracking dataset.
- Haphazardly mixing two very different test populations into one dataset adds uncertainty. Today's tracking datasets mix diagnostic tests of symptomatic patients with screening tests of asymptomatic people. The two populations have different means and different variability. They are not combined in any controlled fashion, adding uncertainty to the signal.
- Current data suggests that there may be a uniform threshold of undiagnosed COVID infection prevalence that identifies an emerging outbreak. When expressed as a measure of case rate of confirmatory diagnostic tests, the number appears to be about 20 cases per 100,000. 

The shortcomings with the current monitoring systems create uncertainty and anxiety for public officials who are charged with trying to keep the pandemic under control in their jurisdiction while also minimizing economic disruption. It's already a difficult balancing act. The shortcomings of today's surveillance systems only make it more difficult.

## Where are things being done differently?

TBD ND

## Proposed early warning system

One simple approach would be to add a threshold to the case rate charts. This would add a measure of objectivity. It's a good start, but the problems with haphazardly mixing the two populations with different means violates the normal distribution assumption behind the standard deviation calculation.

<img src="img/COVID-case-rate-with-threshold.png" width = '1000'></img>

<img src="img/COVID-surveillance-of-prevalence.png" width = '1000'></img>

<img src="img/COVID-early-warning-cusum-chart.png" width = '1000'></img>


## Contributors
[Rob Salvino](https://github.com/salvir1)


## License
[MIT ©](https://choosealicense.com/licenses/mit/)
