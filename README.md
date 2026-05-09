# React Job App

A modern job listing web application built with **React**, **Vite**, **React Router**, and **Tailwind CSS**. Browse, create, edit, and manage job postings with a clean, responsive interface.

## Features

- 📋 **Browse Jobs** – View all available job listings with filtering and search
- 🔍 **Job Details** – Click on any job to see full details, company info, and contact information
- ➕ **Add Jobs** – Post new job listings with automatic ID assignment
- ✏️ **Edit Jobs** – Modify existing job postings
- 🗑️ **Delete Jobs** – Remove job listings from the platform
- 🎨 **Responsive Design** – Fully responsive UI built with Tailwind CSS
- ⚡ **Fast Development** – Hot Module Replacement (HMR) with Vite
- 🔄 **RESTful API** – JSON Server backend with real-time data synchronization

## Tech Stack

- **Frontend**: React 19.2, React Router 7.15
- **Build Tool**: Vite 8.0
- **Styling**: Tailwind CSS 4.2
- **Backend**: JSON Server 0.17 (mock REST API)
- **Icons**: React Icons 5.6
- **Loading State**: React Spinners 0.17
- **Linting**: ESLint 10.2
- **Process Manager**: Concurrently 9.2

## Getting Started

### Prerequisites

- Node.js 18+ and npm

### Installation

1. Clone the repository:
```bash
git clone <repo-url>
cd react-job-app
```

2. Install dependencies:
```bash
npm install
```

### Running the Application

Start both the frontend (Vite) and backend (JSON Server) with a single command:

```bash
npm start
```

This runs:
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:3333

#### Alternative Commands

- **Frontend only** (dev mode): `npm run dev`
- **Backend API only**: `npm run server`
- **Build for production**: `npm run build`
- **Preview production build**: `npm run preview`
- **Lint code**: `npm run lint`

## Project Structure

```
src/
├── pages/                 # Page components
│   ├── HomePage.jsx
│   ├── JobsPage.jsx
│   ├── JobPage.jsx        # Job detail page
│   ├── AddJobPage.jsx     # Create new job
│   ├── EditJobPage.jsx    # Edit job
│   └── NotFoundPage.jsx
├── components/            # Reusable components
│   ├── Navbar.jsx
│   ├── Hero.jsx
│   ├── JobListings.jsx
│   ├── JobListing.jsx
│   ├── Card.jsx
│   ├── HomeCards.jsx
│   ├── ViewAllJobs.jsx
│   └── Spinner.jsx
├── layouts/               # Layout wrappers
│   └── MainLayout.jsx
├── jobs.json              # Mock database
├── App.jsx                # Main app with routes
├── main.jsx               # Entry point
└── index.css              # Global styles
```

## API Endpoints

The backend runs on `http://localhost:3333`:

- `GET /jobs` – Fetch all jobs
- `GET /jobs/:id` – Fetch a single job by ID
- `POST /jobs` – Create a new job
- `PUT /jobs/:id` – Update a job
- `DELETE /jobs/:id` – Delete a job

## Job Data Structure

```json
{
  "id": "1",
  "title": "Senior React Developer",
  "type": "Full-Time",
  "description": "Job description here...",
  "location": "Boston, MA",
  "salary": "$70K - $80K",
  "company": {
    "name": "Company Name",
    "description": "Company description...",
    "contactEmail": "contact@example.com",
    "contactPhone": "555-555-5555"
  }
}
```

## Key Features Implementation

### Dynamic ID Assignment

When adding a new job, the app automatically assigns the next available ID based on existing jobs:

```javascript
const nextId = String(
  jobs.reduce((highestId, job) => Math.max(highestId, Number(job.id)), 0) + 1
);
```

### Responsive Layout

The job detail page uses Tailwind's grid and order utilities to display company info on the left side on medium+ screens:

```jsx
<div className="grid grid-cols-1 md:grid-cols-70/30 w-full gap-6">
  <main className="md:order-last">
  <aside className="md:order-first">
```

### Concurrent Process Management

The app uses `concurrently` to run both Vite and JSON Server in parallel with automatic shutdown (`-k` flag) if either process fails:

```json
"start": "concurrently -k \"npm run server\" \"npm run dev\""
```

## Development

### Code Quality

Run ESLint to check for code issues:

```bash
npm run lint
```

### Making Changes

- Edit React components in `src/pages/` and `src/components/`
- Modify styles with Tailwind CSS classes
- Add new routes in `src/App.jsx`
- Update job data in `src/jobs.json` or through the API

## Deployment

Build for production:

```bash
npm run build
```

Output will be in the `dist/` directory. Deploy this folder to any static host (Netlify, Vercel, GitHub Pages, etc.).

Note: For production, replace JSON Server with a proper backend (Node/Express, Python/Flask, etc.).

## License

MIT
