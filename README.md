# Breeze Golang Case - Model and Endpoint Overview

## Introduction

This document provides an overview of the models and endpoints in the Breeze Golang Case. It is designed to help you quickly understand the system's structure, allowing you to focus on showcasing your skills in the exercise.

## Models

The system revolves around four primary models:

### 1. User

- **Description**: Represents a user in the system.
- **Fields**:
    - `Email`: The user's email address.
    - `Password`: The user's password (Note: In a real-world scenario, passwords should be stored securely).
    - `Name`: The user's name.

### 2. Possibility

- **Description**: Represents a potential connection between two users, with a score indicating the quality of the match.
- **Fields**:
    - `IdFrom`: UUID of the user from whom the possibility originates.
    - `IdTo`: UUID of the user to whom the possibility is directed.
    - `SuggestionID`: Optional UUID linking to a Suggestion.
    - `Score`: An integer score from 0 to 100, where 100 is the best possible match.

### 3. Suggestion

- **Description**: A more concrete proposal derived from a Possibility, suggesting a potential match between two users.
- **Fields**:
    - `SuggestionSetID`: UUID identifying the pair of Suggestions.
    - `UserID`: UUID of the user to whom the suggestion is made.
    - `Accepted`: Boolean indicating if the user has accepted the suggestion.

### 4. Match

- **Description**: A confirmed connection created when both users in a Suggestion pair agree.
- **Fields**:
    - `SuggestionSetID`: UUID of the connected Suggestion pair.
    - `Paid`: Indicates if the match is a paid connection.
    - `PlannedAt`: Optional timestamp for when the match is planned.
    - `CancelledAt`: Optional timestamp for when the match is cancelled.

## Endpoints

The following endpoint is available for interacting with the system that will reset the database with dummy data:

1. **Generate Database**
    - **Endpoint**: `GET /generate-db`
    - **Functionality**: Initializes the database with default values or structures.
    - 100 users are generated with possibilties between them.
    - User with id '11111111-1111-1111-1111-111111111111' will always be created and will have suggestions preloaded
    - You can use this user to keep testing easily after regenerating the database

## Preparing for the Case

- Familiarize yourself with the models and their relationships.
- Understand the functionality provided by each endpoint.
- Consider how these models interact within the scope of the given user stories.

This overview is meant to streamline your understanding of and allow you to focus on the coding challenges ahead.

### Additional Notes

-   Model Relationships:

    -   A `Possibility` is a potential match between two `User` instances, these are not visible to users.
    -   A `Suggestion` is derived from a `Possibility` and directly involves a `User`, suggestions are visible to users.
    -   A `Match` is the result of two `User` instances mutually accepting a `Suggestion`.
-   Data Flow:

    -   The process starts with identifying `Possibilities` between users.
    -   These `Possibilities` can be converted into `Suggestions`.
    -   If both users involved in a `Suggestion` accept it, a `Match` is created.

## Goal of the case
It is a 2-hour time-capped exercise where you can show off your skills in Golang.
In the README.md of the case you will find a list of different tasks you can tackle, we DON'T expect you to finish all of them.
Decide for yourself which tasks you want to tackle and in which order. 

Conclusion
----------

We hope this document provides a clear understanding of the models and endpoints you will be working with in the Breeze Golang Case. We look forward to seeing your approach to solving the challenges presented in this exercise. Good luck!
