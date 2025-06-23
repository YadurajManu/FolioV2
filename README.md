<!-- GitAds-Verify: ENB2TFOVJ7Q5BPBRUDQKV6L25NY2KTIK -->
# FolioV2 - Personal Portfolio Website

## Description
This is Yaduraj Singh's personal portfolio website, designed to showcase projects, skills, and experience. The website is built with a strong focus on interactivity and animation to provide an engaging user experience.

## Technology Stack

**Frontend:**
*   **Vite**: Fast frontend build tool for development and bundling.
*   **JavaScript (ES6+)**: Core programming language for interactivity and dynamic content.
*   **SCSS**: CSS preprocessor for advanced, modular, and maintainable styling.
*   **GSAP (GreenSock Animation Platform)**: Used for sophisticated animations, transitions, and scroll-triggered effects.
*   **Locomotive Scroll**: Provides smooth scrolling effects across the site.
*   **Three.js**: Powers the dynamic, dithered wave background animation for a unique visual experience.
*   **Vercel Analytics & Speed Insights**: For performance monitoring and user behavior tracking.

**Backend (Contact Form):**
*   **Node.js**: JavaScript runtime for the server.
*   **Express.js**: Minimalist web framework for building the API endpoint for the contact form.
*   **Nodemailer**: Module to send emails from the server (e.g., contact form submissions and auto-replies).

*(Note on Frontend Dependencies: The `package.json` may list React and related Three.js-React libraries. These were part of an earlier exploration and are not currently used in the active version of the site. The primary 3D background is achieved with vanilla Three.js.)*

## Code Structure Overview
The project is organized into two main parts: the frontend source code in the `src` directory and the backend server code in the `server` directory.

**`src` (Frontend):**
*   `src/fonts`: Holds custom font files used in the project.
*   `src/index.html`: The main HTML entry point for the application.
*   `src/js`: Contains all JavaScript files, further organized into:
    *   `classes`: Base classes, such as `Component.js`, for creating reusable UI elements.
    *   `components`: Specific UI components like `Time.js` (displays current time), custom cursor logic, etc.
    *   `pages`: Page-specific JavaScript logic. Currently, `Home.js` is minimal as most logic is component-based or in `index.js`.
    *   `utils`: Utility functions used across the project (e.g., DOM manipulation helpers, math functions).
    *   `index.js`: The main JavaScript entry point. It initializes animations, components (like the Three.js background manager), and global event listeners.
*   `src/public`: Stores static assets that are copied directly to the build output, such as the resume PDF and favicon.
*   `src/scss`: Contains all SCSS stylesheets, structured as follows:
    *   `base`: Global styles, CSS resets, and font face definitions.
    *   `components`: Styles specific to individual UI components (e.g., buttons, cards, custom cursor).
    *   `pages`: Styles specific to particular pages (though most styling is component or section-based).
    *   `sections`: Styles for distinct sections of the website (e.g., hero, about, projects, contact).
    *   `shared`: Shared styling elements like typography, links, and layout utilities.
    *   `utils`: SCSS variables (colors, fonts, breakpoints), mixins, and functions.
    *   `index.scss`: The main SCSS file that imports all other SCSS partials.

**`server` (Backend):**
*   `server/server.js`: The main file for the Express.js backend, handling contact form submissions.
*   `server/package.json`: Defines dependencies for the backend server (Express, Nodemailer, etc.).
*   `server/vercel.json`: Configuration for deploying the backend as a serverless function on Vercel.
*   `server/.env` (not committed, example below): Stores sensitive credentials for the email service.


## Backend (Contact Form)

The backend for this portfolio is a simple Node.js application using the Express.js framework. Its primary responsibility is to handle submissions from the contact form.

**Functionality:**
*   Receives form data (name, email, project type, budget, message) via a POST request to the `/api/contact` endpoint.
*   Validates the incoming data.
*   Uses Nodemailer to send an email containing the form details to your specified email address.
*   Sends an automated confirmation email to the user who submitted the form.
*   Includes security measures like CORS, Helmet, and rate limiting.

**Environment Variables:**
The backend server requires certain environment variables to be set for it to function correctly, especially for the email service. These should be stored in a `.env` file within the `server` directory.

Create a file named `.env` in the `server/` directory and add the following variables:

```env
# Server Configuration
PORT=3001 # Optional: Port the local backend server will run on, defaults to 3001

# Nodemailer Email Configuration (e.g., for Gmail)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587 # Or 465 if using SSL
EMAIL_SECURE=false # true for port 465, false for others (like 587 with STARTTLS)
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-gmail-app-password # Or regular password if less secure apps allowed (not recommended)
EMAIL_TO=recipient-email@example.com # Email address to receive contact form submissions
EMAIL_FROM="Your Name/Portfolio" <your-email@gmail.com> # Sender for auto-replies, often same as EMAIL_USER

# CORS Configuration
# Comma-separated list of allowed frontend origins
# Example: ALLOWED_ORIGINS=http://localhost:3000,https://yourdomain.com
ALLOWED_ORIGINS=http://localhost:3000,https://yaduraj.me
```

**Important Notes for Email Configuration:**
*   If using Gmail, you'll likely need to generate an "App Password" for `EMAIL_PASS` if you have 2-Step Verification enabled on your Google account. Using your regular Gmail password may not work and is less secure.
*   `EMAIL_TO` is the address where you will receive the messages from the contact form.
*   `EMAIL_FROM` is the "From" address that will appear on the auto-reply emails sent to users. It's good practice to have this be an address you control.
*   Ensure `ALLOWED_ORIGINS` includes the URLs where your frontend is hosted (both local development and production).

