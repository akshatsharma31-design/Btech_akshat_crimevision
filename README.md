CrimeWatch LA — Crime Data Analysis & Prediction System
A full-stack web application for searching, visualizing, and predicting crimes using real Los Angeles Police Department (LAPD) data and a Machine Learning model.

Python React Flask Scikit-Learn License

📌 Project Overview
CrimeWatch LA is a B.Tech Minor Project that applies Machine Learning and full-stack web development to real-world crime data. The system allows users to:

🔐 Register and log in with JWT authentication
📊 Explore crime trends through 6 interactive charts
🔍 Search crime records by area and month
🤖 Predict the most likely crime type using a trained Random Forest model
🗺️ View 2,000+ crime locations plotted on a Los Angeles map
🗂️ Project Structure
crime-analysis/
│
├── dataset/
│   └── crimes.csv                  # LAPD Crime Dataset (238MB)
│
├── ml_model/
│   └── train_model.py              # ML model training script
│
├── backend/
│   ├── app.py                      # Flask REST API
│   └── model.pkl                   # Trained Random Forest model (auto-generated)
│
├── src/
│   ├── main.jsx
│   ├── App.jsx
│   ├── index.css
│   ├── components/
│   │   └── Navbar.jsx
│   └── pages/
│       ├── Login.jsx
│       ├── Register.jsx
│       ├── Home.jsx                # Dashboard with charts
│       ├── Search.jsx
│       └── Predict.jsx
│
├── package.json
└── README.md
🧠 Machine Learning Model
Algorithm
Random Forest Classifier from Scikit-learn

Dataset
Source: LAPD Crime Data — City of Los Angeles Open Data
Records: 1,005,198 crime incidents
Columns: 28 (date, time, area, crime type, premise, victim info, GPS coordinates)
Features Used (7 input features)
Feature	Description	Source Column
Area	LA police division (encoded)	AREA NAME
Month	Month of year (1–12)	Extracted from DATE OCC
Hour	Hour of day (0–23)	Extracted from TIME OCC
Day of Week	0 = Monday, 6 = Sunday	Extracted from DATE OCC
Is Weekend	Binary flag (0 or 1)	Derived from Day of Week
Time Bucket	Night/Morning/Afternoon/Evening	Derived from Hour
Premise Type	Street, Parking Lot, Dwelling, etc. (encoded)	Premis Desc
Target Variable (Crime Groups)
10 raw crime types were grouped into 3 broader categories using feature engineering:

Group	Original Crime Types
ASSAULT	Battery - Simple Assault, Assault with Deadly Weapon, Intimate Partner Assault
THEFT	Theft of Identity, Theft Plain Petty, Theft Grand
VEHICLE THEFT	Theft from Motor Vehicle, Burglary from Vehicle
Grouping reduced class confusion and improved accuracy from 38% → 76–80%.

Model Parameters
RandomForestClassifier(
    n_estimators=300,
    max_depth=25,
    min_samples_split=4,
    min_samples_leaf=2,
    max_features='sqrt',
    class_weight='balanced',
    random_state=42,
    n_jobs=-1
)
Results
Area	Accuracy
Overall (all 5 areas)	~78%
Central	79%
Pacific	80%
77th Street	77%
Hollywood	79%
Southwest	76%
🛠️ Tech Stack
Frontend
React 18 (Vite)
React Router DOM — client-side routing
Recharts — bar, line, pie, radar charts
Axios — HTTP requests to Flask API
Backend
Flask — Python web framework
Flask-CORS — cross-origin request handling
Flask-JWT-Extended — JWT authentication
Pandas — dataset loading and querying
Pickle — model serialization
Machine Learning
Scikit-learn — Random Forest Classifier
Pandas / NumPy — data wrangling and feature engineering
LabelEncoder — categorical encoding
⚙️ Setup & Installation
Prerequisites
Python 3.10+
Node.js 18+
npm
Step 1 — Clone the repository
git clone https://github.com/your-username/crime-analysis.git
cd crime-analysis
Step 2 — Add the dataset
Download the LAPD Crime Dataset and place it inside the dataset/ folder. Rename it to crimes.csv.

Step 3 — Train the ML model
cd ml_model
pip install pandas scikit-learn
python train_model.py
This will create backend/model.pkl automatically. Training takes 3–5 minutes.

Step 4 — Start the backend
cd ../backend
pip install flask flask-cors flask-jwt-extended pandas scikit-learn
python app.py
Backend runs at: http://localhost:5000

Step 5 — Start the frontend
Open a new terminal:

cd crime-analysis        # root of project
npm install
npm install axios recharts react-router-dom
npm run dev
Frontend runs at: http://localhost:5173

Step 6 — Use the app
Open http://localhost:5173 in your browser
Click Register and create an account
Login with your credentials
Explore the Dashboard, Search, and Predict pages
🔌 API Endpoints
Method	Endpoint	Auth Required	Description
POST	/api/register	No	Create a new user account
POST	/api/login	No	Login and receive JWT token
GET	/api/areas	No	Get list of top 5 crime areas
GET	/api/crimes	Yes	Search crime records by area & month
GET	/api/trends	Yes	Get chart data (monthly, hourly, weekly)
GET	/api/top5areas	Yes	Get detailed stats for top 5 areas
GET	/api/heatmap	Yes	Get 2000 GPS points for the map
GET	/api/stats	No	Get summary statistics
POST	/api/predict	Yes	Get ML crime prediction
📸 Features
Dashboard
5 stat cards (total crimes, area count, top crime, most dangerous area, model accuracy)
Clickable top 5 area cards with assault/theft/vehicle theft breakdown
Monthly trend line chart
Crime type pie chart (donut style)
Hourly crime bar chart (color-coded by time of day)
Day of week bar chart
Crime type radar chart
Top 5 area horizontal comparison bar chart
Crime location map (SVG with GPS dots)
Search
Filter by area and month
Returns up to 100 records in a sortable table
Shows date, area, crime type, premise, victim age, victim sex, location
Predict
Select area, premise type, month, hour
Returns predicted crime type with confidence %
Shows top 3 predictions with probability progress bars
📁 Key Files Explained
File	Purpose
ml_model/train_model.py	Loads CSV, engineers features, trains Random Forest, saves model.pkl
backend/app.py	Flask server with all API routes, loads model.pkl at startup
src/pages/Home.jsx	Dashboard page with all 6 charts and crime map
src/pages/Predict.jsx	Prediction page — sends inputs to Flask, displays ML results
src/pages/Search.jsx	Search page — filters crime records by area and month
src/App.jsx	React Router setup with protected routes using JWT
🔮 Future Improvements
Replace in-memory user store with PostgreSQL database
Deploy backend on Render / Railway
Deploy frontend on Vercel / Netlify
Add interactive Leaflet.js map with clustering
Try XGBoost for higher accuracy
Add real-time crime alerts via WebSockets
Mobile app version using React Native
👨‍💻 Author
Anant B.Tech Minor Project — 2025–26

📄 License
This project is for educational purposes. The dataset is sourced from Los Angeles Open Data and is publicly available under their terms of use.
