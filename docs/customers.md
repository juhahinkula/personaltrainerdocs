# Customers

## Base URL
```
https://customerrestservice-personaltraining.rahtiapp.fi/api
```
## Endpoints

### Get All Customers
Retrieve all customers

**Request:**

- HTTP Method: `GET`
- Endpoint: `/customers`
- Request parameters: None

**Response:**

The response is a JSON object with a `_embedded` field containing an array of customers. Each customer object includes the following fields:

- `firstname`: The customer's first name. (string)
- `lastname`: The customer's last name. (string)
- `streetaddress`: The customer's street address. (string)
- `postcode`: The customer's postal code. (string)
- `city`: The city where the customer lives. (string)
- `email`: The customer's email address. (string)
- `phone`: The customer's phone number. (string)
- `_links`: A set of links related to the customer. Each link object includes:
    - `self`: A link to the customer's own information. (string)
    - `customer`: A link to the customer's information. (string)
    - `trainings`: A link to the customer's trainings. (string)

Example Response
```json
{
  "_embedded": {
    "customers": [
      {
        "firstname": "Mark",
        "lastname": "Johnson",
        "streetaddress": "5th Street",
        "postcode": "23110",
        "city": "Flintsone",
        "email": "john@mail.com",
        "phone": "232-2345540",
        "_links": {
          "self": {
            "href": "https://customerrestservice-personaltraining.rahtiapp.fi/api/customers/1002"
          },
          "customer": {
            "href": "https://customerrestservice-personaltraining.rahtiapp.fi/api/customers/1002"
          },
          "trainings": {
            "href": "https://customerrestservice-personaltraining.rahtiapp.fi/api/customers/1002/trainings"
          }
        }
      },
      // Additional customers...
    ]
  }
}
```

### Get Customer by Id
Retrieve a specific customer's details.

**Request:**

- HTTP Method: `GET`
- Endpoint: `/customers/{id}`
- Path parameters: `{id}` (integer, required) is the unique identifier of the customer

Example Request:
```
GET /customers/123
```
**Response:**

- Body: JSON object with the customer's details.

### Create New Customer
Create a new customer.

**Request:**

- HTTP Method: `POST`
- Endpoint: `/customers`
- Request Headers:
    - `'Content-Type' : 'application/json'`
- Request body: JSON object with the following fields (all required)
    - `firstname`: The customer's first name. (string, required)
    - `lastname`: The customer's last name. (string, required)
    - `email`: The customer's email address. (string, required)
    - `phone`: The customer's phone number. (string, required)
    - `streetaddress`: The customer's street address. (string, required)
    - `postcode`: The customer's postal code. (string, required)
    - `city`: The city where the customer lives. (string, required)

Example Request:
```json
POST https://customerrestservice-personaltraining.rahtiapp.fi/api/customers
Content-Type: application/json

{
  "firstname": "John",
  "lastname": "Smith",
  "email": "j.s@smith.com",
  "phone": "343-2332345",
  "streetaddress": "Yellow Street 23",
  "postcode": "344342",
  "city": "Yellowstone"
}
```

**Response:**

- Body: JSON object with the created customer's details.

### Update Customer

Update a specific customer's details.

**Request:**

- HTTP Method: `PUT`
- Endpoint: `/customers/{id}`
- Path Parameters: `id` (integer, required): The unique identifier of the customer.
- Request Headers:
    - `'Content-Type' : 'application/json'`
- Request body: JSON object containing the updated customer details (all fields optional).

Example Request:
```json
PUT /customers/123
Content-Type: application/json

{
    "firstname": "John",
    "lastname": "Smith",
    "email": "j.s@smith.com",
    "phone": "342-2332345",
    "streetaddress": "Yellow Street 23",
    "postcode": "144342",
    "city": "Yellowstone"
}
```
**Response:**

- Body: JSON object with the updated customer's details.

### Delete Customer

Delete a specific customer.

**Request:**

- HTTP Method: `DELETE`
- Endpoint: `/customers/{id}`
- Path Parameters: `id` (integer, required): The unique identifier of the customer.

**Response:**

- Upon successful deletion, the API will return a 204 No Content status code. If the customer with the provided id does not exist, the API will return a 404 Not Found status code.

***Important Note:***

Deleting a customer will also delete all associated training sessions for that customer. This operation cannot be undone, so ensure that you want to delete both the customer and all their training sessions before making this request.
