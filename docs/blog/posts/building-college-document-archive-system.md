---
date: 2026-01-07
description: Building a College Document Management System from idea to production with Python, Flask, PostgreSQL, and Docker.
tags:
  - python
  - flask
  - postgresql
  - docker
  - project-journey
author: arthurcc
title: Building a College Document Archive System: A Journey from Idea to Production
---

# Building a College Document Archive System: A Journey from Idea to Production

*January 2026*

---

## The Problem

I needed a document management system for a college to organize, track, and search administrative documents. The requirements were simple:

- Upload and categorize documents
- Search across content and metadata
- Track activity with audit logs
- Simple admin interface
- No complex user management (single admin)

What started as a "simple Flask app" evolved into a complete production-ready system with modern tooling, containerization, and cloud deployment support.

---

## The Stack

| Component | Technology |
|-----------|------------|
| Backend | Python 3.13 + Flask 3.1.2 |
| Database | PostgreSQL 17.7 |
| ORM | SQLAlchemy 2.0 + Flask-SQLAlchemy |
| Auth | Flask-Login |
| Cache | Redis 7.4.7 |
| Frontend | Jinja2 + Custom CSS (Dark Theme) |
| Container | Docker + Docker Compose |

---

## Key Features

1. **Document Management**
   - Upload with auto-filename title detection
   - Category organization (Admissions, Finance, HR, Academics)
   - Academic period tracking (Fall/Spring/Summer by year)
   - Tags for flexible labeling
   - Automatic folder organization

2. **Search**
   - Full-text search across titles, content, descriptions
   - PostgreSQL-powered search

3. **Admin Features**
   - Statistics dashboard
   - Audit logging for all actions
   - REST API for integrations
   - Trash/restore functionality

---

## Design Evolution

### Phase 1: Bootstrap Defaults

Started with Bootstrap 5, vanilla styling, light theme. Functional but generic.

### Phase 2: Custom Dark Theme

Midway through, I decided to create a distinctive look:

- **Fonts**: Space Grotesk (display) + Spectral (body)
- **Colors**: Deep black (#0a0a0a) with orange accent (#ff4d00)
- **Animations**: Smooth transitions, hover effects
- **Layout**: Fixed sidebar with responsive design

The result is a modern, professional interface that stands out from typical Bootstrap apps.

---

## Challenges & Solutions

### Challenge 1: PostgreSQL Version Mismatch

When upgrading from PostgreSQL 15 to 17, the Docker container failed to start due to incompatible data directory.

**Solution**: 
- Removed old volumes with `docker compose down -v`
- Fresh database initialization
- Documented the issue for future reference

### Challenge 2: Python 3.14 Compatibility

Attempted to use Python 3.14 (latest), but many packages (psycopg2-binary, Pillow) lacked pre-built wheels.

**Solution**:
- Downgraded to Python 3.13 (stable, all packages supported)
- All dependencies work seamlessly

### Challenge 3: GitHub Codespaces 1-Click Experience

Initial devcontainer required Docker-in-Docker, which isn't enabled by default in Codespaces.

**Solution**:
- Switched from PostgreSQL to SQLite for development
- Removed Docker dependency from devcontainer
- Added auto-start Flask command
- True 1-click experience achieved

---

## Deployment Options Explored

| Option | Pros | Cons |
|--------|------|------|
| **Local (ngrok)** | Free, quick | Exposes laptop, data usage |
| **GitHub Codespaces** | Cloud VM, 60hrs free | Requires internet |
| **Railway** | Full Docker, managed DB | $5/month after trial |
| **Render** | Good free tier | Sleeps after 15min inactivity |

Final choice: **GitHub Codespaces** for demos and development, with option to deploy to Railway for production.

---

## File Structure

```
archive-system/
├── app/
│   ├── admin/          # Dashboard, stats, logs
│   ├── api/            # REST API endpoints
│   ├── auth/           # Login/logout
│   ├── documents/      # CRUD, upload, download
│   ├── search/         # Full-text search
│   ├── templates/      # Jinja2 HTML templates
│   └── static/         # CSS, JS
├── scripts/
│   ├── init-db.py      # Database setup
│   └── seed-docs.py    # Generate test data
├── .devcontainer/      # GitHub Codespaces config
├── docker-compose.yml
├── Dockerfile
├── requirements.txt
└── README.md
```

---

## GitHub Integration

The project is now hosted at: **https://github.com/arthiccc/archive-system**

Features:
- **"Open in GitHub Codespaces"** badge for 1-click try
- Complete README with setup instructions
- Devcontainer configuration for cloud development
- Clean git history with meaningful commits

---

## Lessons Learned

1. **Start simple, iterate fast** - Don't over-engineer early
2. **Containerization first** - Docker from day one saved time
3. **Design matters** - A distinctive UI makes projects memorable
4. **Test deployment early** - Found issues before they became problems
5. **Document everything** - README and comments help future you

---

## Future Improvements

- [ ] Add bulk upload functionality
- [ ] Document versioning
- [ ] Email notifications
- [ ] Multi-user support with roles
- [ ] Deploy to production (Railway/Render)

---

## Source Code

**https://github.com/arthiccc/archive-system**

Try it live: [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/arthiccc/archive-system)

---

*Built with Python, Flask, PostgreSQL, Docker, and ❤️*
