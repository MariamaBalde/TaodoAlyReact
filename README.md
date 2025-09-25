# TodoAly - Todo List Application

TodoAly is a full-stack todo list application built with React (frontend) and Node.js/TypeScript (backend) with MySQL database using Prisma ORM. The application allows users to create, manage, and track their tasks with features like user authentication, task permissions, voice messages, and image uploads.

## Features

- **User Authentication**: Login and registration system with JWT tokens
- **Task Management**: Create, read, update, and delete tasks
- **Task Status**: Track tasks with statuses (A_FAIRE, EN_COURS, TERMINEE)
- **User Roles**: Support for different user roles (ADMIN, ETUDIANT, PROFESSEUR)
- **Task Permissions**: Grant permissions to other users to edit specific tasks
- **Voice Messages**: Record and attach voice messages to tasks
- **Image Uploads**: Attach images to tasks
- **Automated Tasks**: Automatic task completion based on time settings
- **Notifications**: Notification system for task updates
- **Responsive Design**: Modern UI built with React and Tailwind CSS

## Prerequisites

Before running this application, make sure you have the following installed:

- **Node.js** (version 16 or higher)
- **npm** (comes with Node.js)
- **MySQL** (version 8.0 or higher)
- **Git** (for cloning the repository)

## Installation

### 1. Clone the Repository

```bash
git clone <repository-url>
cd TodoAly
```

### 2. Backend Setup

Navigate to the backend directory:

```bash
cd projetAly/Live2
```

Install dependencies:

```bash
npm install
```

### 3. Database Setup

Make sure MySQL is running on your system. Create a database for the application.

Update the `.env` file in the `projetAly/Live2` directory with your database credentials:

```env
DATABASE_URL="mysql://username:password@localhost:3306/your_database_name"
PORT=3000
TOKEN=your_secret_token_here
```

Run database migrations:

```bash
npm run migrate
```

Generate Prisma client:

```bash
npm run generate
```

### 4. Frontend Setup

Navigate to the frontend directory:

```bash
cd ../todolist
```

Install dependencies:

```bash
npm install
```

## Running the Application

### Start the Backend

From the `projetAly/Live2` directory:

```bash
npm run dev
```

The backend will start on `http://localhost:3000`

### Start the Frontend

From the `projetAly/todolist` directory:

```bash
npm run dev
```

The frontend will start on `http://localhost:5173` (default Vite port)

## Usage

### First Time Setup

1. **Register a new account**: Visit the frontend application and click on registration
2. **Login**: Use your credentials to log in
3. **Create tasks**: Start adding your todo items

### Using the Application

#### Task Management
- **Add Task**: Click the "Add Task" button and fill in the title and description
- **Edit Task**: Click the edit button on any task to modify it
- **Delete Task**: Click the delete button to remove a task
- **Change Status**: Use the status dropdown to change task status
- **Mark Complete**: Click the checkbox to toggle task completion

#### Advanced Features
- **Voice Messages**: Click the microphone icon to record voice messages
- **Image Upload**: Click the image icon to attach images to tasks
- **Permissions**: Grant other users permission to edit your tasks
- **Automated Tasks**: Set tasks to auto-complete at specific times

#### User Management
- **User Roles**: Different roles have different permissions
- **Profile Management**: Update your user information

## API Endpoints

### Authentication
- `POST /auth/login` - User login
- `POST /auth/register` - User registration

### Tasks
- `GET /taches` - Get all tasks for authenticated user
- `POST /taches` - Create a new task
- `PUT /taches/:id` - Update a task
- `DELETE /taches/:id` - Delete a task

### Users
- `GET /users` - Get all users
- `POST /users` - Create a new user
- `PUT /users/:id` - Update a user
- `DELETE /users/:id` - Delete a user

### Permissions
- `GET /permissions` - Get permissions
- `POST /permissions` - Grant permissions
- `DELETE /permissions/:id` - Revoke permissions

### Notifications
- `GET /notifications` - Get user notifications
- `POST /notifications` - Create notification

## Project Structure

```
TodoAly/
├── projetAly/
│   ├── Live2/                 # Backend (Node.js + TypeScript)
│   │   ├── src/
│   │   │   ├── controller/    # Route controllers
│   │   │   ├── middleware/    # Authentication middleware
│   │   │   ├── repository/    # Data access layer
│   │   │   ├── route/         # API routes
│   │   │   ├── service/       # Business logic
│   │   │   ├── Validation/    # Input validation
│   │   │   └── index.ts       # Application entry point
│   │   ├── prisma/            # Database schema and migrations
│   │   ├── uploads/           # File uploads directory
│   │   └── .env               # Environment variables
│   └── todolist/              # Frontend (React + Vite)
│       ├── src/
│       │   ├── composant/     # React components
│       │   ├── hooks/         # Custom React hooks
│       │   ├── validation/    # Form validation
│       │   └── assets/        # Static assets
│       ├── public/            # Public assets
│       └── db.json            # Mock data (for development)
└── README.md                  # This file
```

## Technologies Used

### Backend
- **Node.js** - JavaScript runtime
- **TypeScript** - Typed JavaScript
- **Express.js** - Web framework
- **Prisma** - ORM for database management
- **MySQL** - Relational database
- **JWT** - JSON Web Tokens for authentication
- **Multer** - File upload handling
- **Zod** - Schema validation
- **CORS** - Cross-origin resource sharing

### Frontend
- **React** - UI library
- **Vite** - Build tool and development server
- **React Router** - Client-side routing
- **Tailwind CSS** - Utility-first CSS framework
- **Lucide React** - Icon library
- **JWT Decode** - JWT token decoding

## Development

### Backend Development Scripts
- `npm run dev` - Start development server with hot reload
- `npm run build` - Build for production
- `npm run start` - Start production server
- `npm run migrate` - Run database migrations
- `npm run generate` - Generate Prisma client

### Frontend Development Scripts
- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint
- `npm run server:api` - Start JSON server (for development)

## Troubleshooting

### Common Issues

1. **Database Connection Error**
   - Ensure MySQL is running
   - Check DATABASE_URL in .env file
   - Verify database credentials

2. **Port Already in Use**
   - Change PORT in .env file
   - Kill process using the port: `lsof -ti:3000 | xargs kill -9`

3. **CORS Errors**
   - Backend is configured to allow all origins in development
   - Check if backend is running on correct port

4. **Authentication Issues**
   - Clear localStorage in browser
   - Check TOKEN in .env file
   - Verify JWT token expiration

### File Upload Issues
- Ensure `uploads/` directory exists and is writable
- Check file size limits in multer configuration

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run tests
5. Submit a pull request

## License

This project is licensed under the ISC License.

## Support

For support or questions, please contact the development team.