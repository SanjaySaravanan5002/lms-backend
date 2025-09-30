# MERN LMS Backend API

A robust Node.js backend API for the MERN Learning Management System with authentication, course management, payments, and file uploads.

## 🚀 Features

- **User Authentication** with JWT tokens
- **Role-based Access** (Students, Instructors, Admin)
- **Course Management** (CRUD operations)
- **File Upload** with Cloudinary integration
- **Payment Processing** with PayPal
- **Course Progress Tracking**
- **Order Management**
- **RESTful API Design**

## 🛠️ Tech Stack

- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database with Mongoose ODM
- **JWT** - Authentication tokens
- **Bcrypt** - Password hashing
- **Cloudinary** - File storage
- **PayPal SDK** - Payment processing
- **Multer** - File upload middleware
- **CORS** - Cross-origin resource sharing

## 📦 Installation

1. Clone the repository:
```bash
git clone https://github.com/your-username/mern-lms-backend.git
cd mern-lms-backend
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
```bash
cp .env.example .env
```

4. Update the `.env` file with your credentials:
```env
MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/mern-lms
JWT_SECRET=your-super-secret-jwt-key-here
CLIENT_URL=http://localhost:5173
CLOUDINARY_CLOUD_NAME=your-cloudinary-name
CLOUDINARY_API_KEY=your-cloudinary-api-key
CLOUDINARY_API_SECRET=your-cloudinary-api-secret
PAYPAL_MODE=sandbox
PAYPAL_CLIENT_ID=your-paypal-client-id
PAYPAL_CLIENT_SECRET=your-paypal-client-secret
PORT=5000
```

## 🚀 Development

Start the development server:
```bash
npm run dev
```

Start the production server:
```bash
npm start
```

The API will be available at `http://localhost:5000`

## 📱 Deployment

### Render (Recommended)

1. Connect your GitHub repository to Render
2. Set environment variables in Render dashboard
3. Deploy with the following settings:
   - **Build Command**: `npm install`
   - **Start Command**: `npm start`

### Railway (Alternative)

1. Connect your GitHub repository to Railway
2. Set environment variables
3. Deploy automatically

## 🔧 Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `MONGO_URI` | MongoDB connection string | ✅ |
| `JWT_SECRET` | Secret for JWT tokens | ✅ |
| `CLIENT_URL` | Frontend application URL | ✅ |
| `CLOUDINARY_CLOUD_NAME` | Cloudinary cloud name | ✅ |
| `CLOUDINARY_API_KEY` | Cloudinary API key | ✅ |
| `CLOUDINARY_API_SECRET` | Cloudinary API secret | ✅ |
| `PAYPAL_MODE` | PayPal mode (sandbox/live) | ✅ |
| `PAYPAL_CLIENT_ID` | PayPal client ID | ✅ |
| `PAYPAL_CLIENT_SECRET` | PayPal client secret | ✅ |
| `PORT` | Server port (default: 5000) | ❌ |

## 📁 Project Structure

```
├── controllers/           # Request handlers
│   ├── auth-controller/   # Authentication logic
│   ├── instructor-controller/  # Instructor operations
│   └── student-controller/     # Student operations
├── helpers/              # Utility functions
│   ├── cloudinary.js     # File upload helpers
│   └── paypal.js         # Payment processing
├── middleware/           # Express middlewares
│   └── auth-middleware.js # JWT authentication
├── models/              # MongoDB schemas
│   ├── Course.js        # Course model
│   ├── User.js          # User model
│   ├── Order.js         # Order model
│   ├── CourseProgress.js # Progress tracking
│   └── StudentCourses.js # Student enrollments
├── routes/              # API routes
│   ├── auth-routes/     # Authentication routes
│   ├── instructor-routes/ # Instructor routes
│   └── student-routes/   # Student routes
├── uploads/             # Temporary file storage
└── server.js           # Application entry point
```

## 🛡️ API Endpoints

### Authentication
- `POST /auth/register` - User registration
- `POST /auth/login` - User login
- `GET /auth/check-auth` - Verify authentication

### Courses
- `GET /instructor/course/get` - Get instructor courses
- `POST /instructor/course/add` - Create new course
- `PUT /instructor/course/update/:id` - Update course
- `DELETE /instructor/course/delete/:id` - Delete course

### Student Operations
- `GET /student/course/get` - Get available courses
- `GET /student/course/details/:id` - Get course details
- `POST /student/order/create` - Create order
- `POST /student/order/capture` - Capture payment

### File Upload
- `POST /media/upload` - Upload files to Cloudinary
- `DELETE /media/delete/:id` - Delete uploaded files

## 🔒 Authentication

The API uses JWT (JSON Web Tokens) for authentication:

1. User registers/logs in and receives a JWT token
2. Token must be included in the Authorization header for protected routes:
   ```
   Authorization: Bearer <your-jwt-token>
   ```
3. Middleware validates the token and extracts user information

## 💳 Payment Integration

PayPal integration for course purchases:

1. Student creates an order
2. PayPal payment is processed
3. Upon successful payment, course access is granted
4. Order details are stored in the database

## 📤 File Upload

Cloudinary integration for file management:

- Course thumbnails and materials
- Video uploads for course content
- Automatic file optimization and CDN delivery

## 🧪 Testing

Test the API endpoints using:
- **Postman** - Import the API collection
- **Thunder Client** - VS Code extension
- **curl** - Command line testing

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🔗 Related Repositories

- **Frontend React App**: [mern-lms-frontend](https://github.com/your-username/mern-lms-frontend)

## 📞 Support

For support, email support@yourapp.com or create an issue in this repository.

## 🚀 Health Check

The API includes a health check endpoint at `/` that returns:
```json
{
  "success": true,
  "message": "MERN LMS Server is running successfully!",
  "timestamp": "2024-01-01T00:00:00.000Z"
}
```
