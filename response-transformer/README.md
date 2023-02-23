# Transformer

Transform Response coming from backend in a response service

## Service

- `backend`: This service runs your backend application and exposes port 8080 to accept requests.

- `api-gateway`: This service runs an API Gateway and listens on port 80 to accept requests from the clients. It depends on the backend service to route the requests to the backend application.

- `response-transform`: This service runs the response transformation microservice and listens on port 8081. It depends on the api-gateway service to route requests to the Flask application.

- `flask-app`: This service runs the Flask application that performs the response transformation. It builds the Flask application from the current directory and listens on port 5000. It depends on the response-transform service to transform the response from the backend service.

## Nginx Variable

1. `$request_uri`

    $request_uri is an NGINX variable that contains the original request URI (Uniform Resource Identifier) as received from the client, including any query parameters.

    For example, if a client makes a request to <http://example.com/path/to/resource?foo=bar>, the value of $request_uri will be /path/to/resource?foo=bar.
