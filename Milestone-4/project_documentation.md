# Prediction AI – Startup & Project Risk Analyzer

## Milestone 4 – Final Project Documentation

### 1. Project Overview

**Prediction AI – Startup & Project Risk Analyzer** is an AI-assisted decision-support system designed to evaluate the potential risks and feasibility of a startup or project before major resources are committed.

The system collects project information, analyzes market and competitor factors, evaluates multiple risk dimensions, generates a risk score and success probability, and provides AI-assisted strategic recommendations, risk mitigation strategies, improvement suggestions, and an overall strategic assessment.

### 2. Problem Statement

Startups and projects can fail because of factors such as high market competition, insufficient resources, financial constraints, weak technical capabilities, poor feasibility, and inadequate planning.

Traditional project evaluation can depend heavily on manual review. This project provides a structured system to:

- collect project information;
- analyze market and competitor information;
- calculate an overall risk score;
- classify risk as low, medium, or high;
- estimate success probability;
- perform SWOT analysis;
- evaluate feasibility;
- generate risk-linked recommendations;
- generate mitigation strategies;
- identify improvement opportunities; and
- present the results through an executive dashboard.

The system is a decision-support tool and does not replace human judgment.

---

## 3. Project Objectives

1. Build a structured project information collection system.
2. Analyze market and competitor information.
3. Calculate an overall project risk score.
4. Classify projects into low, medium, and high risk.
5. Calculate an estimated success probability.
6. Perform SWOT analysis.
7. Calculate project feasibility.
8. Generate strategic recommendations.
9. Generate mitigation strategies for major risks.
10. Generate structured improvement suggestions.
11. Integrate Gemini for AI-assisted analysis.
12. Implement the M3 workflow using LangGraph.
13. Generate a final strategic assessment.
14. Store assessment results in the database.
15. Provide a centralized Streamlit dashboard.

---

## 4. Milestone 4 Scope

Milestone 4 brings the previous milestones together into a complete, testable, deployable, and documented application.

The final system integrates:

- project information collection;
- market and competitor analysis;
- risk scoring;
- SWOT analysis;
- feasibility analysis;
- AI recommendations;
- risk mitigation;
- improvement planning;
- LangGraph workflow;
- Gemini integration;
- database persistence;
- dashboard visualization;
- testing;
- deployment preparation; and
- final documentation.

---

## 5. End-to-End Workflow

```text
Project Submission
        ↓
Information Collection
        ↓
Market & Competitor Analysis
        ↓
Risk Assessment & Scoring
        ↓
SWOT Analysis
        ↓
Feasibility Analysis
        ↓
AI Strategic Recommendations
        ↓
Risk Mitigation
        ↓
Improvement Plan
        ↓
Final Strategic Assessment
        ↓
Executive Dashboard / Report
```

---

## 6. Technology Stack

### Frontend / UI
- Streamlit
- Python-based interactive dashboard
- Forms, metrics, charts, expanders, and report download

### Backend
- Python
- Modular application services
- Risk engine
- Recommendation engine
- Mitigation engine
- Improvement engine
- Database layer

### AI
- Google Gemini API
- LangGraph
- Prompt-based strategic analysis
- Risk-aware recommendations and mitigation

### Database
- PostgreSQL
- psycopg2

### Development
- Git
- GitHub
- Python virtual environment
- VS Code

---

## 7. Major Components

### 7.1 Project Information Collection

The system collects:

- Project Name
- Project Description
- Project Type
- Target Market
- Target Customers
- Budget
- Resources
- Objectives
- Competitors
- Market Analysis
- Competitor Analysis

This information becomes the shared context for the assessment pipeline.

### 7.2 Risk Assessment Engine

The main risk functions are:

```python
calculate_risk(...)
get_risk_status(score)
calculate_success_probability(score)
```

Risk classification:

| Risk Score | Status |
|---|---|
| 0–39 | LOW RISK |
| 40–69 | MEDIUM RISK |
| 70–100 | HIGH RISK |

Success probability is calculated as:

```text
Success Probability = max(0, 100 - Risk Score)
```

This is an assessment metric, not a calibrated statistical probability.

### 7.3 SWOT Analysis

The system evaluates:

- Strengths
- Weaknesses
- Opportunities
- Threats

### 7.4 Feasibility Analysis

The overall feasibility score is calculated from four numerical components:

```text
Feasibility Score = (S1 + S2 + S3 + S4) / 4
```

---

## 8. AI Strategic Recommendation Engine

The recommendation engine produces:

### A. Overall Strategic Recommendation
Overall strategic direction for the project.

### B. Risk-Based Recommendations
Actions directly connected to identified risks.

### C. Market Recommendations
Actions related to customers, competition, market positioning, and market strategy.