## Key Features
*   **Interactive Animations**: Extensive use of GSAP for various text reveal effects, scroll-triggered animations, hover effects, and UI element transitions.
*   **Smooth Scrolling**: Implemented using Locomotive Scroll to provide a fluid and modern scrolling experience.
*   **Custom Cursor**: A dynamic custom mouse cursor that changes based on context, enhancing user interaction.
*   **Dynamic Three.js Background**: A sophisticated dithered wave background animation powered by Three.js, providing a unique and interactive visual element that subtly changes with section transitions.
*   **Responsive Design**: The website is designed to adapt to different screen sizes using SCSS media queries and JavaScript adjustments for optimal viewing on desktops, tablets, and mobile devices.
*   **Modular Structure**: Both JavaScript (with classes and components) and SCSS (with partials and a BEM-like methodology) are organized modularly for better maintainability and scalability.
*   **Backend Contact Form**: Node.js/Express backend with Nodemailer for reliable contact form submissions and auto-replies, including validation and security features.

## Local Development Setup

To set up and run this project locally, you'll need Node.js and npm installed.

**1. Frontend Setup (Vite + Client-side Code)**

   a. **Navigate to Project Root**:
      Open your terminal and `cd` into the project's root directory.

   b. **Install Dependencies**:
      Run the following command to install frontend dependencies listed in `package.json`:
      ```bash
      npm install
      ```

   c. **Run Development Server**:
      To start the Vite development server (usually available at `http://localhost:3000`):
      ```bash
      npm run dev
      ```
      This command looks at `vite.config.js` which specifies `src` as the root. Vite will serve `src/index.html` and handle hot module replacement.

   d. **Build for Production**:
      To create a production-ready build of the frontend in the `dist/` folder:
      ```bash
      npm run build
      ```

   e. **Preview Production Build**:
      To locally preview the production build from the `dist/` folder:
      ```bash
      npm run preview
      ```

**2. Backend Setup (Express Contact Form Server)**

   a. **Navigate to Server Directory**:
      From the project root, navigate to the backend server's directory:
      ```bash
      cd server
      ```

   b. **Install Dependencies**:
      Run the following command to install backend dependencies listed in `server/package.json`:
      ```bash
      npm install
      ```

   c. **Configure Environment Variables**:
      Create a `.env` file inside the `server` directory. Copy the structure from the example provided in the "Backend (Contact Form)" section above and fill in your actual credentials, especially for the email service.

      Example `server/.env`:
      ```env
      PORT=3001
      EMAIL_HOST=smtp.example.com
      EMAIL_PORT=587
      EMAIL_SECURE=false
      EMAIL_USER=your-email@example.com
      EMAIL_PASS=your-email-password
      EMAIL_TO=recipient-email@example.com
      EMAIL_FROM="Your Name" <your-email@example.com>
      ALLOWED_ORIGINS=http://localhost:3000,https://your-production-domain.com
      ```
      *Refer to the "Backend (Contact Form)" section for detailed explanations of these variables.*

   d. **Run Backend Development Server**:
      To start the backend server (usually on `http://localhost:3001` if `PORT` is set to 3001 in `.env`):
      ```bash
      npm run dev
      ```
      This uses `nodemon` for automatic restarts on file changes. Alternatively, you can run `npm start` for a standard Node execution.

   e. **Testing the Backend**:
      The backend server has a health check endpoint at `/api/health` and a test endpoint at `/api/test`. The contact form endpoint is `POST /api/contact`.

**Running Both Servers Concurrently:**
For full local development, you'll typically run both the frontend Vite server and the backend Express server in separate terminal windows. The frontend (e.g., at `http://localhost:3000`) will make API calls to the backend (e.g., at `http://localhost:3001/api/contact`).

## Deployment

This project is configured for deployment on **Vercel**.

**Frontend Deployment:**
*   The frontend is built using `npm run build`, which creates static HTML, CSS, and JavaScript assets in the `dist/` directory.
*   Vercel automatically detects Vite projects and deploys the contents of the `dist/` directory as a static site.

**Backend Deployment:**
*   The backend server located in the `server/` directory is designed to be deployed as a Vercel Serverless Function.
*   The `server/vercel.json` file configures this, mapping requests to `/api/*` (e.g., `/api/contact`) to the `server/server.js` Express application.
*   Environment variables (as defined in the "Backend (Contact Form)" section) must be configured in the Vercel project settings for the serverless function to work correctly in production (Project Settings -> Environment Variables).

**Custom Domain:**
*   The `CNAME` file in the root directory contains `yaduraj.me`, indicating that this custom domain is likely configured for the Vercel deployment.

**Note on GitHub Actions Workflow:**
*   The repository contains a GitHub Actions workflow file at `.github/workflows/jekyll-gh-pages.yml`. This workflow is configured for building and deploying a Jekyll site to GitHub Pages.
*   Given that the current project uses Vite for the frontend and an Express server for the backend, this Jekyll workflow appears to be outdated or a remnant from a previous version of the portfolio.
*   It is recommended to review this workflow. If it's no longer in use for the live deployment (which is likely handled by Vercel), consider removing it to avoid confusion.

## GitAds Sponsored
[![Sponsored by GitAds](https://gitads.dev/v1/ad-serve?source=yadurajmanu/foliov2@github)](https://gitads.dev/v1/ad-track?source=yadurajmanu/foliov2@github)


