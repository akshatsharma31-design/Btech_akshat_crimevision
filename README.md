🔍 CrimeWatch LA — Crime Data Analysis & Prediction System
A full-stack web application for analyzing and predicting crime patterns in Los Angeles using Machine Learning.

Minor Project | B.Tech Computer Science | 2025-26


📌 Project Overview
CrimeWatch LA is a full-stack crime data analysis system built on the Los Angeles Police Department (LAPD) crime dataset containing over 1 million crime records. The system allows users to search crimes by area and month, visualize trends through interactive charts, and predict the type of crime likely to occur in a specific area using a Random Forest ML model with 76-80% accuracy.

🚀 Features

🔐 User Authentication — Register and Login with JWT token-based security
📊 Interactive Dashboard — 6 charts including Line, Bar, Pie, and Radar charts
🔍 Crime Search — Filter crime records by area and month
🤖 ML Prediction — Predict crime type based on area, premise, time and day
🗺️ Crime Map — Visual map of 2000 crime locations across Los Angeles
📈 Top 5 Area Analysis — Detailed breakdown of the 5 highest crime areas


🛠️ Tech Stack
Frontend
TechnologyPurposeReact.jsUI FrameworkViteBuild Tool & Dev ServerReact Router DOMPage NavigationAxiosAPI CommunicationRechartsData Visualization (Charts)
Backend
TechnologyPurposePythonProgramming LanguageFlaskREST API FrameworkFlask-CORSCross Origin Resource SharingFlask-JWT-ExtendedAuthentication TokensPandasData Processing & AnalysisScikit-learnMachine Learning ModelPickleModel Serialization

🤖 Machine Learning Model

Algorithm: Random Forest Classifier
Dataset: LA Crime Data (1,005,198 records)
Training Data: Top 5 highest crime areas (~164,000 records)
Features Used: 8 features

Area (encoded)
Month
Hour of day
Day of week
Is Weekend (binary)
Time bucket (Night/Morning/Afternoon/Evening)
Season
Premise type (encoded)


Crime Classes: ASSAULT, THEFT, VEHICLE THEFT
Accuracy: 76-80% per area
Trees: 500 estimators


📁 Project Structure
crime-analysis/
│
├── dataset/
│   └── crimes.csv              # LA Crime Dataset (238MB)
│
├── ml_model/
│   └── train_model.py          # ML model training script
│
├── backend/
│   ├── app.py                  # Flask REST API
│   └── model.pkl               # Trained ML model (auto-generated)
│
├── src/
│   ├── components/
│   │   └── Navbar.jsx          # Navigation bar
│   ├── pages/
│   │   ├── Login.jsx           # Login page
│   │   ├── Register.jsx        # Register page
│   │   ├── Home.jsx            # Dashboard with charts
│   │   ├── Search.jsx          # Crime search page
│   │   └── Predict.jsx         # ML prediction page
│   ├── App.jsx                 # Routes configuration
│   ├── main.jsx                # Entry point
│   └── index.css               # Global styles
│
├── package.json                # Node dependencies
└── vite.config.js              # Vite configuration

📊 Dataset Information

Source: Los Angeles Police Department (LAPD)
Records: 1,005,198 crime incidents
Time Period: 2020 onwards
Key Columns Used:

AREA NAME — Police division/area
DATE OCC — Date crime occurred
TIME OCC — Time crime occurred
Crm Cd Desc — Crime type description
Premis Desc — Premise/location type
LAT, LON — GPS coordinates
Vict Age, Vict Sex — Victim details




⚙️ Installation & Setup
Prerequisites

Python 3.12+
Node.js 18+
npm

Step 1 — Clone the repository
bashgit clone https://github.com/yourusername/crime-analysis.git
cd crime-analysis
Step 2 — Add Dataset
Place your crimes.csv file inside the dataset/ folder.
Step 3 — Train the ML Model
bashcd ml_model
pip install pandas scikit-learn
python train_model.py
Step 4 — Install Backend Dependencies
bashcd ../backend
pip install flask flask-cors flask-jwt-extended pandas scikit-learn
Step 5 — Install Frontend Dependencies
bashcd ..
npm install
npm install axios recharts react-router-dom
Step 6 — Run the Application
Terminal 1 — Start Backend:
bashcd backend
python app.py
Terminal 2 — Start Frontend:
bashnpm run dev
Open http://localhost:5173 in your browser.

🔗 API Endpoints
MethodEndpointDescriptionAuth RequiredPOST/api/registerRegister new userNoPOST/api/loginLogin and get tokenNoGET/api/areasGet top 5 crime areasNoGET/api/statsGet overall statisticsNoGET/api/crimesSearch crimes by area/monthYesGET/api/trendsGet crime trends dataYesGET/api/top5areasGet top 5 area breakdownYesGET/api/heatmapGet map location dataYesGET/api/premisGet premise typesNoPOST/api/predictPredict crime typeYes

📷 Screenshots
Login Page

Secure JWT-based authentication system

Dashboard

6 interactive charts — Monthly trends, Crime type breakdown, Hourly distribution, Weekly patterns, Radar chart, Area comparison

Crime Search

Filter 1 million records by area and month

Prediction Page

ML-powered crime type prediction with confidence score and top 3 predictions


📐 Data Preprocessing

Missing Values: Removed using dropna() on critical columns
Feature Engineering:

Extracted Month, Hour, DayOfWeek from datetime columns
Created IsWeekend binary feature
Created TimeBucket (Night/Morning/Afternoon/Evening)
Created Season feature from month


Label Encoding: Used LabelEncoder for categorical columns
Crime Grouping: Grouped 8 similar crime types into 3 broader categories
Class Balancing: Used class_weight='balanced' in Random Forest



B.Tech Computer Science
Minor Project — 2025-26

📄 License
This project is for educational purposes only.
Dataset sourced from Los Angeles Open Data.
