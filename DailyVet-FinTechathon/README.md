# DailyVet - AI-Powered Livestock FinTech Ecosystem

Submitted for: 2026 Shenzhen International FinTech Competition (FinTechathon)
Theme: AI as a Financial Participant
Selected Topics: 
- Topic E: SME Finance Copilot (Farm Cashflow & Credit Readiness)

Live Demo Link: https://dailyvetfinance.vercel.app/

## Overview

DailyVet is an all-in-one, AI-driven financial and healthcare companion designed specifically for farmers and livestock owners in Bangladesh. By fusing NASA satellite climate data, Generative AI, and parametric insurance models, DailyVet bridges the financial gap for rural micro-entrepreneurs. 

Instead of traditional paperwork, DailyVet acts as an autonomous financial participant, predicting climate risks, calculating dynamic insurance premiums, auto-triggering claims, and forecasting farm cashflows, all through a mobile-first web application.

## Key Features (Aligned with FinTechathon Topics)

Topic D: Insurance Assistant
Live NASA Risk Assessment: Fetches real-time satellite data (flood, heat stress, air quality) to calculate a dynamic, risk-based monthly premium.
Parametric Insurance Purchase: Farmers can buy micro-insurance policies instantly without physical paperwork.
Manual Payment and Proof Verification: Integrated bKash/Nagad manual payment flow with TrxID and screenshot uploads for fraud prevention.
Automated Claim Guidance: When weather triggers (e.g., severe flood, extreme heat) are met, the AI automatically verifies the trigger and guides the user to file a claim.
Coverage Gap Analysis: AI analyzes the user's location risk versus their policy and advises on coverage gaps.

Topic E: SME Finance Copilot
Voice-Activated Ledger: Farmers can speak naturally (e.g., "Sold milk for 2000 taka, bought feed for 1500") to log income and expenses.
AI Cashflow Forecast: Uses live NASA weather data to predict 30/60/90-day income drops due to climate risks (e.g., "Flood risk is high; expected milk yield will drop by 15%").
Credit Readiness Score: Analyzes the farm's ledger data to generate a 0-999 credit score, helping farmers access micro-loans from banks.

## User Account and Profile Management

DailyVet includes a robust and secure user management system to ensure a personalized experience for every farmer.

Account Creation (Sign Up):
Users can create a new account using their mobile number and password.
During registration, users can select their location (District and Area) and add the types of animals they own (e.g., Cow, Goat, Chicken).
Profile pictures can be uploaded directly during the sign-up process.

Profile Dashboard (My Info):
The profile page acts as the central hub for the user's personal and financial data.
Users can update their Name, District, and Area.
Profile Picture update: Users can change their profile photo at any time.
Pet Management: Users can add or remove animals from their profile.
Payout Account Setup: Users must link their bKash, Nagad, Rocket, or Bank account to receive insurance claim payouts. (Custom UI with official logos).
Insurance Policy History: Users can view their active, pending, and rejected insurance policies, along with their past claims.
Vet Account Integration: If the user is also a registered veterinarian, a special section appears to access the Vet Dashboard.
Account Security: Users can securely log out or permanently delete their account.

## Technology Stack

Frontend: HTML5, CSS3, Vanilla JavaScript (Progressive Web App architecture)
Backend / Database: Firebase (Firestore, Authentication)
AI Models: Google Gemini (Vision and Text for Claims/Chat), Groq (Llama-3 for Voice Ledger)
Data Sources: NASA POWER and GPM (Weather and Climate data), Open-Meteo (Air Quality)
Maps: Leaflet.js and LocationIQ API (for district/upazila geolocation)
Payments: Manual bKash/Nagad integration (Merchant flow)

## How to Run the Project Locally

Step 1: Extract the ZIP (or clone the repo).
API keys: end users and judges need no key. On the live demo, AI requests go through the project's server-side proxy (/api/ai-proxy), which holds the keys. Only a self-hosting developer sets keys: as environment variables on Netlify/Vercel (GEMINI_KEY_*, GROQ_KEY_*, OPENROUTER_KEY_*, FIREBASE_SERVICE_KEY), or in the js/ key arrays for localhost testing. Never commit real keys.

Step 2: Firebase: create a project, enable Authentication (Anonymous) and Firestore, and paste the config into js/firebase-config.js.
Serve: npx serve . (or VS Code Live Server).

Step 3: Set up Firebase. Create a Firebase project at console.firebase.google.com. Enable Authentication (Anonymous) and Firestore Database. Copy your Firebase config and paste it into js/firebase-config.js.

Step 4: Run the application. Since the app uses Firebase and PWA features, it is recommended to run it through a local server like VS Code Live Server or Netlify CLI. Use the command "npx serve ." in your terminal inside the extracted folder.

## Test Cases / How to Test

To evaluate the core features of DailyVet, please follow these steps:

Step 1: Sign Up or Login. Create a dummy account using any 11-digit mobile number (e.g., 01712345678) and a password. Fill in the profile details and add at least one animal.

Step 2: Setup Payout Account. Go to the Profile page and scroll down to add a bKash/Nagad payout number. This is required for insurance.

Step 3: Buy Insurance (Topic D). Navigate to FarmFin AI and select Buy Insurance. Select a location on the map, get a live NASA quote, and submit a dummy TrxID with a screenshot.

Step 4: SME Cashflow (Topic E). Navigate to Finance Copilot. Use the microphone button and say, "Sold milk 2000 taka and bought feed 1000 taka." See the AI auto-parse the data and update the ledger.

Step 5: Check Cashflow Forecast. Go to Cashflow Forecast to see how NASA weather risks impact the farm's future income.

DailyVet is a competition prototype; no real money moves (payments and payouts run in demo mode).

In place: AI calls on the deployed site go through a server-side proxy, so users never see or enter an API key. Passwords are stored as salted SHA-256 hashes. Deployment sets HSTS, X-Frame-Options, nosniff, Referrer-Policy, and Permissions-Policy headers.

Security Note : 

DailyVet is a competition prototype; no real money moves (payments and payouts run in demo mode).

In place: AI calls on the deployed site go through a server-side proxy, so users never see or enter an API key. Passwords are stored as salted SHA-256 hashes. Deployment sets HSTS, X-Frame-Options, nosniff, Referrer-Policy, and Permissions-Policy headers.

Not yet production-ready:

The proxy is wired into js/ai.js only; other AI modules still call providers from the browser, and the proxy has no caller authentication, rate limit, or origin restriction.
Login and password reset run client-side against Firestore with no OTP, and no firestore.rules file is shipped.
Payment and payout functions are unauthenticated demo handlers.
No Content-Security-Policy; several pages render with innerHTML.

Before production: rotate all keys, route every AI call through an authenticated proxy, use Firebase Phone Auth with strict Firestore rules, verify and recompute amounts server-side, and add CSP and output escaping.

Team Name: TechsparkBD
Team Leader: Al Fitar Ahmed Siam 
Institution: Bangladesh university of Business and Technolology 
