# COVID Early Warning System Project Overview

This project is an attempt to define a good early warning indicator for COVID outbreaks. States and public health agencies have a difficult job to keep COVID transmission under control while simultaneously managing their economies and battling pandemic fatigure. One of the keys to controlling infections is a system that provides governments with an early and accurate warning of an increase in new COVIC infections in their jurisdiction. How good is the data that they are currently using at providing that early indiactor? Is there a way to improve upon the timeliness and accuracy of the warning?

This project grew out of an interest to compare the available data from states that had experienced an outbreak vs. states that hadn't experienced an outbreak. As the analysis progressed it became clear that the common statistical measures of COVID-19 infection spread that are utilized today--total cases, case rates, and positive test rates--all have their shortcomings. The essential problem is that the data feeding into these measures comes from two distinct populations--people who are symptomatic and those who are asymptomatic. These two populations have different rates of infection. Tests from both populations are combined in a haphazard fashion making statistical comparisons from one day to the next or one state to the next problematic. The data source issues don't impact all measures equally. The study identifies case rate as the one metric that most clearly and consistently correlates with outbreaks-albeit not as quickly or definitively as desired. [Results and discussion from this data analysis can be found here.](https://github.com/salvir1/COVID-19-outbreak-data-analysis)

The data analysis informs a proposed alternative regional COVID-19 early warning system. This proposal addresses some of the shortcomings of the currently available tools to provide an earlier and more certain warning of an increase in new COVID infections. Simulations of these alternative concepts are modeled to compare its theoretical improvement in performance over current options. Ideally, a system like this could ultimately allow state governments and public health agencies a more timely picture of COVID prevalence in their jurisdictions so that they know when they need to respond to keep an uptick from turning into an outbreak. 

## Goals

The high level goals of this project are:
- To propose a statistically sound COVID-19 earling warning system
- To characterize the data signals that correspond to the various COVID outbreaks that have occurred in the US
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

The exploratory data analysis (EDA) portion of this project ([click here](https://github.com/salvir1/COVID-19-outbreak-data-analysis) for details) highlighted two big shortcomings with the current methods used to monitor COVID infections in the general population. These shortcomings are considered below.

## Outbreaks grow faster than what the data shows

When an outbreak occurs, new active infections increase faster than what today's COVID case diagnosis metrics show. Two factors are behind this. Typically a positive diagnosis is made and enters a tracking dataset many days after infection. As a result, an outbreak may be emerging 6 or more days before it begins to appear in the metrics. The second factor relates to the size of the infected population. The CDC has been conducting large-scale  seroprevalence surveys (prevalence of antibodies to COVID in blood samples) in people across the country. They have found many times more people have antibodies than have been positively diagnosed [CDC](https://www.cdc.gov/coronavirus/2019-ncov/cases-updates/geographic-seroprevalence-surveys.html). The actual number of new infections could be 2.5 times or more larger. The slope of the actual outbreak curve compared to the observed curve is correspondingly that much steeper.

The following *case rate* charts illustrate what the actual outbreak curve could look like compared to the chart of actual positive diagnoses. The green trendlines of estimated new infections are earlier and steeper than the smoothed  blue trendlines of actual diagnoses reported as case rates.

<img src="img/COVID-case-rate-with-threshold.png" width = '1000'></img>

There are some additional points to make about the charts. These graphs have all been scaled to have the same y-axis scale. Vertical black lines have been added to indicate when state governments notified the public of what they viewed to be a concerning rise in cases this fall. (Ignore the red lines for now.) 

Three of the charts show *case rates* for states with outbreaks occurring in September. Based upon the *estimated infections* trendlines, new infections may have been on the rise for many days before state governments officially recognized them. The governor of the state of Washington took a very different approach. With large outbreaks occurring in neighboring states and case rates creeping up in certain parts of the state, he announced an emerging outbreak much earlier in the cycle. An outbreak isn't even detectable in this data. There's another key difference to point out with the charts. The *case rate* for Washington state over the summer was much lower than it was for the other states. The differences raise the question, "Is there a safe threshold that applies to all states?" 

Finally, the black lines only indicate when the respective state governments first publicly recognized an emerging outbreak. The charts do not illustrate what kind of efforts were taken to control the outbreak subsequent to that. Analysis of these efforts is beyond the scope of this project other than to say that they varied significantly from one state to the next. Additionally, case rates continued to rise unabated in the states with September outbreaks after government recognition.

Horizontal red lines were constructed from measures of August *case rate* mean and variability. The red lines have been added to demonstrate what could be a desirable statistical measure. The horizontal red lines are two standard deviations above the August mean rate. The vertical red lines indicate when the moving average first crosses the *two standard deviations* control line in the fall. This is a simple control chart approach to help to indicate when the mean of a time series is likely to have shifted with a certain degree of confidence--in this case two standard deviations or 95%. It is a flashing *warning signal* from the chart. Unfortunately, problems with the source data make this control line a flawed statistic, and it can't reliably be used in this way--which brings us to the second big shortcoming.

## COVID datasets mix data from two dissimilar populations 

Today's COVID tracking datasets mix diagnostic tests of symptomatic people with screening tests of asymptomatic people. The two populations have different means and different variability. They are not combined in any controlled fashion. Haphazardly mixing two very different test populations into one dataset reduces strength of inferences that can be made on new data is it comes in (by violating both stationarity and homoscedasticity).

It's worth expanding on this. Most of the positive test results that feed into today's COVID tracking metrics come from confirmatory diagnostic testing of symptomatic people. Positive test rates for this subpopulation will be 25% or more. Numerous screening tests of asymptomatic people are also reported in the total test numbers. Positive test rates in this subpopulation will be much lower--closer to the prevalence of undiagnosed COVID within the larger population. Positive test rates are likely to be an order of magnitude lower. The proportion of these types of tests that make up a daily sample fluctuate significantly may fluctuate significantly from one day to the next. One would expect a lot of variation in the metrics that are based on these data--and there is ([click here](https://github.com/salvir1/COVID-19-outbreak-data-analysis) for a more thorough analysis of this topic).

State governments and public health agencies face a daunting challenge of protecting peoples' lives and livelihoods during the COVID pandemic. Early intervention is critical to stemming an emerging outbreak which can in turn reduce economic impact. Good data is essential to timely decision-making. Good data is essential to having confidence in those decisions. There are several issues with the data underpinning many of the metrics in use today. This impacts both the timeliness of and confidence in any decisions based on those metrics. 

# Proposed early warning system

This notebook proposes variations of a COVID Early Warning System meant to address the shortcomings in current approaches. These variations are designed to create a *surveillance* system that measures the prevalence of undiagnosed COVID infections as opposed to statistics that rely on a haphazard mix of tests from confirmatory diagnoses of symptomatic people and screening tests from asymptomatic people. The statistics for these models are also designed using common statistical process techniques to allow for more certain decision-making.

The basic concept is to separate out the results from diagnostic testing from the results of screening tests and report them separately. The *total cases* and *case rate* metrics would not change much from what is being reported today. Most of the reported positive diagnoses come from symptomatic people. The big change--which would be a major improvement--would be that the screening test data could now be looked at separately.

Reporting on pure screening test data may help to address both of the major shortcomings with the common COVID metrics in use today. Many, if not most, of the positive tests in the asympomatic subsample may come from people who are not yet symptomatic. As such, the positives may come earlier in the infection cycle for this group, thus potentially leading to an earlier signal. The other big benefit is that the data would be more statistically robust. The positive test rate among screening tests would fairly accurately represent the active undiagnosed COVID infection prevalence in the larger population (with some error introduced because the samples wouldn't be truly random). 

Medical professionals assign codes to medical records when ordering tests that indicate the reason for the test. Codes have been created specifically for COVID testing. While the codes do not specifically state if a patient is symptomatic or asymptomatic, it may be possible to assign status based upon the coding. If true, then separating out the databases could be straightforward. If that's possible, here are examples of charts for the states above that could be produced with this data. The *prevalence of undiagnosed COVID* data points were simulated by generating a binomial random variable from the *estimated undiagnosed infection* trendlines. Since the *estimated undiagnosed infection* trendline stops a few days before the end of the time series, a linear regression was performed to complete the trendlines. The simulations use 4000 daily samples which is less than the number of asymptomatic tests that a state like Washington

<img src="img/COVID-surveillance-of-prevalence.png" width = '1000'></img>

In two of the above charts it appears that the daily *undiagnosed infection prevalence* datapoints cross red horizontal line well before the state governments first issued public notices of upticks. In other words, the simulated data could conceivably have indicated the emerging outbreak sooner than the current metrics. 

Another important benefit is that the data won't suffer the same stationarity and homoscedasticity issues since data is not being mixed haphazardly from two very different populations. The data may be better-behaved and better-suited to common statistical process control tools like CUSUM sequential analysis. The charts below contain the same simulated data as the previous charts. Control lines have been added indicating if and when the means of the *prevalence of undiagnosed COVID* statistic cross the 2 standard deviation thresholds. The signals are clear and provide a much more statistically sound warning. 

<img src="img/COVID-early-warning-cusum-chart.png" width = '1000'></img>

## Further thoughts on data collection from asymptomatic people

The data from the previous charts assumes that information about the type of test being performed--diagnostic vs. screening--is available in some form and can be used to parse the dataset. What if this assumption isn't valid or if the size of the sample isn't sufficient? States could set up a daily surveillance testing regimen made up of volunteers. This may sound like a daunting effort, but one observation may make this easier to accomplish. 

### Oversampling from the subpopulation of people with high contact rates can reduce sample size needs

Not everyone is equally likely to be infected by COVID. A surveillance system could be designed to take advantage of the fact that COVID is mainly transmitted from person to person through respiratory droplets, which means that a person's likelihood of acquiring and obtaining COVID increases the more one has close interaction with others. While less interactive people may ultimately be infected by someone who is more interactive, the continued spread of COVID depends on those who are highly interactive. 

A surveillance system could be set up to monitor people who are highly interactive including those who work in front line medicine (primary care, emergency medicine, hospital-based, nursing home-based); service industry workers (restaurant employees, grocery store front end employees, bartenders, hair stylists, those who work in salons, Uber and Lyft drivers, etc.); public safety (police, fire, EMS, airport); and younger people in general. COVID prevalence is likely to be higher in this group given that people in this group have more chances for infection. This is especially true in the early stages of an outbreak before infections have a chance to be passed on to less interactive people. A good random sample design would sample people from this *high contact rate* subpopulation. 

How many daily samples are sufficient? It depends on the prevalence of undiagnosed, active COVID infections in the overall population and how much of a difference one wants to detect and how quickly. Accurate detection of a lower prevalence rate requires a bigger sample. In the charts above, the lower end of the estimated undiagnosed COVID prevalence rate is about .25%. This translates to about 1 in 400 people in the general population. Contact rates--the measure of interaction with other people--probably follow something along the lines of a Pareto distribution where approximately 20% of the population could be responsible for 80% of the interactions. If a state could establish a random sampling program made up of people who are highly interactive, the prevalence rate in that subpopulation might be 0.75% or higher. 

Let's start by assuming one wants to detect a 60% increase in prevalence within two days 85% of the time with alpha = 0.1. Without targeted sampling of the *high contact rate* subpopulation, one would need 4280 daily samples. With sampling, the daily sample size would only need to be 1419.

There may be an added benefit to setting up a randomized surveillance testing program like the one above. Currently, it can take days for test results from labs to find their way into report datasets. The state of Washington advises that data may be revised for up to 10 days as more results come back. Incomplete test results add yet more obscurity to today's statistics that rely on cases as a numerator. Statistics from a randomized surveillance testing program would not have the same integrity issues since the pertinent statistic is the positive test rate. 

### Does a 'safe' threshold exist?

The analysis in the [first part of this project](https://github.com/salvir1/COVID-19-outbreak-data-analysis) suggested that there might be a safe level of COVID prevalence in the general population which avoids outbreaks. In other words, one can manage the COVID reproduction rate by managing the infection prevalence since transmission is dependent on person-to-person contact. The analysis in the first part of the project looked at *case rate* and estimated a safe level below 20 cases per 100,000. 

Further analysis needs to be done in this area to determine a safe level for infection prevalence. Knowing a threshold would be incredibly helpful for a state seeking to minimize the impact of the COVID pandemic to both lives and livelihoods.

## Future areas of study

- Data was simulated to create the undiagnosed infection control charts above. A reasonable next step would be to seek to find COVID datasets that can be separated by test type--diagnostic vs. screening.

- A threshold analysis for infection prevalence could be done using the simulated data.

- Sensitivity analysis could be done by changing the parameters that feed into the simulation.

## Contributors
[Rob Salvino](https://github.com/salvir1)


## License
[MIT ©](https://choosealicense.com/licenses/mit/)
