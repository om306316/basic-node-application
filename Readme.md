# Basic Node Application

This is a basic Node.js application that includes rate limiting, token generation, and caching.

## Prerequisites

- Node.js
- npm (Node Package Manager)

## Installation

1. Clone the repository:

    ```sh
    git clone <repository-url>
    ```

2. Navigate to the project directory:

    ```sh
    cd basic-node-application
    ```

3. Install the dependencies:

    ```sh
    npm install
    ```

4. Create a `.env` file in the root directory and add the following environment variables:

    ```plaintext
    SECRET_KEY=omprakashkey
    PORT=3000
    RATE_LIMIT_WINDOW_MS=60000
    RATE_LIMIT_MAX=5
    CACHE_TTL=300
    ```

## Running the Application

1. Start the server:

    ```sh
    npm start
    ```

2. The server will start listening on the port specified in the `.env` file (default is `3000`).

## API Endpoints

### Generate Token

- **Endpoint:** `/generate-token`
- **Method:** `GET`
- **Parameters:**
  - `id` (required): The user ID.
  - `username` (required): The username.

- **Example Request:**

    ```sh
    curl "app-demo-node-bkapemhuecbhhcbe.eastus-01.azurewebsites.net/generate-token?id=1&username=testuser"
    ```

- **Example Response:**

    ```json
    {
      "token": "<your-jwt-token>"
    }
    ```

### Fetch JSON Data

- **Endpoint:** `/app/json`
- **Method:** `GET`
- **Headers:**
  - `authentication` (required): The JWT token obtained from the `/generate-token` endpoint.

- **Example Request:**

    ```sh
    curl -H "authentication: <your-jwt-token>" "app-demo-node-bkapemhuecbhhcbe.eastus-01.azurewebsites.net/app/json"
    ```

- **Example Response:**

    ```json
    [
      {
        "userId": 1,
        "id": 1,
        "title": "delectus aut autem",
        "completed": false
      },
      ...
    ]
    ```

## Environment Variables

- `SECRET_KEY`: The secret key used for signing JWT tokens.
- `PORT`: The port on which the server will listen.
- `RATE_LIMIT_WINDOW_MS`: The time window in milliseconds for rate limiting.
- `RATE_LIMIT_MAX`: The maximum number of requests allowed per IP within the rate limit window.
- `CACHE_TTL`: The time-to-live for the cache in seconds.

## License

This project is licensed under the ISC License.
