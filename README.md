# URL Shortener

This repository contains a URL shortener system using **AWS Lambda**, **S3**, **Amazon API Gateway**, and **Java**. The project is divided into two Lambda functions:

## CreateUrlLambda

- **Description**: Creates a short URL based on an original URL provided by the user and an expiration date.
  
- **Functionality**:
  - Receives an HTTP request via Amazon API Gateway containing the original URL and expiration time.
  - Generates a unique code (UUID) for the short URL.
  - Stores the data in Amazon S3 as a JSON file.

- **Libraries Used**:
  - `aws-lambda-java-core`
  - `aws-lambda-java-log4j2`
  - `software.amazon.awssdk:s3`
  - `jackson-databind` for JSON manipulation.

## RedirectUrlShortener

- **Description**: Redirects the short URL to the original destination, checking its validity based on the expiration date.
  
- **Functionality**:
  - Receives an HTTP request via Amazon API Gateway containing the short URL code as part of the route.
  - Retrieves the corresponding data from Amazon S3.
  - Redirects the user to the original URL or returns an error message if the URL has expired.

- **Libraries Used**:
  - `aws-lambda-java-core`
  - `aws-lambda-java-log4j2`
  - `software.amazon.awssdk:s3`
  - `jackson-databind` for JSON manipulation.

## Environment Setup

### Prerequisites
- AWS CLI configured to manage S3 and Lambda resources.
- S3 bucket.
- Java 17 and Maven installed.
- Amazon API Gateway configured to:
  - Create endpoints for the `CreateUrlLambda` and `RedirectUrlShortener` Lambda functions.

### Technologies Used

- AWS Lambda: To run serverless functions.
- Amazon API Gateway: To manage and expose the endpoints of the functions.
- AWS S3: For storing URL data.
- Java 17: The main programming language of the project.
- Maven: Dependency and build management tool.
