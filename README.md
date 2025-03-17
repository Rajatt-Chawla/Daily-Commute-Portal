# Daily-Commute-Portal
The objective of this is to develop a web portal that helps users manage their daily commute by providing real-time location services, route optimization, and commute history tracking using the MERN stack and Google Maps API (or alternative mapping services).
Project Setup Instructions
Follow these steps to set up the Daily Commute Portal locally on your machine:

Clone the Repository

bash
git clone https://github.com/Rajatt-Chawla/daily_commute_portal.git
cd daily_commute_portal
Install Dependencies

Backend (Node.js, Python, Java, etc. – depending on your tech stack)
bas
# Example for Node.js:
cd backend
npm install
Frontend (React, Angular, Vue, etc. – as required)
bash
# Example for React:
cd ../frontend
npm install
Set Environment Variables

Create a file like .env (or .env.local) in both frontend and backend (if required) to store any secret keys or environment-specific variables.
Example:
env

REACT_APP_API_URL=http://localhost:5000/api
DB_CONNECTION_STRING=your_database_connection_string
Database Setup

If you’re using a specific database (e.g., MongoDB, MySQL, PostgreSQL), ensure you have it installed and running.
Update config files (e.g., db.js, config.js) with your correct connection strings.
Run the Application

Backend:
bash
npm run start
or
bash
npm run dev
(depending on how your scripts are set up)
Frontend:
bash
npm start
The frontend should now be accessible in your browser at something like http://localhost:3000 (depending on your settings).
Build for Production (Optional)

For the frontend, you might run:
bash
npm run build
Serve the build directory through your chosen server or cloud hosting.
API Endpoints and Functionalities
Below is a quick overview of key API endpoints. (Adjust based on your actual routes and controllers.)

User Authentication

POST /api/auth/register
Description: Creates a new user account.
Request Body: { username, email, password }
Response: Success or error message.
POST /api/auth/login
Description: Authenticates user.
Request Body: { email, password }
Response: Auth token or error.
Commute Scheduling

GET /api/commutes
Description: Retrieves a list of available commutes/routes.
Query Params: Optional filters (e.g., origin, destination).
Response: List of commute objects.
POST /api/commutes
Description: Creates a new commute listing (e.g., a carpool schedule).
Request Body: Commute details (e.g., { origin, destination, time, seatsAvailable }).
Response: Newly created commute object or error message.
Booking / Joining Commutes

POST /api/bookings
Description: Book a seat in a listed commute.
Request Body: { commuteId, userId }.
Response: Booking confirmation or error.
Payment or Expense Tracking

GET /api/expenses/:userId
Description: Retrieve all expenses for a specific user.
Response: Array of expense objects.
POST /api/expenses
Description: Add a new expense record (e.g., fuel cost).
Request Body: { amount, description, date }.
Response: Updated list of expenses or success message.
Note: Make sure to secure your routes with appropriate authentication and authorization as needed.

Challenges Faced and Solutions Applied
Large File / Media Handling

Challenge: Needed to store or serve large media files (like a background image) which exceeded GitHub’s size limit.
Solution: Used Git LFS for large files or compressed the file size to stay within limits. Alternatively, used external storage (CDN / cloud storage).
Database Integration

Challenge: Ensuring real-time or fast data retrieval for route listings.
Solution: Indexed frequently queried fields (e.g., origin, destination) in the database and implemented caching where necessary.
Authentication & Security

Challenge: Protecting endpoints from unauthorized access.
Solution: Implemented JWT-based authentication (or session-based) and middleware checks for role-based access control if needed.
Handling Concurrent Bookings

Challenge: Avoiding seat overbooking when multiple users simultaneously try to book.
Solution: Implemented transaction-based approach or used database-level locks/optimistic concurrency checks to ensure seat count updates were atomic.
Performance Optimization

Challenge: Large data sets or multiple concurrent users slowing down the app.
Solution: Added server-side pagination, used efficient queries, and introduced caching (e.g., Redis) for frequently accessed data.
