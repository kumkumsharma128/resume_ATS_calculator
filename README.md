# AI-Powered Resume & ATS Evaluator

A full-stack MERN web application that analyzes PDF resumes against a target job description using the Google Gemini API. It provides an ATS-style score, job-match percentage, strengths, weaknesses, missing keywords, and actionable recommendations.

## Features

- PDF resume upload (maximum 5 MB)
- AI-powered resume analysis with Google Gemini
- ATS-style overall score and job-match percentage
- Strengths, weaknesses, missing keywords, and recommendations
- JWT-based user authentication
- Password hashing with bcryptjs
- User-specific evaluation history stored in MongoDB
- React/Vite responsive dashboard

## Tech Stack

- **Frontend:** React, Vite, Axios, Lucide React, CSS
- **Backend:** Node.js, Express
- **Database:** MongoDB, Mongoose
- **AI:** Google Gemini API (`@google/genai`)
- **Authentication:** JWT, bcryptjs
- **File Processing:** Multer, pdf-parse

## Project Structure

```text
resume_analyzer-main/
├── client/
│   ├── public/
│   ├── src/
│   │   ├── App.jsx
│   │   ├── Auth.jsx
│   │   ├── HistoryDrawer.jsx
│   │   ├── api.js
│   │   └── ...
│   ├── package.json
│   └── vite.config.js
├── server/
│   ├── middleware/
│   │   └── auth.js
│   ├── models/
│   │   ├── User.js
│   │   └── ResumeAnalysis.js
│   ├── package.json
│   └── server.js
├── .gitignore
└── README.md
```

## Environment Variables

Create a `.env` file inside the `server` folder:

```env
MONGO_URI=your_mongodb_connection_string
GEMINI_API_KEY=your_gemini_api_key
JWT_SECRET=your_long_random_secret
PORT=5000
```

Do **not** commit `.env` or API keys to GitHub.

## Run Locally

### 1. Start the backend

```bash
cd server
npm install
npm start
```

The backend runs on `http://localhost:5000`.

### 2. Start the frontend

Open another terminal:

```bash
cd client
npm install
npm run dev
```

Vite will show the local frontend URL in the terminal.

## Production Build

Build the frontend with:

```bash
cd client
npm run build
```

The Express server is configured to serve the generated `client/dist` folder when deployed together with the backend.

## Notes

- The application accepts PDF resumes only.
- Each authenticated user can access only their own analysis history.
- Gemini is used to generate the structured resume evaluation.
