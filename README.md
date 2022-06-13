<!-- PROJECT LOGO -->
<br />
<div align="center">
  <img src="https://drivendata-public-assets.s3.amazonaws.com/airportconfig-tile.jpg" alt="Logo" width="800" height="330">

  <h3 align="center"> NASA Run-way competition: Predict Reconfigurations at US Airports </h3>

  <p align="center">
    Stuytown team repository to develop the models and serve the prediction functionalities for the 2022 NASA Runway prediction challenge 
    <br />
    <a href="https://www.drivendata.org/competitions/92/competition-nasa-airport-configuration-prescreened/page/440/"><strong>Visit competition site »</strong></a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
## Table of contents
  <ol>
    <li> <a href="#context-of-the-challenge">Context of the challenge</a> </li>
    <li><a href="#approach-of-our-solution">Approach of our solution</a></li>
    <li><a href="#results-obtained">Results obtained</a></li>
    <li><a href="#repository-structure">Repository structure</a></li>
    <li><a href="#usage">Usage</a></li>
     <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#execution">Execution</a></li>
      </ul>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>



<!-- CONTEXT -->
## Context of the challenge

Every year millions of flights arrive and depart from US airports. Intelligent scheduling and system control is a very pressing problem. Knowing in advance or accurately forecasting which runways will be available for departure and arrival is one of the key inputs to arrange optimized schedules. With the surge of Big Data and Advanced Analytics techniques most of these forecasts are based on Machine Learning methods.

In a [2022 analytics competition](https://www.drivendata.org/competitions/89/competition-nasa-airport-configuration/), NASA partnered with DrivenData to facilitate real-world data to develop these types of models and suggest alternative approaches to the [existing research](https://aviationsystems.arc.nasa.gov/publications/2021/20210017593_Khater_Aviation2021_paper.pdf). 

More precisely, participants in this challenge were given the task to build an Advanced Analytics model capable of forecasting the likelihood of multiple configurations taking place for 10 US airports at 12 different time horizons ranging from 30 minutes to 6 hours ahead of time. Each configuration contains information about which runways are open for departure and arrivals respectively and in which direction they can be utilized. 

A graphical representation of the desired output by the model can be observed below as a grid crossing airports, configurations and lookahead periods:



The metric with which the above forecasts are evaluated is with the aggregated logloss across airports and lookahead periods.


<!-- APPROACH -->
## Approach of our solution

XXX



<!-- RESULTS -->
## Results obtained
XXX


<!-- REPOSITORY -->
## Repository structure

The approach and results discussed earlier are structured in two main subrepositories to tackle separate tasks. There is a *training* task under /code and a *prediction* task under /submission. The *training* task consists of a pipeline which loads the raw data, creates a master table and generates 120 models, one for each combination of airport-lookahead. And the *prediction* task is built to run on DrivenData's runtime environment to retrieve live forecasts for new and unseen data. The skeleton of the repository can be found below:

```
NASA-runways
│   README.md
│
└───code
│   │   main.py
│   └───src
│       │   CheckPredictions.py
│       │   CreateMaster.py
│       │   ExtractFeatures.py
|       |   GeneralUtilities.py
|       |   GeneratePredictions.py
│   
└───sumbission
│   │   main.py
│   └───src
└───data
    │   katl
    │   kclt
    │   kden
    │   kdfw
    │   kjfk
    │   kmem
    │   kmia
    │   kord
    │   kphx
    │   ksea
    │   open_submission_format.csv
    │   master_table.parquet
```

<!-- USAGE -->
## Usage

Having an understanding of the approach, results and repository structure, we will cover the usage of the developed code in this fifth section. First studying the necessary requirements and then specifying the execution steps. 

### Prerequisites

In order to execute the routines mentioned above two sets of requirements are needed:

- To execute *main.py* in /submission: Replicate the docker image of the [runtime DrivenData repository](https://github.com/drivendataorg/nasa-airport-config-runtime)
- To execute *main.py* in /code: Use a version of python 3 and have the packages from *requirements.txt* installed

### Execution

Once the previous requirements are met, the execution of the above pipelines is depicted below:

```python 
$ python3 main.py data_path models_path build_master
```

And in order to run the submission *main.py* script in DrivenData's runtime:

```python 
main(prediction_time: datetime)
```

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

As a closing remark, we would like to place on record our deepest sense of gratitude towards the NASA and DrivenData teams for organizing and hosting this competition respectively. Their continuous support and encouragement have been invaluable to develop the final product described earlier.
