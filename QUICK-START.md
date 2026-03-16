# 🚀 QUICK START GUIDE - VS CODE

## ✅ PROJECT LOCATION
Your complete authentication system is ready at:
**C:\Users\Rakes\Desktop\auth-system-project**

## 📖 STEP-BY-STEP INSTRUCTIONS

### Step 1: Open in VS Code
1. Open VS Code
2. Click "File" → "Open Folder"
3. Navigate to: `C:\Users\Rakes\Desktop\auth-system-project`
4. Click "Select Folder"

### Step 2: Start MongoDB
Open a NEW terminal in VS Code (Terminal → New Terminal) and run:
```bash
mongod
```
**Keep this terminal running!**

### Step 3: Setup Backend
Open a NEW terminal (click the + icon) and run:
```bash
cd backend
npm install
npm run dev
```
✅ Backend will run on: http://localhost:5000

### Step 4: Setup Frontend
Open ANOTHER NEW terminal (click the + icon again) and run:
```bash
cd frontend
npm install
npm run dev
```
✅ Frontend will run on: http://localhost:5173

### Step 5: Access the Application
Open your browser and go to:
**http://localhost:5173**

## 🎯 WHAT YOU CAN DO

### 1. Register a New User
- Click "Register" button
- Fill in: Name, Email, Password (min 6 characters)
- Submit → Auto-login → Redirected to Dashboard

### 2. Login
- Click "Login" button
- Enter your email and password
- Submit → Redirected to Dashboard

### 3. Test Admin Access
To create an admin user:
1. Register/Login as a normal user first
2. Open MongoDB shell or MongoDB Compass
3. Connect to: `mongodb://localhost:27017/auth_system`
4. Run this command:
```javascript
db.users.updateOne(
  { email: "your-email@example.com" },
  { $set: { role: "admin" } }
)
```
5. Logout and login again
6. You'll now see "Admin" link in navbar
7. Click it to access Admin Dashboard

## 📁 PROJECT STRUCTURE

```
auth-system-project/
├── backend/              # Node.js + Express + MongoDB
│   ├── config/          # Database configuration
│   ├── controllers/     # Business logic
│   ├── middleware/      # Auth & Role middleware
│   ├── models/          # User model
│   ├── routes/          # API routes
│   ├── .env            # Environment variables
│   ├── package.json    # Dependencies
│   └── server.js       # Entry point
│
├── frontend/            # React + Vite + TailwindCSS
│   ├── src/
│   │   ├── components/ # Reusable components
│   │   ├── context/    # Auth context
│   │   ├── pages/      # Page components
│   │   ├── App.jsx     # Main app
│   │   └── main.jsx    # Entry point
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
│
└── README.md           # This file
```

## 🔧 VS CODE RECOMMENDED EXTENSIONS

Install these extensions for better development experience:
1. **ES7+ React/Redux/React-Native snippets**
2. **Tailwind CSS IntelliSense**
3. **ESLint**
4. **Prettier - Code formatter**
5. **MongoDB for VS Code**

## 🐛 TROUBLESHOOTING

### MongoDB Not Starting?
```bash
# Make sure MongoDB is installed
# Download from: https://www.mongodb.com/try/download/community
```

### Port Already in Use?
```bash
# Kill process on port 5000 (backend)
netstat -ano | findstr :5000
taskkill /PID <PID_NUMBER> /F

# Kill process on port 5173 (frontend)
netstat -ano | findstr :5173
taskkill /PID <PID_NUMBER> /F
```

### Dependencies Not Installing?
```bash
# Clear npm cache
npm cache clean --force

# Delete node_modules and package-lock.json
# Then run npm install again
```

## 📝 USEFUL VS CODE SHORTCUTS

- **Ctrl + `** → Open/Close Terminal
- **Ctrl + Shift + `** → New Terminal
- **Ctrl + P** → Quick file search
- **Ctrl + Shift + F** → Search in all files
- **F5** → Start debugging

## 🎨 FEATURES IMPLEMENTED

✅ User Registration with validation
✅ User Login with JWT
✅ Password hashing (bcrypt - 10 rounds)
✅ JWT in httpOnly cookies
✅ Protected routes
✅ Role-based access control (user/admin)
✅ Session management
✅ Secure logout
✅ Beautiful UI with TailwindCSS
✅ Responsive design
✅ Error handling
✅ Input validation

## 🔒 SECURITY FEATURES

✅ Helmet.js for security headers
✅ CORS configured
✅ Password hashing with bcrypt
✅ JWT token authentication
✅ httpOnly cookies (XSS protection)
✅ Input validation
✅ Role-based authorization

## 📡 API ENDPOINTS

### Public
- POST `/api/auth/register` - Register user
- POST `/api/auth/login` - Login user
- POST `/api/auth/logout` - Logout user

### Protected
- GET `/api/auth/me` - Get current user
- GET `/api/user/profile` - User profile
- GET `/api/user/admin/dashboard` - Admin only

## 🎓 LEARNING RESOURCES

- **React**: https://react.dev
- **Express**: https://expressjs.com
- **MongoDB**: https://www.mongodb.com/docs
- **JWT**: https://jwt.io
- **TailwindCSS**: https://tailwindcss.com

---

**🎉 You're all set! Happy coding!**

**Need help? Check the console logs in VS Code terminal for any errors.**
