Agustin Lew

# A5. Project Proposal

According to multiple sources (1), more than 100,000 traffic tickets are issued per day in the United States, and each ticket costs $150 on average. A traffic ticket quota is the number of traffic infractions a police officer must administer in a given period of time. Ticket quotas are illegal in many states, such as California, Texas, and Florida. In Washington State, a bill (2) to prohibit traffic ticket quotas was introduced in 2016, but it is not in effect yet. Still, both Washington State Patrol and Seattle Police state that there is no regulation regarding the minimum number of traffic stops (3).

Some police departments use “productivity goals”, “work productivity” or performance reviews as excuses to implicitly enforce traffic ticket quotas. The purpose of this project is to explore the possibility that a traffic ticket quota is implicitly enforced in the state of Washington. There are additional points to be addressed if there is evidence of traffic ticket quota policies, such as the demographics of the drivers being stopped, the most common places and time for traffic stops, or the type of violation used to justify the traffic stop. It would be interesting to see if quotas are in place because this is an issue that costs drivers millions of dollars per year and working on solutions could alleviate tensions between the public and the police. A possible ethical consideration when using this dataset is that even though the police officers’ ids are hashed and anonymized, the police officers might still be identifiable by looking at the data to figure out the time and location of the infractions. Or it could be used to know which routes to avoid while driving, allowing violators to circumvent the law. 

The dataset is provided by The Stanford Open Policing Project (4), and can be obtained either from their website or from Kaggle (5) . It contains records of traffic stops by law enforcement in the state of Washington from January 2009 to December 2015. The data includes date, time and location (address, county, latitude and longitude) of the traffic stop, officer id (hashed), driver information (gender, age and race), type of violation, whether it led to an arrest, etc.

The Stanford Open Policing Project data are made available under the Open Data Commons Attribution License. 

One of the limitations of the dataset is that the most recent record is from December 2015. Given that the bill prohibiting traffic ticket quotas was introduced in 2016, it would be impossible to see if the introduction of the bill had any effect on the number of traffic stops without any additional data. 

A limiting factor that could impact the completion of the project is the fact that there is no labeled data regarding the ground truth of traffic ticket quotas, making it difficult to confirm whether the results are valid or not. This also means that constructing a machine learning model that predicts whether or not a police office is under a quota will be much harder or infeasible.







(1) https://www.good2go.com/blog/traffic-and-speeding-ticket-statistics/, https://auto.howstuffworks.com/under-the-hood/cost-of-car-ownership/cost-of-speeding-ticket.htm

(2) https://app.leg.wa.gov/billsummary/?BillNumber=2399&Year=2015&Initiative=false

(3) https://blog.seattlepi.com/seattle911/2009/01/13/do-cops-have-quotas-for-speeding-tickets/

(4) https://openpolicing.stanford.edu/

(5) https://www.kaggle.com/stanford-open-policing/stanford-open-policing-project-washington-state
