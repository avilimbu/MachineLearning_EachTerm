# API (Application Programming Interface)

## What is an API?

**API** stands for **Application Programming Interface**.

An API is a way for two different software applications to **communicate with each other** and exchange data.

In simple words:

> **An API allows one program to request data or functionality from another program.**

For example, suppose you are building a Machine Learning project and need movie data. Instead of manually downloading or entering thousands of movies, you can request the data from a movie API.

```text
Your Python Program
       |
       |  Request
       ↓
      API
       |
       |  Response
       ↓
Movie Database
```

Your Python program asks the API for data, and the API sends the requested data back.

---

# Why are APIs Important in Machine Learning?

APIs are very useful in Machine Learning because ML projects often require large amounts of data.

Instead of manually collecting data, you can use APIs to automatically retrieve data from online services.

For example:

* Weather data
* Stock market data
* Movie information
* Sports statistics
* Social media data
* Government data
* Financial data
* Maps and location data
* News articles
* Product information
* Scientific data

### Example

Suppose you want to build a **movie recommendation system**.

You need information such as:

```text
Movie ID
Movie Title
Overview
Release Date
Popularity
Rating
Vote Count
```

If a movie API provides this information, Python can request the data automatically.

---

# API in Simple Terms

Think of an API like a **waiter in a restaurant**.

```text
You
 |
 | "I want a pizza."
 ↓
Waiter (API)
 |
 | Gives your request to the kitchen
 ↓
Kitchen (Server/Database)
 |
 | Prepares the pizza
 ↓
Waiter (API)
 |
 | Brings the pizza
 ↓
You
```

In this example:

| Restaurant | API           |
| ---------- | ------------- |
| Customer   | Client        |
| Waiter     | API           |
| Kitchen    | Server        |
| Food       | Data/Response |
| Order      | Request       |

Your program is the **client**.

The API acts as the communication layer between your program and the server.

---

# Client and Server

Most APIs follow a **client-server architecture**.

### Client

The **client** is the application that requests information.

Examples:

* Python program
* Web browser
* Mobile application
* Frontend application

### Server

The **server** receives the request, processes it, and sends back a response.

```text
Client
  |
  | Request
  ↓
Server
  |
  | Response
  ↓
Client
```

For example:

```python
import requests

response = requests.get("https://example.com/api/data")
```

Here:

* Python program → Client
* `requests.get()` → Sends request
* API → Receives request
* Server → Processes request
* Response → Returned to Python

---

# What is an API Endpoint?

An **endpoint** is a specific URL where an API provides a particular resource or service.

Example:

```text
https://api.example.com/movies
```

This could represent an endpoint for retrieving movie information.

Another endpoint might be:

```text
https://api.example.com/movies/123
```

This could return information about movie `123`.

### Think of an endpoint as an address

Just like a house has an address, an API resource has an endpoint.

```text
API
 |
 ├── /movies
 ├── /movies/123
 ├── /users
 └── /users/123
```

Different endpoints provide different resources.

---

# API Request

An **API request** is a message sent by the client to the API asking for something.

A request can contain:

* URL
* HTTP method
* Parameters
* Headers
* Authentication information
* Request body

Example:

```python
import requests

response = requests.get(
    "https://api.example.com/movies"
)
```

This sends a request to the `/movies` endpoint.

---

# API Response

After receiving a request, the server sends back a **response**.

For example:

```json
{
    "id": 101,
    "title": "Example Movie",
    "rating": 8.5
}
```

The response contains the information requested by the client.

---

# HTTP Methods

APIs commonly use **HTTP methods** to tell the server what operation should be performed.

The most common methods are:

| Method   | Purpose               |
| -------- | --------------------- |
| `GET`    | Retrieve data         |
| `POST`   | Create/send data      |
| `PUT`    | Replace/update data   |
| `PATCH`  | Partially update data |
| `DELETE` | Delete data           |

For Machine Learning data collection, you will most commonly use:

```text
GET
```

because you usually want to **retrieve data**.

---

# GET Request

A `GET` request is used to retrieve data from an API.

