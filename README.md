
# 🔐 Internal Password Manager

A secure and role-based password manager for internal staff, with real-time access control, request workflows, and audit logs.

## 🚀 Features

### 👥 Roles
- **Super Admin**: Full access, manages all credentials, users, and requests.
- **Admin**: Manages passwords and requests for their department or group.
- **User**: Can view only approved credentials and request access to others.

### 🔐 Credential Entry Structure
Each password record includes:
- Service Name
- Department / Group
- Website / App Link
- Username / Email
- Encrypted Password (AES-256)
- Phone Number / Recovery Info
- 2FA Status (Enabled/Disabled)
- Notes / Tags
- Created By / Modified Date
- Access Logs

### ⚙️ Real-Time Functionalities
- **Access Request Flow**:
  - Users request password access
  - Super Admin/Admin receives live notification
  - Decision is pushed in real-time
- **Live Audit Logs**:
  - Tracks who accessed, when, and how
- **Temporary Access Sharing**:
  - Time-limited password sharing (e.g., 15 mins)
- **Password Rotation Tracker**:
  - Tracks when passwords are due for change
- **2FA Tracker**:
  - Notifies when 2FA is disabled on sensitive services
- **Credential Grouping**:
  - Organize passwords into categories (e.g., DevOps, Finance)
- **Smart Notifications**:
  - Real-time alerts for:
    - Viewed credentials
    - New requests
    - Password age

## 🧱 Tech Stack

| Layer       | Technology               |
|-------------|--------------------------|
| Frontend    | React, Tailwind CSS, DaisyUI |
| Backend     | Node.js, Express         |
| Realtime    | Socket.IO                |
| Database    | MongoDB                  |
| Auth        | JWT + Role-based Access  |
| Encryption  | AES-256 + Bcrypt         |

## 🛠️ Installation

### Backend

```bash
cd server
npm install
npm run dev
```

### Frontend

```bash
cd client
npm install
npm run dev
```

## 📦 Folder Structure

```
/client
  /src
    /pages
    /components
    /contexts
    /services
    /utils
    App.jsx
    main.jsx

/server
  /controllers
  /routes
  /models
  /middleware
  /utils
  server.js
```

## 🔑 API Routes Overview

| Route                                 | Method | Role         | Description                      |
|---------------------------------------|--------|--------------|----------------------------------|
| `/api/auth/login`                     | POST   | All          | Login with email/password        |
| `/api/passwords`                      | GET    | Super/Admin  | Get all credentials              |
| `/api/passwords/:id`                  | GET    | Authorized   | View specific credential         |
| `/api/passwords`                      | POST   | Super/Admin  | Add new password                 |
| `/api/passwords/:id`                  | PUT    | Super/Admin  | Update existing credential       |
| `/api/access-request`                 | POST   | User         | Request access to a password     |
| `/api/access-request`                 | GET    | Admin/Super  | View pending access requests     |
| `/api/access-request/:id/approve`     | PUT    | Admin/Super  | Approve access request           |
| `/api/logs`                           | GET    | Admin/Super  | Get access and audit logs        |

## 🔒 Security Practices

- Passwords encrypted with AES-256 and never exposed in raw form
- Role-based access middleware on all endpoints
- JWT Auth with refresh tokens
- Real-time Socket.IO for notifications and request workflows
- Access logs with IP, timestamp, role

## 🧪 Future Ideas

- Google Authenticator integration for 2FA
- Import from CSV / Bitwarden
- Browser Extension
- Scheduled auto-rotation for passwords
- Department-based access control and analytics

## 📸 UI Features

- Theme-switcher (DaisyUI)
- Table/List view for credentials
- Modal for viewing passwords securely
- Real-time toast notifications (React Toastify)
- Access status icons (Pending, Granted, Denied)

## 📄 License

This project is internal and private. For enterprise use only.
