# 🐳 DevOps Learning Project: Docker, Nginx & MERN

A comprehensive learning project demonstrating containerization, reverse proxy configuration, and CI/CD pipeline automation with a full-stack MERN application.

## 📋 Project Overview

This repository showcases a practical implementation of DevOps concepts through a complete MERN (MongoDB, Express, React, Node.js) application. The project was built specifically to master:

- **Docker** containerization and orchestration
- **Nginx** reverse proxy configuration
- **GitLab CI/CD** pipeline automation
- **Full-stack development** with modern technologies

The MERN application serves as a real-world example to understand how these DevOps tools and practices work together in a production-like environment.

### Project Purpose

This is an educational project created to gain hands-on experience with:
- Building and deploying containerized applications
- Setting up CI/CD pipelines for automated testing and deployment
- Configuring web servers for production environments
- Managing multiple services with Docker Compose

---

## 🎯 What You'll Learn in This Project

### 1. **Docker Fundamentals**
- ✅ Writing efficient Dockerfiles for Node.js applications
- ✅ Creating separate containers for frontend, backend, and database
- ✅ Docker image optimization and layer caching
- ✅ Container networking and communication
- ✅ Volume management for persistent data
- ✅ Multi-stage builds for reduced image sizes

### 2. **Docker Compose Orchestration**
- ✅ Defining multi-container applications
- ✅ Service dependencies and startup order
- ✅ Environment variable management
- ✅ Port mapping and network configuration
- ✅ Development and production compose files

### 3. **Nginx Reverse Proxy**
- ✅ Nginx as a reverse proxy for Node.js backend
- ✅ Load balancing multiple backend instances
- ✅ SSL/TLS configuration
- ✅ Static file serving and caching
- ✅ Request routing and URL rewriting
- ✅ Gzip compression for optimized delivery

### 4. **GitLab CI/CD Pipeline**
- ✅ `.gitlab-ci.yml` configuration and structure
- ✅ Building Docker images automatically
- ✅ Pushing images to registries
- ✅ Automated testing in pipeline
- ✅ Deployment stages (dev, staging, production)
- ✅ Environment variables and secrets management

### 5. **Full-Stack MERN Development**
- ✅ React + Vite + TypeScript frontend
- ✅ Express + TypeScript backend
- ✅ MongoDB Atlas integration
- ✅ RESTful API design
- ✅ Modern development practices

---

## 🏗️ Project Architecture

```
devops/
├── client/                 # React + Vite frontend
│   ├── src/
│   ├── Dockerfile
│   ├── nginx.conf         # Frontend Nginx config
│   └── package.json
├── server/                 # Express + Node.js backend
│   ├── src/
│   ├── Dockerfile
│   └── package.json
├── docker-compose.yml      # Multi-container orchestration
├── .gitlab-ci.yml         # GitLab CI/CD pipeline
└── README.md
```

---

## 🚀 Quick Start

### Prerequisites
- Docker and Docker Compose installed
- Node.js 16+ (for local development)
- MongoDB Atlas account (for database)
- GitLab account (for CI/CD pipeline)

### Local Development Setup

#### 1. Backend Setup
```bash
cd server
npm install
# Update .env with your MongoDB connection string
npm run dev
```

#### 2. Frontend Setup
```bash
cd client
npm install
# Update .env with backend API URL
npm run dev
```

**Backend Environment (`server/.env`)**
```env
PORT=5000
MONGODB_URI=mongodb+srv://YOUR_USERNAME:YOUR_PASSWORD@YOUR_CLUSTER.mongodb.net/devops_demo?retryWrites=true&w=majority
```

**Frontend Environment (`client/.env`)**
```env
VITE_API_URL=http://localhost:5000
```

### Docker Compose Deployment

Run the entire stack with a single command:

```bash
docker-compose up -d
```

Access the application:
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:5000
- **Nginx Reverse Proxy**: http://localhost:80

---

## 📦 Application Features

### API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health` | Health check for Docker/Compose verification |
| GET | `/api/products` | Retrieve all products |
| POST | `/api/products` | Create a new product |
| DELETE | `/api/products/:id` | Delete a product by ID |

### Sample Product Payload

```json
{
  "name": "Black Hoodie",
  "price": 1499,
  "category": "Clothing"
}
```

### Frontend Features

- 📱 Responsive React UI with Vite
- ✏️ Add new products
- 📋 View all products
- 🗑️ Delete products
- ⚡ Fast development with Hot Module Replacement (HMR)

