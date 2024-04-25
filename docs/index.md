# General

## Personal Trainer REST API Documentation

This REST API is designed to manage the relationship between personal trainers and their customers. It provides a set of CRUD (Create, Read, Update, Delete) operations to manage both customers and their associated training sessions.

Overview:

The API is structured around two main resources: [**Customers**](customers.md) and [**Trainings**](trainings.md).

- Customers represent the individuals who are receiving personal training. Each customer has attributes such as name and contact information.

- Trainings represent the individual training sessions that a customer has with their personal trainer. Each training session has attributes such as date, time, duration, and the specific exercises performed.

There is a one-to-many relationship between customers and trainings, meaning that each customer can have multiple associated training sessions, but each training session is associated with only one customer.

## Base URL
```
https://customerrestservice-personaltraining.rahtiapp.fi/api
```

## Reset Database
To reset database you can use the following request that deletes all data from the database and re-populate it with the original demo data. 

```
POST https://customerrestservice-personaltraining.rahtiapp.fi/reset
```
Response:

Upon successful reset, the API will return a 200 OK status code and the response body contains text: **DB reset done**. If the reset operation fails for any reason, the API will return an appropriate error status code and message.
