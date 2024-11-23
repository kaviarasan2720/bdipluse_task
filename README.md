# bdipluse_task
A brief description of what this project does and who it's for


# User Registration and Authentication System

## Project Overview

This project is a **User Registration and Authentication System** built with the following technologies:

- **Frontend**: ReactJS with Material UI for building the user interface.
- **Backend**: Flask REST API for handling user authentication and management.
- **Database**: PostgreSQL for data storage.
- **Authentication**: JWT (JSON Web Tokens) for secure access and token-based authentication.

The project allows users to register, log in, and access secured resources based on their JWT tokens.

---

## Technologies and Libraries Used

### Frontend:
- **ReactJS**: JavaScript library for building user interfaces.
- **Material UI**: React components library for building UI with pre-built styles.
- **React Router**: For managing client-side routing.
- **Axios**: For making API requests from the frontend to the Flask backend.

---

### Backend:
- **Flask**: Micro web framework for building the RESTful API.
- **Flask-JWT-Extended**: For handling JWT-based authentication.
- **Flask-SQLAlchemy**: For ORM-based interaction with PostgreSQL.
- **Flask-Cors**: For handling Cross-Origin Resource Sharing (CORS) between the frontend and backend.
- **PostgreSQL**: Relational database for storing user data.

---

## How to Run the Project Locally

### 1. Clone the Repository

```bash
git clone <repository-url>
```
### 2. Setup Backend (Flask API)
Install Dependencies
Make sure you have pip and virtualenv installed.

### 3.Create a virtual environment:

```bash
python -m venv venv
```
### 4.Activate the virtual environment:

**Windows:**
```bash
venv\Scripts\activate
```
### 5.Install required packages:
```bash
pip install -r requirements.txt
```
### 6.Setup PostgreSQL Database:
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,               -- Unique identifier for each user
    name VARCHAR(100) NOT NULL,          -- User's name
    email VARCHAR(100) UNIQUE NOT NULL,  -- User's email (must be unique)
    password_hash TEXT NOT NULL,         -- Hashed password for security
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP, -- Timestamp of when the user was created
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP  -- Timestamp of the last update
);
```
```SQLALCHEMY_DATABASE_URI = 'postgresql://your_username:your_password@localhost/user_management'```
#### Run Comment:
`python app.py `
By default, the backend will be available at `http://127.0.0.1:5000.`
### 7.Access Swagger documentation:
    - Open your browser and navigate to http://127.0.0.1:5000/swagger.
  ---
## Swagger Integration Steps
### 1.Swagger Setup in Code:
    - Swagger is integrated using the flask-swagger-ui package.
    - The Swagger JSON file is located at static/swagger.json
### 2.Access the Swagger UI:
    - Visit the Swagger UI at /swagger (e.g., http://127.0.0.1:5000/swagger).
### 3.Testing Endpoints:
    - Each API endpoint is documented with details about parameters, responses, and request bodies.
    - You can test API requests directly from the Swagger UI.
---
## Endpoints Overview
### User Management:
| Method | Endpoint  | Description|Authentication Required|
| ------- | ---------| ---------- |--------|
| **POST** | `/api/register`| Register a new user | No |
| **POST** |`/api/login` |Log in a user|No|
| **GET** |  `/api/users` |Retrieve all users|Yes|
| **PUT** | `/api/user/<id>` |Update user information	|Yes|
| **PUT** | `/api/user/<id>` |Delete a user| Yes|

## Running Unit Tests:
To ensure all endpoints work as expected, run the unit tests:
```bash
pytest test_app.py
```
### Swagger UI
Example of the Swagger UI:
![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)




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

Flask==2.3.2
Flask-SQLAlchemy==3.0.2
Flask-JWT-Extended==4.4.4
Flask-Cors==3.1.1
Flask-Swagger-UI==4.1.0
psycopg2-binary==2.9.6  # PostgreSQL adapter for Python
pytest==7.1.0



If you have any questions or need further assistance, feel free to reach out to the project maintainers.
