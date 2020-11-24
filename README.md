# ormae
## Architecture for real-time vehicle tracking
This is the system architecture for a service that tracks the real-time location of vehicles, and displays the result to the front end. The design makes the following assumptions:

## Assumptions
* The company providing this service has many clients, who want to use this service to keep track of their fleet of vehicles
* Each client has vehicles that can range between 1 to 1000
* No of clients can be very large
* Keeping in mind the point above, the system needs to be highly scalable
* The company designing this wants to avoid engineering effort for server maintenance, leading to a largely serverless design

## Architecture
Image

## The reasoning behind the design decisions

* Since one of the assumptions we have is we need high scalability without effort towards server maintenance, we are using AWS managed services, with a serverless architecture
* We use msgpack to serialize the data so as to efficiently transfer the data from the mobile to AWS API Gateway
* We use Kinesis to capture and queue the data, and Lambda to deserialize, and insert the data to the DynamoDB. With this, we do not have to worry about scalability or server management till here
* DynaoDB archives the data to S3 for later use
* Sockets to push the data to the frontend

