🚀 Evidently AI in Docker: A Deep Dive into Data Monitoring 📊🐳
📌 Introduction
This guide walks through setting up an Evidently AI-based Streamlit application running inside a Docker container. The application:

✅ Uses Evidently AI for monitoring machine learning models.
✅ Provides an interactive dashboard in Streamlit.
✅ Organizes reports and projects efficiently.
✅ Uses Docker for easy deployment and management.

📂 Project Structure
Ensure your working directory contains the following files and folders:

php
Copy
Edit
📁 evidently-ai-streamlit
 ├── 📂 projects                # Contains different ML monitoring projects
 │    ├── 📂 project_1
 │    │    ├── 📂 reports       # Stores monitoring reports
 │    │    ├── ...
 │    ├── 📂 project_2
 │    │    ├── 📂 reports
 │    │    ├── ...
 │    ├── ...
 │
 ├── 📂 src                     # Contains Python scripts for UI and utilities
 │    ├── ui.py                 # UI components
 │    ├── utils.py              # Utility functions
 │    ├── ...
 │
 ├── 📂 static                  # Stores static assets (CSS, images, etc.)
 │    ├── style.css             # Custom styling
 │    ├── ...
 │
 ├── 📄 app.py                   # Main Streamlit application
 ├── 📄 Dockerfile               # Defines the Docker image for Streamlit
 ├── 📄 requirements.txt         # Python dependencies
 ├── 📄 README.md                # Project documentation
📝 Main Application (app.py - Overview)
The app.py script:

🔹 Loads available projects and reports dynamically.
🔹 Allows users to select a project, period, and report.
🔹 Renders Evidently AI reports inside Streamlit.
🔹 Handles errors gracefully if a project or report is missing.
🔹 Uses src/ui.py for UI elements and src/utils.py for helper functions.

Key Functions:
📌 display_sidebar_header(): Renders the sidebar with branding and navigation.
📌 select_project(): Lets users pick a project.
📌 select_period(): Allows selection of a reporting period.
📌 select_report(): Fetches available reports.
📌 display_report(): Loads and displays the selected report.

🐳 Dockerfile (Containerizing Streamlit App)
Create a file named Dockerfile in your project directory and add the following content:

dockerfile
Copy
Edit
# Use the official Python base image
FROM python:3.10

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file and install dependencies
COPY requirements.txt /app/
RUN pip install --no-cache-dir --break-system-packages -r requirements.txt

# Copy the entire project into the container
COPY . /app/

# Expose the port Streamlit runs on
EXPOSE 8501

# Run the Streamlit app
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
🐍 Python Dependencies (requirements.txt)
Ensure you have a requirements.txt file with the following dependencies:

ini
Copy
Edit
category_encoders==2.6.0
evidently==0.2.6
jupyter==1.0.0
jupyter_contrib_nbextensions==0.7.0
matplotlib==3.7.0
numpy==1.24.2
pandas==1.5.3
pyarrow==11.0.0
python-box==5.4.1
requests==2.28.2
streamlit==1.19.0
pyyaml==5.1
scikit-learn==1.2.1
scipy==1.10.1
seaborn==0.12.2
altair==4.0
🛠 Steps to Run the Application
1️⃣ Clone the Repository & Navigate to the Project
bash
Copy
Edit
git clone <repo-link>
cd evidently-ai-streamlit
2️⃣ Build & Run Containers
bash
Copy
Edit
docker build -t evidently-streamlit .
docker run -p 8501:8501 evidently-streamlit
3️⃣ Access the Streamlit App
🌐 Open http://localhost:8501 in your browser. 🚀
