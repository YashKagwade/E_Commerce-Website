E-Commerce Project - React Frontend + Java Backend
A full-stack e-commerce application with React frontend and Java Servlet backend.

🚀 Project Overview
**Frontend: React.js with Context API for state management**

**Backend: Java Servlets with MySQL database**

**Server: Apache Tomcat**

Styling: CSS-in-JS with styled components

**Project Structure**

ecommerce-project/
├── frontend/                 # React application
│   ├── src/
│   │   ├── App.jsx          # Main application component
│   │   ├── ProductList.jsx  # Product display component
│   │   ├── CartPage.jsx     # Shopping cart component
│   │   ├── CheckoutPage.jsx # Checkout form component
│   │   ├── CartContext.js   # Global cart state management
│   │   └── styling.js       # Styled components
│   └── package.json
└── backend/                  # Java servlet application
    ├── src/
    │   └── backend/
    │       ├── ProductServlet.java    # Products API
    │       ├── CorsFilter.java        # CORS configuration
    │       └── DatabaseConnection.java # DB connection pool
    ├── web.xml              # Servlet configuration
    └── lib/                 # Database driver


**-- Create database and table**


CREATE DATABASE ecommerce;
USE ecommerce;

CREATE TABLE products (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    price DECIMAL(10,2) NOT NULL,
    category VARCHAR(100),
    image_url VARCHAR(500),
    stock_quantity INT DEFAULT 0
);

-- Insert sample data
INSERT INTO products (name, description, price, category, image_url, stock_quantity) VALUES
('Laptop', 'High-performance laptop', 999.99, 'Electronics', 'laptop.jpg', 10),
('Smartphone', 'Latest smartphone model', 699.99, 'Electronics', 'phone.jpg', 25),
('Headphones', 'Wireless noise-cancelling', 199.99, 'Electronics', 'headphones.jpg', 15);

**Change these values according to your MySQL setup**

String url = "jdbc:mysql://localhost:3306/ecommerce";
String username = "your_mysql_username";  // Typically 'root'
String password = "your_mysql_password";

__________________**2. Frontend Setup (React)**_______________________________________




Port Configuration:
The React app runs on port 5173 (Vite default). If you need to change this:)
Port Configuration:
The React app runs on port 5173 (Vite default). If you need to change this:

// vite.config.js
export default {
  server: {
    port: 3000, // Change to your preferred port
  }
}

**CORS Headers**
// Ensure these match your frontend URL
httpResponse.setHeader("Access-Control-Allow-Origin", "http://localhost:5173");
httpResponse.setHeader("Access-Control-Allow-Methods", "GET, POST, PUT, DELETE, OPTIONS");
httpResponse.setHeader("Access-Control-Allow-Headers", "Content-Type, Authorization");


**IF  CORS ERRORS OCCURS**

 
Check ports match: Frontend (5173) ↔ Backend (8080)

Update CORS headers in both CorsFilter.java and ProductServlet.java

Alternative solutions:

Use a proxy in development

Disable CORS in browser (development only)

4. Environment Setup Checklist
Prerequisites:
Node.js (v14 or higher)

Java JDK (v8 or higher)

Apache Tomcat (v9 or higher)

MySQL Server

MySQL Connector/J driver

Backend Setup Steps:
Create MySQL database and tables

Update database credentials in DatabaseConnection.java

Build backend as WAR file: backend.war

Deploy to Tomcat webapps directory

Start Tomcat server

Verify backend: http://localhost:8080/backend/api/products

Frontend Setup Steps:
Install dependencies: npm install

Start development server: npm run dev

Verify frontend: http://localhost:5173

5. Common Issues and Solutions
CORS Blocking Requests:
Symptoms: "Access to fetch has been blocked by CORS policy"
Solutions:

Ensure CorsFilter.java is properly deployed

Check that frontend URL matches Access-Control-Allow-Origin header

Restart Tomcat after deploying changes

Database Connection Issues:
Symptoms: "Cannot get database connection" or SQL exceptions
Solutions:

Verify MySQL service is running

Check database credentials in DatabaseConnection.java

Ensure MySQL connector JAR is in WEB-INF/lib/

Port Conflicts:
Symptoms: "Address already in use" or connection refused
Solutions:

Change ports in configuration files

Kill processes using ports 8080 or 5173

Update CORS headers with new ports

6. Development URLs
Frontend: http://localhost:5173

Backend API: http://localhost:8080/backend/api/products

Tomcat Manager: http://localhost:8080/manager

7. Build and Deployment
Production Build:
bash
# Frontend
npm run build

# Backend
# Export as WAR file from your IDE or use Maven
Production Considerations:
Update CORS to allow your production domain

Use environment variables for database credentials

Configure proper database connection pooling

Set up HTTPS in production

🛠 Troubleshooting
Quick Test Steps:
Test backend directly: http://localhost:8080/backend/api/products

Check browser console for CORS errors

Verify Tomcat logs for backend errors

Test database connection separately

Logs Location:
Tomcat logs: tomcat/logs/catalina.out

Browser logs: F12 Developer Tools → Console

This project requires manual configuration of database connections, server ports, and CORS settings after cloning. Follow the steps above carefully to set up the development environment.