Example:

```python
import requests

response = requests.get(
    "https://api.example.com/movies"
)
```

The API may return:

```json
{
    "results": [
        {
            "id": 1,
            "title": "Movie A"
        },
        {
            "id": 2,
            "title": "Movie B"
        }
    ]
}
```

---

# POST Request

A `POST` request is generally used to send data to a server to create something.

Example:

```python
import requests

data = {
    "name": "Avhishek",
    "age": 20
}

response = requests.post(
    "https://api.example.com/users",
    json=data
)
```

The server can process the submitted data.

---

# PUT Request

`PUT` is commonly used to replace an existing resource.

Example:

```python
import requests

data = {
    "name": "Avhishek",
    "age": 21
}

response = requests.put(
    "https://api.example.com/users/1",
    json=data
)
```

---

# PATCH Request

`PATCH` is commonly used when you want to update only part of a resource.

Example:

```python
import requests

data = {
    "age": 21
}

response = requests.patch(
    "https://api.example.com/users/1",
    json=data
)
```

---

# DELETE Request

`DELETE` is used to delete a resource.

Example:

```python
import requests

response = requests.delete(
    "https://api.example.com/users/1"
)
```

---

# HTTP Status Codes

When an API responds, it usually provides an **HTTP status code**.

These codes tell us whether the request was successful.

## Common Status Codes

| Status Code | Meaning                            |
| ----------- | ---------------------------------- |
| `200`       | OK / Request successful            |
| `201`       | Created successfully               |
| `204`       | Successful request with no content |
| `400`       | Bad Request                        |
| `401`       | Unauthorized                       |
| `403`       | Forbidden                          |
| `404`       | Resource not found                 |
| `429`       | Too many requests                  |
| `500`       | Internal Server Error              |
| `502`       | Bad Gateway                        |
| `503`       | Service Unavailable                |

---

# Checking the Status Code in Python

```python
import requests

response = requests.get(
    "https://api.example.com/movies"
)

print(response.status_code)
```

If the request is successful:

```text
200
```

---

# What is JSON?

When working with APIs, you will frequently encounter **JSON**.

JSON stands for:

**JavaScript Object Notation**

It is a common format for exchanging structured data between applications.

Example:

```json
{
    "name": "Avhishek",
    "age": 20,
    "skills": [
        "Python",
        "Machine Learning",
        "Pandas"
    ]
}
```

JSON looks similar to a Python dictionary.

### JSON

```json
{
    "name": "Avhishek",
    "age": 20
}
```

### Python Dictionary

```python
{
    "name": "Avhishek",
    "age": 20
}
```

This makes JSON relatively easy to work with in Python.

---

# Python `requests` Library

The `requests` library is commonly used in Python to communicate with HTTP APIs.

Install it using:

```powershell
pip install requests
```

Or:

```powershell
python -m pip install requests
```

Then import it:

```python
import requests
```

---

# Making Your First API Request

A basic API request looks like this:

```python
import requests

url = "https://api.example.com/data"

response = requests.get(url)

print(response.status_code)
print(response.text)
```

Let's understand each line.

### 1. Import requests

```python
import requests
```

This imports the `requests` library.

### 2. Store the API URL

```python
url = "https://api.example.com/data"
```

The URL tells Python where to send the request.

### 3. Send the request

```python
response = requests.get(url)
```

This sends a `GET` request.

### 4. Check the status

```python
print(response.status_code)
```

This tells us whether the request succeeded.

### 5. View the response

```python
print(response.text)
```

This prints the response as text.

---

# `response.text`

`response.text` returns the response as a string.

```python
print(response.text)
```

Example:

```text
{"name":"Avhishek","age":20}
```

---

# `response.json()`

If the API returns JSON, you can use:

```python
response.json()
```

Example:

```python
data = response.json()

print(data)
```

The JSON response can then be converted into Python data structures.

For example:

```json
{
    "name": "Avhishek",
    "age": 20
}
```

can become approximately:

```python
{
    "name": "Avhishek",
    "age": 20
}
```

