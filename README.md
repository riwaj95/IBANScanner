# **Approach, Design and steps to solve the challenge:**


This project extends a malware scanning service with Kafka integration for processing PDF documents. The application consumes messages from a Kafka topic, performs IBAN blacklisting checks on PDF documents, and then produces results to another Kafka topic. It includes a RESTful endpoint for uploading PDF files.

**Components**

Kafka Producer: Sends CheckEvent messages containing PDF file URLs to a Kafka topic.

Kafka Consumer: Listens to the Kafka topic, processes incoming PDFs for blacklisted IBANs, and sends results as CheckResultEvent messages to another topic.

**Services**

ContentExtractorControl: Extracts text content from PDF files using Apache PDFBox.

MalwareScannerController: REST controller for handling file uploads and initiating Kafka messages.

**Models**

CheckEvent: Represents an event with the URL and type of the file to check.

CheckResultEvent: Contains the result of the malware check, including a status (OK, SUSPICIOUS, ERROR, IGNORED).

**Exception Handling**

PdfProcessingException: User defined exception for handling errors during PDF processing.

**Setup and Configuration**

Dependencies: Ensure the following dependencies are included:
Spring Kafka
Apache PDFBox (for PDF processing)
Spring Boot Web (for RESTful services)

application.properties: Configure Kafka producer and consumer properties, server settings, and any other necessary configurations.

**Usage**

Start the Spring Boot application.
Upload PDF files using the REST endpoint /api/scan/upload. The files are processed, and their check results are sent to the configured Kafka topic.

To extract the url, we first saved the file locally and extract the url.

**Further improvements in the code**

1. Logging
2. More user defined exception handling
3. Defining DTO
4. More secure async communication
5. More unit and integration test

**I have also developed unit and integration test for all the features and service.I completed this challenge honestly in 3 days. I have not tested the application in postman because
I have problem running zookeeper and kafka services in my windows 11 laptop which i rented from Grover since my original
laptop is in repair. I would have certainly tested in postman and improved if i had my laptop so sorry if in postman it gives error.I hope the application gives the expected result when tested in postman.I had a great time doing this challenge.Thank you**