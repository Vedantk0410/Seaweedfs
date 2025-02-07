
## SeaweedFS set up Using docker-compose





## Project Overview

1) Master Server: Manages metadata and coordinates volume servers.

2) Volume Server: Stores data chunks.

3) Filer Server: Provides a file interface to the storage system.

## 1. Define Docker Services

Master Server:

1)Use the SeaweedFS Docker image. 

2)Expose ports 9333 and 19333.

3)Command: master -ip=master.

Use a volume for data persistence.

Volume Server:

1)Use the SeaweedFS Docker image.

2)Expose ports 8080 and 18080.

3)Command: volume -mserver="master:9333" -port=8080 -ip=volume.

4)Use a volume for data persistence.

5)Depends on the master server.

Filer Server:

1)Use the SeaweedFS Docker image.

2)Expose port 8888.

3)Command: filer -master="master:9333".

4)Use a volume for data persistence.

5)Depends on the master and volume servers.

## 2. Create Docker Compose Configuration

Define services for master, volume, and filer.

Specify volumes for data persistence.

Create a custom network for communication.
## 3. Build and Run the Application

docker-compose up --build

## 4. Accessing the Services

The master server will be accessible at http://localhost:9334 and http://localhost:19334.

The volume server will be accessible at http://localhost:8081 and http://localhost:18081.

The filer server will be accessible at http://localhost:8889.