### D. Technical Recommendations
Actions related to technology, technical capability, implementation, and resources.

### E. Financial Recommendations
Actions related to budget, cost control, and financial resources.

### F. Operational Recommendations
Actions related to execution, resources, and processes.

### G. Improvement Suggestions
Areas where the project can be strengthened.

### H. Short-Term Action Plan
Immediate priorities.

### I. Long-Term Action Plan
Longer-term strategic actions.

Recommendations are intended to explain the problem or risk, why it matters, what should be done, and how the action reduces risk.

---

## 9. Risk Mitigation Engine

The mitigation engine creates actionable strategies for major risks.

Each mitigation contains:

- Risk Name
- Category
- Description
- Impact
- Priority
- Recommended Mitigation Strategy
- Preventive Action
- Contingency Action

The objective is to move from simply identifying a risk to defining a practical response.

```text
Risk
  ↓
Impact
  ↓
Mitigation Strategy
  ↓
Preventive Action
  ↓
Contingency Action
```

---

## 10. Improvement Engine

Improvement suggestions are generated across:

- Product
- Market
- Technical
- Financial
- Operational
- Marketing

Each improvement contains:

- Improvement
- Reason
- Expected Benefit
- Priority

---

## 11. LangGraph Agent Workflow

The M3 AI workflow uses the following node structure:

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

### `analyze_project`
Organizes the project context.

### `analyze_risks`
Processes risk information, risk score, risk status, SWOT, and feasibility.

### `generate_recommendations`
Generates strategic recommendations using the project and risk context.

### `generate_mitigation`
Generates mitigation strategies for major risks.

### `generate_improvements`
Generates structured improvement suggestions.

### `generate_final_response`
Combines the outputs into the final strategic assessment.

A shared workflow state allows information generated by earlier nodes to be used by later nodes.

---

## 12. Gemini AI Integration

Gemini is integrated as the LLM layer for strategic recommendations, mitigation, and improvements.

The API key is loaded through an environment variable rather than hardcoded.

Example:

```env
GEMINI_API_KEY=YOUR_API_KEY
GEMINI_MODEL=YOUR_MODEL
```

The application also supports demo/fallback behavior when an API key is unavailable.

Main AI service functions include:

```python
generate_llm_recommendations(...)
generate_llm_mitigation(...)
generate_llm_improvements(...)
```

This keeps the AI layer modular and independently maintainable.

---

## 13. Database Integration

PostgreSQL is used for persistent storage.

The database layer stores assessment information such as:

- Project information
- Risk score
- Risk status
- Success probability
- SWOT information
- Recommendations
- Mitigation strategies
- Improvement suggestions
- Assessment timestamp

This allows assessment information to persist beyond a single application session.

---

##Above was just some changes that i made which i think would make this project more refined. Below from here is the main work according to milestone 4 Dashboard,
##testing, deployement.

## 14. Final Dashboard

The final Streamlit dashboard provides an executive overview instead of simply repeating every detail from the earlier milestones.

### Risk Analytics

Displays:

- Overall Risk
- Success Probability
- Market Risk
- Technical Risk
- Project Health / Feasibility
- Risk Distribution
- Project Snapshot

### Assessment Report

Contains:

- Key Findings
- Risk Assessment
- Recommendations
- Risk Mitigation
- Strategic Assessment

### Strategic Insights

Contains:

- Highest Risk
- Project Feasibility
- Recommended Next Steps
- Assessment Status

The dashboard therefore gives decision-makers a quick overview while still providing access to the important assessment details.

---

## 15. Final Strategic Assessment

The final response follows this structure:

```text
PROJECT SUMMARY

RISK SUMMARY

KEY STRATEGIC RECOMMENDATIONS

RISK-BASED RECOMMENDATIONS

MITIGATION STRATEGIES

IMPROVEMENT SUGGESTIONS

SHORT-TERM ACTION PLAN

LONG-TERM ACTION PLAN

FINAL STRATEGIC ASSESSMENT
```

This structure connects project information, risk analysis, recommended actions, mitigation, and long-term planning.

---

## 16. Project Structure

```text
Failure-Prediction-AI/
│
├── app.py
├── app_streamlit.py
├── database.py
├── database.sql
├── feasibility.py
├── market_analysis.py
├── risk_engine.py
├── recommendation_engine.py
├── mitigation_engine.py
├── improvement_engine.py
├── llm_service.py
├── requirements.txt
├── README.md
│
├── templates/
│   ├── base.html
│   ├── dashboard.html
│   ├── project.html
│   ├── risk_assessment.html
│   └── placeholder.html
│
├── static/
│   ├── css/
│   │   └── style.css
│   └── js/
│       └── dashboard.js
│
└── .gitignore
```

