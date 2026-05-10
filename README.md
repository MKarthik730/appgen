# AppGen 🚀

**Config-driven full-stack application generator** — define your app with a single JSON config and get a fully functional backend + frontend, instantly.

```json
{
  "app": { "name": "Task Manager", "auth": { "enabled": true } },
  "database": { "tables": [{ "name": "tasks", "fields": [{ "name": "title", "type": "string" }] }] },
  "ui": [{ "type": "form", "api_binding": "create_task" }],
  "apis": [{ "path": "/tasks", "method": "GET", "action": "list", "table": "tasks" }]
}
```

---

## ✨ Features

- ⚡ **Dynamic Route Generation** — API endpoints created on-the-fly from config
- 🗄️ **Auto Database Models** — Sequelize models generated dynamically from JSON schema
- 🎨 **UI Renderers** — Form, Table, and Dashboard components rendered from config
- 🔐 **Authentication** — JWT-based auth with register/login flow
- 🌐 **i18n Support** — Multi-locale ready
- 📥 **Config Import** — Upload configs via JSON/CSV
- 🔔 **Notifications** — Built-in notification system
- 🐳 **Docker Compose** — One-command startup

## 🛠️ Tech Stack

### Backend
| Technology | Purpose |
|---|---|
| **Node.js** | Runtime |
| **Express** | Web framework |
| **TypeScript** | Language |
| **Sequelize** | ORM |
| **PostgreSQL** | Database |
| **JWT** | Authentication |
| **Multer** | File uploads |
| **bcrypt** | Password hashing |

### Frontend
| Technology | Purpose |
|---|---|
| **Next.js 14** | React framework |
| **React 18** | UI library |
| **TypeScript** | Language |
| **Tailwind CSS** | Styling |
| **Axios** | HTTP client |

### Infrastructure
| Technology | Purpose |
|---|---|
| **Docker** | Containerization |
| **Docker Compose** | Orchestration |

## 📁 Project Structure

```
├── backend/
│   ├── src/
│   │   ├── index.ts                  # Express app entry
│   │   ├── config-parser/            # Validates & normalises config
│   │   ├── route-factory/            # Dynamically creates routes
│   │   ├── schema-factory/           # Creates Sequelize models
│   │   ├── models/                   # User, ConfigStore models
│   │   ├── middleware/               # Auth middleware
│   │   └── routes/                   # Auth, Configs, Import, i18n, Notifications
│   ├── package.json
│   └── Dockerfile
├── frontend/
│   ├── app/
│   │   ├── layout.tsx
│   │   ├── page.tsx                  # Config upload/paste
│   │   └── app/[appId]/page.tsx      # Generated app
│   ├── components/
│   │   ├── renderers/                # Form, Table, Dashboard renderers
│   │   ├── ConfigUpload.tsx
│   │   └── AppRenderer.tsx
│   ├── lib/                          # API client, validators
│   ├── types/                        # TypeScript types
│   └── package.json
└── docker-compose.yml
```

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- Docker & Docker Compose (for PostgreSQL)
- npm

### 1. Clone & Install

```bash
git clone <repo-url>
cd appgen

# Install backend deps
cd backend && npm install

# Install frontend deps
cd ../frontend && npm install
```

### 2. Start Database

```bash
docker compose up db -d
```

### 3. Run Backend

```bash
cd backend
npm run dev
```

Server starts on `http://localhost:8000`.

### 4. Run Frontend

```bash
cd frontend
npm run dev
```

App starts on `http://localhost:3000`.

### Or Use Docker Compose (All Services)

```bash
docker compose up --build
```

## 📝 How It Works

1. **Define a config** — JSON with `app`, `ui`, `apis`, `database`, and `locale` sections
2. **Upload it** via the web UI or API
3. **Backend auto-generates**: Sequelize models for each `database.tables[]`, Express routes for each `apis[]`
4. **Frontend renders**: UI components (form, table, dashboard) based on your `ui[]` definitions

## 📄 License

MIT
