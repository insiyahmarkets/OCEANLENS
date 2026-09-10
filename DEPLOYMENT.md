# OceanVision 3D - Public Deployment Guide

This document provides step-by-step instructions to deploy **OceanVision 3D** to **Vercel** or **Netlify** for public demonstration during the Smart India Hackathon (SIH 2026).

---

## 🚀 Option 1: Deploy to Vercel via GitHub (Recommended)

### Step 1: Push Project to GitHub
1. Open your terminal inside the project directory:
   ```bash
   cd C:\Users\Insiyah\.gemini\antigravity\scratch\oceanvision-3d
   ```
2. Initialize Git (if not already initialized) and commit all files:
   ```bash
   git init
   git add .
   git commit -m "OceanVision 3D global release"
   ```
3. Create a new repository on GitHub (e.g. `oceanvision-3d`) and push your code:
   ```bash
   git remote add origin https://github.com/YOUR_GITHUB_USERNAME/oceanvision-3d.git
   git branch -M main
   git push -u origin main
   ```

### Step 2: Connect Repository to Vercel
1. Go to [https://vercel.com/](https://vercel.com/) and sign in with your GitHub account.
2. Click **"Add New..."** → **"Project"**.
3. Select your `oceanvision-3d` repository from the list.
4. Vercel will automatically detect **Vite** configuration:
   - **Framework Preset**: `Vite`
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist`
5. Click **"Deploy"**.

Within ~60 seconds, Vercel will generate your live public URL, such as:
**`https://oceanvision-3d.vercel.app`**

---

## ⚡ Option 2: Deploy via Vercel CLI (Direct Command Line)

If you have Node.js installed, you can deploy directly from your local terminal using Vercel CLI:

1. Install Vercel CLI globally:
   ```bash
   npm install -g vercel
   ```
2. Run the deployment command inside the project directory:
   ```bash
   cd C:\Users\Insiyah\.gemini\antigravity\scratch\oceanvision-3d
   vercel
   ```
3. Follow the interactive prompts:
   - *Set up and deploy?* → `Y`
   - *Which scope?* → `Select your user account`
   - *Link to existing project?* → `N`
   - *What's your project's name?* → `oceanvision-3d`
   - *In which directory is your code located?* → `./`
   - *Want to modify build settings?* → `N`

4. For production deployment:
   ```bash
   vercel --prod
   ```

---

## 🌐 Option 3: Deploy to Netlify

1. Go to [https://www.netlify.com/](https://www.netlify.com/) and log in.
2. Click **"Add new site"** → **"Import an existing project"**.
3. Connect your GitHub repository.
4. Set Build Settings:
   - **Build Command**: `npm run build`
   - **Publish directory**: `dist`
5. Click **"Deploy site"**.

---

## 🛠 Project Build Verification

Before deploying, you can verify that the production bundle builds cleanly on your local machine:

```bash
npm run build
```

The output dist bundle will be created inside `./dist` ready for hosting!
