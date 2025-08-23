# JO Service Marketplace Backend

A robust Node.js backend API for the On-Demand Service Marketplace mobile application. This service connects users with service providers, facilitating bookings, real-time chat, ratings, and notifications.

## 🚀 Features

- **User Management**: Registration, authentication, profile management
- **Provider Management**: Service provider profiles, verification, search
- **Booking System**: Service scheduling, status tracking, payment integration
- **Real-time Chat**: WebSocket-based messaging between users and providers
- **Rating & Reviews**: Service quality feedback system
- **Push Notifications**: Firebase Cloud Messaging integration
- **OAuth Integration**: Google and Facebook authentication
- **File Uploads**: Image handling for profiles and chat
- **Admin Panel**: User management and system oversight
- **API Documentation**: Swagger/OpenAPI 3.0 specification

## 🛠️ Tech Stack

- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JWT, Passport.js, OAuth 2.0
- **Real-time**: WebSocket (ws)
- **File Handling**: Multer
- **Email**: Nodemailer
- **SMS**: Twilio
- **Push Notifications**: Firebase Admin SDK
- **Documentation**: Swagger/OpenAPI 3.0
- **Development**: Nodemon

## 📋 Prerequisites

- Node.js (v16 or higher)
- MongoDB database
- npm or yarn package manager

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone <your-repo-url>
cd joservice_backend
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Environment Configuration
Create a `.env` file in the root directory:

```env
# Server Configuration
PORT=3000
NODE_ENV=development

# Database
MONGODB_URI=mongodb://localhost:27017/joservice

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key
JWT_EXPIRES_IN=7d

# Email Configuration (Gmail)
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password

# Twilio Configuration
TWILIO_ACCOUNT_SID=your-twilio-account-sid
TWILIO_AUTH_TOKEN=your-twilio-auth-token
TWILIO_PHONE_NUMBER=your-twilio-phone-number

# OAuth Configuration
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret
GOOGLE_REDIRECT_URI=http://localhost:3000/api/auth/google/callback

FACEBOOK_APP_ID=your-facebook-app-id
FACEBOOK_APP_SECRET=your-facebook-app-secret
FACEBOOK_REDIRECT_URI=http://localhost:3000/api/auth/facebook/callback

# Firebase Configuration
FIREBASE_PROJECT_ID=your-firebase-project-id
FIREBASE_PRIVATE_KEY=your-firebase-private-key
FIREBASE_CLIENT_EMAIL=your-firebase-client-email

# Frontend URL
FRONTEND_URL=http://localhost:3000
```

### 4. Start the Server

**Development Mode:**
```bash
npm run dev
```

**Production Mode:**
```bash
npm start
```

The server will start on `http://localhost:3000`

## 📚 API Documentation

Once the server is running, access the interactive API documentation at:

- **Swagger UI**: `http://localhost:3000/api-docs`
- **API Base URL**: `http://localhost:3000/api`

### Production URLs
- **Live API**: `https://joservicebackend-production.up.railway.app/`
- **Live API Documentation**: `https://joservicebackend-production.up.railway.app/api-docs`
- **Live API Base**: `https://joservicebackend-production.up.railway.app/api`

## 🏗️ Project Structure

```
joservice_backend/
├── src/
│   ├── app.js                 # Main application entry point
│   ├── config/                # Configuration files
│   │   ├── db.js             # Database connection
│   │   └── swagger.js        # API documentation config
│   ├── controllers/          # Request handlers
│   │   ├── auth.controller.js
│   │   ├── user.controller.js
│   │   ├── provider.controller.js
│   │   ├── booking.controller.js
│   │   ├── chat.controller.js
│   │   ├── rating.controller.js
│   │   ├── notification.controller.js
│   │   └── admin.controller.js
│   ├── middlewares/          # Custom middleware
│   │   ├── auth.middleware.js
│   │   └── upload.middleware.js
│   ├── models/               # Database models
│   │   ├── user.model.js
│   │   ├── provider.model.js
│   │   ├── booking.model.js
│   │   ├── message.model.js
│   │   ├── rating.model.js
│   │   └── notification.model.js
│   ├── routes/               # API route definitions
│   │   ├── auth.routes.js
│   │   ├── user.routes.js
│   │   ├── provider.routes.js
│   │   ├── booking.routes.js
│   │   ├── chat.routes.js
│   │   ├── rating.routes.js
│   │   ├── notification.routes.js
│   │   └── admin.routes.js
│   ├── services/             # Business logic services
│   │   ├── notification.service.js
│   │   ├── oauth.service.js
│   │   ├── upload.service.js
│   │   ├── verification.service.js
│   │   └── websocket.service.js
│   └── utils/                # Utility functions
│       └── jwt.utils.js
├── public/                   # Static files and uploads
│   ├── uploads/             # User uploaded files
│   ├── profile-pictures/    # User profile images
│   └── verify-email.html    # Email verification page
├── package.json             # Project dependencies
└── README.md               # This file
```