### Backend Features

- 🔧 Express REST API
- 📊 MongoDB Atlas integration
- 🔍 Product CRUD operations
- 💪 TypeScript for type safety
- 🏥 Health check endpoint

---

## 🐳 Docker Configuration

### Building Images

```bash
# Build backend image
docker build -t devops-backend ./server

# Build frontend image
docker build -t devops-frontend ./client
```

### Key Dockerfile Practices Demonstrated

✅ **Multi-stage builds** - Reduces final image size
✅ **Layer optimization** - Leverages Docker cache
✅ **Security** - Non-root user execution
✅ **Environment variables** - Build-time and runtime configuration
✅ **Health checks** - Container health verification

---

## 🌐 Nginx Configuration

### Reverse Proxy Setup

The Nginx configuration demonstrates:

- **Backend Proxy**: Routes `/api` requests to the Express backend
- **Frontend Serving**: Serves static React build files
- **SPA Routing**: Rewrites all unmapped routes to `index.html`
- **Gzip Compression**: Optimizes asset delivery
- **Caching Headers**: Improves performance

### Example Nginx Config Structure

```nginx
upstream backend {
    server backend:5000;
}

server {
    listen 80;
    
    # Static frontend
    location / {
        root /usr/share/nginx/html;
        try_files $uri /index.html;
    }
    
    # API proxy
    location /api {
        proxy_pass http://backend;
    }
}
```

---

## 🔄 GitLab CI/CD Pipeline

### Pipeline Stages

The `.gitlab-ci.yml` includes:

1. **Build Stage** 🔨
   - Build Docker images for frontend and backend
   - Run linting and tests

2. **Test Stage** ✅
   - Unit tests for backend
   - Integration tests
   - Component tests for frontend

3. **Push Stage** 📤
   - Push images to Docker Registry
   - Tag with commit SHA and `latest`

4. **Deploy Stage** 🚀
   - Deploy to development environment
   - Deploy to staging (manual trigger)
   - Deploy to production (manual trigger)

### Running CI/CD Locally

```bash
# Install GitLab Runner
# Verify pipeline locally
gitlab-runner exec docker build
```

---

## 📚 Learning Outcomes

After working through this project, you'll understand:

### Docker
- How to containerize Node.js and React applications
- Dockerfile best practices and optimization
- Docker networking and communication
- Volume management strategies

### Nginx
- Reverse proxy configuration for production
- Load balancing capabilities
- Static file serving and caching strategies
- SSL/TLS implementation

### CI/CD
- Pipeline design and stages
- Automated testing and building
- Container registry integration
- Automated deployment workflows

### MERN Stack
- Full-stack TypeScript development
- MongoDB Atlas for cloud database
- Express API development
- React with Vite for optimal development experience

---

## 🛠️ Technology Stack

| Component | Technology | Version |
|-----------|-----------|---------|
| **Frontend** | React + Vite + TypeScript | Latest |
| **Backend** | Express + Node.js + TypeScript | 16+ |
| **Database** | MongoDB Atlas | Latest |
| **Containerization** | Docker | Latest |
| **Orchestration** | Docker Compose | Latest |
| **Web Server** | Nginx | Latest |
| **CI/CD** | GitLab CI | Latest |

---

## 📖 Useful Commands

### Docker Commands

```bash
# Build images
docker-compose build

# Start services
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs -f

# Execute command in container
docker-compose exec backend npm run dev
```

### Development Commands

```bash
# Backend
cd server && npm run dev

# Frontend
cd client && npm run dev

# Build for production
npm run build
```

---

## 🎓 Resources & References

- [Docker Documentation](https://docs.docker.com/)
- [Docker Compose Guide](https://docs.docker.com/compose/)
- [Nginx Documentation](https://nginx.org/en/docs/)
- [GitLab CI/CD](https://docs.gitlab.com/ee/ci/)
- [MERN Stack Guide](https://www.mongodb.com/languages/mern-stack)

---

## 🔗 Repository Links

- **Repository**: https://github.com/Sathwik-Devireddy/devops
- **Issues & Discussion**: Open an issue for questions or suggestions

---

## 📝 Notes for Future Learning

- Implement database migrations strategy
- Add Redis caching layer
- Implement comprehensive logging (ELK stack)
- Setup monitoring and alerting
- Implement auto-scaling policies
- Add security scanning in CI/CD pipeline

---

## 📄 License

This project is open source and available for educational purposes.

---

**Happy Learning! 🚀 Keep building and deploying!**
