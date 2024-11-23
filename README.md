# bdipluse_task
README.txt
Project Overview
This project is a User Registration and Authentication System built with the following technologies:

Frontend: ReactJS with Material UI for building the user interface.
Backend: Flask REST API for handling user authentication and management.
Database: PostgreSQL for data storage.
Authentication: JWT (JSON Web Tokens) for secure access and token-based authentication.
The project allows users to register, log in, and access secured resources based on their JWT tokens.

Technologies and Libraries Used
Frontend:
ReactJS: JavaScript library for building user interfaces.
Material UI: React components library for building UI with pre-built styles.
React Router: For managing client-side routing.
Axios: For making API requests from the frontend to the Flask backend.
Backend:
Flask: Micro web framework for building the RESTful API.
Flask-JWT-Extended: For handling JWT-based authentication.
Flask-SQLAlchemy: For ORM-based interaction with PostgreSQL.
Flask-Cors: For handling Cross-Origin Resource Sharing (CORS) between the frontend and backend.
PostgreSQL: Relational database for storing user data.
How to Run the Project Locally
1. Clone the Repository
bash
Copy code
git clone <repository-url>
cd <project-folder>
2. Setup Backend (Flask API)
Install Dependencies
Make sure you have pip and virtualenv installed.

Create a virtual environment:

bash
Copy code
python -m venv venv
Activate the virtual environment:

Windows:
bash
Copy code
venv\Scripts\activate
Mac/Linux:
bash
Copy code
source venv/bin/activate
Install required packages:

bash
Copy code
pip install -r requirements.txt
Setup PostgreSQL Database
Create a PostgreSQL database and user:

sql
Copy code
CREATE DATABASE user_management;
CREATE USER your_username WITH PASSWORD 'your_password';
ALTER ROLE your_username SET client_encoding TO 'utf8';
ALTER ROLE your_username SET default_transaction_isolation TO 'read committed';
ALTER ROLE your_username SET timezone TO 'UTC';
GRANT ALL PRIVILEGES ON DATABASE user_management TO your_username;
Update the database connection string in the config.py or .env file:

python
Copy code
SQLALCHEMY_DATABASE_URI = 'postgresql://your_username:your_password@localhost/user_management'
Initialize the database:

bash
Copy code
python manage.py db upgrade
Start Flask Backend
To run the Flask backend API:

bash
Copy code
flask run
By default, the backend will be available at http://127.0.0.1:5000.

3. Setup Frontend (ReactJS)
Install Dependencies
Navigate to the frontend directory:

bash
Copy code
cd frontend
Install dependencies using npm or yarn:

bash
Copy code
npm install
Configure API Base URL
In the frontend project, configure the Axios instance to use the correct API base URL. Open src/Utils/axiosInstance.js and update the base URL:

javascript
Copy code
const axiosInstance = axios.create({
  baseURL: 'http://127.0.0.1:5000',  // Flask backend URL
});

export default axiosInstance;
Start React Development Server
To run the React app:

bash
Copy code
npm start
The frontend will be available at http://localhost:3000.

Testing the APIs
API Endpoints
POST /register: User registration endpoint.

Request Body:
json
Copy code
{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "password": "password123",
  "confirmPassword": "password123"
}
Response: 201 Created (Success) or error message (e.g., 400 Bad Request for invalid input).
POST /login: User login endpoint to receive a JWT token.

Request Body:
json
Copy code
{
  "email": "john.doe@example.com",
  "password": "password123"
}
Response: 200 OK with the JWT token if successful.
json
Copy code
{
  "access_token": "<jwt-token>"
}
GET /profile: Protected route to retrieve user profile information. Requires JWT token in the Authorization header.

Headers:
makefile
Copy code
Authorization: Bearer <jwt-token>
Response: 200 OK with user data.
UI Screenshots
Here are some screenshots of the user interface:

Registration Screen:

Login Screen:

User Profile Screen:

Additional Notes
Ensure that the Flask API is running before starting the React frontend.
The JWT token from the login response should be stored securely (e.g., in localStorage or sessionStorage) for authentication on protected routes.
Ensure the PostgreSQL server is running and the database is properly set up as mentioned above.
License
This project is licensed under the MIT License - see the LICENSE file for details.

Customizing for Your Own Setup
Feel free to adjust the backend URLs, database credentials, or other configurations based on your environment.



If you have any questions or need further assistance, feel free to reach out to the project maintainers.
