# VideoStream MVP

**A Full-Stack Video Streaming Platform**

A comprehensive video streaming application built with modern technologies including Node.js, Express, React, TypeScript, PostgreSQL, and AWS S3 for scalable video storage and delivery.

## 🚀 Features

### Core Functionality
- **Video Upload & Processing**: Secure video upload with format validation and metadata extraction
- **Video Catalog**: Organized video library with search and filtering capabilities
- **Video Streaming**: Smooth video playback with adaptive quality streaming
- **User Management**: User registration, authentication, and profile management
- **Responsive Design**: Mobile-first design that works across all devices

### Technical Features
- **Cloud Storage**: AWS S3 integration for reliable video storage
- **Database**: PostgreSQL for robust data management
- **API Security**: JWT-based authentication and authorization
- **Error Handling**: Comprehensive error handling and logging
- **Type Safety**: Full TypeScript implementation for better code quality

## 🏗️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   React Client  │    │  Express API    │    │   PostgreSQL    │
│   (TypeScript)  │◄──►│   (Node.js)     │◄──►│    Database     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                              │
                              ▼
                       ┌─────────────────┐
                       │     AWS S3      │
                       │  Video Storage  │
                       └─────────────────┘
```

## 🛠️ Technology Stack

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web application framework
- **TypeScript** - Type-safe JavaScript
- **PostgreSQL** - Primary database
- **Sequelize** - ORM for database operations
- **JWT** - Authentication tokens
- **Multer** - File upload handling
- **AWS SDK** - S3 integration

### Frontend
- **React** - UI library
- **TypeScript** - Type safety
- **React Router** - Client-side routing
- **Axios** - HTTP client
- **Material-UI** - Component library
- **React Hook Form** - Form handling

### Infrastructure
- **AWS S3** - Video storage
- **Docker** - Containerization
- **PM2** - Process management
- **Nginx** - Reverse proxy (production)

## 📋 Prerequisites

Before running this project, make sure you have:

- **Node.js** (v16 or higher)
- **npm** or **yarn**
- **PostgreSQL** (v12 or higher)
- **AWS Account** with S3 access
- **Git**

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/devendrakumar-code/videostream-mvp.git
cd videostream-mvp
```

### 2. Backend Setup
```bash
# Navigate to backend directory
cd backend

# Install dependencies
npm install

# Create environment file
cp .env.example .env

# Configure your environment variables in .env
# DATABASE_URL=postgresql://username:password@localhost:5432/videostream
# JWT_SECRET=your_jwt_secret_key
# AWS_ACCESS_KEY_ID=your_aws_access_key
# AWS_SECRET_ACCESS_KEY=your_aws_secret_key
# AWS_REGION=your_aws_region
# AWS_S3_BUCKET=your_s3_bucket_name

# Run database migrations
npm run migrate

# Start the development server
npm run dev
```

### 3. Frontend Setup
```bash
# Navigate to frontend directory (open new terminal)
cd frontend

# Install dependencies
npm install

# Create environment file
cp .env.example .env

# Configure API URL in .env
# REACT_APP_API_URL=http://localhost:5000/api

# Start the development server
npm start
```

### 4. Database Setup
```bash
# Create PostgreSQL database
createdb videostream

# Run migrations from backend directory
npm run migrate

# (Optional) Seed sample data
npm run seed
```

## 📁 Project Structure

```
videostream-mvp/
├── backend/
│   ├── src/
│   │   ├── config/          # Database and AWS configuration
│   │   ├── controllers/     # Route controllers
│   │   ├── middleware/      # Custom middleware
│   │   ├── models/         # Database models
│   │   ├── routes/         # API routes
│   │   ├── services/       # Business logic
│   │   └── utils/          # Helper functions
│   ├── migrations/         # Database migrations
│   ├── package.json
│   └── tsconfig.json
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/     # React components
│   │   ├── pages/          # Page components
│   │   ├── services/       # API services
│   │   ├── hooks/          # Custom hooks
│   │   ├── types/          # TypeScript types
│   │   └── utils/          # Helper functions
│   ├── package.json
│   └── tsconfig.json
├── docker-compose.yml
├── README.md
└── .gitignore
```

