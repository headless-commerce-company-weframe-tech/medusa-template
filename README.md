# 🧱 Medusa + Storefront Starter (Local + Railway)

This project contains a full monorepo setup for a headless eCommerce stack using:

- 🛍️ Medusa v2 (Headless Commerce Backend)
- 🖥️ Storefront (Next.js or similar)
- ⚡ Railway deployment
- 🐘 PostgreSQL on NeonDB or Railway

---

## 📁 Project Structure

```
medusa-template/         → Medusa backend (v2)
medusa-storefront/       → Frontend Storefront (e.g. Next.js)
```

---

## 🚀 Running Locally

### 1. Clone the Repo

```bash
git clone https://github.com/youruser/medusa-ecommerce-template.git
cd medusa-ecommerce-template
```

### 2. Install Dependencies (from root)

```bash
pnpm install
```

### 3. Setup `.env` files

#### 🔧 Backend: `medusa-template/.env`

```env
NODE_ENV=development
DATABASE_URL=postgresql://<user>:<pass>@<host>/<db>?sslmode=require
JWT_SECRET=supersecret
COOKIE_SECRET=supersecret
CORS=http://localhost:3000
ADMIN_CORS=http://localhost:7000
```

#### 🔧 Frontend: `medusa-storefront/.env.local`

```env
NEXT_PUBLIC_MEDUSA_BACKEND_URL=http://localhost:9000
```

> ⚠️ Replace with your actual DB connection string (e.g. from NeonDB or Railway).

---

### 4. Run Backend (Medusa)

```bash
cd medusa-template
pnpm dev
```

By default runs at: [http://localhost:9000](http://localhost:9000)

---

### 5. Run Frontend (Storefront)

```bash
cd ../medusa-storefront
pnpm dev
```

By default runs at: [http://localhost:3000](http://localhost:3000)

---

## ☁️ Deployment on Railway

You’ll deploy **two Railway projects** — one for backend, one for frontend.

---

### 🧱 1. Medusa Backend

#### ➕ Steps

1. Go to [Railway](https://railway.app)
2. Create a new project
3. Select **GitHub repo**, and point to the folder `medusa-template`
4. Railway will detect `railway.toml` inside `medusa-template`
5. Add these environment variables under "Variables":

```env
DATABASE_URL=postgresql://<railway-user>:<railway-pass>@<host>/<db>?sslmode=require
JWT_SECRET=supersecret
COOKIE_SECRET=supersecret
CORS=https://<your-storefront>.railway.app
ADMIN_CORS=https://<your-admin-panel>.railway.app
```

---

### 🌐 2. Storefront

#### ➕ Steps

1. Create another Railway project
2. Connect to the same GitHub repo, but choose folder `medusa-storefront`
3. Railway reads `railway.toml` from `medusa-storefront`
4. Add the following env variable:

```env
NEXT_PUBLIC_MEDUSA_BACKEND_URL=https://<your-backend>.railway.app
```

---

## 🧪 Sample Admin Login

After seeding (or manually creating a user):

- **Email**: `admin@medusajs.com`
- **Password**: `supersecret`

---

## 🧰 Useful Commands

```bash
# Seed Medusa data (optional)
cd medusa-template
pnpm medusa seed

# Build Storefront
cd ../medusa-storefront
pnpm build
```

---

## 💬 Need Help?

- [Medusa Docs](https://docs.medusajs.com)
- [Railway Docs](https://docs.railway.app)

---
