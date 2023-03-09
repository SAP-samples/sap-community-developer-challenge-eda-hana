# SAP Community Developer Challenge: Exploratory Data Analysis with SAP HANA and Python

This repository is a starting point of the **SAP Community Code Challenge for Exploratory Data Analysis** (see [the corresponding blog post](https://blogs.sap.com/2023/03/08/sap-community-developer-challenge-eda-with-sap-hana-and-python/)).

The goal for this month's Developer Challenge is to help you getting started with fundamentals of the [Python machine learning client for SAP HANA](https://help.sap.com/doc/cd94b08fe2e041c2ba778374572ddba9/2022_4_QRC/en-US/hana_ml.html): DataFrames and EDA Visualizations.

## Participation

In order to complete each of the challenges, you need to:

1. Look into the [Challenges](challenges.md) to see what the challenge is each week.
2. Submit your solution to the corresponding thread in [SAP Community Application Development discussion](https://groups.community.sap.com/t5/forums/tagdetailpage/tag-cloud-grouping/message/tag-cloud-style/recent/message-scope/core-node/board-id/application-developmentforum-board/user-scope/all/tag-scope/single/tag-id/3477/timerange/all/tag-visibility-scope/public).
3. You can join the challenge and submit your solutions during any time of the month of March of 2023, but you need to complete challenges from previous weeks, if not done yet.

## Setup for the challenge

To be able to participate in this challenge, it's essential that you complete the following steps to satisfy [requirements](#requirements):

### Software setup
1. [Setup your SAP HANA database in SAP HANA Cloud trial](https://developers.sap.com/group.hana-cloud-get-started-1-trial.html). 
   * Please note that it is recommended to use a **Trial** of SAP Business Technology Platform (aka SAP BTP), and not a **Free Tier** or your organization's account.
1. Get [SAP HANA Client installed on your local machine](https://developers.sap.com/tutorials/hana-clients-install.html).
   * If you are new to SAP HANA Client utilities, like `hdbsql` and `hdbuserstore`, then please check the tutorial ["Create a User, Tables and Import Data Using SAP HANA HDBSQL"](https://developers.sap.com/tutorials/hana-clients-hdbsql.html).
1. Get [JupyterLabs](https://jupyterlab.readthedocs.io/en/stable/getting_started/installation.html), or other environment where you can work with Jupyter notebooks (`.ipynb` files) using Python. There are many possible approaches for that.
   * Here is one of the recommended sequence of [steps using miniconda](setup/miniconda.md).
   * Alternatively -- if you have time and skills -- you can explore using [SAP Business Application Studio with Jupyter](https://blogs.sap.com/2023/02/08/running-a-jupyter-notebook-in-sap-business-application-studio/), or using [Binder](https://mybinder.org/) with this GitHub repository.
1. Get [Python machine learning client for SAP HANA (hana-ml)](https://help.sap.com/doc/cd94b08fe2e041c2ba778374572ddba9/latest/en-US/Installation.html).

### Security setup
We suggest you create a separate database user -- in our examples `DevChallenger` -- to use for the challenge.

1. In your SAP HANA database use an admin account to create a database user and assign a required role to it.

   Below are required SQL statements, with more explanation about how to execute them available [here](setup/DevChallenger.md).

   ```SQL
   CREATE USER DevChallenger 
   PASSWORD "Up2TheChallenge!Iam" --replace this with your password of choice!
   NO FORCE_FIRST_PASSWORD_CHANGE;

   GRANT AFL__SYS_AFL_AFLPAL_EXECUTE TO DevChallenger;
   ```

2. On your client machine add that user to the SAP HANA Client's secure store.
   ```Shell
   hdbuserstore -i Set DevChallenger <your.hana.instance.host>:<port> DevChallenger
   hdbuserstore list DevChallenger
   ```

   Verify it works.
   ```Shell
   hdbsql -j -U DevChallenger "SELECT Current_user FROM DUMMY;"
   ```
   > If you are not familiar with commands above or not clear where to find `your.hana.instance.host` and `port`, please check the tutorial ["Create a User, Tables and Import Data Using SAP HANA HDBSQL"](https://developers.sap.com/tutorials/hana-clients-hdbsql.html).

## Requirements

* A database user in SAP HANA database. The user should have required roles.
* In your client environment:
   * SAP HANA Client
   * JupyterLabs
   * Python 3.7 - 3.10
   * Python machine learning client for SAP HANA

## Download and Installation

You can fork or clone this repository.

## Recommended Learning

There is quite a lot to digest when working in the world of Data Science. If you need an introduction, then you should check out [Diving into the HANA DataFrame: Python Integration – Part 1](https://blogs.sap.com/2018/12/17/diving-into-the-hana-dataframe-python-integration-part-1/).

These resources may also be helpful for a broader overview of capabilities of the Python machine learning client for SAP HANA:
* Devtoerfest 2022 session ["Build your Machine Learning Scenario for your SAP HANA Cloud application from Python"](https://www.youtube.com/watch?v=CX38-95uBtc&t=138s&ab_channel=SAPDevelopers)
* SAP TechEd 2020 session ["Translytical Data Processing with SAP HANA Cloud"](https://youtu.be/fSiVmL4S00w)

## Known Issues

No known issues.

## How to obtain support

[Create an issue](https://github.com/SAP-samples/sap-community-developer-challenge-eda-hana/issues) in this repository, if you find a bug or have questions about the content.

For additional support, [ask a question in the thread](https://groups.community.sap.com/t5/application-development/questions-re-quot-eda-with-sap-hana-quot-developer-challenge/td-p/223590).

## Contributing

If you wish to contribute code, offer fixes or improvements, please send a pull request. Due to legal reasons, contributors will be asked to accept a DCO when they create the first pull request to this project. This happens in an automated fashion during the submission process. SAP uses [the standard DCO text of the Linux Foundation](https://developercertificate.org/).

## License

Copyright (c) 2023 SAP SE or an SAP affiliate company. All rights reserved. This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSE) file.
