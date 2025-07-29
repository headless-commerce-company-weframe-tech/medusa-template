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
## 🧪 Running Locally (Using `yarn`)

### 🔧 Backend (Medusa)

```bash
cd medusa-template
yarn install        # install dependencies
yarn build          # optional if using TypeScript
yarn start          # starts the Medusa server
```

This runs the Medusa backend on: [http://localhost:9000](http://localhost:9000)

---

### 🖥️ Frontend (Storefront)

```bash
cd medusa-storefront
yarn install        # install dependencies
yarn build          # builds the frontend
yarn start          # starts the Next.js server
```

This runs the Storefront on: [http://localhost:3000](http://localhost:3000)

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
yarn run seed

# Build Storefront
cd ../medusa-storefront
yarn run build
```

---

## 💬 Need Help?

- [Medusa Docs](https://docs.medusajs.com)
- [Railway Docs](https://docs.railway.app)

---


