---
title: 'Home Credit Default Prediction Service'
date: 2020-09-13
permalink: /projects/2020/09/project-post-1/
tags:
  - API Service
  - Data Science
  - Machine Learning
---

# 1. Inspiration

A qualified senior full-stack data scientist is supposed to know how to develop a well-structured end-to-end data science solution; it does not make sense for a data scientist that he can only develop a model prototype and he has to heavily depend on other software engineers to finish the project especially when the data science team is small.

An end-to-end data science solution pipeline should be similar to the following:
<p align="center">
<img src="/images/ds_pipeline.png" width="55%" height="80%">
</p>
Typically, the data ingestion part is the starting point where the service is connected with the data warehouse like AWS Redshift or the data streaming service like Apache Flink. The end of the service can be either model deployment or performance monitoring depending whether you plan to use the external monitoring service provider like Splunk or some running statistical hypothesis tests incorporated into the service.

In this project, I developed an API service that includes everything between data ingestion and model deployment. For the data warehouse part, I will design a simple process that mimics the ETL process.

# 2. Some Background

[Home Credit](https://www.homecredit.net/) is an international non-bank financial institution. It focuses on lending primarily to people with little or no credit. This service aims to help Home Credit predict applicants' repayment abilities based on the data as follows:

* Basic application information.
* Credit bureau data.
* Point of sale (POS) balance: POS (a.k.a consumer finance) is one of Home Credit products.
* Credit card balance: credit card (a.k.a line of credit) is one of Home Credit products.
* Previous application data.
* Installment payments: This includes installment payments (the concept of installment payment is that people will for the money monthly, usually 12, 24, or 36 for consumer finance) of all Home Credit products.

The full dataset can be obtained from [kaggle](https://www.kaggle.com/c/home-credit-default-risk/data).

The basic working flow of the service looks like the following process:
<p align="center">
<img src="/images/hc_flow.png" width="55%" height="80%">
</p>
Please note that based on the nature of the dataset, this service would have the best performance on returning customers, therefore in reality the main service should call this service if and only if when the customers are already in the data warehouse and they have business with Home Credit.

The algorithm that is used for prediction is **LightGBM**

# 3. Core Technology Used

This is a list of core packages and frameworks that a developer needs to know in order to be able to work with this service and actively maintain or add features.

* [Alembic](https://alembic.sqlalchemy.org/en/latest/): Database migration tool.
* [Docker](https://www.docker.com/): Containers
* [FastApi](https://github.com/tiangolo/fastapi):  API framework.
* [Numpy](https://numpy.org/): Numerical computing package
* [Pandas](https://pandas.pydata.org/): Data manipulation package
* [Poetry](https://github.com/sdispater/poetry): Dependency management tool
* [PyDantic](https://pydantic-docs.helpmanual.io/): Case classes and validation tool
* [Pytest](https://pytest.org/en/latest/): Testing framework
* [python-json-logger](https://github.com/madzak/python-json-logger): Logging library
* [SQLAlchemy](https://www.sqlalchemy.org/): Database ORM tool.

If you are interested in this project and you want to delve deeper into the code, please visit [the project page](https://github.com/Superhzf/API-development)