## 🔐 API Endpoints

### Authentication (`/api/auth`)
- `POST /register` - User registration
- `POST /login` - User login
- `POST /logout` - User logout
- `POST /refresh-token` - Refresh JWT token
- `POST /verify-email` - Email verification
- `POST /verify-phone` - Phone verification
- `GET /google` - Google OAuth initiation
- `GET /facebook` - Facebook OAuth initiation

### Users (`/api/users`)
- `GET /profile` - Get user profile
- `PUT /profile` - Update user profile
- `DELETE /profile` - Delete user account

### Providers (`/api/providers`)
- `GET /` - Search and filter providers
- `GET /:id` - Get provider details
- `POST /` - Create provider profile
- `PUT /:id` - Update provider profile
- `DELETE /:id` - Delete provider profile

### Bookings (`/api/bookings`)
- `POST /` - Create new booking
- `GET /` - Get user's bookings
- `GET /:id` - Get booking details
- `PUT /:id` - Update booking status
- `DELETE /:id` - Cancel booking

### Chat (`/api/chats`)
- `GET /` - Get chat conversations
- `GET /:id/messages` - Get chat messages
- `POST /:id/messages` - Send message
- `POST /:id/messages/image` - Send image message

### Ratings (`/api/ratings`)
- `POST /` - Create rating/review
- `GET /provider/:id` - Get provider ratings
- `PUT /:id` - Update rating
- `DELETE /:id` - Delete rating

### Notifications (`/api/notifications`)
- `GET /` - Get user notifications
- `PUT /:id/read` - Mark notification as read
- `DELETE /:id` - Delete notification

### Admin (`/api/admin`)
- `GET /users` - Get all users
- `GET /providers` - Get all providers
- `PUT /users/:id/verify` - Verify user account
- `PUT /providers/:id/verify` - Verify provider account

## 🔌 WebSocket Events

The application supports real-time communication through WebSocket connections:

- **Connection**: `connection`
- **Join Room**: `join-room`
- **Leave Room**: `leave-room`
- **Send Message**: `send-message`
- **Typing**: `typing`
- **Stop Typing**: `stop-typing`

## 📱 Mobile App Integration

This backend is designed to work with React Native mobile applications. Key integration points:

- **Authentication**: JWT-based session management
- **Real-time Chat**: WebSocket connections for instant messaging
- **Push Notifications**: FCM integration for mobile notifications
- **File Uploads**: Image handling for profiles and chat
- **Location Services**: Geospatial queries for provider search

## 🚀 Deployment

### Railway Deployment
1. Connect your GitHub repository to Railway
2. Set environment variables in Railway dashboard
3. Deploy automatically on push to main branch

### Environment Variables for Production
Ensure all required environment variables are set in your production environment, especially:
- `MONGODB_URI`
- `JWT_SECRET`
- `EMAIL_USER` and `EMAIL_PASS`
- OAuth credentials
- Firebase configuration

### Production Deployment
Your application is currently deployed on Railway at:
- **Main URL**: `https://joservicebackend-production.up.railway.app/`
- **API Documentation**: `https://joservicebackend-production.up.railway.app/api-docs`
- **Health Check**: `https://joservicebackend-production.up.railway.app/`

## 🧪 Testing

Run the test server:
```bash
node test-server.js
```

Test verification services:
```bash
node test-verification.js
```

## 📝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the ISC License.

## 🆘 Support

For support and questions:
- Email: support@joservice.com
- API Documentation: Available at `/api-docs` when server is running
- Issues: Please use GitHub issues for bug reports and feature requests

## 🔄 Version History

- **v1.0.0** - Initial release with core functionality
- Authentication and user management
- Provider search and booking system
- Real-time chat and notifications
- Admin panel and verification system

---

**Built with ❤️ for the JO Service Marketplace**
