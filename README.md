# SAVANNAH-FRONTEND
# 🏢 Savannah Property Management System - Frontend

[![React](https://img.shields.io/badge/React-18.3.1-61DAFB?logo=react)](https://reactjs.org/)
[![Vite](https://img.shields.io/badge/Vite-5.0.0-646CFF?logo=vite)](https://vitejs.dev/)
[![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3.4.0-06B6D4?logo=tailwindcss)](https://tailwindcss.com/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

## 📌 Overview

The **Savannah Property Management System Frontend** is a modern, responsive web application built with **React** and **Vite** that provides an intuitive interface for property managers, accountants, and tenants. It seamlessly integrates with the FastAPI backend to handle property management, rent collection, and M-Pesa payment processing.

> **Note:** This is the frontend repository. The backend FastAPI application can be found [here](https://github.com/Gittechie-111/SAVANNAH-BACKEND).

---

## ✨ Features

### 👑 Admin Dashboard
- **Overview Dashboard** – Real-time KPI cards with occupancy rates, revenue collection, and arrears tracking
- **Property Management** – View all properties with occupancy statistics
- **Transaction History** – Complete audit trail of all payments
- **Arrears Management** – Identify tenants with outstanding balances
- **Manual Payment Recording** – Record payments on behalf of tenants

### 👤 Tenant Portal
- **Personal Dashboard** – View unit information, rent amount, and payment history
- **M-Pesa Integration** – Pay rent directly via STK Push to your phone
- **Payment Status Tracking** – Real-time updates on payment processing
- **Transaction History** – View all your past payments

### 🔐 Authentication
- Secure login with JWT tokens
- User registration for new tenants
- Role-based access control (Admin, Accountant, Tenant)
- Password hashing and validation

### 📱 Responsive Design
- Fully responsive layout for desktop, tablet, and mobile devices
- Dark-themed modern UI with gradients and smooth animations
- Accessible components with proper contrast ratios

---

## 🛠️ Tech Stack

| Category | Technology |
|----------|------------|
| **Framework** | React 18.3.1 |
| **Build Tool** | Vite 5.0.0 |
| **Styling** | CSS-in-JS with inline styles |
| **HTTP Client** | Native Fetch API |
| **Authentication** | JWT (sessionStorage) |
| **Payment Integration** | M-Pesa Daraja API (via backend) |
| **Icons** | Emoji-based icons |
| **Fonts** | DM Sans, Playfair Display |

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ or higher
- npm 9+ or yarn
- Backend server running (see [SAVANNAH-BACKEND](https://github.com/Gittechie-111/SAVANNAH-BACKEND))

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Gittechie-111/SAVANNAH-FRONTEND.git
   cd SAVANNAH-FRONTEND

    Install dependencies
    bash

    npm install

    Set up environment variables
    Create a .env file in the root directory:
    env

    VITE_API_URL=http://localhost:8000

        For production, update this to your deployed backend URL.

    Start the development server
    bash

    npm run dev

    Open your browser
    Navigate to http://localhost:3000

📁 Project Structure
text

SAVANNAH-FRONTEND/
├── src/
│   ├── App.jsx                 # Main application component
│   ├── main.jsx                # Application entry point
│   ├── components/
│   │   └── MpesaPayment.jsx    # M-Pesa payment component
│   └── index.css               # Global styles
├── index.html                  # HTML template
├── package.json                # Dependencies and scripts
├── vite.config.js              # Vite configuration (with proxy)
├── .env                        # Environment variables (gitignored)
├── .env.example                # Example environment variables
└── README.md                   # This file

🔧 Configuration
Vite Proxy Setup

The vite.config.js file includes a proxy to avoid CORS issues during development:
javascript

export default defineConfig({
  server: {
    port: 3000,
    proxy: {
      '/api': {
        target: 'http://localhost:8000',
        changeOrigin: true,
      }
    }
  }
})

This automatically forwards /api/* requests to your backend running on port 8000.

Environment Variables
  Variable	Description	Default
  VITE_API_URL	Backend API URL	http://localhost:8000
  For production, update this to your deployed backend URL
     https://savannah-backend-kcxm.onrender.com

🧪 Testing M-Pesa Payments (Sandbox)

    Ensure your backend is running with ngrok for callbacks

    Login as a tenant (see default accounts below)

    Click "Pay Rent with M-Pesa"

    Enter test phone number: 708374149

    Click "Pay with M-Pesa"

    Simulate payment at Safaricom Developer Portal

🎨 UI Features
Dashboard Components

    Stat Cards – Animated gradient cards with key metrics

    Bar Chart – 6-month collection trends visualization

    Donut Chart – Occupancy and collection rate indicators

    Transaction Table – Color-coded status badges

    Properties Grid – Occupancy progress bars for each property

Payment Flow

    Phone Validation – Real-time phone number formatting

    Loading States – Animated spinner during payment processing

    Success/Error Feedback – Toast notifications and alerts

    Auto-refresh – Dashboard updates after successful payment

🔑 Default Test Accounts
Role	Email	Password
Admin	admin@savannah.co.ke	admin123
Accountant	accountant@savannah.co.ke	account123
Tenant	tenant001@savannah.co.ke	tenant123

    ⚠️ Important: These are demo accounts. Change credentials in production!

📡 Backend API Endpoints Used
Method	Endpoint	Purpose
POST	/api/auth/login	User authentication
POST	/api/auth/register	New tenant registration
GET	/api/dashboard/stats	Fetch KPI statistics
GET	/api/properties	List all properties
GET	/api/units	List all rental units
GET	/api/transactions	Fetch payment history
GET	/api/arrears	Fetch tenants in arrears
POST	/api/payments/initiate	Record manual payment
POST	/api/mpesa/stkpush	Initiate M-Pesa STK Push
GET	/api/mpesa/status/{id}	Check payment status
🚢 Deployment
Deploy to Vercel (Recommended)

    Push your code to GitHub

    Go to Vercel and click "New Project"

    Import your GitHub repository

    Configure environment variables:

        VITE_API_URL = https://savannah-backend-kcxm.onrender.com

    Click "Deploy"

Deploy to Netlify

    Push your code to GitHub

    Go to Netlify and click "New site from Git"

    Connect your repository

    Build settings:

        Build command: npm run build

        Publish directory: dist

    Add environment variables (same as above)

    Click "Deploy site"

Local Production Build
bash

npm run build
# The build output will be in the 'dist' folder
npm run preview  # Preview the production build locally

🐛 Common Issues & Solutions
Issue	Solution
CORS errors	Ensure Vite proxy is configured or backend CORS is enabled
API calls failing	Check VITE_API_URL in .env and restart dev server
M-Pesa payment fails	Verify ngrok is running and callback URL is updated in backend
Login not working	Confirm backend is running on port 8000
Blank screen	Check browser console for errors; verify all imports
🤝 Contributing

    Fork the repository

    Create a feature branch (git checkout -b feature/amazing-feature)

    Commit your changes (git commit -m 'Add some amazing feature')

    Push to the branch (git push origin feature/amazing-feature)

    Open a Pull Request

📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
🙏 Acknowledgements

    Backend API – SAVANNAH-BACKEND

    M-Pesa Integration – Safaricom Daraja API

    Icons – Emoji icons for simplicity

    Fonts – Google Fonts (DM Sans, Playfair Display)

📞 Contact

Developer: Gittechie-111

Project Link: https://github.com/Gittechie-111/SAVANNAH-FRONTEND


⭐ If you found this project helpful, please give it a star on GitHub!
