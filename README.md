Download Link: https://assignmentchef.com/product/solved-comp93211-assignment-2
<br>
<h2>Data Service for World Bank Economic Indicators</h2>

In this assignment, you are asked to develop a Flask-Restplus data service that allows a client to read and store some publicly available economic indicator data for countries around the world, and allow the consumers to access the data through a REST API.

<strong><em>IMPORTANT </em></strong><em>: For this assignment , you will be asked to access the given Web content programmatically. Some Web hosts do not allow their web pages to be accessed programmatically, some hosts may block your IP if you access their pages too many times. During the implementation, download a few test pages and access the content locally – try not to perform too many programmatically.</em>

The source URL: <a href="http://api.worldbank.org/v2/">http://api.worldbank.org/v2/ (http://api.worldbank.org/v2/) </a><a href="http://api.worldbank.org/v2/">(http://api.worldbank.org/v2/)</a> Documentations on API Call Structure:

<a href="https://datahelpdesk.worldbank.org/knowledgebase/articles/898581-api-basic-call-structure">(https://datahelpdesk.worldbank.org/knowledgebase/articles/898581-api-basic-call-structure) </a><a href="https://datahelpdesk.worldbank.org/knowledgebase/articles/898581-api-basic-call-structure">https://datahelpdesk.worldbank.org/knowledgebase/articles/898581-api-basic-call-structure (https://datahelpdesk.worldbank.org/knowledgebase/articles/898581-api-basic-call-structure)</a>

<a href="https://datahelpdesk.worldbank.org/knowledgebase/articles/898581-api-basic-call-structure">(https://datahelpdesk.worldbank.org/knowledgebase/articles/898581-api-basic-call-structure)</a>

The World Bank indicators API provides 50 year of data over more than 1500 indicators for countries around the world.

List of indicators can be found at: <a href="http://api.worldbank.org/v2/indicators">http://api.w </a><a href="http://api.worldbank.org/v2/indicators">o </a><a href="http://api.worldbank.org/v2/indicators">rldbank.org/v2/indicators (http://api.worldbank.org/v2/indicators) </a><a href="http://api.worldbank.org/v2/countries">List of countries can be found at: (http://api.worldbank.org/v2/countries)</a> <a href="http://api.worldbank.org/v2/countries">http://api.worldbank.org/v2/countries (http://api.worldbank.org/v2/countries)</a>

As the documentation shows , you can construct URLs specifying different parameters to acquire necessary data. Use a custom URL to get information about a specific indicator. For example, the data on the GDP of all countries from 2012 to <a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017">2017 </a><a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017">can be acquired via this URL: (http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?</a>

<a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000">date=2012:2017)</a> <a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000">http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD? date=2012:2017&amp;format=json&amp;per_page=1000 (http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD? date=2012:2017&amp;format=json&amp;per_page=1000)</a>

For this assignment we are interested in annual values of a user specified indicator from 2012 to 2017 for one or all countries. The content of the file is quite straightforward. The data service specification will ask you to ‘import’ this data into a ‘data storage’. You should inspect the content of the file carefully and decide on a data model and storage method. You will find that a JSON format is suitable to accessing data and publishing it.

<h2>Assignment Specification</h2>

The data service should use JSON format to publish its data and implement following operations.

<h3>Question-1: Import a collection from the data service (2.5 marks)</h3>

<a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000">This operation can be considered as an on-demand ‘import’ operation. The service will download the JSON data for all countries (http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?</a>

<a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000">date=2012:2017&amp;format=json&amp;per_page=1000)</a> <a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000">respective to the year 2012 to 2017 and identified by the indicator id </a>given by the user and process the content into an internal data format and store it in the database; use <strong>sqlite </strong>for storing the data (the name of the database should be <strong>YOURZID.db </strong>) .

<a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000">For example, the following link can be used to obtain data for the indicator called: </a><a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000"><strong>NY.GDP.MKTP.CD</strong></a>

<a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000">(http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000)</a> <a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000">http://api.worldbank.org/v2/countries/all/indicators/ </a><a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000"><strong>NY.GDP.MKTP.CD </strong></a><a href="http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000">?date=2012:2017&amp;format=json&amp;per_page=1000 (http://api.worldbank.org/v2/countries/all/indicators/NY.GDP.MKTP.CD?date=2012:2017&amp;format=json&amp;per_page=1000)</a>

To import data your require an indicator as a parameter given by the API user. The parameter should be a query parameter named:

<strong> </strong><a href="http://api.worldbank.org/v2/indicators"><strong>indicator_id </strong></a><a href="http://api.worldbank.org/v2/indicators">: an indicator (http://api.worldbank.org/v2/indicators)</a> <a href="http://api.worldbank.org/v2/indicators">http://api.worldbank.org/v2/indicators (http://api.worldbank.org/v2/indicators)</a>

After importing the collection, the service should return a response containing at least the following information:

<strong>uri </strong>: the URL with which the imported collection can be retrieved <strong>id </strong>: a unique integer identifier automatically generated <strong>creation_time </strong>: the time the collection stored in the database <em>Example:</em>

HTTP operation: POST /collections?indicator_id=NY.GDP.MKTP.CD

Returns: 201 Created

{

“uri” : “/collections/1”,

“id” : 1,

“creation_time”: “2019-04-08T12:06:11Z”,

“indicator_id” : “NY.GDP.MKTP.CD”

}

You should return appropriate responses (JSON formatted) in case of already imported collections, invalid indicators or any invalid attempts to use the endpoint ( e.g. If the input indicator id doesn’t exist in the data source, return error 404 )

<h3>Question 2- Deleting a collection with the data service (2.5 marks)</h3>

This operation deletes an existing collection from the database. The interface should look like as below:

HTTP operation: DELETE /collections/{id}

Returns: 200 OK

{

“message” :”The collection 1 was removed from the database!”,

“id”: 1

}

<h3>Question 3 – Retrieve the list of available collections (2.5 marks)</h3>

This operation retrieves all available collections. The interface should look like as like below:

HTTP operation: GET /collections?order_by={+id,+creation_time,+indicator,-id,-creation_time,-ind

“order_by” is a comma separated string value to sort the collection based on the given criteria. Each segment of this value indicates how the collection should be sorted, and it consists of two parts (+ or -, and the name of column e.g., id). In each segment, + indicates ascending order, and – indicates descending order. Here are some samples:

+id,+creation_time                      order by “id ascending” and then “creation_time ascending”

In this case sorting by “id” has priority over “creation_time ”

-creation_time                            order by “creation_time descending”

Returns: 200 OK

[

{

“uri” : “/collections/1”,

“id” : 1,

“creation_time”: “2019-04-08T12:06:11Z”,

“indicator” : “NY.GDP.MKTP.CD”

},

{

“uri” : “/collections/2”,

“id” : 2,

“creation_time”: “2019-05-08T12:16:11Z”,

“indicator” : “2.0.cov.Math.pl_3.all”

},    …

<h3>Question 4 – Retrieve a collection (2.5 marks)</h3>

This operation retrieves a collection by its ID . The response of this operation will show the imported content from world bank API for all 6 years. That is, the data model that you have designed is visible here inside a JSON entry’s content part.

The interface should look like as like below:

HTTP operation: GET /collections/{id}

Returns: 200 OK

{

“id” : 1,

“indicator”: “NY.GDP.MKTP.CD”,

“indicator_value”: “GDP (current US$)”,

“creation_time” : “2019-04-08T12:06:11Z”

“entries” : [

{“country”: “Arab World”,  “date”: 2016,  “value”: 2500164034395.78 },

{“country”: “Australia”,   “date”: 2016,  “value”: 780016444034.00 },

…

]

}

<h3>Question 5 – Retrieve economic indicator value for given country and a year (2.5 marks)</h3>

The interface should look like as like below:

HTTP operation: GET /collections/{id}/{year}/{country}

Returns: 200 OK

{

“id”: 1,

“indicator” : “NY.GDP.MKTP.CD”,

“country”: “Arab World”,

“year”: 2016,

“value”: 780016444034.00

}

<h3>Question 6 – Retrieve top/bottom economic indicator values for a given year (2.5 marks)</h3>

The interface should look like as like below:

HTTP operation: GET /collections/{id}/{year}?q=&lt;query&gt;

Returns: 200 OK

<table width="762">

 <tbody>

  <tr>

   <td width="762">{“indicator”: “NY.GDP.MKTP.CD”,“indicator_value”: “GDP (current US$)”,“entries” : [{“country”: “Arab World”,“value”: 2500164034395.78},                   …]}</td>

  </tr>

 </tbody>

</table>

The &lt;query&gt; is an optional integer parameter which can be either of following:

<strong>+N (or simply N) </strong>: Returns top N countries sorted by indicator value (highest first) <strong>-N </strong>: Returns bottom N countries sorted by indicator value where N can be an integer value between 1 and 100. For example, a request like ” GET /collections/1 /2015?q=+10 ” should returns top 10 countries according to the indicator value.

Notice:

Your code must implemented in <strong>flask-restplus </strong>and automatically generate swagger doc for testing the endpoints.

Your code must be executable in CSE machines

Your code must not require installing any software (python libraries are fine) Your code must be written in Python 3.5 or newer versions.

Your operations (API methods) must return appropriate responses in JSON format, and appropriate HTTP response code! e.g., <strong>500 Internal Server Error </strong>is inappropriate response!

Make sure you are using right datatypes in the database and in you API methods (e.g., not string for years ‘2017’)

Install flask_restplus on cse machines by pip3 command, and make sure you install <strong>pip3 install </strong>