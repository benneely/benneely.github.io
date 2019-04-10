---
layout: post
title: Toward Synthetic Data
---

In the healthcare field, every data scientist I know has run into the problem of
accessing data. And there is good reason... the 
[HIPPA Minimum Necessary Requirement](https://www.hhs.gov/hipaa/for-professionals/privacy/guidance/minimum-necessary-requirement/index.html). 
However, as data scientist we are a curious bunch. We still want to apply a new methods to familar data or
kick the tires on a new [data pipelining](https://www.tensorflow.org/guide/performance/datasets) technique. 
How can we test new technology on pertient data? One possible solution is synthetic data.
 
## Synthetic vs. Fake
Before getting to synthetic data, I think there is a subtile distinction that needs to be made between fake
and synthetic data. Synthetic data connotes something
 more than fake data. To me, there seems to be this implication that the relationships in the data make sense. For
 example, a date related to a visit with a primary care provider is after a person's birthdate. If someone 
 mentions they have a fake dataset related to patient visits with their primary care provider, I don't
 necessarily expect the same relationships to hold. Statistically, we might say that all of the variables in 
 the dataset are mutually independent. We can 
 extend this notion of independence to not only datasets, but relational databases. Consider the following ER
 diagram from a simple toy example:
 
![mail](/images/er_diagram.png)

In a fake representation of the database, we would not expect to see accurate relationships between a patient
with a broken hip and the number of procedures related to correcting such an issue. In a synthetic representation of the 
database, the numbers should align to something that would be realistic based on some true data.

## First Steps
In order to facilitate the development of products within a health system, data scientists and developers must
work together to identify the right technology to implement algorithms that advance patient care. This work happens
fastest when sharing code and ideas. One way to expedite this work is to stand up a fake database asset that mimics
a health system's real electronic health records database. In doing so, there is no actual patient data exposed and all
team members have access to a resource for prototyping tools. Of course, this would be best if it were a synthetic 
data store and the relationships made sense, but the easiest first step is fake data.

## [fakeymcfakerson](https://github.com/benneely/fakeymcfakerson)
In going with the saying `"if you're not embarrassed by the first version of your product, you’ve launched too late"`,
I've developed a python package aimed at replicating a relational database by creating a fake version elsewhere. The 
purpose (as noted earlier), is to allow teams to prototype applications and pipelines where sensitive data might not
allow for collaboration. This fake data store poses no threat because all columns are mutually independent and no relationships
exist between tables. Under the hood, `fakeymcfakerson` will connect to a real instance of the data, generate a configuration
file. This file contains metadata about the tables and columns and can be shared freely. When ready to generate
 a new database, I've developed a `generator` class that can be used to stand up a new database using metadata from
 the configuration file. 
 
 Not convinced? Have more questions? Try the example on [fakeymcfakerson](https://github.com/benneely/fakeymcfakerson) 
 and provide feedback. Thanks for reading!