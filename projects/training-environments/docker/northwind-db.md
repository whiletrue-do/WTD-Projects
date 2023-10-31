---
title: Northwind DB for SQL
layout: default
parent: Docker
grand_parent: Training Environments
nav_order: 1
---

# SQL Northwind Docker Image

## Versions

- `latest`: Represents the most recent update.

This Docker image is an extension of the `microsoft/mssql-server-linux` container. For more details, including important license information, please visit the [official Docker Hub page](https://hub.docker.com/r/microsoft/mssql-server-linux/).

## Overview

This image not only includes the base Microsoft SQL Server on Linux but also comes pre-loaded with the MSSQL command-line tools and the Northwind sample database. This setup is ideal for learning SQL and testing queries in a real-world-like database environment.

## Requirements

### Hardware and Software

- Docker Engine 1.8+ on any supported platform.
- Minimum 2GB of RAM (3.25 GB if using versions prior to 2017-CU2).

**Note**: If you're running Docker on Mac or Windows, make sure to allocate enough memory to the Docker VM.

## How to Use This Image

To run this image, execute the following command in your terminal:

```bash
docker run -d --name <container_name> -p 1433:1433 kcornwall/sqlnorthwind
```

### Access Credentials

- **SA Password**: `Passw0rd2018`

## Supporting Resources

### Azure Data Studio

For a more user-friendly experience, you can download Azure Data Studio, a cross-platform tool for SQL Server, from [here](https://docs.microsoft.com/en-us/sql/sql-operations-studio/download?view=sql-server-2017).

### Logging In

When prompted for login credentials, use the following:

- **Connection Type**: Microsoft SQL Server
- **Server**: `localhost, SA`
- **Authentication Type**: SQL Login
- **Username**: `SA`
- **Password**: `Passw0rd2018`

Click "Connect" to access the database.

## Training Resources

- **W3C Schools**: This platform uses the Northwind database for its SQL tutorials, offering numerous examples to help you learn SQL. Access it [here](https://www.w3schools.com/sql/).