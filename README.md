<!-- PROJECT SHIELDS -->
[![LinkedIn][linkedin-shield]][linkedin-url]
___

<h3 align="center">AI for S.E.A</h3>
<p align="center">
  :bar_chart: How may we improve the traffic congestion for Southeast Asia's roads by leveraging Grab's booking demand data? <strong>Traffic Management</strong>
  <br><br>
  <a href="https://www.aiforsea.com/">
    <img alt="Traffic Management" src="https://static.wixstatic.com/media/397bed_5d7ca71009b54dcf895b447920495d40~mv2.png/v1/fill/w_305,h_305,al_c,q_80,usm_0.66_1.00_0.01/Grab%20EDM_Safety.webp">
  </a>
</p>

___

<!-- TABLE OF CONTENTS -->
### Table of Contents

* [Grab Challenge](#Grab-Challenge)
  * [PROBLEM STATEMENT](#Problem-Statement)
  * [Objective](#Objective)
  * [Built With](#built-with)
* [Prerequisites](#prerequisites)
* [Getting Started](#getting-started)
  * [Installation](#installation)
* [Usage](#usage)
* [Contributing](#contributing)
* [License](#license)
* [Contact](#contact)
* [Acknowledgements](#acknowledgements)

<!-- ABOUT THE PROJECT -->
## Grab Challenge
### Traffic Management
How may we improve the traffic congestion for Southeast Asia's roads by leveraging Grab's booking demand data? This is a data science assignment where you are expected to create a data model from a given training dataset.

### Problem Statement
Economies in Southeast Asia are turning to AI to solve traffic congestion, which hinders mobility and economic growth. The first step in the push towards alleviating traffic congestion is to understand travel demand and travel patterns within the city.

Can we accurately forecast travel demand based on historical Grab bookings to predict areas and times with high travel demand?


The given dataset contains normalised historical demand of a city, aggregated spatiotemporally within geohashes and over 15 minute intervals. The dataset span over a two month period. A brief description of data set fields are found below:
*geohash: geohash level 6
*day: day, where the value indicates the sequential order and not a particular day of the month
*timestamp: start time of 15-minute intervals, in the following format: hour and minute, where hour range from 0 to 23 and minute is either one of (0,15,30,45)
*demand: aggregate demand normalised to be in the range [0,1]

### Objective
To build a model trained on a historical demand dataset, that can forecast demand on a Hold-out test dataset. The model should be able to accurately forecast ahead by T+1 and T+5 time intervals (where each interval is 15-min) given all data up to time T.

### Built With
* [Anaconda](https://www.anaconda.com/)
* [Jupyter Notebook](https://jupyter.org/)

<!-- Prerequisites -->
## Prerequisites
* geohash
```sh
pip install python-geohash
```
* xgboost
```sh
conda install -c anaconda py-xgboost
```

<!-- GETTING STARTED -->
## Getting Started
1. Data Collection, click [here] to get the data. (https://s3-ap-southeast-1.amazonaws.com/grab-aiforsea-dataset/traffic-management.zip)
2. Data Investigation
3. Data Visualisation and Exploration
4. Split the training.csv data for train and test model
5. Feature Engineering
6. Train the model
7. Train the model
8. Train the model
9. Compare the model
10. Test the best model
11. Verify the best model with hold out test data

<!-- CONTACT -->
## Contact

Teng Chun Man - [@linkedin](https://www.linkedin.com/in/tengchunman/)
Email: tengchunman@gmail.com
Project Link: [https://github.com/cmxteng/aiforsea-traffic-management](https://github.com/cmxteng/aiforsea-traffic-management)

<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [GitHub Emoji Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet)
* [GitHub Pages](https://pages.github.com)


<!-- MARKDOWN LINKS & IMAGES -->
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/tengchunman/
[product-screenshot]: https://raw.githubusercontent.com/othneildrew/Best-README-Template/master/screenshot.png