which is a Python dictionary.

---

# Accessing JSON Data

Suppose the API returns:

```json
{
    "id": 101,
    "title": "Example Movie",
    "rating": 8.5
}
```

Python:

```python
data = response.json()

print(data["id"])
print(data["title"])
print(data["rating"])
```

Output:

```text
101
Example Movie
8.5
```

---

# JSON Lists

APIs often return multiple records.

Example:

```json
{
    "results": [
        {
            "id": 1,
            "title": "Movie A"
        },
        {
            "id": 2,
            "title": "Movie B"
        },
        {
            "id": 3,
            "title": "Movie C"
        }
    ]
}
```

You can access the list using:

```python
data = response.json()

movies = data["results"]

print(movies)
```

Then loop through the movies:

```python
for movie in movies:
    print(movie["title"])
```

Output:

```text
Movie A
Movie B
Movie C
```

---

# Query Parameters

Sometimes you want to specify additional information in your request.

For example:

```text
https://api.example.com/movies?page=2
```

Here:

```text
?page=2
```

is a query parameter.

Instead of manually creating the URL, Python's `requests` library allows you to use `params`.

```python
import requests

url = "https://api.example.com/movies"

params = {
    "page": 2
}

response = requests.get(
    url,
    params=params
)
```

This produces a request similar to:

```text
https://api.example.com/movies?page=2
```

---

# Multiple Query Parameters

You can send multiple parameters:

```python
params = {
    "page": 2,
    "limit": 20,
    "language": "en"
}

response = requests.get(
    url,
    params=params
)
```

The resulting URL may look like:

```text
https://api.example.com/movies?page=2&limit=20&language=en
```

---

# API Keys

Some APIs require an **API key**.

An API key is a credential that identifies your application or account when making requests.

For example:

```python
api_key = "YOUR_API_KEY"

params = {
    "api_key": api_key
}

response = requests.get(
    url,
    params=params
)
```

### Important

**Never publicly upload your API key to GitHub.**

Avoid doing this:

```python
api_key = "123456789abcdef"
```

inside a public repository.

---

# Environment Variables

A safer approach is to store API keys in environment variables.

Example:

```python
import os

api_key = os.getenv("API_KEY")

print(api_key)
```

You can also use a `.env` file with the `python-dotenv` package.

Example `.env`:

```text
API_KEY=your_secret_key
```

Python:

```python
from dotenv import load_dotenv
import os

load_dotenv()

api_key = os.getenv("API_KEY")
```

### Important

Add `.env` to `.gitignore`:

```text
.env
```

This prevents the file from accidentally being committed to Git.

---

# Headers

Some APIs require HTTP headers.

Headers provide additional information about the request.

Example:

```python
headers = {
    "Authorization": "Bearer YOUR_TOKEN"
}

response = requests.get(
    url,
    headers=headers
)
```

Common uses of headers include:

* Authentication
* Content type
* API versions
* Client information

---

# Authentication

Some APIs require you to prove that you are authorized to access them.

Common authentication approaches include:

### API Key

```text
api_key = "..."
```

### Bearer Token

```text
Authorization: Bearer YOUR_TOKEN
```

### OAuth

OAuth is commonly used when an application needs authorized access to resources on behalf of a user.

You should always follow the authentication method specified in the API's documentation.

---

# API Documentation

Before using an API, you should read its **official documentation**.

API documentation usually tells you:

* Base URL
* Available endpoints
* HTTP methods
* Required parameters
* Optional parameters
* Authentication
* Response format
* Status codes
* Rate limits
* Pagination
* Examples

For example, you might find documentation structured like:

```text
GET /movies

Parameters:
    page
    language
    api_key
```

Then you can construct your Python request based on those instructions.

---

# Base URL

An API may have a common base URL.

Example:

```text
https://api.example.com
```

Different endpoints can be added to it:

```text
https://api.example.com/movies
https://api.example.com/users
https://api.example.com/products
```

So:

```text
Base URL + Endpoint
```

gives you the complete API URL.

---

# Pagination

