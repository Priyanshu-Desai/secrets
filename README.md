# Secrets

An Express + EJS web app where users can register, log in, and share anonymous secrets.  
Authentication supports both local username/password and Google OAuth (Passport.js), with user data stored in MongoDB.

## Features

- User registration and login with `passport-local-mongoose`
- Google sign-in with `passport-google-oauth20`
- Session-based authentication with `express-session`
- Submit a secret after logging in
- Public secrets feed showing submitted secrets from all users

## Tech Stack

- Node.js + Express
- EJS templates
- MongoDB + Mongoose
- Passport.js (local + Google OAuth 2.0)

## Prerequisites

- Node.js (LTS recommended)
- npm
- MongoDB running locally on default port (`mongodb://localhost:27017`)
- Google OAuth credentials (for Google login)

## Setup

1. Install dependencies:
   ```bash
   npm install
   ```
2. Create a `.env` file in the project root:
   ```env
   CLIENT_ID=your_google_oauth_client_id
   CLIENT_SECRET=your_google_oauth_client_secret
   ```
3. In Google Cloud Console, add this authorized redirect URI:
   ```text
   http://localhost:5000/auth/google/secrets
   ```

## Run

```bash
npm start
```

The app runs on:

```text
http://localhost:5000
```

## Project Structure

```text
.
├── server.js
├── public/
│   └── css/
└── views/
    ├── partials/
    ├── home.ejs
    ├── login.ejs
    ├── register.ejs
    ├── secrets.ejs
    └── submit.ejs
```

## Main Routes

- `GET /` – landing page
- `GET /register`, `POST /register` – local registration
- `GET /login`, `POST /login` – local login
- `GET /auth/google` – start Google auth
- `GET /auth/google/secrets` – Google auth callback
- `GET /secrets` – view submitted secrets
- `GET /submit`, `POST /submit` – submit a secret (authenticated users)
- `GET /logout` – log out

## Notes

- The app currently connects to a local MongoDB database named `UserDB`.
- Environment variables are required for Google login.
