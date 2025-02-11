# my-fr.flashcard-app
Development of a Flashcard-Based Learning App Utilizing the ChatGPT API

# Flashcard-Based French Learning Application

This repository hosts a flashcard-based French learning application designed for language learners who wish to improve their vocabulary effectively. The system integrates real-time word difficulty classification, an interactive flashcard interface, and a feedback-driven spaced repetition mechanism to enhance the learning experience.

## Overview

The application offers the following features:

- **Word Difficulty Classification**:  
  Using FastAPI and scikit-learn's DecisionTreeClassifier, the system classifies French words into three difficulty levels (beginner, intermediate, advanced) and provides instant feedback.

- **Interactive Flashcards**:  
  Developed with Streamlit, the flashcard interface displays words and fetches translations and additional information via the ChatGPT API when a card is clicked.

- **Feedback and Spaced Repetition**:  
  Learners can submit feedback such as "Mastered", "Partially Remembered", or "Not Remembered". This data is stored (e.g., in CSV format) and later used to dynamically schedule review sessions.

## Current Features

### 1. Word Difficulty Determination System

- **Data Preprocessing**:  
  Data cleaning, formatting, and categorical encoding are handled using Pandas and scikit-learn pipelines.

- **Model Building**:  
  A DecisionTreeClassifier categorizes the input words into appropriate difficulty levels. Training is enhanced by using train-test splitting and stratified sampling.

- **API Implementation**:  
  A FastAPI endpoint (`/predict/`) processes input asynchronously and returns classification results in real time.

### 2. Flashcard Learning Module

- **Flashcard Display and Translation**:  
  The application uses Streamlit to render flashcards. Clicking a flashcard triggers a call to the ChatGPT API, which returns the word’s translation and supplementary details.

- **Feedback Recording**:  
  Users can record their learning status by selecting options (e.g., "Mastered", "Partially Remembered", "Not Remembered"). The feedback, along with timestamps, is stored and used for calculating future review timings.

## Spaced Repetition & Machine Learning Integration

- **Basic Algorithm**:  
  Initially, simple rule-based logic adjusts review intervals based on user feedback (e.g., longer intervals for mastered words and shorter intervals for words not remembered).

- **Future Enhancements**:  
  - Analyzing user feedback over time to predict optimal review intervals via regression or time-series models.
  - Balancing the dataset to avoid bias (e.g., by oversampling underrepresented difficulty levels).
  - Incorporating principles from the Ebbinghaus forgetting curve to fine-tune review schedules.

## Deployment and Future Directions

- **Deployment Plans**:  
  Currently running on local servers, the plan is to deploy the application to cloud platforms (such as Heroku, AWS, or GCP) for real-time performance monitoring and data collection.

- **Continuous Improvement**:  
  Future updates will focus on refining the feedback loop, integrating advanced machine learning models for personalized scheduling, and enhancing the UI/UX.

## Repository Structure

my-fr.flashcard-app/
├── backend/
│   ├── level_checker.py   # FastAPIエンドポイント（単語の難易度判定用）のコード
│   └── api.py             # 翻訳機能やフラッシュカードのバランス調整のAPIコード
├── frontend/
│   └── app.py             # Streamlitを利用したUI（フラッシュカード＆スペースドレペティション）のコード
├── data/
│   ├── updated_final_data_with_levels.csv  # 単語の難易度判定に使うデータセット
│   └── feedback.csv       # ユーザーのフィードバックデータの保存ファイル
├── requirements.txt       # プロジェクトで必要なPythonパッケージの一覧
└── README.md              # プロジェクトの概要、使用方法、指示などを記載したファイル


## Installation & Usage

1. **Clone the Repository**
   ```bash
   git clone https://github.com/Yumiuse/my-fr.flashcard-app.git
   cd my-fr.flashcard-app
2. Install Dependencies
   
   pip install -r requirements.txt

3. Run the Backend and Frontend

      uvicorn backend/level_checker.py --reload

   Launch the Streamlit app
   
      streamlit run frontend/app.py

Future Enhancements
Develop personalized review scheduling using advanced machine learning models.
Expand the application to include additional language resources and real-time analytics.
Continuously refine the UI/UX based on user feedback.
License
This project is licensed under the MIT License. See LICENSE for details.


Contact
For questions or further information, please contact [parisnokujira@gmail.com].
