# Fake News Detection API
A FastAPI-based machine learning API that detects fake news articles with a feedback loop and retraining support.

# Overview
This project provides a simple yet powerful API for classifying news articles as **REAL** or **FAKE**.  
It is built with **FastAPI** and uses a machine learning model trained with text data.
The API also includes a **feedback mechanism**, allowing users to correct predictions. These corrections are stored in a database and can be used to **retrain the model**, improving accuracy over time.

# Features
- Predict whether a news article is REAL or FAKE  
- Confidence score for each prediction  
- Feedback loop for users to correct misclassifications  
- Feedback storage using SQLite  
- Retrainable ML model that adapts based on feedback  
- Interactive API documentation with Swagger UI  

# Tech Stack
- Python 3.x  
- FastAPI (Web Framework)  
- Uvicorn (ASGI Server)  
- Scikit-learn (Machine Learning)  
- SQLite (Database)  
- Joblib (Model persistence)  
- NumPy (Numerical processing)  

# Installation
1. Clone the repository :
   ```bash
   git clone https://github.com/akashaether12/Fake-News-Detection-API.git
   cd Fake-News-Detection-API
   
2.Create and activate a virtual environment (PyCharm recommended) :
- python -m venv venv
- venv\Scripts\activate     # On Windows
- source venv/bin/activate  # On Mac/Linux

3.Install dependencies :
- pip install -r requirements.txt

# Running the API
1.Start the server with : uvicorn main:app --reload

2.The API will be available at : http://127.0.0.1:8000

3.Interactive API documentation (Swagger UI) will be available at : http://127.0.0.1:8000/docs

# API Endpoints
1. Predict Fake/Real News
POST /predict
Request body :
   {
     "title": "Breaking News",
     "text": "BREAKING: Celebrity endorses miracle cure doctors hate this!"
   }
Response :
   {
     "prediction": "REAL",
     "confidence": 0.87
   }

3. Provide Feedback
POST /feedback
Request body :
   {
     "id": "12345",
     "correct_label": "FAKE"
   }

4. Retrain Model
POST /retrain
Retrains the model using all feedback stored in the database.

# Project Structure
- .model_version       # Version info for the ML model
- fake_news.db         # Database for storing news and feedback
- fake_news_api.py     # Main FastAPI backend file (API routes + model usage)
- model.joblib         # Serialized trained ML model
- README.md            # Project documentation
- LICENSE              # License file

# License
This project is licensed under the MIT License. See the LICENSE file for details.
