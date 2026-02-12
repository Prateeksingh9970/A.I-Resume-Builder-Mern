# Gemini Project Context: Resume Builder

This document provides a comprehensive overview of the Resume Builder project, its architecture, technology stack, and development conventions.

## Project Overview

The Resume Builder is a full-stack web application designed to help users create, manage, and share professional resumes. It leverages AI to enhance resume content and automate data entry from existing text.

### Main Technologies

- **Frontend:**
  - **Framework:** React 19 (Vite)
  - **State Management:** Redux Toolkit
  - **Styling:** Tailwind CSS
  - **Icons:** Lucide React
  - **Routing:** React Router DOM
  - **Notifications:** React Hot Toast
- **Backend:**
  - **Runtime:** Node.js
  - **Framework:** Express
  - **Database:** MongoDB (via Mongoose)
  - **Authentication:** JWT (JSON Web Tokens)
  - **AI Integration:** OpenAI API
  - **Image Hosting:** ImageKit
  - **File Uploads:** Multer

### Architecture

The project follows a client-server architecture with separate directories for each:

- `client/`: React frontend.
- `server/`: Node.js/Express backend.

## Building and Running

### Prerequisites

- Node.js (Latest LTS recommended)
- MongoDB (Local or Atlas)
- OpenAI API Key
- ImageKit Account (Public Key, Private Key, and URL Endpoint)

### Server Setup

1. Navigate to the `server` directory: `cd resume-builder/server`
2. Install dependencies: `npm install`
3. Create a `.env` file based on the following required variables:
   - `PORT`: Server port (default: 3000)
   - `MONGODB_URI`: MongoDB connection string
   - `JWT_SECRET`: Secret key for JWT signing
   - `OPENAI_API_KEY`: OpenAI API key
   - `OPENAI_MODEL`: OpenAI model name (e.g., `gpt-4o-mini`)
   - `IMAGEKIT_PUBLIC_KEY`: ImageKit public key
   - `IMAGEKIT_PRIVATE_KEY`: ImageKit private key
   - `IMAGEKIT_URL_ENDPOINT`: ImageKit URL endpoint
4. Start the server:
   - Development: `npm run server` (uses nodemon)
   - Production: `npm start`

### Client Setup

1. Navigate to the `client` directory: `cd resume-builder/client`
2. Install dependencies: `npm install`
3. Create a `.env` file with:
   - `VITE_API_URL`: Backend API URL (e.g., `http://localhost:3000`)
4. Start the development server: `npm run dev`
5. Build for production: `npm run build`

## Key Features

- **User Authentication:** Sign up/Login with JWT-based persistent sessions.
- **Dashboard:** Overview of all created resumes.
- **Interactive Builder:** Real-time resume editing with fields for personal info, experience, education, projects, and skills.
- **AI Tools:**
  - **Enhance Summary:** AI-powered refinement of professional summaries.
  - **Enhance Job Description:** AI-powered refinement of work experience details.
  - **Resume Import:** Extract structured data from raw resume text using OpenAI.
- **Templates:** Multiple resume templates (Classic, Modern, Minimal, etc.) with customizable accent colors.
- **Public Sharing:** Generate unique public links for sharing resumes.
- **Profile Image:** Upload and host profile pictures using ImageKit.

## Development Conventions

- **Module System:** Both client and server use ES Modules (`type: "module"` in `package.json`).
- **Styling:** Utility-first approach using Tailwind CSS.
- **State Management:** Use Redux Toolkit for global state (like user authentication). Local state is managed via React hooks.
- **API Calls:** Axios is used for HTTP requests. A pre-configured axios instance is available in `client/src/configs/api.js`.
- **Backend Structure:**
  - `controllers/`: Business logic.
  - `models/`: Mongoose schemas.
  - `routes/`: API endpoint definitions.
  - `middlewares/`: Authentication and other request processing.
  - `configs/`: External service configurations (DB, AI, ImageKit).
- **Naming:** CamelCase for functions and variables, PascalCase for React components.
- **Error Handling:** Centralized error handling in controllers with appropriate HTTP status codes.
