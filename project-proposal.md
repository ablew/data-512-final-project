### Agustin Lew
# A5. Project Proposal
## Introduction
According to multiple sources [1], more than 100,000 traffic tickets are issued per day in the United States, and each ticket costs $150 on average. A traffic ticket quota is the number of traffic infractions a police officer must administer in a given period of time. Ticket quotas are illegal in many states, such as California, Texas, and Florida. In Washington State, a bill [2] to prohibit traffic ticket quotas was introduced in 2016, but it is not in effect yet. Still, both Washington State Patrol and Seattle Police state that there is no regulation regarding the minimum number of traffic stops [3]. Some police departments use “productivity goals”, “work productivity” or performance reviews as excuses to implicitly enforce traffic ticket quotas. The purpose of this project is to explore the possibility that a traffic ticket quota is implicitly enforced in the state of Washington. 
## Research Questions
•	Are there traffic ticket quotas imposed on police officers in Washington/Seattle?
o	If so, what is the traffic ticket quota number or rate, and what is its periodicity?
o	What is the demographic of the drivers being stopped by police officers who enforce quotas?
•	What are the most common places and time for traffic stops?
•	What are the most common traffic violations or reasons for stops?
## Data
The dataset is provided by The Stanford Open Policing Project [4], and can be obtained either from their website or from Kaggle [5]. It contains records of traffic stops by law enforcement in the state of Washington from January 2009 to December 2015. 
The Stanford Open Policing Project data are made available under the Open Data Commons Attribution License.

The csv file is 1.85 GB, with 34 columns and 8,624,032 rows of data. The data corresponds to 1484 unique police officers.

The dataset has the following schema:

Column | Data Type | Description
--- | --- | ---
id | String | Stop unique identifier.
state | String | State where the stop happened.
stop_date | String | Date of stop.
stop_time | String | Time of stop.
location_raw | String | Original location value.
county_name | String | Name of county.
county_fips | Float | FIPS county code.
fine_grained_location | String | Higher resolution location.
police_department | String | Police department or agency that made the stop.
driver_gender | String | Driver's gender.
driver_age_raw | Float | Driver's age, birth year, or birth date.
driver_age | Float | Standarized driver's age.
driver_race_raw | String | Original value for driver's race.
driver_race | String | Standarized driver's race.
violation_raw | String | Violation committed by the driver, in the language of the original data.
violation | String | Standarized violation.
search_conducted | Boolean | Indicates whether a search was performed.
search_type_raw | String | Justification of the search, in the language of the original data.
search_type | String | Standarized justification of the search.
contraband_found | Boolean | whether a search was performed and contraband was found. FALSE if no search was performed.
stop_outcome | String | Outcome of the stop.
is_arrested | Float | Indicates whether an arrest was made.
violations | String | List of violation codes.
officer_id | String | Officer's hashed unique identifier.
officer_gender | String | Officer's gender.
officer_race | String | Officer's race.
highway_type | String | Type of highway.
road_number | String | Road number where stop occurred.
milepost | Float | Nearest milepost where stop occurred.
lat | Float | Latitude coordinate where stop occurred.
lon | Float | Longitude coordinate where stop occurred.
contact_type | String | Type of contact.
enforcements | String | Enforcement Pattern
drug_related_stop | Boolean | Indicates whether it was a drug related stop.

It would be interesting to see if quotas are in place because this is an issue that costs drivers millions of dollars per year and working on solutions could alleviate tensions between the public and the police. A possible ethical consideration when using this dataset is that even though the police officers’ ids are hashed and anonymized, the police officers might still be identifiable by looking at the data to figure out the time and location of the infractions. 
## Background and Related Work
A 2017 statistical analysis [6] by a Columbia Ph.D. student investigates traffic stop quotas in New York City. The study focuses on just one precinct and shows various statistical methods for handling the data that might prove useful for this project. One of the trends that the study mentions is that officers tend to dispense more tickets on the second half of the month.

