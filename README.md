# Tenerife Café – Website Application

A modern, high-performance React application built with TypeScript, Tailwind CSS, and Vite for **Tenerife Café** (Jail Road, Main Gulberg, Lahore).

---

## Why did opening `index.html` directly result in a white screen?

Modern React applications use **TypeScript (`.tsx`)**, **ES Modules (`import/export`)**, and **Vite**. 
When you double-click `index.html` directly in your file explorer (`file:///C:/.../index.html`):
1. **Browsers cannot execute raw `.tsx` files directly** without a build tool like Vite to compile them into JavaScript.
2. **CORS Security**: Browsers block local file module imports when accessed via `file://`.
3. **Paths**: Root-relative paths like `/src/main.tsx` resolve to the drive's root folder rather than your project folder.

---

## 🚀 How to Run Locally in 3 Simple Steps

### Prerequisites
Make sure you have **Node.js** (version 18 or higher) installed on your computer.
- Download Node.js from: [https://nodejs.org/](https://nodejs.org/)

### 1. Open Terminal in the Project Folder
Open your terminal (Command Prompt, PowerShell, or macOS Terminal) and navigate to this folder:
```bash
cd path/to/this-project-folder
```

### 2. Install Project Dependencies
Run this command once to install React, Tailwind, and Vite:
```bash
npm install
```

### 3. Start the Development Server
Run:
```bash
npm run dev
```

You will see output like:
```text
  VITE v8.3.0  ready in 240 ms

  ➜  Local:   http://localhost:3000/
  ➜  Network: http://192.168.x.x:3000/
```
Now open **`http://localhost:3000`** in your browser!

---

## 📦 How to Build for Production & Plain HTML/CSS/JS

To produce optimized, production-ready static files:
```bash
npm run build
```
This generates a **`dist/`** folder containing compiled, standard HTML, CSS, JavaScript, and images that can be hosted on any web server.

To preview that production build locally:
```bash
npm run preview
```

---

## 🌐 How to Deploy for Free

### Option 0: Deploy on GitHub Pages (Fixed for White Screen)

A dedicated GitHub Actions workflow (`.github/workflows/deploy.yml`) and relative base path (`base: './'`) have been configured for you.

#### Step-by-Step Fix on GitHub:
1. Push your updated code to your GitHub repository:
   ```bash
   git add .
   git commit -m "Configure GitHub Pages automated build"
   git push
   ```
2. Go to your repository on GitHub.com and click **Settings**.
3. In the left sidebar, click **Pages**.
4. Under **Build and deployment > Source**, change the dropdown from *"Deploy from a branch"* to **"GitHub Actions"**.
5. Go to the **Actions** tab at the top of your GitHub repository. You will see the **Deploy Tenerife Cafe to GitHub Pages** workflow running.
6. Once the green checkmark appears (usually ~45 seconds), your website will be live without the white screen!

---

### Option 1: Deploy on Vercel (Recommended - Fastest)
1. Push this folder to a GitHub repository or download [Vercel CLI](https://vercel.com/download):
   ```bash
   npx vercel
   ```
2. Or connect your GitHub repo on [Vercel.com](https://vercel.com).
3. Vercel automatically detects Vite:
   - **Framework Preset:** Vite
   - **Build Command:** `npm run build`
   - **Output Directory:** `dist`
4. Click **Deploy** — your live website URL will be ready in under 1 minute!

### Option 2: Deploy on Netlify
1. Go to [Netlify.com](https://www.netlify.com/).
2. Run `npm run build` on your computer.
3. Drag and drop the generated **`dist`** folder directly into the Netlify Dashboard (Netlify Drop).
4. Your site will be live immediately with a free SSL certificate!

### Option 3: Deploy on Firebase Hosting
1. Install Firebase tools:
   ```bash
   npm install -g firebase-tools
   firebase login
   firebase init hosting
   ```
2. Set public directory to **`dist`**.
3. Configure as single-page app: **Yes**.
4. Run:
   ```bash
   npm run build
   firebase deploy
   ```

---

## 🖼️ How to Change or Add Images

All website photos can be changed using one of the three easy methods below:

### Method 1: The Quickest Way (Replace Existing Image Files)
Inside the project folder, open **`src/assets/images/`**. You will see:
- `hero_tenerife_dining_1790765123450.jpg` → The main hero & restaurant interior background
- `dish_moroccan_chicken_1790765143053.jpg` → The savory mains / chicken dishes
- `dish_chocolate_heaven_1790765158438.jpg` → The Chocolate Heaven & patisserie desserts
- `dish_cocktails_mojito_1790765174329.jpg` → The Kiwi Mojito & signature mocktails

Simply replace these files with your own `.jpg` files using the same file names, and the website will automatically update!

---

### Method 2: Add New Photos via the `public/` Folder (Recommended)
1. Create or open the **`public/images/`** directory in your project root.
2. Put any image files there, for example: `steak.jpg`, `interior.jpg`, `coffee.jpg`.
3. In **`src/data/restaurantData.ts`**, update the `image` field for any dish:
   ```typescript
   {
     id: "steak-1",
     name: "The King's Cut Beef Steak",
     image: "/images/steak.jpg", // <-- points to public/images/steak.jpg
     ...
   }
   ```
4. In **`src/components/Hero.tsx`**, update the hero image source:
   ```tsx
   <img src="/images/interior.jpg" alt="Tenerife Dining" ... />
   ```

---

### Method 3: Use Web Image URLs
You can also use external image URLs directly in `src/data/restaurantData.ts` or component files:
```typescript
image: "https://your-domain.com/path-to-image.jpg"
```

---

## 🛠 Available Scripts

- `npm run dev`: Starts local Vite dev server with hot reload.
- `npm run build`: Compiles TypeScript and creates optimized production assets in `dist/`.
- `npm run preview`: Previews the production build locally.
- `npm run lint`: Checks for TypeScript errors with `tsc --noEmit`.
