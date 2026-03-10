# Mini Snippet Vault - Backend

This is the server-side (backend) for the Mini Snippet Vault application, providing an API for managing code snippets (notes).

## Tech Stack
- **Node.js & Express**: Web framework for building the REST API.
- **MongoDB**: NoSQL database for storing user data and notes.
- **Celebrate**: Middleware for validating incoming request payloads.
- **Cors**: Cross-Origin Resource Sharing.
- **Dotenv**: Centralized loading of environment variables.

## Environment Variables
Create a `.env` file in the root of the project. You can copy the structure from the `.env.example` file:
```env
PORT=
BASE_URL=http://localhost:PORT
MONGO_URL=
```

## Running Locally
1. Ensure your MongoDB instance is running locally or you have a valid cloud cluster URL configured in your `MONGO_URL`.
2. Install the necessary project dependencies (run from the root directory):
   ```bash
   npm install
   ```
3. Start the backend server:
   ```bash
   # Make sure you navigate to the backend folder or run it correctly from the root
   node backend/src/server.js
   ```

## API Endpoints (Testing the API)
The base URL for local development runs on `http://localhost:PORT` (or your configured `PORT`). All note endpoints are prefixed with `/notes`.

Brief examples of how to consume the endpoints:

- **`GET /notes`**: Fetch a paginated list of notes.
  - **Query Params**: `page` (default 1), `perPage` (default 10), `tag`, `search` (for text searching).
  - **Example**: `curl http://localhost:PORT/notes?page=1&perPage=5&tag=react`
- **`GET /notes/:noteId`**: Fetch a specific note by ID.
- **`POST /notes`**: Create a new note.
  - **Body Example**: 
    ```json
    {
      "title": "string",
      "content": "string",
      "tag": "string"
    }
    ```
- **`PATCH /notes/:noteId`**: Update an existing note by ID.
- **`DELETE /notes/:noteId`**: Delete a note by its ID.

## Build and Run in Production
Since this is a standard Node.js API, there is no separate "build" step required like there is for frontend code. To run it in production:
1. Ensure environment variables are fully configured (e.g., `NODE_ENV=production`, real `MONGO_URL`).
2. Use a robust process manager like PM2 to keep the app running continuously:
   ```bash
   npm install -g pm2
   pm2 start backend/src/server.js --name "snippet-vault-api"
   ```
  
