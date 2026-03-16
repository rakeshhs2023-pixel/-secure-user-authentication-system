# 🔐 SECURE USER AUTHENTICATION SYSTEM

Complete production-ready authentication system with JWT, role-based access control, and secure session management.

## 📦 PACKAGE CONTENTS

```
auth-system-complete/
├── backend/          # Node.js + Express + MongoDB backend
├── frontend/         # React + Vite + TailwindCSS frontend
└── README.md         # This file
```

## 🚀 QUICK START GUIDE

### Prerequisites
- Node.js v18+ installed
- MongoDB installed and running
- npm or yarn package manager

### Step 1: Start MongoDB
Open a terminal and run:
```bash
mongod
```
Keep this terminal running.

### Step 2: Setup Backend
Open a NEW terminal:
```bash
cd backend
npm install
npm run dev
```
Backend runs on: http://localhost:5000

### Step 3: Setup Frontend
Open ANOTHER NEW terminal:
```bash
cd frontend
npm install
npm run dev
```
Frontend runs on: http://localhost:5173

### Step 4: Access Application
Open browser: http://localhost:5173

## 📋 FEATURES

✅ User Registration with validation
✅ User Login with JWT authentication
✅ Password hashing with bcrypt (10 salt rounds)
✅ JWT tokens in httpOnly cookies
✅ Protected routes (authentication required)
✅ Role-based access control (user/admin)
✅ Session management
✅ Secure logout
✅ Input validation
✅ Security headers with Helmet
✅ CORS configuration

## 🔑 DEFAULT CONFIGURATION

**Backend (.env file already configured):**
- PORT: 5000
- MONGO_URI: mongodb://localhost:27017/auth_system
- JWT_SECRET: supersecretkey
- JWT_EXPIRE: 7d

**Frontend:**
- PORT: 5173
- API URL: http://localhost:5000

## 📖 USAGE

### 1. Register New User
- Go to: http://localhost:5173/register
- Enter: Name, Email, Password (min 6 chars)
- Click "Register"
- Auto-redirected to dashboard

### 2. Login
- Go to: http://localhost:5173/login
- Enter: Email, Password
- Click "Login"
- Redirected to dashboard

### 3. Test Admin Access
To create an admin user, connect to MongoDB and run:
```javascript
use auth_system
db.users.updateOne(
  { email: "your-email@example.com" },
  { $set: { role: "admin" } }
)
```
Then login and access: http://localhost:5173/admin

## 🛠️ TECH STACK

**Backend:**
- Node.js & Express.js
- MongoDB with Mongoose
- JWT (jsonwebtoken)
- bcryptjs for password hashing
- Helmet for security
- CORS
- Cookie-parser
- Express-validator

**Frontend:**
- React 18
- Vite
- React Router v6
- Axios
- Context API
- TailwindCSS

## 📡 API ENDPOINTS

### Public Routes
- POST /api/auth/register - Register new user
- POST /api/auth/login - Login user
- POST /api/auth/logout - Logout user

### Protected Routes
- GET /api/auth/me - Get current user (requires auth)
- GET /api/user/profile - User profile (requires auth)
- GET /api/user/admin/dashboard - Admin only (requires admin role)

## 🔒 SECURITY FEATURES

1. **Password Hashing**: bcrypt with 10 salt rounds
2. **JWT Tokens**: Secure token-based authentication
3. **httpOnly Cookies**: Prevents XSS attacks
4. **Helmet**: Security headers
5. **CORS**: Configured for frontend origin only
6. **Input Validation**: Server-side validation
7. **Role-Based Access**: Middleware for authorization

## 📁 PROJECT STRUCTURE

### Backend
```
backend/
├── config/
│   └── db.js                 # MongoDB connection
├── controllers/
│   └── authController.js     # Auth logic (register, login, logout)
├── middleware/
│   ├── authMiddleware.js     # JWT verification (verifyToken)
│   └── roleMiddleware.js     # Role authorization (authorizeRoles)
├── models/
│   └── User.js               # User schema with password hashing
├── routes/
│   ├── authRoutes.js         # Auth endpoints
│   └── userRoutes.js         # Protected endpoints
├── .env                      # Environment variables
├── package.json              # Dependencies
└── server.js                 # Express server entry point
```

### Frontend
```
frontend/
├── src/
│   ├── components/
│   │   ├── Navbar.jsx           # Navigation bar
│   │   └── ProtectedRoute.jsx   # Route protection component
│   ├── context/
│   │   └── AuthContext.jsx      # Global auth state
│   ├── pages/
│   │   ├── Login.jsx            # Login page
│   │   ├── Register.jsx         # Registration page
│   │   ├── Dashboard.jsx        # User dashboard
│   │   └── AdminDashboard.jsx   # Admin dashboard
│   ├── App.jsx                  # Main app with routing
│   ├── main.jsx                 # React entry point
│   └── index.css                # Tailwind CSS
├── index.html
├── vite.config.js
├── tailwind.config.js
└── package.json
```

## 🐛 TROUBLESHOOTING

### MongoDB Connection Error
```
Error: connect ECONNREFUSED
```
**Solution**: Make sure MongoDB is running with `mongod` command

### CORS Error
```
Access to XMLHttpRequest has been blocked by CORS policy
```
**Solution**: Verify backend is running on port 5000 and frontend on 5173

### Port Already in Use
```
Error: listen EADDRINUSE: address already in use :::5000
```
**Solution**: Kill the process using the port or change PORT in .env

### JWT Token Issues
**Solution**: Clear browser cookies and login again

## 🌐 PRODUCTION DEPLOYMENT

### Backend
1. Set `NODE_ENV=production` in .env
2. Use strong `JWT_SECRET` (generate random string)
3. Use MongoDB Atlas or production database
4. Enable HTTPS
5. Update CORS origin to production frontend URL

### Frontend
1. Build production bundle:
   ```bash
   npm run build
   ```
2. Deploy `dist/` folder to hosting service
3. Update API base URL in `src/context/AuthContext.jsx`

## 📝 TESTING

### Test Registration (using curl)
```bash
curl -X POST http://localhost:5000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"John Doe","email":"john@example.com","password":"password123"}'
```

### Test Login
```bash
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"john@example.com","password":"password123"}' \
  -c cookies.txt
```

### Test Protected Route
```bash
curl -X GET http://localhost:5000/api/user/profile \
  -b cookies.txt
```

## 📄 LICENSE

MIT License - Free to use for personal and commercial projects

## 👨‍💻 SUPPORT

For issues or questions:
1. Check MongoDB is running
2. Verify all dependencies are installed
3. Check console for error messages
4. Ensure ports 5000 and 5173 are available

---

**Built with ❤️ as a complete authentication system template**

**Ready to use in production with proper security configurations!**
