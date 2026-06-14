# 📝 Blog App

A full-stack blogging platform with role-based access control, built with **React** and **Express.js**.

## 🌐 Live Demo

| Service  | URL |
|----------|-----|
| Frontend | Deployed on **Vercel** |
| Backend  | Deployed on **Render** |

---

## ✨ Features

- **User Registration & Login** — secure authentication with JWT (HTTP-only cookies)
- **Role-Based Access** — three roles: `USER`, `AUTHOR`, `ADMIN`
  - **User** — browse articles, post comments
  - **Author** — write, edit, and manage their own articles
  - **Admin** — manage users, enable / disable accounts
- **Article Management** — full CRUD for articles with categories & comments
- **Image Uploads** — profile pictures & article images via Cloudinary + Multer
- **Protected Routes** — client-side route guards based on user role

---

## 🛠 Tech Stack

### Frontend
| Technology | Purpose |
|------------|---------|
| React 19 | UI library |
| React Router 7 | Client-side routing |
| Zustand | Global state management |
| Axios | HTTP client |
| React Hook Form | Form handling & validation |
| React Hot Toast | Toast notifications |
| Tailwind CSS 4 | Styling |
| Vite 8 | Build tool & dev server |

### Backend
| Technology | Purpose |
|------------|---------|
| Express 5 | Web framework |
| Mongoose 9 | MongoDB ODM |
| JSON Web Token | Authentication |
| bcryptjs | Password hashing |
| Cloudinary | Cloud image storage |
| Multer | File upload middleware |
| cookie-parser | HTTP-only cookie handling |
| dotenv | Environment variable management |

### Database
- **MongoDB Atlas** (cloud-hosted)

---

## 📁 Project Structure

```
blog-app/
├── blog-app-backend/
│   ├── APIs/
│   │   ├── AdminAPI.js       # Admin routes (user management)
│   │   ├── AuthorAPI.js      # Author routes (article CRUD)
│   │   ├── CommonAPI.js      # Auth routes (register, login, logout)
│   │   └── UserAPI.js        # User routes (profile, comments)
│   ├── config/               # Cloudinary & other config
│   ├── middlewares/
│   │   └── verifyToken.js    # JWT verification middleware
│   ├── models/
│   │   ├── ArticleModel.js   # Article & Comment schemas
│   │   └── UserModel.js      # User schema
│   ├── server.js             # App entry point
│   ├── render.yaml           # Render deployment config
│   └── .env                  # Environment variables (not committed)
│
├── blog-app-frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Header.jsx          # Navigation bar
│   │   │   ├── Home.jsx            # Landing page
│   │   │   ├── Register.jsx        # User registration
│   │   │   ├── Login.jsx           # User login
│   │   │   ├── UserProfile.jsx     # User dashboard
│   │   │   ├── AuthorProfile.jsx   # Author dashboard
│   │   │   ├── AuthorArticles.jsx  # Author's article list
│   │   │   ├── WriteArticles.jsx   # Create new article
│   │   │   ├── EditArticle.jsx     # Edit existing article
│   │   │   ├── ArticleByID.jsx     # Single article view
│   │   │   ├── ProtectedRoute.jsx  # Role-based route guard
│   │   │   └── Unauthorized.jsx    # 403 page
│   │   ├── store/            # Zustand state stores
│   │   ├── styles/           # Custom stylesheets
│   │   ├── axiosConfig.js    # Centralized Axios instance
│   │   └── App.jsx           # Router configuration
│   ├── vercel.json           # Vercel deployment config
│   └── vite.config.js        # Vite configuration
│
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** ≥ 18
- **npm** ≥ 9
- A **MongoDB Atlas** cluster (or local MongoDB instance)
- A **Cloudinary** account (for image uploads)

### 1. Clone the repository

```bash
git clone https://github.com/MedipallyRajasri-06/BlogApp.git
cd blog-app
```

### 2. Backend setup

```bash
cd blog-app-backend
npm install
```

Create a `.env` file in `blog-app-backend/`:

```env
PORT=4000
DB_URL=mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/BlogApp
SECRET_KEY=your_jwt_secret_key
FRONTEND_URL=http://localhost:5173
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

Start the server:

```bash
npm start
```

### 3. Frontend setup

```bash
cd blog-app-frontend
npm install
npm run dev
```

The app will be available at **http://localhost:5173**.

---

## 📡 API Endpoints

### Auth (`/auth`)
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/auth/register` | Register a new user |
| POST | `/auth/login` | Login & receive JWT cookie |
| POST | `/auth/logout` | Clear auth cookie |

### User (`/user-api`)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/user-api/articles` | Get all articles |
| POST | `/user-api/comment` | Add a comment to an article |

### Author (`/author-api`)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/author-api/articles` | Get author's articles |
| POST | `/author-api/article` | Create a new article |
| PUT | `/author-api/article` | Update an article |
| DELETE | `/author-api/article/:id` | Soft-delete an article |

### Admin (`/admin-api`)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/admin-api/users` | Get all users |
| PUT | `/admin-api/user/toggle` | Enable / disable a user account |

---

## 🚢 Deployment

| Layer | Platform | Config File |
|-------|----------|-------------|
| Frontend | Vercel | `vercel.json` |
| Backend | Render | `render.yaml` |

> Set the same environment variables listed above in each platform's dashboard.

Blog App
A full-stack blog application with role-based access for readers, authors, and admins. Users can register, log in, read articles, and comment. Authors can create, edit, delete, and restore their own articles. Admins can view registered users and block or unblock user accounts.

Tech Stack
#Frontend:

React 19
Vite
React Router
Zustand
Axios
React Hook Form
React Hot Toast
Tailwind CSS
#Backend:

