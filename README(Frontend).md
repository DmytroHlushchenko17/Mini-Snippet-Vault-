# Mini Snippet Vault - Frontend

This is the client-side (frontend) of the Mini Snippet Vault app. It provides a web interface to seamlessly categorize, manage, and view code snippets.

## Tech Stack
- **Next.js (App Router)**: React-based framework utilizing the modern App Router approach.
- **React (v19)**: Library for creating robust user interfaces.
- **TypeScript**: Statically typed JavaScript for enhanced safety.
- **React Query (@tanstack/react-query)**: Efficient caching, data fetching, and server state management.
- **Zustand**: Lightweight manager for global states.
- **Axios**: HTTP client for communication with the backend.
- **React-Hot-Toast**: Beautiful and simple toast notifications.
- **React-Paginate**: Accessible pagination component.

## Environment Variables
The application looks for environment variables to communicate with the backend. Ensure your `.env` file (located in the project root) is properly set up. Example:
```env
# .env.example
PORT=
BASE_URL=http://localhost:PORT
MONGO_URL=
```
*(Note: If Next.js needs to expose these explicitly to the browser, they usually start with `NEXT_PUBLIC_`. Ensure your Axios configs point to the right backend URL).*

## Running Locally
1. Install project dependencies from the root directory:
   ```bash
   npm install
   ```
2. Start the development server (make sure you've also started the backend!):
   ```bash
   npm run dev
   ```
3. Open [http://localhost:PORT](http://localhost:PORT) (or the port your frontend is assigned to) in your browser.

## API Integration (Testing)
The frontend communicates directly with the backend API (`/notes` endpoints). 
To verify that everything connects correctly:
1. Ensure your backend server is running simultaneously.
2. The UI natively triggers `GET` requests (via `react-query`) to load all notes upon visiting the main dashboard.
3. You can test submissions simply by interacting with the forms on the web interface—they trigger `POST`, `PATCH`, and `DELETE` requests depending on the user interaction.

## Build and Run in Production
To prepare the application for a production environment, you need to create an optimized bundle and launch the Next.js production server.
1. Build the production application from the root directory:
   ```bash
   npm run build
   ```
2. Once the build succeeds, start the server in production mode:
   ```bash
   npm run start
   ```
