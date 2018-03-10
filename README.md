# Project 7: Authenticated brevet time calculator service

## Author and Contact
# Luyao Wang
# luyaow@uoregon.edu

Register a new_user:
* http://localhost:5001/api to register username
After register then u go
* http://localhost:5001/api/register to get the value
Get Token (this is example)
* http://localhost:5001/api/token?username=luyaow&password=UOCIS322 to test username and password, here you can change the username and password


*  http://localhost:5001/api/protected/eyJhbGciOiJIUzI1NiIsImlhdCI6MTUyMDY2Mzg4OSwiZXhwIjoxNTIwNjY0NDg5fQ.eyJpZCI6Mn0.m7-4hp7fJPNGkW69uskZFppqGes39xf5j_s_6kY9vGI to get the token

* http://localhost:5001/listOpenOnly?token=eyJhbGciOiJIUzI1NiIsImlhdCI6MTUyMDY2NTExOCwiZXhwIjoxNTIwNjY1NzE4fQ.eyJpZCI6MX0.C4vY73Qo-P_CUw6_QIattVQZQLd8JI_U3BVEVcJm5V0 change the token =, and listOpenOnly to any other request.


## Recap

You will reuse *your* code from project
6 (https://github.com/UOCIS322/proj6-rest). Recall: you created the
following three parts:

* You designed RESTful services to expose what is stored in MongoDB.
Specifically, you used the boilerplate given in DockerRestAPI folder, and
created the following:

** "http://<host:port>/listAll" should return all open and close times in the database

** "http://<host:port>/listOpenOnly" should return open times only

** "http://<host:port>/listCloseOnly" should return close times only

* You also designed two different representations: one in csv and one
 in json. For the above, JSON should be your default representation.

** "http://<host:port>/listAll/csv" should return all open and close times in CSV format

** "http://<host:port>/listOpenOnly/csv" should return open times only in CSV format

** "http://<host:port>/listCloseOnly/csv" should return close times only in CSV format

** "http://<host:port>/listAll/json" should return all open and close times in JSON format

** "http://<host:port>/listOpenOnly/json" should return open times only in JSON format

** "http://<host:port>/listCloseOnly/json" should return close times only in JSON format

* You also added a query parameter to get top "k" open and close
times. For examples, see below.

** "http://<host:port>/listOpenOnly/csv?top=3" should return top 3 open times only (in ascending order) in CSV format

** "http://<host:port>/listOpenOnly/json?top=5" should return top 5 open times only (in ascending order) in JSON format

* You'll also designed consumer programs (e.g., in jQuery) to expose the services.

## Functionality you will add

In this project, you will add the following functionality:

- POST **/api/register**

    Registers a new user. On success a status code 201 is returned. The body of the response contains
a JSON object with the newly added user. A `Location` header contains the URI
of the new user. On failure status code 400 (bad request) is returned. Note: The
password is hashed before it is stored in the database. Once hashed, the original
password is discarded. Your database should have three fields: id (unique index),
username and password.

- GET **/api/token**

    Returns a token. This request must be authenticated using a HTTP Basic
Authentication (see password.py for example). On success a JSON object is returned
with a field `token` set to the authentication token for the user and
a field `duration` set to the (approximate) number of seconds the token is
valid. On failure status code 401 (unauthorized) is returned.

- GET **/RESOURCE-YOU-CREATED-IN-PROJECT-6**

    Return a protected <resource>, which is basically what you created in project 6. This request must be authenticated using token-based authentication only (see testToken.py). HTTP password-based (basic) authentication is not allowed. On success a JSON object with data for the authenticated user is returned. On failure status code 401 (unauthorized) is returned.

## Tasks

You'll turn in your credentials.ini using which we will get the following:

* The working application with three parts.

* Dockerfile

* docker-compose.yml