APIs often contain thousands or millions of records.

Returning everything in a single request would be inefficient.

Therefore, APIs often divide data into **pages**.

Example:

```text
Page 1 → Movies 1–20
Page 2 → Movies 21–40
Page 3 → Movies 41–60
```

You might request:

```python
params = {
    "page": 1
}

response = requests.get(
    url,
    params=params
)
```

Then:

```python
params = {
    "page": 2
}

response = requests.get(
    url,
    params=params
)
```

---

# Fetching Multiple Pages

A common ML data collection pattern is:

```python
import requests

all_data = []

for page in range(1, 6):

    params = {
        "page": page
    }

    response = requests.get(
        url,
        params=params
    )

    data = response.json()

    all_data.extend(data["results"])
```

Now:

```python
print(len(all_data))
```

can tell you how many records were collected.

---

# API Data → Pandas DataFrame

This is especially important for Machine Learning.

Once you retrieve JSON data, you can convert it into a Pandas DataFrame.

```python
import requests
import pandas as pd

response = requests.get(url)

data = response.json()

df = pd.DataFrame(data["results"])

print(df.head())
```

Now the API data becomes tabular data:

```text
       id       title       rating
0       1    Movie A        8.2
1       2    Movie B        7.5
2       3    Movie C        8.7
```

This is where APIs become particularly useful for ML learners.

---

# Complete API → DataFrame Workflow

A common workflow looks like this:

```text
API Documentation
       ↓
Find Endpoint
       ↓
Create Request
       ↓
Send GET Request
       ↓
Check Status Code
       ↓
Receive JSON
       ↓
Extract Required Data
       ↓
Convert to DataFrame
       ↓
Clean Data
       ↓
Explore Data
       ↓
Visualize Data
       ↓
Train ML Model
```

---

# Example ML Data Collection Workflow

Suppose an API provides movie information.

```python
import requests
import pandas as pd

url = "https://api.example.com/movies"

response = requests.get(url)

if response.status_code == 200:

    data = response.json()

    df = pd.DataFrame(data["results"])

    print(df.head())

else:

    print("Request failed")
    print(response.status_code)
```

This workflow is very common in data science.

---

# Handling API Errors

Never assume that every API request will succeed.

You can check:

```python
if response.status_code == 200:
    data = response.json()
else:
    print("Request failed")
```

You can also use:

```python
response.raise_for_status()
```

Example:

```python
import requests

response = requests.get(url)

response.raise_for_status()

data = response.json()
```

If the request fails with an HTTP error, an exception can be raised.

---

# Using `try-except`

For more robust code:

```python
import requests

try:

    response = requests.get(url)

    response.raise_for_status()

    data = response.json()

    print(data)

except requests.exceptions.RequestException as e:

    print("API request failed:", e)
```

This helps handle problems such as:

* Connection errors
* Timeout errors
* Invalid URLs
* HTTP errors

---

# Request Timeout

It is a good practice to specify a timeout.

```python
response = requests.get(
    url,
    timeout=10
)
```

This prevents your program from waiting indefinitely for a response.

---

# API Rate Limits

Many APIs limit how many requests you can make within a certain period.

For example:

```text
100 requests per minute
```

If you exceed the limit, you may receive:

```text
429 Too Many Requests
```

Therefore, when collecting large datasets, always check the API documentation for its rate limits.

---

# APIs and Data Collection

APIs can be used as an automated data source.

For example:

```text
          API
           ↓
      Raw JSON Data
           ↓
    Python Requests
           ↓
      Pandas DataFrame
           ↓
       Data Cleaning
           ↓
     Exploratory Analysis
           ↓
      Feature Engineering
           ↓
      Machine Learning
```

---

# API vs CSV

You may wonder:

> Why use an API if I can download a CSV?

### CSV

A CSV file is usually a **static dataset**.

```text
Download CSV
     ↓
Save File
     ↓
Read with Pandas
```

Example:

```python
df = pd.read_csv("data.csv")
```

### API

An API allows you to **request data programmatically**.

