# Capstone (Casting agency)

Udacity Full Stack Nanodegree capstone (Casting Agency)

## Motivation

This is a graduation project is for Udacity Full Stack web development nanondegree.

It is the fruit of the whole course using all capabilities learned.

## Getting Started

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### PIP Dependencies

Run this command to install all the required packages

```bash
pip install -r requirements.txt
```


After installing the dependencies run the following command

```bash
source setup.sh
```

##### Key Dependencies

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server.

- [jose](https://python-jose.readthedocs.io/en/latest/) JavaScript Object Signing and Encryption for JWTs. Useful for encoding, decoding, and verifying JWTS.


## API Documentation

This section will introduce you to API endpoints and error handling


### Error handling

Errors are returned in JSON format:

```json
{
  "success": False,
  "error": 404,
  "message": "resource not found"
}
```

Returned errors types:

- 400 – bad request
- 404 – resource not found
- 422 – unprocessable
- 500 - internal server error

### API Endpoints

#### GET /movies

- General:
  - Returns all the movies data.
  - Authorized for : Executive Producer,Casting Assistant,Casting Director.

- Sample response:

```json
{
    "movies": [
        {
            "id": 1,
            "release_date": "Tue, 01 April 1956 00:00:00 GMT",
            "title": "Cukur"
        },
        {
            "id": 2,
            "release_date": "Mon, 01 May 2089 00:00:00 GMT",
            "title": "EDHO"
        }
    ],
    "success": true
}
```

#### GET /movies/\<int:id\>

- General:
  - Return one movie based on id.
  - Authorized for : Executive Producer,Casting Assistant,Casting Director.

- Sample response:

```json
{
    "movie": {
        "id": 1,
        "release_date": "Tue, 01 April 1956 00:00:00 GMT",
        "title": "Cukur"
    },
    "success": true
}
```

#### POST /movies

- General:
  - Create a new movie based .
  - Authorized for : Executive Producer.

- Sample response:
}'`

```json
{
    "movie": {
        "id": 3,
        "release_date": "Sun, 02 July 2020 00:00:00 GMT",
        "title": "Blacklist"
    },
    "success": true
}
```

#### PATCH /movies/\<int:id\>

- General:
  - Update a movie found by id .
  - Authorized for : Executive Producer,Casting Director.

- Sample response:

```json
{
    "movie": {
        "id": 3,
        "release_date": "Sun, 02 May 2045 00:00:00 GMT",
        "title": "Blacklist 2"
    },
    "success": true
}
```


#### DELETE /movies/<int:id\>


- General:
  - Delete a movies by found by passed id.
  - Authorized for: Executive Producer.

- Sample response:

```json
{
    "success": true,
    "message": "Movie was deleted successfully"
}
```

#### GET /actors

- General:
  - Returns all the actors data.
  - Authorized for: Casting Assistant,Casting Director,Executive Producer.

- Sample response:

```json
{
    "actors": [
        {
            "id": 1,
            "name": "Aras bulut",
            "age": 35,
            "gender": "M"
            
        },
        {
            "id": 2,
            "name": "Fatima weshay",
            "age": 50,
            "gender": "F"
            
        }
    ],
    "success": true
}
```

#### GET /actors/\<int:id\>

- General:
  - Returns an actor based on passed id.
  - Authorized for : Executive Producer,Casting Assistant,Casting Director.

- Sample response:

```json
{
    "actor": {
            "id": 1,
            "name": "Aras bulut",
            "age": 35,
            "gender": "M"
    },
    "success": true
}
```

#### POST /actors

- General:
  - Create an actor.
  - Authorized for : Executive Producer,Casting Director.

- Sample response:

```json
{
    "actor": {
            "id": 4,
            "name": "Oktay",
            "age": 55,
            "gender": "M"
    },
    "success": true
}
```

#### PATCH /actors/\<int:id\>

- General:
  - Update an actor using passed id.
  - Authorized for : Executive Producer,Casting Director.

- Sample response:

```json
{
    "actor": {
            "id": 4,
            "name": "Oktay kaynarca",
            "age": 58,
            "gender": "M"
    },
    "success": true
}
```


#### DELETE /actors/<int:id\>


- General:
  - Delete an actor using passed id.
  - Authorized for :Executive Producer,Casting Director.

- Sample response:

```json
{
    "message": "actor was deleted successfully",
    "success": true
}
```

## Authentication 

For authentication we used Auth0 (a third party authentication app), it enable ust to assign roles and permissions to users.

### App roles with their permissions :



1. Casting Assistant:

- GET /actors (get:actors): can get all actors
- GET /movies (get:movies): can get all movies

2. Casting Director:
- GET /actors (get:actors): can get all actors
- GET /movies (get:movies): can get all movies
- POST /actors (create:actors): can create new actors
- PATCH /actors (update:actors): can update existing actors
- PATCH /movies (update:movies): can update existing movies
- DELETE /actors (delete:actors): can delete actors from database

3. Exectutive Director:
- GET /actors (get:actors): can get all actors
- GET /movies (get:movies): can get all movies
- POST /actors (create:actors): can create new actors
- POST /movies (create:movies): Can create new movies
- PATCH /actors (update:actors): can update existing actors
- PATCH /movies (update:movies): can update existing movies
- DELETE /actors (delete:actors): can delete actors from database
- DELETE /movies (delete:movies): Can delete movies from database

## Authors
- Ayoub RHOUTTAISS
- Thanks to Udacity for providing the instructions
