# A Comparison of COVID-19 Early Warning Systems

- This project describes a comparison of several different COVID surveillance systems. It approaches a widely-analyzed problem perhaps in a novel way to demonstrate data analytics and data science techniques, but also to ultimately propose an alternate surveillance system for regional governments that may be able to provide a more accurate assessment of COVID-19 infection rate status and an early indication of an emerging outbreak.
This is an ongoing project. New information will be added soon. Please recognize that the ideas and reasearch in this repo are a work in process.

## Goals

The goals of this project are:
> - To compare regional COVID-19 surveillance systems
> - To work with various EDA and data visualization tools and techniques

## Tools and techniques used in this project
- **Tools**
> - Python, Jupyter Lab, SciKitLearn, Pandas, Numpy
- **Visualization**
> - Plotly, Matplotlib
- **Techniques**
> - Supervised learning model development, spatial mapping, simple moving average

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
