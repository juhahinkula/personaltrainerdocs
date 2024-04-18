# Customers

## Base URL
```
https://customerrestservice-personaltraining.rahtiapp.fi/api
```
## Endpoints

### Get All Customers
To retrieve all customers , you can use the `GET /customers` endpoint.

Request:

No parameters are required for this endpoint.

Response:

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
To retrieve a specific customer's details, you can use the `GET /customers/{id}` endpoint, where `{id}` is the unique identifier of the customer.

Request:

- The request does not require a request body, only the customer's id as a path parameter.

Path Parameters:

- `id` (required): The unique identifier of the customer. This is an integer.

Example Request:
```
GET /customers/123
```

### Create New Customer
To create a new customer you can use `POST /customers` endpoint.

Request:

This endpoint requires a JSON object in the request body with the following fields:

- `firstname`: The customer's first name. (string, required)
- `lastname`: The customer's last name. (string, required)
- `email`: The customer's email address. (string, required)
- `phone`: The customer's phone number. (string, required)
- `streetaddress`: The customer's street address. (string, required)
- `postcode`: The customer's postal code. (string, required)
- `city`: The city where the customer lives. (string, required)

Headers:

 `'Content-Type': 'application/json'`.

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

### Update Customer

To update a specific customer's details, you can use the `PUT /customers/{id}` endpoint, where `{id}` is the unique identifier of the customer.

Request:

The request requires the customer's id as a path parameter and the updated customer details in the request body as a JSON string.

Headers:

`Content-Type: 'application/json'`

Path Parameters:

`id` (required): The unique identifier of the customer. This is an integer.

Request Body:
The request body should be a JSON object containing the updated customer details. All fields are optional, and only the provided fields will be updated.

- `firstname`: The first name of the customer.
- `lastname`: The last name of the customer.
- `email`: The email address of the customer.
- `phone`: The phone number of the customer.
- `streetaddress`: The street address of the customer.
- `postcode`: The postal code of the customer's address.
- `city`: The city of the customer's address.

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
### Delete Customer

To delete a specific customer, you can use the `DELETE /customers/{id}` endpoint, where `{id}` is the unique identifier of the customer.

Request:

The request does not require a request body, only the customer's ``id` as a path parameter.

Path Parameters:

`id` (required): The unique identifier of the customer. This is an integer.
Example Request


Response:

Upon successful deletion, the API will return a 204 No Content status code. If the customer with the provided id does not exist, the API will return a 404 Not Found status code.

Important Note:

Deleting a customer will also delete all associated training sessions for that customer. This operation cannot be undone, so ensure that you want to delete both the customer and all their training sessions before making this request.