Sensitive files such as `.env`, API keys, passwords, local databases, and virtual environments must not be committed.

---

## 17. Backend Contribution

My primary contribution was **Backend and Application Integration**.

### Responsibilities

- Developed and maintained backend application logic.
- Integrated the risk engine with the application.
- Connected project inputs to the assessment pipeline.
- Integrated SWOT and feasibility outputs.
- Integrated recommendation, mitigation, and improvement modules.
- Implemented the LangGraph workflow integration.
- Integrated Gemini AI services.
- Connected the assessment pipeline with the database layer.
- Worked on dashboard data flow and final assessment presentation.
- Supported debugging, testing, and deployment preparation.

### Main files contributed to / maintained

```text
app_streamlit.py
llm_service.py
database.py
database.sql
requirements.txt
```

The backend work focused on connecting the individual modules into one end-to-end assessment workflow.

---

## 18. Testing and Validation

### Functional Testing

The following components were tested:

- Project submission
- Risk score calculation
- Risk classification
- Success probability
- SWOT generation
- Feasibility calculation
- Recommendation generation
- Mitigation generation
- Improvement generation
- LangGraph workflow
- Gemini integration
- Database persistence
- Dashboard rendering

### AI Integration Testing

The Gemini service functions were tested independently to verify that the AI layer could be imported and invoked correctly.

The application also supports demo/fallback behavior when the API service is unavailable.

### Error Handling

The application was tested for common issues including:

- Missing AI API configuration
- AI service failures
- Invalid inputs
- Database connectivity problems
- Missing assessment outputs
- Dashboard rendering problems

---

## 19. Deployment

The application is designed for Streamlit-compatible deployment.

Deployment requires:

- GitHub repository
- `requirements.txt`
- Streamlit application entry point
- Secure environment variables
- Gemini API key configured through deployment secrets
- Database configuration

Credentials must be stored as secrets/environment variables rather than committed to GitHub.

---

## 20. Security Considerations

1. API keys are stored in environment variables.
2. Secrets are excluded using `.gitignore`.
3. Database credentials should not be hardcoded into a public repository.
4. Project data should be accessed through controlled database operations.
5. AI-generated recommendations should be treated as decision-support information.
6. Sensitive configuration values should not be displayed in the dashboard.

---

## 21. Limitations

- Risk scoring depends on the quality of project inputs.
- The current risk engine is a structured rule-based assessment rather than a trained historical failure-prediction model.
- Success probability is derived from the risk score and should not be interpreted as a calibrated probability of actual business success.
- AI recommendations depend on the availability and quality of the configured Gemini model.
- Market and competitor analysis depends on the information available to the system.
- AI outputs should be reviewed by a human before important business decisions.
- The system is intended as a decision-support tool, not a guarantee of project success or failure.

---

## 22. Future Enhancements

Potential future improvements include:

- Train a machine-learning model using historical startup/project datasets.
- Add automated market and competitor intelligence.
- Add real-time competitor monitoring.
- Add cash-flow, burn-rate, break-even, and financial scenario analysis.
- Add explainable AI for risk and recommendation generation.
- Add historical risk tracking for repeated assessments.
- Add user authentication and role-based access.
- Generate downloadable PDF assessment reports.
- Expand the LangGraph architecture with specialized agents for market, financial, technical, and strategic analysis.

---

## 23. Expected Final Outcome

The completed system provides an end-to-end platform for structured project risk assessment.

A user can submit a project, receive a quantitative risk assessment, understand strengths and weaknesses, identify major risks, obtain AI-generated recommendations, review mitigation strategies, evaluate improvement opportunities, and view the final strategic assessment through a centralized dashboard.

```text
Project Data
     ↓
Risk Analysis
     ↓
Strategic Intelligence
     ↓
AI Recommendations
     ↓
Risk Mitigation
     ↓
Improvement Planning
     ↓
Final Decision Support
```

---

## 24. Conclusion

Prediction AI – Startup & Project Risk Analyzer demonstrates how structured risk assessment, business analysis, database persistence, workflow orchestration, and generative AI can be combined into a single decision-support application.

The project progressed from project information collection and risk scoring to a complete AI-assisted workflow. The final Milestone 4 system integrates the earlier milestones into a unified application containing a dashboard, persistent storage, Gemini-based intelligence, LangGraph workflow orchestration, mitigation planning, improvement suggestions, and final strategic assessment.

The system is designed to help users identify potential problems early, understand the factors contributing to project risk, and receive structured actions for improving project viability.

---

## 25. Milestone 4 Status

**Status: Completed / Final Integration**

- [x] Streamlit dashboard
- [x] Final strategic assessment
- [x] Demo/fallback mode
- [x] Testing and deployment preparation
- [x] Final documentation

---


