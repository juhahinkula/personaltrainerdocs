
# Trainings 

## Base URL
```
https://customer-rest-service-frontend-personaltrainer.2.rahtiapp.fi/api/
```
## Endpoints

### Get All Trainings
Retrieve all training sessions

**Request:**

- HTTP Method: `GET`
- Endpoint: `/trainings`
- Request parameters: None

Example Request:
```
GET /trainings
```

**Response:** 

- The response will be a JSON object containing an array of training sessions. Each training session object includes the date, duration, activity, and several links related to the training session.

Response Object:

The response object will contain an `_embedded` object, which includes an array of trainings. Each training object will have the following properties:

- `date`: The date and time of the training session.
- `duration`: The duration of the training session, in minutes.
- `activity`: The type of activity performed during the training session.
- `_links`: An object containing links related to the training session.
    - `self`: A link to the training session itself.
    - `training`: Another link to the training session itself.
    - `customer`: A link to the customer associated with the training session.

```json
{
  "_embedded": {
    "trainings": [
      {
        "date": "2024-04-18T18:59:46.350+00:00",
        "duration": 30,
        "activity": "Gym training",
        "_links": {
          "self": {
            "href": "https://customerrestservice-personaltraining.rahtiapp.fi/api/trainings/3417"
          },
          "training": {
            "href": "https://customerrestservice-personaltraining.rahtiapp.fi/api/trainings/3417"
          },
          "customer": {
            "href": "https://customerrestservice-personaltraining.rahtiapp.fi/api/trainings/3417/customer"
          }
        }
      },
      {
        "date": "2024-04-19T18:59:46.350+00:00",
        "duration": 90,
        "activity": "Zumba",
        "_links": {
          "self": {
            "href": "https://customerrestservice-personaltraining.rahtiapp.fi/api/trainings/3418"
          },
          "training": {
            "href": "https://customerrestservice-personaltraining.rahtiapp.fi/api/trainings/3418"
          },
          "customer": {
            "href": "https://customerrestservice-personaltraining.rahtiapp.fi/api/trainings/3418/customer"
          }
        }
      }
    ]
  }
}
```
### Get Trainings with Customer Info
Retrieve all training sessions along with their associated customer information.

**Request:**

- HTTP Method: `GET`
- ENDPOINT: `/gettrainings`
- Request parameters: None
 
Example Request:
```
GET https://customer-rest-service-frontend-personaltrainer.2.rahtiapp.fi/api/gettrainings
```
**Response:** 

The response will be a JSON object containing an array of training sessions. Each training session object includes the id, date, duration, activity, and the associated customer's information.

- `id`:  The unique identifier of the training session.
- `date`: The date and time of the training session.
- `duration`: The duration of the training session, in minutes.
- `activity`: The type of activity performed during the training session.
- `customer`: An object containing the associated customer's information.

Example Response:
```json
[
  {
    "id": 3417,
    "date": "2024-04-18T18:59:46.350+00:00",
    "duration": 30,
    "activity": "Gym training",
    "customer": {
      "id": 1087,
      "firstname": "John",
      "lastname": "Johnson",
      "streetaddress": "5th Street",
      "postcode": "23110",
      "city": "Flintsone",
      "email": "john@mail.com",
      "phone": "232-2345540"
    }
  },
  {
    "id": 3418,
    "date": "2024-04-19T18:59:46.350+00:00",
    "duration": 90,
    "activity": "Zumba",
    "customer": {
      "id": 1088,
      "firstname": "Mary",
      "lastname": "Philips",
      "streetaddress": "Hill Street 3",
      "postcode": "23322",
      "city": "Flintsone",
      "email": "m.philips@mail.com",
      "phone": "232-310122"
    }
  }
]
```

### Add Training
Add a new training session and link it to a customer.

**Request:**

- HTTP Method: `POST`
- Endpoint: `/trainings`
- Request Headers:
    - `'Content-Type' : 'application/json'`
- Body: JSON object containing the details of the new training session and a reference link to the customer.
    - `date`: The date of the training session. The format must be ISO-8601 (e.g., "2024-11-27T09:12:00.000+000").
    - `activity`: The type of activity performed during the training session.
    - `duration`: The duration of the training session, in minutes.
    - `customer`: A link to the customer associated with the training session.

Example Request:
```json
POST /trainings
Content-Type: application/json

{
    "date": "2024-01-01T12:00:00.000+000",
    "activity": "Spinning",
    "duration": "50",
    "customer": "https://myserver.personaltrainer.api/api/customers/123"
}
```

**Response:**

The response will be a JSON object containing the details of the newly created training session. If the creation is successful, the API will return a 201 Created status code.

### Delete Training
Delete a specific training session.

**Request:**

- HTTP Method: `DELETE`
- Endpoint: `/trainings/{id}`
- Path Parameters: `id` (integer, required). The unique identifier of the training session.

Example Request:
```
DELETE /trainings/123
```

**Response:**

- Upon successful deletion, the API will return a 204 No Content status code. If the training session with the provided id does not exist, the API will return a 404 Not Found status code.
