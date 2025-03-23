import streamlit as st
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity
import nltk
from nltk.corpus import stopwords
import re
import PyPDF2
import io

nltk.download('stopwords')
stop_words = set(stopwords.words('english'))

def extract_resume_text(pdf_file):
    try:
        with io.BytesIO(pdf_file.read()) as file:
            reader = PyPDF2.PdfReader(file)
            text = " ".join([page.extract_text() for page in reader.pages if page.extract_text()])
        return text
    except Exception as e:
        return f"Error extracting text: {e}"

def preprocess_text(text):
    text = text.lower()
    text = re.sub(r'[^\w\s]', '', text)
    tokens = text.split()
    tokens = [word for word in tokens if word not in stop_words]
    return " ".join(tokens)

def calculate_similarity(resume_text, job_description):
    vectorizer = TfidfVectorizer()
    tfidf_matrix = vectorizer.fit_transform([resume_text, job_description])
    similarity_score = cosine_similarity(tfidf_matrix[0], tfidf_matrix[1])
    return similarity_score[0][0]

st.title("AI Resume Screening and Candidate Ranking")

uploaded_files = st.file_uploader("Upload Resumes (PDF)", type="pdf", accept_multiple_files=True)
job_description = st.text_area("Enter Job Description")

if uploaded_files and job_description:
    results = []
    for uploaded_file in uploaded_files:
        resume_text = extract_resume_text(uploaded_file)
        if "Error extracting text" not in resume_text:
            processed_resume = preprocess_text(resume_text)
            processed_job = preprocess_text(job_description)
            similarity = calculate_similarity(processed_resume, processed_job)
            results.append({"filename": uploaded_file.name, "similarity": similarity})
        else:
            results.append({"filename": uploaded_file.name, "similarity": "Error"})

    st.subheader("Candidate Ranking:")
    import pandas as pd
    df = pd.DataFrame(results)
    st.dataframe(df)

    # Example Skill Matching(Very basic)
    st.subheader("Example Skill Matching:")
    if len(uploaded_files)>0:
        st.write("Resume example")
        resume_example = extract_resume_text(uploaded_files[0])
        st.write(resume_example[0:200] + "...")
        st.write("Job description example")
        st.write(job_description[0:200] + "...")

    st.subheader("Example Experience Extraction")
    st.write("Experience Extraction is not implemented in this example")
