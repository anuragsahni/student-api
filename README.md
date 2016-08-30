Sample Student API
========

Objective
---------

Develop a RESTful API in Java using the existing Spring dependencies (Web, JPA) provided in the Maven pom.xml file included in the quickstart. 

Feel free to add additional dependencies as necessary, so long as they are available in the standard maven repository. 

The purpose of the API is to serve data about people. These people may be students, faculty, or staff members of a University. 
It should allow an end user to upload a comma separated values (CSV) file -- as included under data/People.csv -- that will populate a simple in memory or file-based relational database such as HSQL that can then be queried to search for people by certain fields.

To run the API, you'll use the following command. More information about testing and running Spring Boot applications can be found in the Spring documentation online.

    mvn spring-boot:run   



Resources
---------------

The API should minimally include the following resources:

- **POST /people** to upload a CSV file with a Content-Type of multipart/form-data
- **POST /people** to subject a JSON representation of a person with a Content-Type of application/json
- **GET /people** with zero or more query parameters as shown below to retrieve a JSON representation of search results


#### Upload csv file

This is the primary mechanism by which data is added to the data store. 

    POST /people
    Content-Type: multipart/form-data
    
The content of the multipart request would be a file formatted as shown by the data/People.csv file provided. 
    

#### Add a single person in JSON format

This resource should create a new person and assign a unique identifier on each POST. The example below shows what this would look like if the representation for
 a single person object was passed, but feel free to adjust the request body to be a JSON list of people if you prefer, though you may need to adjust the response code and
 body to reflect that change. 

    POST /people
    { 
        "firstName": "Tim",
        "lastName": "Tester",
        "affiliations": [ "faculty", "staff", "student"],
        "birthDate": "1988-09-20",
        "lastEnrolledTerm": "Spring",
        "lastEnrolledYear": "2015",
        "hireDate": "2002-07-31",
        "separationDate": "",
        "address": {
            "line1": "1 Testington Ln",
            "line2": "",
            "city": "Seattle",
            "state": "WA",
            "zip": "98103"
        }
    }
    
    201 Created
    Location: http://localhost:8080/people/583453

----------------------
#### Search for people

If time permits add some basic search for people exposing the REST API to search by zipcode , name etc.

-------------------
#### Expectations

The basic expectation of this assignment is that you will use Spring Boot and Spring Web to build a RESTful API -- you may want to take a look at this guide if you haven't used the Spring Java Config annotations to build web services in the past: https://spring.io/guides/gs/rest-service/

1. The API should use an in memory relational database, such as H2 or HSQL 
2. It should take advantage of Spring Boot's embedded servlet container to run and test the resources.
3. It does NOT need to provide any security or authentication
4. It should use Maven for dependency and build management
5. It should follow common Java best practices in terms of documentation, style, and use of collections and design patterns
6. It should use JDK version 1.7 or 1.8.
7. Some basic exception handling should be provided, including use of standard HTTP status codes to indicate when a query parameter is unacceptable, for example
8. To test out the API you can use Postman App (www.getpostman.com).

--------------------
#### General Advice

If you feel that any information is missing or unclear, then please make a choice that makes sense for you and provide the reason of your choice, either in the code or in an attached document.

    
    
    