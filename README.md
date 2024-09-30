# Social Network API

## Description

This project is a NoSQL-based API for a social network web application that allows users to share their thoughts, react to friends' thoughts, and create a friend list. It is built using MongoDB for data storage, Express.js for routing, and Mongoose as the ODM (Object Data Modeling) library.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Models](#models)
- [Walkthrough Video](#walkthrough-video)
- [License](#license)

## Installation

1. Make sure you have MongoDB installed on your machine. Follow the [MongoDB installation guide](https://coding-boot-camp.github.io/full-stack/mongodb/how-to-install-mongodb) if you haven't installed it yet.
2. Clone the repository:
    ```bash
    git clone <REPOSITORY_URL>
    ```
3. Navigate to the project directory:
    ```bash
    cd social-network-api
    ```
4. Install the required dependencies:
    ```bash
    npm install
    ```
5. Start the server:
    ```bash
    npm start
    ```

## Usage

- The API allows users to manage thoughts, reactions, and a friend list. You can test the endpoints using [Insomnia](https://insomnia.rest/download) or any other API testing tool.
- No seed data is provided, so you can create your own data using POST requests.

## API Endpoints

### Users

- `GET /api/users` - Get all users
- `GET /api/users/:userId` - Get a single user by ID
- `POST /api/users` - Create a new user
- `PUT /api/users/:userId` - Update a user by ID
- `DELETE /api/users/:userId` - Delete a user by ID
- `POST /api/users/:userId/friends/:friendId` - Add a friend to a user's friend list
- `DELETE /api/users/:userId/friends/:friendId` - Remove a friend from a user's friend list

### Thoughts

- `GET /api/thoughts` - Get all thoughts
- `GET /api/thoughts/:thoughtId` - Get a single thought by ID
- `POST /api/thoughts` - Create a new thought
- `PUT /api/thoughts/:thoughtId` - Update a thought by ID
- `DELETE /api/thoughts/:thoughtId` - Delete a thought by ID

### Reactions

- `POST /api/thoughts/:thoughtId/reactions` - Add a reaction to a thought
- `DELETE /api/thoughts/:thoughtId/reactions/:reactionId` - Remove a reaction by ID

## Models

### User

The User model has the following fields:

- `username` (String, required, unique, trimmed)
- `email` (String, required, unique, valid email format)
- `thoughts` (Array of Thought IDs)
- `friends` (Array of User IDs)

Virtual: `friendCount` - Retrieves the total number of friends for a user.

### Thought

The Thought model has the following fields:

- `thoughtText` (String, required, 1-280 characters)
- `createdAt` (Date, default current timestamp)
- `username` (String, required, creator of the thought)
- `reactions` (Array of Reaction documents)

Virtual: `reactionCount` - Retrieves the total number of reactions for a thought.

### Reaction (Subdocument Schema)

- `reactionId` (ObjectId, default to a new ObjectId)
- `reactionBody` (String, required, max 280 characters)
- `username` (String, required)
- `createdAt` (Date, default current timestamp)

## Walkthrough Video

A walkthrough video demonstrating the functionality of the application can be found at the link below:
[Walkthrough Video](<YOUR_VIDEO_LINK>)

## License

This project is licensed under the MIT License.
