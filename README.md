# Automated testing of the Requests API test resource

[Reqres API](https://reqres.in) is a popular test API that provides dummy data for developers to test their applications without using real data. It is possible to execute various HTTP requests (GET, POST, PUT, DELETE, etc.) and receive responses in JSON format.

My colleagues and I worked together on this project. Our collaborative project can be seen [here](https://github.com/RomanBurlaka78/ReqresForwardApi).

My tests can be found in this repository.

## Test Scenarios

The table below outlines the test cases, including the endpoint, test type (positive/negative), description, expected behavior, and assertions.

| **Endpoint**         | **Test Type**  | **Test Description**                                               | **Expected Behavior**                                                                 | **Assertions**                                                                                 |
|-----------------------|----------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| `GET /api/users/2`    | Positive       | Retrieve details of an existing user.                              | Returns a `200` status and the user data for ID 2.                                    | Status code is `200`; response contains `id: 2`, `email`, `first_name`, `last_name`.           |
| `GET /api/users/23`   | Negative       | Attempt to retrieve a non-existent user.                           | Returns a `404` status with an empty response body.                                   | Status code is `404`; response body is empty.                                                 |
| `POST /api/users`     | Positive       | Successfully create a new user with valid data.                    | Returns a `201` status with the user’s name, job, ID, and created timestamp.          | Status code is `201`; response contains `name`, `job`, `id`, and `createdAt`.                 |
| `POST /api/users`     | Negative       | Attempt to create a user with missing required fields.             | Returns a `400` status with an error message.                                        | Status code is `400`; response contains `error: Missing required fields`.                     |
| `PUT /api/users/2`    | Positive       | Update an existing user with valid data.                           | Returns a `200` status and the updated user data.                                     | Status code is `200`; response contains updated `name`, `job`, and `updatedAt`.               |
| `PUT /api/users/2`    | Negative       | Attempt to update a user with invalid data types.                  | Returns a `400` status with an error message.                                        | Status code is `400`; response contains `error: Invalid input`.                               |
| `DELETE /api/users/2` | Positive       | Delete an existing user.                                           | Returns a `204` status with no response body.                                        | Status code is `204`; response body is empty.                                                 |
| `DELETE /api/users/23`| Negative       | Attempt to delete a non-existent user.                             | Returns a `404` status with an error message.                                        | Status code is `404`; response contains `error: User not found`.                              |
| `POST /api/register`  | Positive       | Successfully register a user with valid email and password.        | Returns a `200` status with the user’s ID and token.                                  | Status code is `200`; response contains `id` and `token`.                                     |
| `POST /api/register`  | Negative       | Attempt to register a user with missing password.                  | Returns a `400` status with an error message.                                        | Status code is `400`; response contains `error: Missing password`.                            |
| `POST /api/login`     | Positive       | Successfully log in a user with valid credentials.                 | Returns a `200` status with the user’s token.                                         | Status code is `200`; response contains `token`.                                              |
| `POST /api/login`     | Negative       | Attempt to log in a user with incorrect credentials.               | Returns a `400` status with an error message.                                        | Status code is `400`; response contains `error: Invalid credentials`.                         |
| `GET /api/unknown`    | Positive       | Retrieve a list of resources.                                      | Returns a `200` status with a list of resources.                                      | Status code is `200`; response contains a `data` array with resource objects.                 |
| `GET /api/unknown/2`  | Positive       | Retrieve details of a specific resource.                           | Returns a `200` status with the resource data for ID 2.                               | Status code is `200`; response contains `id`, `name`, `year`, `color`, and `pantone_value`.   |
| `GET /api/unknown/23` | Negative       | Attempt to retrieve a non-existent resource.                       | Returns a `404` status with an empty response body.                                   | Status code is `404`; response body is empty.                                                 |
