# 🚀 Deployment Guide: Aditya University Smart Library

This guide provides step-by-step instructions for deploying both the **Frontend** and the **Backend** of the Smart Library application.

---

## 🎨 Part 1: Deploying the Frontend on Vercel (Recommended)

Since the frontend consists of static `HTML`, `CSS`, `JS`, and asset files located inside the `frontend/` directory, **Vercel** is the fastest and most secure platform for hosting it.

### Step 1: Connect your GitHub Repository to Vercel
1. Go to [Vercel](https://vercel.com) and log in using your **GitHub** account.
2. Once logged in, click the **Add New...** button in the top right and select **Project**.
3. Under **Import Git Repository**, find your repository `AdityaUniversity` and click **Import**.

### Step 2: Configure Project Settings (CRITICAL)
Before clicking deploy, you must configure the **Root Directory** so Vercel knows to serve your static files from the `frontend/` folder:
1. In the **Configure Project** window, find the **Root Directory** setting.
2. Click **Edit** next to it, select the `frontend` folder, and click **Continue**.
3. **Keep the default settings** for Build and Development Settings (no build commands are needed for static HTML).

### Step 3: Click Deploy!
1. Click the **Deploy** button.
2. Vercel will build and launch your application in less than a minute!
3. You will receive a premium development URL (e.g., `https://aditya-university.vercel.app`).

> [!TIP]
> **Automatic Redeployments:** Every time you run `git push origin main` in the future, Vercel will automatically detect the changes and redeploy your website instantly!

---

## ⚡ Part 2: Deploying the Backend on Render (Already Configured)

Your frontend is currently pointing to a live Express backend hosted on **Render**:
`https://smartlibrary-h80l.onrender.com/api`

If you ever need to deploy your own backend instance on Render, follow these steps:

### Step 1: Create a Web Service on Render
1. Go to [Render](https://render.com) and log in with GitHub.
2. Click **New +** and select **Web Service**.
3. Connect your `AdityaUniversity` repository.

### Step 2: Configure the Build & Start Commands
* **Name:** `aditya-library-backend`
* **Environment:** `Node`
* **Region:** Choose the region closest to you.
* **Branch:** `main`
* **Root Directory:** Keep empty (root of the repo).
* **Build Command:** `npm install`
* **Start Command:** `node server.js`

### Step 3: Add Environment Variables
Click on the **Environment** tab on Render and add the variables from your `.env` file:
* `PORT` = `5002`
* `MONGO_URI` = *Your MongoDB Atlas Connection String*
* `JWT_SECRET` = *Your Secure Session Key*

### Step 4: Update API Base URL in Frontend
If you deploy your own backend, simply update the `API_BASE_URL` at the top of these three files to point to your new Render URL:
1. [index.html](file:///e:/SmartLibrary/frontend/index.html) (Line 470)
2. [studentdashboard.html](file:///e:/SmartLibrary/frontend/studentdashboard.html) (Line 1366)
3. [admindashboard.html](file:///e:/SmartLibrary/frontend/admindashboard.html) (Line 1203)
