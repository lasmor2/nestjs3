# Project Name

A NestJS REST API with JWT authentication, user management, and bookmark functionality built with Prisma ORM and PostgreSQL.

## Features

- **Authentication & Authorization**: JWT-based authentication with Passport
- **User Management**: User registration, login, and profile updates
- **Bookmarks**: CRUD operations for user bookmarks
- **Database**: PostgreSQL with Prisma ORM
- **Validation**: Request validation using class-validator
- **Testing**: E2E tests with separate test database
- **Docker**: Containerized PostgreSQL databases for development and testing

## Tech Stack

- **Framework**: NestJS 11
- **Database**: PostgreSQL 13
- **ORM**: Prisma 7
- **Authentication**: JWT with Passport
- **Password Hashing**: Argon2
- **Validation**: class-validator & class-transformer
- **Testing**: Jest & Pactum
- **Containerization**: Docker Compose

## Prerequisites

- Node.js (v18 or higher)
- Docker & Docker Compose
- npm or yarn

## Installation

```bash
npm install
```

## Environment Setup

Create a `.env` file in the root directory:

```env
PORT=3001
DATABASE_URL="postgresql://username:yourPassword@localhost:5434/nest?schema=public"
JWT_SECRET="your-secret-key"
```

## Database Setup

### Development Database

```bash
# Start development database
npm run db:dev:up

# Run migrations
npm run prisma:dev:deploy

# Restart database (removes existing data)
npm run db:dev:restart
```

### Test Database

```bash
# Start test database
npm run db:test:up

# Run test migrations
npm run prisma:test:deploy

# Restart test database
npm run db:test:restart
```

## Running the Application

```bash
# Development mode
npm run start:dev

# Production mode
npm run build
npm run start:prod

# Debug mode
npm run start:debug
```

The API will be available at `http://localhost:3001`

## Testing

```bash
# Unit tests
npm test

# E2E tests (automatically sets up test database)
npm run test:e2e

# Test coverage
npm run test:cov

# Watch mode
npm run test:watch
```

## API Endpoints

### Authentication

- `POST /auth/signup` - Register new user
- `POST /auth/signin` - Login user

### Users

- `GET /users/me` - Get current user profile
- `PATCH /users` - Update user profile

### Bookmarks

- `GET /bookmarks` - Get all user bookmarks
- `GET /bookmarks/:id` - Get bookmark by ID
- `POST /bookmarks` - Create new bookmark
- `PATCH /bookmarks/:id` - Update bookmark
- `DELETE /bookmarks/:id` - Delete bookmark

## Project Structure

```
src/
├── auth/           # Authentication module (JWT, guards, strategies)
├── user/           # User management module
├── bookmark/       # Bookmark CRUD module
├── todo/           # Todo module
├── prisma/         # Prisma service module
├── app.module.ts   # Root application module
└── main.ts         # Application entry point

prisma/
├── migrations/     # Database migrations
└── schema.prisma   # Prisma schema definition
```

## Database Schema

### User

- id, email (unique), hash (password)
- firstName, lastName
- timestamps (createdAt, updatedAt)
- Relations: bookmarks[]

### Bookmark

- id, title, description, link
- userId (foreign key)
- timestamps (createdAt, updatedAt)

## Scripts

| Command                   | Description                              |
| ------------------------- | ---------------------------------------- |
| `npm run start:dev`       | Start development server with watch mode |
| `npm run build`           | Build production bundle                  |
| `npm run lint`            | Run ESLint                               |
| `npm run format`          | Format code with Prettier                |
| `npm run db:dev:restart`  | Reset development database               |
| `npm run db:test:restart` | Reset test database                      |
| `npm run test:e2e`        | Run E2E tests                            |
