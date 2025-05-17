[![Python 3.6](https://img.shields.io/badge/python-3.6-blue.svg)](https://www.python.org/downloads/release/python-360/)


<!-- PROJECT LOGO -->
<br />
<p align="center">
    <img src="reports/new-aggregation.jpg" alt="Logo" width="500" height="250">
  </a>

  <h3 align="center">News Aggregator with FastAPI</h3>

  <p align="center">
    Boilerplate news aggregation application build for Reddit and NewsAPI. Main idea is to use lightweight development frameworks like FastAPI rather than heavy weight lifting with Django/ Flask. Problem Statement</a> document.
    <br />
    <br />
    <br />
  </p>
</p>



<!-- TABLE OF CONTENTS -->
## Table of Contents

* [About the Project](#about-the-project)
  * [Built With](#built-with)
* [Getting Started](#getting-started)
  * [Prerequisites](#prerequisites)
  * [Installation](#installation)
* [Roadmap](#roadmap)



<!-- ABOUT THE PROJECT -->
## About The Project

[![Product Name Screen Shot][product-screenshot]](#about-the-project)


Problem Statement</a> document. All of the features are implemented. All the contraints are implemented, along with project documentation and unit-tests.

<br>


#### What's Not Implemented
Current version of this project does not implement cache server or job queue to minimize performance dependence on external APIs.


<br>

### Built With

* [Python](http://python.org/)
* [FastAPI](https://fastapi.tiangolo.com/)



<!-- GETTING STARTED -->
## Getting Started

#### General Technique to Aggregate

1. Get list of registered APIs
2. Loop over APIs
3. Make JSON object of configurations for each API
4. Write JSON parsers for each API
5. Combine result in uniform format to display
6. Return results



#### Detailed Approach

Every Request to API should be async; put the request in job tracker, get results and push back responses

##### News Listing Endpoint:
api.route('/news')

def get_top_news():
  1. Get all available APIs
  2. Call each API for getting top 10 news in JSON; Listing Function for Each API
  3. Aggregate news from all APIs, discard empty responses
       

##### News Search Endpoint
api.route('/news?query=bitcoin')

def get_search_results():
  1. Get all available APIs
  2. Call each API with search query to get top 10 results in JSON; Searching Function for Each API
  3. Aggregate results from all APIs, discard empty responses


##### Other Helper Functions
  1. News_API json parser for listing responses; 
    should return only required fields; ["title",  "link", "source"]
  2. Reddit_API json parser for listing results


##### Steps to Add any New API
  1. Make a new file for new-API in ```src/external_api/```
  2. Take ```src/external_api/sample_api.py``` as reference
  3. Prepare API Mapping object
  4. Write JSON parser for that API
  5. Register your API in API_COLLECTION in ```src/api_helper.py```


### Prerequisites

To run this project, should install project dependencies:

1. Python3
2. pip
3. Intsall Python packages


<br>

<!-- Product Screenshot -->
[product-screenshot]: reports/news_aggregator_ss.png
