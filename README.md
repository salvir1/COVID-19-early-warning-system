# COVID Early Warning System Project Overview

This project is an attempt to define a good early warning indicator for COVID outbreaks. States and public health agencies have a difficult job to keep COVID transmission under control. One of the keys to control is a system that provides them an early and accurate warning of an increase in new COVIC infections in their jurisdiction. How good is the data that they are currently using at providing that early indiactor? Is there a way to improve upon the timeliness and accuracy of the warning?

This project grew out of an interest to compare the available data from states that had experienced an outbreak vs. states that hadn't experienced an outbreak. As the analysis progressed it became clear that the common statistical measures of COVID-19 infection spread that are utilized today--total cases, case rates, and positive test rates--are not all equally informative. One is better than the others, yet all of them have their shortcomings. The first part of this project explores the shortcomings with the measures that are currently available. It identifies the data that most clearly and consistently correlates with outbreaks.

## Part 2: An Alternative COVID Early Warning System

The first part of this project (described [here](https://github.com/salvir1/part-1-covid-outbreak-analysis)) informs this second part--a proposed alternative regional COVID-19 early warning system. This proposal addresses some of the shortcomings of the currently available tools to provide an earlier and more accurate warning of an increase in new COVID infections. Simulations of this alternative systems are modeled to compare its theoretical improvement in performance over current options. Ideally, a system like this could ultimately allow state governments and public health agencies to react sooner and keep an uptick from turning into an outbreak. That is the focus of this repo.

## Goals

The high level goals of this project are:
- To characterize the difference at the regional level between an uptick and an outbreak in COVID case rates
- To develop statistics that could become the foundation of a COVID-19 earling warning system (described [here](https://github.com/salvir1/part-2-covid-early-warning-system))
- To work with various EDA and data visualization tools and techniques
- To propose an alternative early warning system that could provide an earlier and more accurate indication of an emerging COVID outbreak

## Tools and techniques used in this project

**Tools**
- Python, Jupyter Lab, SciKitLearn, Pandas, Numpy

**Visualization**
- Plotly, Matplotlib

**Techniques**
- Time series, spatial mapping, simple moving average, simulation

## Raw data sourced from COVID Tracking Project

- Terms of use: The COVID Tracking Project at The Atlantic’s data and website content is published under a Creative Commons CC BY 4.0 license, which requires users to attribute the source and license type (CC BY 4.0) when sharing our data or website content.
- Citation: [the COVID Tracking Project](https://www.covidtrackingproject.com), Creative Commons CC BY 4.0 license

## Conventional state-level approach today

- Track the trend of positive diagnoses and the trend of the positivity rate (positive cases / total cases)
- Assuming most cases are eventually diagnosed, this is an attempt at monitoring almost the entire infected population (i.e. it doesn't rely on taking a sample of the population)

- Three clear shortcomings hinder the ability of this method to identify a regional outbreak (such as at a state level) in a timely manner

> - The signal is delayed due to the delay from the time a person with COVID becomes symptomatic (commonly thought to be 4-5 days on average), decides to get tested, and the test results find their way to the tracking system (for PCR tests can vary from 1 to several days).
> - The population monitoring mechanism isn't well-controlled. Testing includes a confusion of symptomatic people, people who have to be tested for work, people who are being tested prior to a medical procedure, people who are being tested due to exposure to someone who may have COVID, and people getting tested for other reasons. All of these test results are thrown together without control. Are the proportions of these subsets consistent over time? If not, what effect do the changes have on aggregate test results? Are test rates of asymptomatic or mildly symptomatic people consistent over time as well? Governments have issued conflicting testing guidance so it probably isn't a valid assumption to say those test rates are steady.
> - Laboratories run tests in batches. Oftentimes batches consist of samples from different days and different locations. Test numbers and positivity rates see large variances from day-to-day. 
> - The data are noisy. Std deviations of case counts for many states are almost as big as the daily mean. The size of the standard deviation means that smoothing (usually 7 days or more) must be employed to see an underlying trend.
> - Best case is a delay of only two weeks after initial infections have been spiking. It's likely to be longer.

- The charts below provide a snapshot of the challenges of using this data as a surveillance tool. 

## Contributors
[Rob Salvino](https://github.com/salvir1)


## License
[MIT ©](https://choosealicense.com/licenses/mit/)
