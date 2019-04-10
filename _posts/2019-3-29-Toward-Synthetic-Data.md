---
layout: post
title: Toward Synthetic Data
---

In the healthcare field, every data scientist I know has run into the problem of
accessing data. And there is good reason... the 
[HIPPA Minimum Necessary Requirement](https://www.hhs.gov/hipaa/for-professionals/privacy/guidance/minimum-necessary-requirement/index.html). 
However, as data scientist we are a curious bunch. We still want to apply a new methods to familar data or
kick the tires on a new [data pipelining](https://www.tensorflow.org/guide/performance/datasets) technique. 
How can we test new technology on pertient data? One possible solution is fake and/or synthetic data.
 
## Synthetic vs. Fake
I think there is a difference between **fake** and **synthetic** data. Synthetic data connotes something
 more than fake data. To me, there seems to be this implication that the relationships in the data make sense. For
 example, a date related to a visit with a primary care provider is after a person's birthdate. If someone 
 mentions they have a fake dataset related to patient visits with their primary care provider, I don't
 necessarily expect the same relationships to hold. Statistically, we might say that all of the variables in 
 the dataset are mutually independent. We can 
 extend this notion of independence to not only datasets, but relational databases. Consider the following ER
 diagram from a simple toy example:
 
![mail](images/er_diagram.png)

In a fake representation of the database, we would not expect to see accuracte relationships between a patient
with a broken hip and the number of procedures related to correcting such an issue. In a synthetic representation of the 
database, the numbers should align to something that would be realistic based on some true data.

## Toward Synthetic Data
