# Practical 3: Microservices & Serverless Applications

This project demonstrates a microservices architecture using Go, gRPC, and Docker Compose. It includes an API Gateway and two core services: Products Service and Users Service. The system is containerized for easy deployment and scalability.

### Project Structure

```
├── api-gateway/           # API Gateway service
│   ├── Dockerfile
│   └── main.go
├── services/
│   ├── products-service/  # Products microservice
│   │   ├── Dockerfile
│   │   └── main.go
│   └── users-service/     # Users microservice
│       ├── Dockerfile
│       └── main.go
├── proto/                 # Protobuf definitions and generated code
│   ├── products.proto
│   ├── users.proto
│   └── gen/
│       └── proto/
│           ├── products_grpc.pb.go
│           ├── products.pb.go
│           ├── users_grpc.pb.go
│           └── users.pb.go
├── docker-compose.yml     # Docker Compose configuration
├── go.mod                 # Go module file
├── go.sum                 # Go dependencies checksum
└── practical3_images/     # Screenshots for running and testing
```

### How to Run

1. **Clone the repository:**
   ```sh
   git clone <repo-url>
   cd <repo-directory>
   ```
2. **Start all services using Docker Compose:**
   ```sh
   docker-compose up --build
   ```
3. **Access the API Gateway:**
   The API Gateway will be available at `http://localhost:8080` (or the port specified in your `docker-compose.yml`).

### Services Overview

- **API Gateway:** Handles incoming HTTP requests and routes them to the appropriate microservice via gRPC.
- **Products Service:** Manages product-related operations.
- **Users Service:** Manages user-related operations.

## Protobuf Definitions

Protobuf files are located in the `proto/` directory. Generated Go files are in `proto/gen/proto/`.

### Testing & Usage

You can test the endpoints using `curl`, Postman, or any HTTP client. Example:

```sh
curl http://localhost:8080/api/purchases/user/38/product/1
```

### Screenshots

Below are screenshots demonstrating the running and testing of the system:

1. Build and Start the Containers

![alt text](<practical3_images/Screenshot 2025-09-08 at 10.24.16 AM.png>)

2. Verify with Consul
- users-service and products-service registered and healthy.

![alt text](<practical3_images/Screenshot 2025-09-08 at 10.16.12 AM.png>)

3. Test the API Gateway

- Create a new user:

![alt text](<practical3_images/Screenshot 2025-09-08 at 10.40.50 AM.png>)

- Retrieve the user: 

![alt text](<practical3_images/Screenshot 2025-09-08 at 10.43.33 AM.png>)

4. Create a new product

![alt text](<practical3_images/Screenshot 2025-09-08 at 10.58.27 AM.png>)

5. Retrieve the product

![alt text](<practical3_images/Screenshot 2025-09-08 at 10.59.02 AM.png>)


6. Retrieve the combined purchase data

![alt text](<practical3_images/Screenshot 2025-09-08 at 10.59.27 AM.png>)

### Link to the actual repository 
https://github.com/Kinleyjigs/AS2025_WEB303_02230313_Practical3.git 
