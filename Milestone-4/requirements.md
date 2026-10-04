# Requirements – Milestone 4

## Project
**Prediction AI – Startup & Project Risk Analyzer**

## Purpose

This document records the software, environment, deployment, and configuration requirements used to run the final application.

---

## 1. System Requirements

### Operating System

The application can be developed and tested on:

- Windows
- Linux
- macOS

### Python

Recommended:

```text
Python 3.10+
```

The development environment used for the project should match the versions supported by the installed packages.

---

## 2. Core Python Dependencies

The final application requires the following dependency groups:

### Streamlit

Used for the interactive web application and dashboard.

```text
streamlit
```

### Pandas

Used for tabular data handling and dashboard/chart preparation.

```text
pandas
```

### PostgreSQL Driver

Used for database connectivity.

```text
psycopg2-binary
```

### Environment Configuration

Used to load environment variables during local development.

```text
python-dotenv
```

### LangGraph

Used to orchestrate the six-node AI workflow.

```text
langgraph
```

### Gemini SDK

Used to communicate with the Google Gemini API.

```text
google-genai
```

---

## 3. Project Modules

The application depends on the project's internal Python modules, including:

```text
app_streamlit.py
database.py
market_analysis.py
risk_engine.py
swot_analysis.py
feasibility.py
recommendation_engine.py
mitigation_engine.py
improvement_engine.py
llm_service.py
```

These modules provide the application layers for:

- User interface
- Database operations
- Market intelligence
- Risk scoring
- SWOT analysis
- Feasibility
- Recommendations
- Mitigation
- Improvements
- Gemini AI integration

---

## 4. Database Requirements

The project uses PostgreSQL for persistent storage.

Required database information for local development includes:

```text
DB_HOST
DB_NAME
DB_USER
DB_PASSWORD
DB_PORT
```

The database credentials must not be hard-coded in application source files.

---

## 5. Gemini AI Requirements

The AI recommendation layer requires a Gemini API key when live Gemini generation is enabled.

Required configuration:

```text
GEMINI_API_KEY
```

The model can be configured through:

```text
GEMINI_MODEL
```

The API key must never be committed to GitHub.

For local development, environment variables or `.env` can be used.

For Streamlit Community Cloud, the equivalent values should be stored using Streamlit Secrets.

---

## 6. LangGraph Requirements

The final workflow requires LangGraph support.

The workflow is:

```text
analyze_project
        ↓
analyze_risks
        ↓
generate_recommendations
        ↓
generate_mitigation
        ↓
generate_improvements
        ↓
generate_final_response
```

The application also contains a fallback path when LangGraph is unavailable so that the rest of the application can remain usable.

---

## 7. Local Installation

Create a virtual environment:

```powershell
python -m venv venv
```

Activate it on Windows:

```powershell
venv\Scripts\activate
```

Install dependencies:

```powershell
pip install -r requirements.txt
```

---

## 8. Local Configuration

Create a local `.env` file when environment variables are required.

Example structure:

```env
GEMINI_API_KEY=YOUR_ACTUAL_GEMINI_KEY
GEMINI_MODEL=YOUR_CONFIGURED_GEMINI_MODEL

DB_HOST=localhost
DB_NAME=YOUR_DATABASE_NAME
DB_USER=YOUR_DATABASE_USER
DB_PASSWORD=YOUR_DATABASE_PASSWORD
DB_PORT=5432
```

Do not commit the real `.env` file.

---

## 9. Running the Application

From the project root:

```powershell
streamlit run app_streamlit.py
```

The Streamlit application normally opens at:

```text
http://localhost:8501
```

---

## 10. Deployment Requirements

For Streamlit Community Cloud:

1. GitHub repository must contain the application source.
2. `app_streamlit.py` must be selected as the application entry point.
3. `requirements.txt` must contain all required Python packages.
4. Gemini credentials must be configured through Streamlit Secrets.
5. Database credentials must be supplied through the appropriate deployment configuration.
6. `.env` and other secrets must not be committed.
7. The deployment environment must be able to install all required dependencies.

---

## 11. Security Requirements

The following must not be committed to the repository:

```text
.env
API keys
Database passwords
Private credentials
Local database files containing sensitive information
```

The `.gitignore` file should exclude sensitive local configuration and runtime artifacts.

---

## 12. Functional Requirements

The final application should allow a user to:

- Enter project information.
- Generate market information.
- View competitor information.
- Enter risk assessment values.
- Calculate risk score and status.
- Calculate success probability.
- Generate SWOT analysis.
- Calculate feasibility.
- Generate strategic recommendations.
- Generate risk mitigation strategies.
- Generate improvement suggestions.
- Execute the LangGraph workflow.
- Generate a final strategic assessment.
- Persist project and assessment information.
- View the final dashboard.

---

## 13. Final Deployment Checklist

Before deployment:

```text
[ ] requirements.txt is present
[ ] google-genai is installed/listed
[ ] langgraph is installed/listed
[ ] app_streamlit.py runs locally
[ ] Gemini API key is not hard-coded
[ ] .env is not committed
[ ] Database configuration is externalized
[ ] Streamlit Secrets are configured
[ ] Application entry point is correct
[ ] Deployment logs are checked if startup fails
[ ] End-to-end workflow is tested
```

---

## 14. Expected Result

After successful installation and configuration, the user should be able to start the application with:

```powershell
streamlit run app_streamlit.py
```

and use the complete Startup & Project Risk Analyzer workflow from project input through final AI-assisted strategic assessment.