```text
Python
  ↓
API Request
  ↓
Server
  ↓
Fresh/available data
  ↓
Python
```

Example:

```python
response = requests.get(url)
```

### Comparison

| Feature                | CSV                  | API                |
| ---------------------- | -------------------- | ------------------ |
| Data access            | File                 | Request            |
| Automation             | Limited              | High               |
| Dynamic data           | Usually no           | Often yes          |
| Real-time data         | Usually no           | Sometimes          |
| Easy to start          | Yes                  | Yes                |
| Large-scale collection | Can be difficult     | Often easier       |
| Authentication         | Usually not required | Sometimes required |

---

# API vs Web Scraping

API and web scraping are different approaches.

### API

```text
Your Program
     ↓
    API
     ↓
Structured Data
```

### Web Scraping

```text
Your Program
     ↓
Web Page
     ↓
HTML
     ↓
Extract Data
```

When an official API provides the data you need, using the API is often simpler and more structured than scraping the webpage.

---

# REST API

One of the most common types of web APIs is a **REST API**.

REST stands for:

**Representational State Transfer**

REST APIs commonly use HTTP methods such as:

```text
GET
POST
PUT
PATCH
DELETE
```

and resources are commonly represented through URLs.

Example:

```text
GET /users
GET /users/1

POST /users

PUT /users/1

DELETE /users/1
```

---

# REST API Example

Imagine an API for students.

### Get all students

```text
GET /students
```

### Get one student

```text
GET /students/101
```

### Create a student

```text
POST /students
```

### Update a student

```text
PUT /students/101
```

### Delete a student

```text
DELETE /students/101
```

---

# API Data Types

API responses can contain different types of data.

Common formats include:

* JSON
* XML
* CSV
* Plain text

JSON is particularly common in modern web APIs.

---

# Nested JSON

API responses can sometimes be complicated.

Example:

```json
{
    "page": 1,
    "results": [
        {
            "id": 1,
            "movie": {
                "title": "Movie A",
                "rating": 8.5
            }
        }
    ]
}
```

You may need to navigate through multiple levels:

```python
data = response.json()

title = data["results"][0]["movie"]["title"]

print(title)
```

Output:

```text
Movie A
```

Understanding Python dictionaries and lists is therefore very important when working with APIs.

---

# Saving API Data

After collecting data, you can save it.

### CSV

```python
df.to_csv(
    "movies.csv",
    index=False
)
```

### JSON

```python
df.to_json(
    "movies.json",
    orient="records"
)
```

This allows you to reuse the collected dataset without making API requests every time.

---

# A Practical API Data Collection Script

```python
import requests
import pandas as pd

url = "https://api.example.com/movies"

all_movies = []

for page in range(1, 6):

    params = {
        "page": page
    }

    response = requests.get(
        url,
        params=params,
        timeout=10
    )

    response.raise_for_status()

    data = response.json()

    all_movies.extend(data["results"])


df = pd.DataFrame(all_movies)

print(df.head())

df.to_csv(
    "movies.csv",
    index=False
)
```

### What is happening?

```text
1. Import requests
        ↓
2. Import pandas
        ↓
3. Define API URL
        ↓
4. Create empty list
        ↓
5. Request multiple pages
        ↓
6. Receive JSON
        ↓
7. Extract results
        ↓
8. Add results to list
        ↓
9. Convert list to DataFrame
        ↓
10. Save as CSV
```

---

# Important API Terms

| Term        | Meaning                                      |
| ----------- | -------------------------------------------- |
| API         | Interface for software communication         |
| Client      | Application making the request               |
| Server      | Application processing the request           |
| Endpoint    | Specific API URL                             |
| Request     | Message sent to an API                       |
| Response    | Data returned by the API                     |
| HTTP        | Protocol commonly used for web communication |
| GET         | Retrieve data                                |
| POST        | Create/send data                             |
| PUT         | Replace/update data                          |
| PATCH       | Partially update data                        |
| DELETE      | Delete data                                  |
| JSON        | Common data exchange format                  |
| Parameter   | Extra information sent with a request        |
| Header      | Additional request/response information      |
| API Key     | Credential used by some APIs                 |
| Token       | Credential used for authentication           |
| Pagination  | Dividing results into multiple pages         |
| Rate Limit  | Restriction on request frequency             |
| Status Code | Indicates the result of a request            |

