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

1. **Clone the repository**  
   ```bash
   git clone <your-repository-url>
   cd sync-service-api
