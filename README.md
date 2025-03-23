AI Resume Screening & Candidate Ranking System
Overview

This project is an AI-powered resume screening and candidate ranking system designed to streamline the recruitment process. It efficiently evaluates resumes against job descriptions using Natural Language Processing (NLP) and Machine Learning (ML) techniques. By extracting key information, assessing candidate suitability, and ranking resumes based on relevance, it aims to save recruiters and hiring managers valuable time.
Key Features

    Resume Parsing: Extracts text from PDF resumes.
    Job Description Parsing: Analyzes job postings to extract relevant requirements.
    Text Preprocessing: Cleans resumes and job descriptions using NLP techniques (e.g., removing stopwords, punctuation, tokenization).
    Similarity Scoring: Computes relevance between resumes and job descriptions using TF-IDF vectorization and cosine similarity.
    Skill Matching: Identifies key skills from resumes and compares them with job requirements (Basic 200 character example provided).
    Experience Matching: Extracts years of experience from resumes and compares them with job postings (Placeholder for future implementation).
    Candidate Ranking: Scores and ranks candidates based on similarity scores.
    Interactive Front-End: Provides a user-friendly Streamlit interface for easy resume upload, job description input, and result visualization.

Project Structure

. ├── app.py # Main Streamlit application script ├── models.py # Machine learning model implementation (placeholder) ├── preprocess.py # Text preprocessing functions (placeholder) ├── resume_parser.py # Resume extraction functions (placeholder) ├── job_parser.py # Job description extraction functions (placeholder) ├── requirements.txt # List of dependencies ├── dataset/ # Sample resumes and job descriptions (optional) ├── README.md # Project documentation
Installation
Requirements

To run this project, ensure you have:

    Python 3.x
    Streamlit
    Scikit-learn
    spaCy
    NLTK
    PyPDF2

Install Dependencies

Install the required libraries using pip:

pip install -r requirements.txt

If requirements.txt is not available, install them manually:
Bash

pip install streamlit scikit-learn spacy nltk PyPDF2

Additional Setup

Download the spaCy English language model:
Bash

python -m spacy download en_core_web_sm

Download NLTK stopwords:
Python

import nltk
nltk.download('stopwords')

Usage
Running Locally

    Start the Streamlit application:
    Bash

    streamlit run app.py

    Upload resumes in PDF format.

    Enter the job description in the text area.

    View the ranked candidates and their similarity scores.

Running on Google Colab
Python

!pip install streamlit scikit-learn spacy nltk PyPDF2
from pyngrok import ngrok
!streamlit run app.py --server.port 8501 &>/dev/null&
public_url = ngrok.connect(8501, "http")
print(f"Streamlit app is live at: {public_url}")

Features & Implementation

    Resume Parsing: Extracts text from PDF resumes using PyPDF2.
    Job Description Parsing: Processes job descriptions to extract key requirements.
    Text Preprocessing:
        Converts text to lowercase.
        Removes stopwords and punctuation.
        Tokenizes text.
    Similarity Scoring:
        Converts text to TF-IDF vectors.
        Calculates cosine similarity.
    Skill & Experience Matching:
        Extracts and compares skills (basic example provided).
        Identifies and compares years of experience (placeholder).
    Candidate Ranking: Ranks resumes based on similarity scores.
    Front-End Interface: Streamlit UI for upload, input, and results.

Customization
Adding More Features

    Keyword Extraction: Use KeyBERT.
    Advanced ML Models: Train Logistic Regression, Random Forest, or BERT.
    Formatting Analysis: Use OpenCV.

Deployment Options

    …
