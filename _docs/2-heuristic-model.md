---
layout: doc
title: Heuristic Model
date: 2019-09-08 8:14:30 +0600
post_image: assets/images/service-icon3.png
tags: [Profile]
toc: true
custom_links:
- text: Prerequisites
  url: /docs/development-setup
- text: New Project Setup
  url: /docs/new-project-setup
  submenu:
  - text: poetry
    url: /new-project-setup#poetry
  - text: docker
    url: /new-project-setup#docker
  - text: Makefile
    url: /new-project-setup#makefile
  - text: linting
    url: /new-project-setup#linting
---
Let’s imagine we are working in a bank and and one day are having lunch with some guys from the credit team. They mention that they are trying to increase adoption of their loan product, but are limited by the current process. Apparently, they have to rely on credit score bureau such as SCHUFA to assess clients’ creditworthiness, which cuts-off most of users with insufficient or non-existent credit history, such as expats. The problem is exacerbated by the fact that expats are the largest customer segment.

You, being part of Data Science team and aware of the vast amounts of data the bank stores, come up with an alternative approach - predict probability of repayment using behavioural data such as history of card transactions. 

Some calls and discussions later, you are officially collaborating with the credit team. Now it is time to come up with an MVP proposal to convince your new stakeholders that putting this solution into production will create value for the business.

Your solution must:

* automate loan giving processes
* increase revenue by increasing number of disbursed (approved) loan while maintaining low risk of default

You have some ideas on how a solution might look like, but there are certain things that needs to be cleared up before you delve in.

## Before You Start Coding

Before investing a lot of time, you want to make sure that your stakeholders are willing to support you. You will need their guidance to understand the business domain, perhaps get other people involved such as backend engineers. It is alright to do some initial scoping to convince them, but make sure the company in general has resources to deploy your project eventually (after proof-of-concept).

To solve the problem, you first need to understand precisely which problem are you trying to solve. How is our label - default on a loan - defined? Does a user default when they did not repay within 30, 60, 90 days? Credit datasets are heavily imbalanced (defaults are very rare), and the longer repayment window you consider, the less minority samples you have to work with. On the other hand, there are user experience considerations. Using 30 days windows can be too strict and create a negative experience for the users that merely forget to up the card balance by the payment date. This trade-off have to be decided together with the credit team. Once you agree on the label definition, you can start analysing the data.

But wait, what relevant data do we have again? Depending on the state of your Data Lake and its documentation, you might also spend some time understanding what data you already have. Does this column mean what you think it means? Why are there some many columns with similar naming in the table? Is this table getting deprecated? Data Engineers and analysts can usually help out with such questions and lead you in the right direction. Also keep in mind that sometimes the data you want might not be available immediately. If you have a good idea of new potential data sources, it’s good to start talking to engineers early on about storing such data for eventual use (it’s not going to help you out much now for building the first version, but could come in handy later). In many Machine Learning solution implementations there is a labeling issue. Namely, it can invoke large spendings on human effort and annotation tools, especially in NLP. Luckily in our case we can directly deduce label (default) from the repayments data.

Finally, **don’t over-engineer a project from the start, but have an idea how a finished product might look like**. It will influence the way you build and structure the project from the beginning. 

How often do we need to serve predictions? If it’s once a day or a week, a REST API might be overdoing it. Still, aim to automate your solution as much as possible. Even if predictiong once a day only, set up a job schedule, upload results to DWH or even Google Drive so that your stakeholders can access them.

Some considerations:

* _Training frequency_: How long does it take and what frequency can we afford? Does it make sense to train often (does an extra day add enough information to warrant retraining daily)?
* _Predictions_: how often they need to be served? Can we compute required features at prediction time? (they can be impossible or too slow to compute)
* _Serving real-time vs performance_

Does it make sense to use ML or a heuristic approach will do? Not every Data Science Product must be a ML learning model served as a microservice. Why build a complex neural network when a Logistic Regression workd just fine (not to mention, much faster)? Think of the time investment when building the solition, as well as resources required.

### Checklist: Questions to ask yourself
#### (and your stakeholders)

* Who are your stakeholders & what do they want? Are they committed to the project?
* Does it Have Potential?
* Can We Get the Data? If not, can we start collecting it soon?
* Does it make sense to use ML or a heuristic approach will do?
* How Might a finished product look like?