---

# Common Python Libraries for APIs

### Requests

The most common starting point:

```python
import requests
```

### Pandas

Useful for converting API data into DataFrames:

```python
import pandas as pd
```

### JSON

Python's built-in JSON module:

```python
import json
```

### python-dotenv

Useful for loading secrets from `.env` files:

```python
from dotenv import load_dotenv
```

---

# Recommended API Learning Workflow

As an ML learner, learn APIs in this order:

### Level 1 — Basics

Learn:

* What is an API?
* Client and server
* Endpoint
* Request
* Response
* HTTP
* JSON

### Level 2 — HTTP

Learn:

* GET
* POST
* PUT
* PATCH
* DELETE
* Status codes
* Headers
* Query parameters

### Level 3 — Python

Practice:

```python
import requests

response = requests.get(url)

print(response.status_code)
print(response.json())
```

### Level 4 — Data Extraction

Learn how to:

* Access dictionaries
* Access lists
* Loop through JSON
* Extract required fields
* Handle nested JSON

### Level 5 — Pandas

Learn:

```python
pd.DataFrame()
```

and convert API responses into DataFrames.

### Level 6 — Advanced API Concepts

Learn:

* API keys
* Authentication
* Tokens
* Pagination
* Rate limits
* Error handling
* Timeouts
* Environment variables

### Level 7 — ML Projects

Finally, build projects where you:

```text
API
 ↓
Data Collection
 ↓
Pandas
 ↓
Data Cleaning
 ↓
EDA
 ↓
Feature Engineering
 ↓
Machine Learning
```

---

# Mini Practice Project

## Movie Data Collection Using an API

### Objective

Collect movie information from an API and create a Pandas DataFrame.

### Steps

```text
1. Find a movie API
2. Read its documentation
3. Get an API key if required
4. Find the movie endpoint
5. Send a GET request
6. Check the status code
7. Convert response to JSON
8. Extract movie records
9. Convert records to DataFrame
10. Clean the data
11. Save the data as CSV
12. Perform EDA
```

Possible columns:

```text
id
title
overview
release_date
popularity
vote_average
vote_count
```

---

# API Learning Checklist

Use this checklist while learning:

* [ ] Understand what an API is
* [ ] Understand client and server
* [ ] Understand endpoints
* [ ] Understand requests and responses
* [ ] Learn HTTP methods
* [ ] Learn status codes
* [ ] Understand JSON
* [ ] Install and use `requests`
* [ ] Make a GET request
* [ ] Read `response.status_code`
* [ ] Read `response.text`
* [ ] Use `response.json()`
* [ ] Access JSON dictionaries
* [ ] Access JSON lists
* [ ] Work with nested JSON
* [ ] Use query parameters
* [ ] Understand headers
* [ ] Understand API keys
* [ ] Learn authentication
* [ ] Learn pagination
* [ ] Learn rate limits
* [ ] Handle API errors
* [ ] Use timeouts
* [ ] Convert API data to Pandas DataFrame
* [ ] Save API data as CSV
* [ ] Build an API-based ML dataset

---

# Key Takeaway

An API provides a structured way for your Python program to communicate with another application or service.

For a Machine Learning learner, the most important workflow to remember is:

```text
API Documentation
       ↓
Endpoint
       ↓
GET Request
       ↓
JSON Response
       ↓
Extract Data
       ↓
Pandas DataFrame
       ↓
Data Cleaning
       ↓
EDA
       ↓
Machine Learning
```

The basic Python pattern is:

```python
import requests
import pandas as pd

response = requests.get(url)

response.raise_for_status()

data = response.json()

df = pd.DataFrame(data["results"])

print(df.head())
```

Once you understand this pattern, you can start collecting real-world datasets from APIs and using them in your Data Science and Machine Learning projects.