## 🔧 Environment Variables

### Backend (.env)
```env
# Database
DATABASE_URL=postgresql://username:password@localhost:5432/videostream
DB_HOST=localhost
DB_PORT=5432
DB_NAME=videostream
DB_USER=your_username
DB_PASSWORD=your_password

# JWT
JWT_SECRET=your_super_secret_jwt_key
JWT_EXPIRES_IN=7d

# AWS S3
AWS_ACCESS_KEY_ID=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret_key
AWS_REGION=us-east-1
AWS_S3_BUCKET=your_bucket_name

# Server
PORT=5000
NODE_ENV=development
```

### Frontend (.env)
```env
# API Configuration
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_APP_NAME=VideoStream MVP
```

## 📚 API Documentation

### Authentication Endpoints
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `GET /api/auth/profile` - Get user profile

### Video Endpoints
- `GET /api/videos` - Get all videos (with pagination)
- `GET /api/videos/:id` - Get specific video
- `POST /api/videos` - Upload new video
- `PUT /api/videos/:id` - Update video metadata
- `DELETE /api/videos/:id` - Delete video
- `GET /api/videos/search` - Search videos

### User Endpoints
- `GET /api/users/profile` - Get current user profile
- `PUT /api/users/profile` - Update user profile
- `GET /api/users/:id/videos` - Get user's videos

## 🎯 Key Components

### Backend Services
- **AuthService**: Handles user authentication and JWT tokens
- **VideoService**: Manages video operations and S3 interactions
- **UploadService**: Processes file uploads and validation
- **DatabaseService**: Database connection and query operations

### Frontend Components
- **VideoPlayer**: Custom video player with controls
- **VideoUpload**: Drag-and-drop video upload interface
- **VideoList**: Grid/list view of videos with pagination
- **SearchBar**: Real-time video search functionality
- **UserDashboard**: User profile and video management

## 🔒 Security Features

- **JWT Authentication**: Secure token-based authentication
- **Input Validation**: Comprehensive input sanitization
- **File Type Validation**: Only allows supported video formats
- **Rate Limiting**: Prevents API abuse
- **CORS Configuration**: Proper cross-origin resource sharing
- **Environment Variables**: Sensitive data protection

## 🚀 Deployment

### Using Docker
```bash
# Build and run with Docker Compose
docker-compose up --build
```

### Manual Deployment
```bash
# Backend
cd backend
npm run build
npm start

# Frontend
cd frontend
npm run build
# Serve build folder with nginx or similar
```

### Production Environment Variables
Ensure all production environment variables are properly configured, especially:
- Database connection strings
- AWS credentials and S3 bucket
- JWT secrets
- CORS origins

## 📊 Performance Considerations

- **Video Compression**: Automatic video optimization for web delivery
- **CDN Integration**: AWS CloudFront for global content delivery
- **Database Indexing**: Optimized queries for video search and retrieval
- **Caching**: Redis integration for improved response times
- **Lazy Loading**: Progressive video loading for better UX

## 🧪 Testing

```bash
# Backend tests
cd backend
npm test

# Frontend tests
cd frontend
npm test

# Run all tests
npm run test:all
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines
- Follow TypeScript best practices
- Write comprehensive tests for new features
- Update documentation for any API changes
- Use meaningful commit messages

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Devendra Kumar**
- GitHub: [@devendrakumar-code](https://github.com/devendrakumar-code)
- Email: [your-devendra012003@gmail.com](mailto:devendra012003@gmail.com)

## 🙏 Acknowledgments

- Thanks to the open-source community for the amazing tools and libraries
- AWS for providing reliable cloud infrastructure
- The React and Node.js communities for excellent documentation

---

**Built with ❤️ using modern web technologies**