Node.js
Express 5
MongoDB with Mongoose
JWT authentication
bcryptjs password hashing
cookie-parser
multer
Cloudinary
CORS
Features
User registration with optional profile image upload
Login and logout using HTTP-only JWT cookies
Role-based protected routes
Reader dashboard for browsing articles
Article detail page with comments
Users can add and delete their own comments
Author dashboard
Authors can write new articles
Authors can edit their own articles
Authors can soft-delete and restore their own articles
Admin dashboard for user management
Admins can block and unblock users/authors
Active article filtering for public article lists
Cloudinary image upload support for profile images
User Roles
USER : Read articles, view article details, add comments, and delete own comments.
AUTHOR : Create, view, edit, delete, and restore own articles.
ADMIN : View users/authors and block or unblock accounts.
Registration currently allows USER and AUTHOR. Admin users must be created separately in the database or through a seed/manual process.

Frontend Routes
/: Home page. Public access.
/register: Register page. Public access.
/login: Login page. Public access.
/articles: Discover all active articles. Authenticated users.
/article/:id: Read a single article and its comments. Authenticated users.
/user-profile: User profile/dashboard. Requires USER.
/author-profile: Author dashboard. Requires AUTHOR.
/author-profile/articles: Author's articles. Requires AUTHOR.
/author-profile/write-article: Create article page. Requires AUTHOR.
/edit-article: Edit article page. Used in the author article flow.
/admin-profile: Admin dashboard. Requires ADMIN.
/unauthorized: Unauthorized access page. Public access.
Backend API Endpoints
Base URL locally:

http://localhost:5000
Current deployed backend used in frontend API calls:

https://blogapp-twid.onrender.com
Auth Routes
Mounted at /auth.

POST /auth/users: Register a user or author. Public access.
POST /auth/login: Log in and set the JWT cookie. Public access.
GET /auth/logout: Clear the JWT cookie. Authenticated access.
GET /auth/check-auth: Check the current authenticated user. Requires USER, AUTHOR, or ADMIN.
PUT /auth/password: Change password. Requires USER, AUTHOR, or ADMIN.
User Routes
Mounted at /user.

GET /user/articles: Get all active articles. Requires USER, AUTHOR, or ADMIN.
GET /user/article/:articleId: Get a single article by ID. Requires USER, AUTHOR, or ADMIN.
PUT /user/articles: Add a comment to an article. Requires USER.
DELETE /user/article/:articleId/comment/:commentId: Delete own comment. Requires USER.
PUT /user/password: Change password. Requires USER, AUTHOR, or ADMIN.
Author Routes
Mounted at /author.

POST /author/article: Create a new article. Requires AUTHOR.
GET /author/articles: Get the logged-in author's articles. Requires AUTHOR.
GET /author/article/:id: Get one owned article. Requires AUTHOR.
PUT /author/articles: Edit an owned article. Requires AUTHOR.
PATCH /author/articles: Soft-delete or restore an owned article. Requires AUTHOR.
Admin Routes
Mounted at /admin.

GET /admin/users: Get all users and authors. Requires ADMIN.
GET /admin/article: Get all articles. Requires ADMIN.
PUT /admin/user/:id: Block a user or author. Requires ADMIN.
PUT /admin/user-unblock/:id: Unblock a user or author. Requires ADMIN.
Environment Variables
Create a .env file inside backend_blog.

Note: Several frontend components currently call the deployed Render backend URL directly. To make local development fully configurable, replace those hard-coded URLs with BACKEND_URL from src/utils/config.js.

Installation and Setup
1. Clone or open the project
cd "Week-7 Assignment"
2. Install backend dependencies
cd backend_blog
npm install
3. Install frontend dependencies
cd ../frontend_blog
npm install
4. Configure environment variables
Add the backend .env values listed above. Make sure MongoDB and Cloudinary credentials are valid.

5. Start the backend
The backend package currently has no dev or start script. Run it directly:

cd backend_blog
node server.js
The server starts on:

http://localhost:5000
6. Start the frontend
cd frontend_blog
npm run dev
The Vite app usually starts on:

http://localhost:5173
Available Scripts
Frontend
npm run dev -- Start Vite development server npm run build -- Build production frontend npm run preview -- Preview production build npm run lint -- Run ESLint

Backend
node server.js --Start Express server npm test --Placeholder test script

Authentication Flow
A user registers with a role of USER or AUTHOR.
Passwords are hashed using bcrypt before storing in MongoDB.
On login, the backend creates a JWT containing user ID, email, role, name, and profile image URL.
The JWT is stored in an HTTP-only cookie named token.
Protected backend routes use verifyToken(...) middleware to validate the cookie and check the allowed role.
The frontend stores the current user state using Zustand persistence.
Image Uploads
Profile images are uploaded during registration using multer memory storage and Cloudinary.

Accepted image types:

JPG
PNG
Maximum file size:

text: 2 MB

Uploaded images are stored in the Cloudinary folder

Deployment Notes
The frontend includes a vercel.json, so it is prepared for Vercel deployment.
The backend also includes a vercel.json, but the frontend currently points to a Render backend URL.
Backend CORS allows:
http://localhost:5173
blog-app-sigma-puce.vercel.app
other vercel.app origins
Cookies are configured with:
httpOnly: true
secure: true
sameSite: "none"
This is suitable for deployed HTTPS frontend/backend communication. For local HTTP-only development, cookie settings may need adjustment.

Suggested Future Enhancements
Add backend scripts such as "start": "node server.js" and "dev": "nodemon server.js".
Replace hard-coded frontend API URLs with BACKEND_URL.
Add an admin creation/seed script.
Add article image uploads.
Add search, category filters, and pagination.
Add automated tests for authentication, article CRUD, and admin actions.
