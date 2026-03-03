# MERN Note App

This is a note-taking full-stack web app developed using the MERN stack.

Redis is incorporated for rate-limiting API requests.

[This tutorial](https://www.youtube.com/watch?v=F9gB5b4jgOI) was followed to develop it.

## Usage

The user starts on the home page where they can view all notes. Each note is a tile
consisting of its title, content and date posted with an edit icon and delete button.

In the top right, there is a **New Note** button which takes you to the note creation page.
On this page there is a form requesting the user to input the note's title and content.
The date of creation is handled automatically by MongoDB. Clicking the **Create Note** button
adds the note to MongoDB so it can be seen the next time the home page is visited.

When clicking on a note tile, the user is taken to a page where they can edit the note's title
and content. They can also delete the note from this page.

## Backend

The backend uses a REST API developed with Express and MongoDB. The endpoint is `/api/notes`.
Performing a GET retrieves all notes while suffixing with an ID retrieves only that note.
Performing a POST with a JSON body consisting of **title** and **content** creates that note
in MongoDB. Performing a PUT with an ID and JSON body updates that note with the new values.
Finally, performing a DELETE with an ID deletes that note.

Rate-limiting is also included in the backend. It uses Redis and blocks the user from making
too many API requests in a given period. That threshold is set at 100 requests per minute.

## Local Setup

### .env

```
MONGO_URI=...
PORT=...
UPSTASH_REDIS_REST_URL=...
UPSTASH_REDIS_REST_TOKEN=...
NODE_ENV=development
```

### Build

Execute `npm install` in both the frontend and backend.

### Start

Execute `npm run dev` in both the frontend and backend and visit the frontend URL.
