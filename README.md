# 🐾 Animal Clinic Management System

A complete full-stack application for managing an animal clinic with React + Redux frontend and Node.js + Express backend.

![Node.js](https://img.shields.io/badge/Node.js-18%2B-green)
![React](https://img.shields.io/badge/React-18-blue)
![TypeScript](https://img.shields.io/badge/TypeScript-5-blue)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue)
![Docker](https://img.shields.io/badge/Docker-Ready-blue)

## ✨ Features

### 🔐 Authentication & Authorization
- JWT-based authentication with refresh tokens
- Role-based access control (Admin, Veterinarian, Assistant, Receptionist)
- Secure password hashing with bcrypt
- Protected routes and middleware

### 🐕 Animal Management
- Complete CRUD operations for animals
- Animal profiles with photos
- Medical history tracking
- Vaccination records
- Search and filter functionality
- Species categorization

### 👥 Owner Management
- Pet owner profiles and contact information
- Emergency contact details
- Link multiple animals to owners
- Owner search and management

### 📊 Dashboard & Analytics
- Real-time statistics and metrics
- Recent activities feed
- Quick access to common actions
- Data visualization with charts

## 🛠 Tech Stack

### Frontend
- **React 18** with TypeScript
- **Redux Toolkit** for state management
- **Ant Design** for UI components
- **React Router** for navigation
- **React Hook Form** for form validation
- **Axios** for API communication

### Backend
- **Node.js** with Express and TypeScript
- **Sequelize** ORM with PostgreSQL
- **JWT** authentication
- **Joi** validation
- **Winston** logging
- **Redis** for session management

### DevOps & Tools
- **Docker** & Docker Compose
- **Nginx** reverse proxy
- **Jest** for testing
- **ESLint** & Prettier
- **GitHub Actions** CI/CD
- **Heroku** deployment ready

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ and npm
- Docker and Docker Compose
- PostgreSQL (for local development)

### Option 1: Docker Compose (Recommended)

1. **Clone and setup:**
```bash
git clone https://github.com/IrinaMakaruk/animal-clinic.git
cd animal-clinic
cp .env.example .env
```

2. **Start all services:**
```bash
docker-compose up --build
```

3. **Access the application:**
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000
- Database: PostgreSQL on port 5432

### Option 2: Local Development

1. **Install dependencies:**
```bash
# Backend
cd server && npm install

# Frontend  
cd ../client && npm install
```

2. **Setup environment:**
```bash
cp .env.example .env
# Edit .env with your database credentials
```

3. **Setup database:**
```bash
# Create database
createdb animal_clinic_dev

# Run migrations
cd server && npm run migrate

# Seed with sample data (optional)
npm run seed
```

4. **Start development servers:**
```bash
# Terminal 1 - Backend
cd server && npm run dev

# Terminal 2 - Frontend
cd client && npm start
```

## 📋 Available Scripts

### Server Commands
```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server
npm run test         # Run tests
npm run test:watch   # Run tests in watch mode
npm run test:coverage # Run tests with coverage
npm run migrate      # Run database migrations
npm run seed         # Seed database with sample data
npm run lint         # Lint code
npm run format       # Format code
```

### Client Commands
```bash
npm start            # Start development server
npm run build        # Build for production
npm run test         # Run tests
npm run test:coverage # Run tests with coverage
npm run lint         # Lint code
npm run format       # Format code
npm run type-check   # TypeScript type checking
```

## 🐳 Docker Commands

```bash
# Development environment
docker-compose up --build

# Production environment
docker-compose -f docker-compose.prod.yml up --build

# Run tests in containers
docker-compose exec server npm test
docker-compose exec client npm test

# Access database
docker-compose exec db psql -U postgres animal_clinic

# View logs
docker-compose logs -f server
docker-compose logs -f client
```

## 🚀 Deployment

### Heroku Deployment

1. **Install Heroku CLI:**
```bash
# macOS
brew tap heroku/brew && brew install heroku

# Windows
# Download from https://devcenter.heroku.com/articles/heroku-cli
```

2. **Setup Heroku app:**
```bash
heroku login
heroku create your-animal-clinic-app
heroku addons:create heroku-postgresql:hobby-dev
```

3. **Configure environment variables:**
```bash
heroku config:set NODE_ENV=production
heroku config:set JWT_SECRET=your-super-secret-jwt-key
heroku config:set CORS_ORIGIN=https://your-animal-clinic-app.herokuapp.com
```

4. **Deploy:**
```bash
git push heroku main
heroku run npm run migrate
heroku open
```

### Environment Variables

Create a `.env` file based on `.env.example`:

```env
# Database
DATABASE_URL=postgresql://username:password@localhost:5432/animal_clinic
DB_HOST=localhost
DB_PORT=5432
DB_NAME=animal_clinic
DB_USER=postgres
DB_PASSWORD=password

# JWT
JWT_SECRET=your-super-secret-jwt-key
JWT_EXPIRES_IN=7d

# Server
NODE_ENV=development
PORT=5000
CORS_ORIGIN=http://localhost:3000

# Client
REACT_APP_API_URL=http://localhost:5000/api
```

## 🧪 Testing

### Backend Tests
```bash
cd server

# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:coverage

# Run specific test file
npm test -- --testNamePattern="auth"
```

### Frontend Tests
```bash
cd client

# Run all tests
npm test

# Run tests with coverage
npm run test:coverage

# Run tests in CI mode
CI=true npm test
```

## 📚 API Documentation

### Authentication Endpoints
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `POST /api/auth/logout` - Logout user
- `GET /api/auth/me` - Get current user
- `PUT /api/auth/profile` - Update user profile
- `PUT /api/auth/password` - Change password
- `POST /api/auth/refresh` - Refresh token

### Animal Endpoints
- `GET /api/animals` - Get all animals (with pagination, search, filters)
- `GET /api/animals/:id` - Get animal by ID
- `POST /api/animals` - Create new animal
- `PUT /api/animals/:id` - Update animal
- `DELETE /api/animals/:id` - Delete animal
- `GET /api/animals/owner/:ownerId` - Get animals by owner
- `GET /api/animals/stats` - Get animal statistics

### Owner Endpoints
- `GET /api/owners` - Get all owners (with pagination, search)
- `GET /api/owners/:id` - Get owner by ID
- `POST /api/owners` - Create new owner
- `PUT /api/owners/:id` - Update owner
- `DELETE /api/owners/:id` - Delete owner
- `GET /api/owners/search` - Search owners
- `GET /api/owners/stats` - Get owner statistics

## 🏗 Project Structure

```
animal-clinic/
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/    # Reusable components
│   │   ├── pages/         # Page components
│   │   ├── store/         # Redux store and slices
│   │   ├── services/      # API services
│   │   ├── types/         # TypeScript type definitions
│   │   └── utils/         # Utility functions
│   └── public/            # Static assets
├── server/                # Node.js backend
│   ├── src/
│   │   ├── controllers/   # Route controllers
│   │   ├── models/        # Database models
│   │   ├── routes/        # API routes
│   │   ├── middleware/    # Custom middleware
│   │   ├── config/        # Configuration files
│   │   ├── utils/         # Utility functions
│   │   └── tests/         # Test files
│   └── uploads/           # File uploads
├── docker/                # Docker configuration
├── .github/               # GitHub Actions workflows
└── docs/                  # Documentation
```

## 🔧 Development Guidelines

### Code Quality
- TypeScript strict mode enabled
- ESLint with Airbnb configuration
- Prettier for code formatting
- Husky for git hooks
- Jest for testing

### Git Workflow
1. Create feature branch from main
2. Make changes with descriptive commits
3. Run tests and linting
4. Create pull request
5. Code review and merge

### Database Migrations
```bash
# Create new migration
npx sequelize-cli migration:generate --name create-new-table

# Run migrations
npm run migrate

# Undo last migration
npm run migrate:undo
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Setup for Contributors

1. **Install dependencies:**
```bash
npm run install:all
```

2. **Run development environment:**
```bash
npm run dev
```

3. **Run tests:**
```bash
npm run test:all
```

4. **Check code quality:**
```bash
npm run lint:all
npm run type-check:all
```

## 📊 Performance

### Optimization Features
- Database query optimization with proper indexing
- Redis caching for frequently accessed data
- Image compression for uploaded photos
- Code splitting and lazy loading
- Memoization for expensive operations

### Monitoring
- Winston logging with different levels
- Error tracking and reporting
- Performance metrics collection
- Health check endpoints

## 🔒 Security

### Security Features
- JWT token authentication with secure headers
- Password hashing with bcrypt (12 rounds)
- Request validation with Joi
- CORS configuration
- Rate limiting
- SQL injection prevention
- XSS protection with helmet

### Best Practices
- Environment variables for sensitive data
- Secure cookie settings
- Input sanitization
- Error message sanitization
- Regular security dependency updates

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- 📧 Email: support@animalclinic.com
- 🐛 Issues: [GitHub Issues](https://github.com/your-repo/issues)
- 📖 Documentation: [Wiki](https://github.com/your-repo/wiki)

## 🎯 Roadmap

### Phase 1 (Current)
- ✅ Basic CRUD operations
- ✅ Authentication system
- ✅ Docker deployment
- ✅ Testing framework

### Phase 2 (Upcoming)
- 📅 Appointment scheduling
- 💰 Billing and invoicing
- 📱 Mobile app
- 🔔 Notification system

### Phase 3 (Future)
- 📊 Advanced analytics
- 🤖 AI-powered recommendations
- 🌐 Multi-clinic support
- 📋 Electronic health records

## 🙏 Acknowledgments

- Ant Design team for the beautiful UI components
- Node.js and React communities
- All contributors and testers

---

**Built with ❤️ for animal care professionals**