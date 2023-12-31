# Intro to Application Programming Interfaces (APIs)

- Bridges communication between two pieces of software
- Examples of APIs: Rest:API, GraphQL, SOAP, gRPC (These are architectural styles)
- API for learning about this: https://bored-api.appbrewery.com/

## Structuring API requests

### Formatting API Requests (Endpoints, Path Parameters and Query Parameters):

- Endpoints:

  - eg: BaseURL/Endpoint
  - The Endpoint can change depending on what information you're trying to access
  - In the case of the above bored-api, you can use the /random endpoint, which will GET you a random activity, or there's a /filter endpoint, for if you want to filter activities by a certain criteria

- Query Parameters (More used for filtering and searching):

  - eg: https://url/endpoint?query=value (or, as an actual link: https://bored-api.appbrewery.com/filter?type=education)
  - You can provide multiple queries using an ampersand (&): https://url/endpoint?query=value&query2=value
    - Postman example URL: https://bored-api.appbrewery.com/filter?type=social&participants=2 (type is social, second query is participants)

- Path Parameters (Identifying resource by a parameter):
  - eg: https://url/endpoint/{path-parameter} - path-parameters are usually things with multiple options, like ids, usernames and very specific
  - Postman example url: https://bored-api.appbrewery.com/activity/3943506 < The number on the end corresponds with the "key" that can be returned as a response to identify a specific activity

## JSON (JavaScript Object Notation):

- A way of formatting data to send in a readable way.

Example of JSON vs JS Object (from which it gets its name):

- all keys must be within quotation marks ""

```
JSON:
{
    "name": "Paige",
    "age": 31,
    "city": "Cardiff",
    "education": [
        {
            "degree": "Level 5 CS",
            "university": "Code Institute",
        }
    ]
}

vs. JavaScript Object:

const paige = {
    name: "Paige",
    age: 31,
    city: "Cardiff",
    education: [{
        degree: "Level 5 CS",
        university: "Code Institute"
    }]
}

```

- To make viewing JSON easier, use a viewer such as: [JSONViewer](https://jsonviewer.stack.hu)

- In order to send things across the internet/server in a readable form, we need to use a serializer, such as the stringify() method:

```
const jsonData = JSON.stringify(data); (the data variable in the parameters is what represents the JS Object that needs to be serialized);
```

- The reverse, so to unpack the JSON into an object (parse()):

```
const data = JSON.parse(jsonData);
```

- Review the folder JSON's code to refresh your knowledge!

## Making Server-Side requests with Axios



## Authentication

## Rest APIs

- Uses HTTP protocol to communicate (GET, POST, PUT, PATCH, DELETE)

## Extra: Making request using WTISSA API via Postman:

- satellites/[id] (this endpoint will be used when structuring your request later)
  Returns position, velocity, and other related information about a satellite for a given point in time. [id] is required and should be the NORAD catalog id. For the ISS, that id is 25544.
- So, as we know from previously using API, the catalogue ID will need to be GET requested from the id key in the returned JSON object.

Example Resource URL
https://api.wheretheiss.at/v1/satellites/25544 < Paste this into a Postman GET request and return the body as JSON.

- This should return the following (example resource):

```
{"name":"iss",
"id":25544,
"latitude":51.795919522034,
"longitude":-165.66020579602,
"altitude":423.81129215421,
"velocity":27586.655394123,
"visibility":"eclipsed",
"footprint":4526.8029991644,
"timestamp":1704035318,
"daynum":2460310.1309954,
"solar_lat":-23.086105636387,
"solar_lon":313.57347872302,
"units":"kilometers"}
```

- These are parameters that can be used to display data.