There is an article [7] from The Seattle Times that explores the trends of traffic tickets in Seattle. The author focuses on the number of citations per year and per day of the week, the amount of dollars in fines per year, and the demographic of the drivers being stopped. This article can serve as the ground truth to which I can compare with a subset of police officers that could be flagged as ‘under traffic quota’ to see if the days of the citations match the overall trend or if the officers are biased toward a certain demographic. 

In addition, there are several news articles from all over the United States showing cases of police departments getting into trouble for forcing their police officers to meet the quota or face penalties like demotions or being posted on unpopular locations [8]. Many of these articles illustrate the ways in which quotas were enforced; this is very useful because it gives a better idea of what trends to look for. For example, a police department in Los Angeles had a traffic ticket quota of 18 tickets a day [9]. In a 2007 article [10], Washington State Patrol had ticket quotas of either 3 tickets a day or 80% of contacts. And this article [11] shows that NYPD officers’ ticket numbers are reviewed on a monthly basis.
## Methodology
I plan to use Jupyter Notebooks to import, clean, analyze and visualize the data and structure it in a way that allows for reproducibility. Most of the analysis will involve using the pandas library to create tables of different time granularity (hour/day/week/month) in order to find trends in citations. In theory, the variance of the number of tickets issued in different periods should help determine if there is a quota since police officers might hover around the threshold. The ratio of number of tickets issued and the number of contacts will also be explored since there are cases where they operate with percentages instead of concrete numbers. This project will also include using matplotlib for visualizing time series and geopandas and geopy to work with the coordinate columns.

I might use unsupervised cluster analysis in order to group the police officers to their precincts, since that information is not present in the data.

More methods will be explored as issues or ideas arise during the course of the project.
## Issues
The ‘police_department’ field is empty, so it will be very difficult to find if there are precinct-mandated traffic stop quotas, since it won’t be easy to identify officers belonging to the same precinct. Cluster analysis might not be feasible because there are over 200 police precincts or departments in the state of Washington. A solution to this would be to filter down to stops in Seattle and cluster the officers into one of the five precincts.

One of the limitations of the dataset is that the most recent record is from December 2015. Given that the bill prohibiting traffic ticket quotas was introduced in 2016, it would be impossible to see if the introduction of the bill had any effect on the number of traffic stops without any additional data.

While there are numerous examples of traffic ticket quotas being implemented that involve reaching a minimum number of citations, many police departments avoid explicitly using numbers in order to avoid being caught. Instead they compare the number of tickets with previous periods, or use ‘shift-averaging’, where smaller teams of officers pool their tickets and the team that does not reach the average is punished [12]. Methods like these will be much harder or impossible to detect.

A limiting factor that could impact the completion of the project is the fact that there is no labeled data regarding the ground truth of traffic ticket quotas, making it difficult to confirm whether the results are valid or not. This also means that constructing a machine learning model that predicts whether a police office is under a quota will be much harder.

## Links
[1] https://www.good2go.com/blog/traffic-and-speeding-ticket-statistics/, https://auto.howstuffworks.com/under-the-hood/cost-of-car-ownership/cost-of-speeding-ticket.htm

[2] https://app.leg.wa.gov/billsummary/?BillNumber=2399&Year=2015&Initiative=false

[3] https://blog.seattlepi.com/seattle911/2009/01/13/do-cops-have-quotas-for-speeding-tickets/

[4] https://openpolicing.stanford.edu/

[5] https://www.kaggle.com/stanford-open-policing/stanford-open-policing-project-washington-state

[6] https://zenodo.org/record/1284317/files/auerbach_jonathan.pdf?download=1

[7] https://www.seattletimes.com/seattle-news/data/have-you-noticed-seattle-police-are-writing-fewer-tickets/

[8] https://www.nytimes.com/2006/01/20/nyregion/police-in-brooklyn-used-illegal-ticket-quotas-arbitrator-decides.html

[9] https://www.latimes.com/local/la-xpm-2011-apr-12-la-me-ticket-quotas-20110412-story.html

[10] https://www.thenewspaper.com/news/20/2090.asp

[11] https://theappeal.org/nypd-commanders-text-messages-show-how-the-quota-system-persists/

[12] https://www.ticketsnipers.com/article/california-cops-sue-over-ticket-quotas

