---
title: MongoDB Seeded DB
layout: default
parent: Docker
grand_parent: Training Environments
nav_order: 2
---

# MongoDB Seeded DB

The aim of this container is to provide access to a NoSQL DB with datasets to build against, practice, and test. Whether you're learning about NoSQL document queries (docs can be found [here](https://www.mongodb.com/docs/manual/tutorial/query-documents/)) or building APIs, you will be able to practice against a viable dataset.

## MongoDB Seeded Database

This image has been set up to provide various data collections to allow you to access and practice against a seeded, local MongoDB instance. The container can be found on [Docker Hub](https://hub.docker.com/repository/docker/kcornwall/mongodbtestdata/general).

### Contents

* [Running the DB](#running-the-db)
* [Connecting to the DB](#connecting-to-the-db)
* [MongoDB Filter Queries](#mongodb-filter-queries)
* [Available Collections](#available-collections)
  * [IMDB Data Structure](#imdb-data-structure)
  * [Quiz Data Structure](#quiz-data-structure)
  * [User Data Structure](#user-data-structure)
  * [Student Details Data Structure](#student-details-data-structure)

### Running the DB

Assuming you have Docker installed, use the following snippet to get the container up and running locally:

```shell
docker run -d --name <name_your_container> -p 27017:27017 kcornwall/mongodbtestdata
```

#### Docker Compose

A simpler way to set up the DB and have mongo-express (a web-based client to interact with the data) is to use `docker-compose`.

##### Installing Docker Compose

Check out the documentation for Docker Compose installation [here](https://docs.docker.com/compose/install/).

##### Running Docker Compose

Copy the `docker-compose.yml` file or simply clone this project, ensure you're in the root folder, and run:

```shell
docker-compose up -d
```

Using the `-d` flag will bring the container up in detached mode. This will create your container and set up mongo-express, allowing you to review the data by visiting `localhost:8081` in any browser.

### Connecting to the DB

The DB credentials are as follows:

- Username: root
- Password: password

Whether using code or an app like MongoDB Compass, connect to the DB using the following connection string:

```shell
mongodb://root:password@localhost:27017
```

### MongoDB Filter Queries

For learning about filter queries, refer to the documentation at [docs.mongodb.com](https://docs.mongodb.com/compass/current/query/filter/).

### Available Collections

Currently, there are four different databases containing collections:

* **imdb**: Movie data
* **quiz**: Random quiz questions
* **random_user_details**: Generic randomly generated user details
* **students**: Randomly generated student data

For both the `student_data` and `user_details`, the data has been randomly generated. The `imdb` and `quiz` data have been taken from public sources.

#### IMDB Data Structure

```json
{
  "title": "Avatar",
  "score": 7.9,
  "year": "2009",
  "duration": 178,
  "rating": "PG-13",
  "budget": 237000000,
  "genres": [
    "Action",
    "Adventure",
    "Fantasy",
    "Sci-Fi"
  ],
  "gross": 760505847,
  "director": "James Cameron",
  "actors": [
    "CCH Pounder",
    "Joel David Moore",
    "Wes Studi"
  ],
  "language": "English",
  "country": "USA"
}
```

#### Quiz Data Structure

**IMPORTANT NOTE:** There are many areas within the data with Unicode in place of certain characters. These are in place on purpose to practice data transformation.

```json
{
  "category": "Entertainment: Video Games",
  "type": "multiple",
  "difficulty": "easy",
  "question": "What is the name of 'Team Fortress 2' update, in which it became Free-to-play?",
  "correct_answer": "Über Update",
  "incorrect_answers": [
    "Pyromania Update",
    "Mann-Conomy Update",
    "Engineer Update"
  ]
}
```

#### User Data Structure

```json
{
  "id": 1,
  "first_name": "Flory",
  "last_name": "Boffey",
  "email": "fboffey0@pen.io",
  "company_name": "Lind Inc",
  "company_city": "Askiz",
  "job_title": "Information Systems Manager",
  "linkedIn_skill": "Access Control"
}
```

#### Student Details Data Structure

```json
{
  "first_name": "Kara",
  "last_name": "Darcey",
  "gender": "Gender Fluid",
  "email": "kara.darcey-71355@hotmail.com",
  "phone_number": "+447774443947",
  "current_status": "In Post Graduate Study",
  "university": "Aberystwyth University",
  "graduation_year": "2020",
  "degree": "Business and Tourism Management with Foundation Year London",
  "visa": "No"
}
```
