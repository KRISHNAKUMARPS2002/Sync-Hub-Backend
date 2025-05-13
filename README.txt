# Sync Service API

A robust Node.js + Express API service for managing client database synchronization operations and user authentication.

---

## 🚀 Overview

This service provides a centralized API for client applications to synchronize data with the main server database. It includes:

- **User Management** (via Admin Panel Backend API)
- **Secure Data Synchronization**
- **JWT-based Authentication**
- **Comprehensive Logging**

---

## ✅ Features

### Admin Panel Backend API
- **User Management** (Create / Read / Update / Delete)
- **Admin Authentication** with JWT
- **Session Management**

### Synchronization API
- **Secure** data synchronization endpoints
- **Client Authentication** via tokens
- **Transaction Support** for data integrity

### Security
- JWT-based authentication
- HTTP-only cookies
- Rate limiting
- Secure headers with [Helmet](https://github.com/helmetjs/helmet)
- CORS protection

### Logging
- Winston-based logging
- Error tracking
- Operation auditing

---

## 📦 Prerequisites

- **Node.js** v14+
- **PostgreSQL** database
- **npm** or **yarn**

---

## ⚙️ Installation


Install dependencies:
npm install
# or
yarn install

Configure environment variables
Create a .env file in the project root:

env
Copy
Edit
# Server Configuration
PORT=5005
NODE_ENV=development
API_URL=http://localhost:5005
FRONTEND_ORIGIN=http://localhost:5173

# PostgreSQL Configuration
PG_HOST=localhost
PG_PORT=5432
PG_DATABASE=your_database_name
PG_USER=your_database_user
PG_PASSWORD=your_database_password

# Authentication
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRES_IN=10d
COOKIE_NAME=superadmin_token

# Logging
LOG_LEVEL=info
🗄️ Database Initialization
After configuring your PostgreSQL connection, initialize the tables:

bash
Copy
Edit
curl -X GET http://localhost:5005/api/admin/initialize
Or open that URL in your browser / API client.

📁 Project Structure
bash
Copy
Edit
sync-service-api/
├── routes/
│   ├── admin.js         # Admin panel routes
│   └── syncApi.js       # Synchronization endpoints
├── middleware/
│   └── auth.js          # Authentication middleware
├── services/
│   └── dbService.js     # Database connection service
├── utils/
│   └── logger.js        # Winston logger configuration
├── logs/                # Log files directory
├── .env                 # Environment variables
├── server.js            # Application entry point
└── package.json         # Project dependencies


🔌 API Endpoints
Admin Routes
Method	Path	Description
GET	/api/admin/initialize	Initialize database tables
POST	/api/admin/login	Admin login
POST	/api/admin/logout	Admin logout
GET	/api/admin/me	Check admin session
GET	/api/admin/list-users	List all sync users
POST	/api/admin/add-users	Create a new sync user
PUT	/api/admin/update-users/:clientId	Update user details
DELETE	/api/admin/delete-users/:clientId	Delete a user
GET	/api/admin/users/:clientId/config	Get user-specific configuration
GET	/api/admin/logs	Fetch synchronization logs

Sync API Routes
Method	Path	Description
POST	/api/sync/data	Synchronize client data
POST	/api/sync/log	Log sync operation details

🚀 Usage
Starting the Server
bash
Copy
Edit
npm start
# or for development with live reload:
npm run dev
Client Configuration
Create a user via the Admin Panel.

Fetch client config at /api/admin/users/:clientId/config.

Provide clients their clientId and accessToken.

Data Synchronization
Clients should POST data in this format:

json
Copy
Edit
{
  "clientId": "client_identifier",
  "accessToken": "access_token",
  "data": [
    {
      "CODE": "value",
      "NAME": "value",
      "ADDRESS": "value",
      "PLACE": "value",
      "SUPER_CODE": "value"
    },
    {
      "ID": "user_id",
      "PASS": "user_password"
    }
  ]
}
🔐 Security Considerations
Use HTTPS in production.

Rotate JWT secrets and access tokens regularly.

Hash and salt user passwords.

Validate and sanitize all inputs.

📈 Production Deployment
Set NODE_ENV=production.

Point to your production PostgreSQL.

Use a process manager like PM2:

bash
Copy
Edit
pm2 start server.js --name sync-service-api
Set up Nginx/Apache as a reverse proxy with SSL/TLS.

🛠️ Custom Configurations
Add new routes in routes/.

Implement middleware in middleware/.

Extend the database schema and services.

📜 Logging
Logs are stored under logs/:

combined.log – all info (and below) logs

error.log – error-level logs only

admin.log – admin operations

