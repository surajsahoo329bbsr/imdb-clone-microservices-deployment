# imdb-clone-microservices
A scalable microservices platform for managing movies, TV shows, reviews, ratings, recommendations, watchlists, and user engagement.

# IMDb Clone - Spring Boot Microservices API Documentation

## 1. Introduction

### 1.1 Purpose
This document provides a comprehensive guide to the API endpoints of our microservices-based architecture. It details authentication mechanisms, request and response formats, API structures, and error-handling strategies.

### 1.2 Features
- Movie and TV show management
- User reviews and ratings
- Watchlists and favorite lists
- Scalable microservices platform

## 2. Authentication & Security
- Uses JWT-based authentication.
- Role-based access control:
  - **Admin**: Full access to create, modify, and delete resources.
  - **User**: Read access and the ability to post reviews, add a watchlist, and mark favorite movies, TV shows, and persons.
- API security is handled with Spring Security.

## 3. API Endpoints

### 3.1 Movie Module

| HTTP Method | Endpoint             | Description                          | Access Level |
|------------|---------------------|----------------------------------|--------------|
| GET        | /movies             | Retrieve all movies with pagination | Public       |
| GET        | /movies/{id}        | Retrieve a specific movie by ID | Public       |
| POST       | /movies             | Create a new movie               | Admin Only   |
| PUT        | /movies/{id}        | Update an existing movie         | Admin Only   |
| DELETE     | /movies/{id}        | Soft delete a movie              | Admin Only   |

### 3.2 TV Show Module

| HTTP Method | Endpoint             | Description                          | Access Level |
|------------|---------------------|----------------------------------|--------------|
| GET        | /tv-shows           | Retrieve all TV shows with pagination | Public       |
| GET        | /tv-shows/{id}      | Retrieve a specific TV show by ID | Public       |
| POST       | /tv-shows           | Create a new TV show               | Admin Only   |
| PUT        | /tv-shows/{id}      | Update a TV show                   | Admin Only   |
| DELETE     | /tv-shows/{id}      | Soft delete a TV show              | Admin Only   |

### 3.3 User Module

| HTTP Method | Endpoint         | Description                          | Access Level |
|------------|-----------------|----------------------------------|--------------|
| POST       | /users/signup    | Register a new user              | Public       |
| POST       | /users/login     | Authenticate a user and generate JWT | Public       |
| GET        | /users/profile   | Fetch public user profile        | Public       |
| PUT        | /users/profile   | Update user profile              | User Only    |

### 3.4 Reviews & Ratings

| HTTP Method | Endpoint                      | Description                               | Access Level |
|------------|------------------------------|---------------------------------------|--------------|
| POST       | /reviews                     | Submit a review for a movie/TV show   | User Only    |
| GET        | /reviews/movies/{id}         | Retrieve all reviews for a specific movie | Public       |
| GET        | /reviews/tv-shows/{id}       | Retrieve all reviews for a TV show    | Public       |
| GET        | /reviews/{id}                | Retrieve a specific review by ID      | Public       |

### 3.5 Watchlist & Favorites

| HTTP Method | Endpoint                | Description                          | Access Level |
|------------|------------------------|----------------------------------|--------------|
| POST       | /watchlist              | Add a movie or TV show to watchlist | User Only    |
| GET        | /watchlist/users/{id}   | Retrieve user watchlist            | User Only    |
| DELETE     | /watchlist/{id}         | Remove from watchlist               | User Only    |
| POST       | /favorites              | Add a movie/TV show/person to favorites | User Only    |
| GET        | /favorites/users/{id}   | Retrieve user favorites            | User Only    |
| DELETE     | /favorites/{id}         | Remove from favorites               | User Only    |

## 4. Error Handling

| Status Code | Meaning                | Description                                     |
|------------|----------------------|-----------------------------------------|
| 200        | OK                     | Request successfully processed         |
| 400        | Bad Request             | Invalid request parameters             |
| 401        | Unauthorized            | Authentication required                |
| 403        | Forbidden               | Access denied                          |
| 404        | Not Found               | Resource not available                 |
| 500        | Internal Server Error   | Unexpected server error                |

## 5. Conclusion
This document serves as a guideline for backend developers working on the API endpoints. Any future modifications should follow the principles outlined here for consistency and maintainability.


