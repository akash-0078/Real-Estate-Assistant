<div align="center">

# BuildEstate

### AI-Powered Real Estate Platform

[![React](https://img.shields.io/badge/React-18.3-61DAFB?style=for-the-badge&logo=react&logoColor=white)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.5-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)

[![Live Demo](https://img.shields.io/badge/Live_Demo-buildestate.vercel.app-4285F4?style=for-the-badge&logo=vercel&logoColor=white)](https://buildestate.vercel.app)
[![Backend API](https://img.shields.io/badge/Backend_API-Render-46E3B7?style=for-the-badge&logo=render&logoColor=white)](https://real-estate-website-backend-zfu7.onrender.com)

[![Stars](https://img.shields.io/github/stars/AAYUSH412/Real-Estate-Website?style=for-the-badge&logo=github&color=yellow)](https://github.com/AAYUSH412/Real-Estate-Website)
[![Forks](https://img.shields.io/github/forks/AAYUSH412/Real-Estate-Website?style=for-the-badge&logo=github&color=blue)](https://github.com/AAYUSH412/Real-Estate-Website)
[![License](https://img.shields.io/github/license/AAYUSH412/Real-Estate-Website?style=for-the-badge&color=green)](LICENSE)

</div>

---

A full-stack real estate platform with AI-powered property search, market analysis, appointment scheduling, and an admin dashboard. Built with React, Node.js, Express, and MongoDB.

---

## Features

- **Property Browsing** — Filter by type, price, availability, amenities with grid/list views
- **AI Property Hub** — GPT-4.1 powered search, market analysis, location trends (local only)
- **Appointment Scheduling** — Book property viewings as guest or registered user
- **User Authentication** — JWT-based sign up, sign in, forgot/reset password with email
- **Admin Dashboard** — Manage properties (CRUD + image upload), appointments, and analytics
- **Email Notifications** — Branded transactional emails via Brevo SMTP
- **Image Management** — Upload up to 4 images per property via ImageKit CDN
- **SEO Optimized** — Structured data, sitemap.xml, robots.txt, per-page meta tags

---

## Tech Stack

| Layer | Technologies |
|---|---|
| **Frontend** | React 18, TypeScript, Vite 6, Tailwind CSS v4, Framer Motion, React Router v7 |
| **Admin Panel** | React 18, Vite 6, Tailwind CSS v3, Chart.js, Lucide React |
| **Backend** | Node.js, Express.js, Mongoose, JWT, Multer, Nodemailer |
| **Database** | MongoDB Atlas |
| **AI Services** | GPT-4.1 (GitHub Models), Firecrawl (web scraping) |
| **Storage** | ImageKit CDN |
| **Deployment** | Vercel (frontend), Render (backend + admin) |

---

## Repository Structure

```
Real-Estate-Website/
├── frontend/          → User-facing website (React + TypeScript + Vite)
├── admin/             → Admin dashboard (React + Vite)
├── backend/           → REST API server (Node.js + Express)
└── .github/           → Issue templates, PR template, CODEOWNERS
```


## API Endpoints

### Authentication — `/api/users`

| Method | Endpoint | Description |
|---|---|---|
| POST | `/register` | Register new user |
| POST | `/login` | Login (returns JWT) |
| POST | `/admin` | Admin login |
| GET | `/me` | Get current user (JWT required) |
| POST | `/forgot` | Send password reset email |
| POST | `/reset/:token` | Reset password |

### Properties — `/api/products`

| Method | Endpoint | Description |
|---|---|---|
| GET | `/list` | List all properties |
| GET | `/single/:id` | Get property by ID |
| POST | `/add` | Add property with images (admin) |
| POST | `/update` | Update property (admin) |
| POST | `/remove` | Delete property (admin) |

### Appointments — `/api/appointments`

| Method | Endpoint | Description |
|---|---|---|
| POST | `/schedule` | Book viewing (guest) |
| POST | `/schedule/auth` | Book viewing (logged in) |
| GET | `/user` | Get appointments by email |
| PUT | `/cancel/:id` | Cancel appointment |
| GET | `/all` | All appointments (admin) |
| PUT | `/status` | Update status (admin) |
| PUT | `/update-meeting` | Add meeting link (admin) |

### Other

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/forms/submit` | Contact form submission |
| GET | `/api/admin/stats` | Dashboard statistics (admin) |
| POST | `/api/ai/search` | AI property search |
| GET | `/api/locations/:city/trends` | Location market trends |

---

## AI Property Hub

The AI Property Hub uses **GPT-4.1** (GitHub Models) and **Firecrawl** to provide:

- Smart natural-language property search
- AI-powered analysis with best value picks
- Location trends — appreciation rates and rental yields
- Investment tips and recommendations

> **Note:** The AI Hub is **disabled on the live Vercel deployment** to conserve API credits.
> Visiting `/ai-hub` on the live site shows instructions to clone and run locally.
> To enable it, set `VITE_ENABLE_AI_HUB=true` in `frontend/.env.local` and add
> `FIRECRAWL_API_KEY` and `GITHUB_MODELS_API_KEY` to `backend/.env.local`.

---

## Deployment

### Frontend → Vercel

1. Import repo in [Vercel](https://vercel.com)
2. Set **Root Directory** to `frontend`
3. Add env variable: `VITE_API_BASE_URL` = your Render backend URL
4. Do **not** set `VITE_ENABLE_AI_HUB` (AI Hub stays disabled in production)
5. Deploy

### Backend → Render

1. Create a **Web Service** on [Render](https://render.com)
2. Set **Root Directory** to `backend`
3. Build Command: `npm install` — Start Command: `npm start`
4. Add all env variables from `backend/.env.example`
5. Set `NODE_ENV=production` and `WEBSITE_URL` to your Vercel URL

### Admin Panel → Render

Same as backend, with **Root Directory** set to `admin` and env variable:
- `VITE_BACKEND_URL` = your Render backend URL

---

## Available Scripts

| Directory | Script | Description |
|---|---|---|
| `backend/` | `npm run dev` | Start with nodemon (auto-reload) |
| `backend/` | `npm start` | Start production server |
| `frontend/` | `npm run dev` | Start Vite dev server |
| `frontend/` | `npm run build` | Production build |
| `admin/` | `npm run dev` | Start Vite dev server |
| `admin/` | `npm run build` | Production build |

---

## Project Structure

<details>
<summary><strong>Frontend (frontend/)</strong></summary>

```
frontend/src/
├── components/
│   ├── ai-hub/            → AI Property Hub UI
│   ├── common/            → Navbar, Footer, SEO, PageTransition
│   ├── home/              → Homepage sections
│   ├── properties/        → Filter sidebar, property cards
│   ├── property-details/  → Gallery, amenities, booking form
│   ├── about/             → About page sections
│   └── contact/           → Contact page sections
├── contexts/              → AuthContext
├── hooks/                 → useSEO
├── pages/                 → All pages (lazy loaded)
├── services/              → api.ts (Axios client)
└── styles/
```

</details>

<details>
<summary><strong>Backend (backend/)</strong></summary>

```
backend/
├── config/         → MongoDB, ImageKit, Nodemailer, AI config
├── controller/     → Route handlers
├── middleware/     → Auth (JWT), Multer, stats tracking
├── models/         → Mongoose schemas
├── routes/         → Express route definitions
├── services/       → AI and Firecrawl services
├── uploads/        → Temp uploads (auto-created, gitignored)
├── server.js       → Entry point
└── email.js        → Branded email templates
```

</details>

<details>
<summary><strong>Admin Panel (admin/)</strong></summary>

```
admin/src/
├── components/     → Login, Navbar
├── config/         → Constants (property types, amenities)
├── contexts/       → AdminContext
└── pages/          → Dashboard, Add, List, Update, Appointments
```

</details>

---

## Contributing

Contributions are welcome! Please read the [Contributing Guide](CONTRIBUTING.md) first.

1. Fork the repository
2. Create a branch: `git checkout -b feature/your-feature`
3. Commit: `git commit -m "feat: add your feature"`
4. Push: `git push origin feature/your-feature`
5. Open a Pull Request

See also: [Code of Conduct](CODE_OF_CONDUCT.md) · [Security Policy](SECURITY.md)

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---
