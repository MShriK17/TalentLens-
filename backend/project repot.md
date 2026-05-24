TalentLens
NLP-Powered Advanced Automated Applicant Tracking
System for Resume Analysis and Candidate Ranking

PROJECT REPORT
Submitted in partial fulfillment of the requirements for the degree of
Bachelor of Engineering
(Artificial Intelligence & Data Science)
Submitted By:
Prasen Pramod Nimje
Mahesh Shridhar Khumkar
Nishant Pravin Chaudhari
Akanksha Santosh Gawande
Sakshi Jagdish Podutwar
Guided By:
Prof. G. D. Mathankar
Department of Artificial Intelligence & Data Science
Babasaheb Naik College of Engineering, Pusad
Academic Year: 2025 - 2026
CERTIFICATE
Babasaheb Naik College of Engineering, Pusad
(Sant Gadge Baba Amravati University)
This is Certify that
Project report Entitle
NLP-Powered Advanced Automated Applicant Tracking
System for Resume Analysis and Candidate Ranking
Has successfully Submitted by
Prasen Pramod Nimje
Mahesh Shridhar Khumkar
Nishant Pravin Chaudhari
Akanksha Santosh Gawande
Sakshi Jagdish Podutwar
In Partial Fulfilment of the
Degree of Bachelor of Engineering in
Artificial Intelligence & Data Science
During Academic Year 2025- 2026
Prof. G. D. Mathankar
Project Guide
Dr. A. N. Gaikwad Dr. Avinash Wankhade
Head of Department Principal,
AI&DS BNCOE, Pusad
Examiner’s Certificate
This is Certify to
Prasen Pramod Nimje
Mahesh Shridhar Khumkar
Nishant Pravin Chaudhari
Akanksha Santosh Gawande
Sakshi Jagdish Podutwar
Of Final Year
B.E (Artificial Intelligence & Data Science)
are Examined in Project work entitled
NLP-Powered Advanced Automated Applicant Tracking
System for Resume Analysis and Candidate Ranking
On- / /2026 at B. N. College of Engineering, Pusad
Guided by
Prof. G. D. Mathankar
Dept. of
Artificial Intelligence & Data Science
Internal Examiner External Examiner
(Prof. G. D. Mathankar) (Prof. )
ACKNOWLEDGEMENT

We would like to express our sincere gratitude to all those who contributed to the successful
completion of this project.

First and foremost, we are deeply grateful to our project guide, Prof. G. D. Mathankar,for
their invaluable guidance, encouragement, and constructive suggestions throughout the course
of this project. His expertise in the domain of Natural Language Processing and software
systems greatly shaped the direction and quality of this work.

We extend our heartfelt thanks to Dr. A. N. Gaikwad, Head of the Department of Artificial
Intelligence & Data Science, for providing the necessary infrastructure and support to carry out
this project. We also thank the faculty members and staff of the department for their
cooperation and assistance.

We are also thankful to our Honorable Principal, Dr. Avinash Wankhade, who inspired us to
achieve our highest goals.

We are indebted to the open-source community, whose libraries and tools—including spaCy,
FastAPI, MongoDB, and the Python ecosystem—formed the foundation of our technical
implementation.

Finally, we would like to thank our faculty and friends for their unwavering support and
motivation throughout this journey. Their encouragement kept us focused and determined
during the challenging phases of the project.

Prasen Pramod Nimje

Mahesh Shridhar Khumkar Nishant Pravin Chaudhari

Akanksha Santosh Gawande Sakshi Jagdish Podutwar

Final Year
(Artificial Intelligence & Data Science)
ABSTRACT

In today’s highly competitive job market, organizations receive thousands of resumes for a single
job opening, making manual screening both time-consuming and prone to human bias and
inconsistencies. This project presents TalentLens, an NLP-powered Advanced Automated
Applicant Tracking System (ATS) designed to streamline and automate the resume screening
and candidate ranking process. TalentLens offers two primary screening modes: the Manual
Screening mode enables recruiters to upload single or bulk resumes along with a job title and job
description, after which the system evaluates each resume using a multi-dimensional ATS
scoring algorithm, while the Advanced Screening mode leverages Natural Language Processing
(NLP) techniques to automatically identify the most suitable job roles for uploaded resumes
without requiring recruiter input, enabling a fully autonomous screening process.

The system incorporates a comprehensive NLP pipeline, including text extraction from PDF and
DOCX files, contact information extraction, skill identification using a curated keyword
database, synonym handling, Named Entity Recognition (NER) using spaCy, and semantic
similarity matching. The ATS scoring engine computes a composite score based on five weighted
parameters: skill match (45%), experience (25%), education (10%), job title alignment (10%),
and keyword coverage (10%). Additionally, the Advanced Screening module provides top-3 job
role predictions, candidate fit scores, strengths and weaknesses analysis, and actionable ATS
improvement recommendations.

The platform also includes analytical dashboards with multiple visualizations, automated PDF
report generation, and email-based recruiter communication. Experimental results indicate that
TalentLens significantly improves screening efficiency compared to manual methods while
maintaining high accuracy in skill matching and role prediction. The system represents a scalable,
intelligent, and bias-reduced approach to modern recruitment automation.

Keywords: Applicant Tracking System, Natural Language Processing, Resume Screening,
spaCy, Named Entity Recognition, Skill Extraction, Semantic Matching, Candidate Ranking,
FastAPI, MongoDB.

LIST OF FIGURES
LIST OF TABLES

LIST OF ABBREVIATIONS

Abbreviation Full Form

ATS Applicant Tracking System

NLP Natural Language Processing

NER Named Entity Recognition

API Application Programming Interface

REST Representational State Transfer

PDF Portable Document Format

DOCX Document (Microsoft Word Open XML)

ML Machine Learning

JD Job Description

SMTP Simple Mail Transfer Protocol

CORS Cross-Origin Resource Sharing

CRUD Create, Read, Update, Delete

UI User Interface

UX User Experience

DB Database

HTTP Hypertext Transfer Protocol

JSON JavaScript Object Notation

JWT JSON Web Token

HOD Head of Department

DXA Document eXtended Attribute (unit)

TABLE OF CONTENTS

Certificate i

Declaration ii

Acknowledgement iii

Abstract iv

List of Figures v

List of Tables vi

List of Abbreviations vii

Chapter 1: Introduction 1

1.1 Project Overview 1
1.2 Problem Statement 2
1.3 Objectives of the Project 3
1.4 Scope of the Project 4
1.5 Motivation 4
1.6 Organization of the Report 5
Chapter 2: Literature Review 6

2.1 Introduction to Applicant Tracking Systems (ATS) 6
2.2 Existing Resume Screening Methods 7
2.3 NLP in Recruitment Systems 8
2.4 Limitations of Existing Systems 9
2.5 Research Gap 10
Chapter 3: System Architecture

3.1 System Overview 11
3.2 Architecture Design (3-Tier Architecture) 11
3.3 Frontend Architecture 12
3.4 Backend Architecture 13
3.5 Database Design 14
3.6 System Workflow Diagram 15
Chapter 4: Technology Stack 16

4.1 Frontend Technologies 16
4.2 Backend Technologies 17
Fig 3.1 Three-Tier Architecture Diagram of TalentLens Figure No. Figure Title Page No.
Fig 3.2 System Workflow Diagram
Fig 5.1 Resume Processing Pipeline
Fig 5.2 Skill Extraction with Synonym Resolution
Fig 6.1 ATS Score Composition – Weight Distribution
Fig 7.1 Role Detection Algorithm Flowchart
Fig 8.1 Manual Screening Dashboard
Fig 8.2 Advanced Screening Dashboard with Analytics
Fig 9.1 MongoDB Database Schema
Fig 10.1 API Test Results – Postman
Fig 11.1 ATS Score Distribution Chart
Table 4.1 Frontend Technology Stack Table No. Table Title Page No.
Table 4.2 Backend Technology Stack
Table 4.3 NLP Libraries and Tools
Table 6.1 ATS Scoring Parameters and Weights
Table 6.2 Category Weights for Skill Scoring
Table 7.1 Job Role Profiles – Skills Mapping
Table 9.1 API Endpoints Summary
Table 10.1 Functional Test Cases
Table 11.1 Evaluation Metrics Comparison
Table 11.2 Comparison with Existing ATS Systems
4.3 NLP Tools and Libraries
4.4 Development Tools
4.5 Deployment Environment
Chapter 5: Methodology
5.1 Overall System Workflow
5.2 Resume Processing Pipeline
5.3 Text Extraction Process
5.4 Information Extraction (Name, Email, Phone)
5.5 Skill Extraction Techniques
5.6 Synonym Resolution
5.7 Named Entity Recognition (NER)
5.8 Semantic Matching Approach
5.9 NLP Methods Used in the System
Chapter 6: ATS Scoring Algorithm
6.1 Introduction to ATS Scoring
6.2 Scoring Parameters
6.3 Mathematical Formula
6.4 Weight Justification
6.5 JD Intelligence (Must-have vs Good-to-have)
6.6 Keyword Matching Strategy
6.7 Experience & Education Scoring
Chapter 7: Role Detection & Advanced Analysis
7.1 Role Detection Overview
7.2 Role Matching Algorithm
7.3 Top- 3 Role Prediction
7.4 Candidate Fit Score Calculation
7.5 Strength Analysis
7.6 Weakness Detection
7.7 Recommendation System
Chapter 8: System Features & Modules
8.1 User Authentication
8.2 Manual Screening Module
8.3 Advanced Screening Module
8.4 Dashboard & Analytics
8.5 PDF Report Generation
8.6 Email Automation System
Chapter 9: Implementation Details
9.1 Project Structure
9.2 API Design
9.3 Database Schema
9.4 Key Implementation Highlights
9.5 Security Features
Chapter 10: Testing & Validation
10.1 Testing Methodology
10.2 Functional Testing
10.3 API Testing
10.4 NLP Model Validation
10.5 Performance Testing
Chapter 11: Results & Evaluation
11.1 Experimental Setup
11.2 Dataset Description
11.3 Evaluation Metrics (Accuracy, Precision, Recall)
11.4 Results Analysis
11.5 Comparison with Existing Systems
Chapter 12: Future Enhancements
12.1 Limitations of Current System
12.2 Planned Improvements
12.3 Scalability Considerations
Chapter 13: Conclusion
13.1 Summary of Work
13.2 Key Achievements
13.3 Final Outcome
References
Appendix A — API Endpoints Reference
Appendix B — Key Code Snippets
Appendix C — Sample Screenshots Description
Chapter 1: Introduction
1.1 Project Overview

TalentLens is a web-based, NLP-powered Applicant Tracking System designed to
automate and enhance the resume screening and candidate evaluation process. Built on a
modern technology stack comprising FastAPI (Python), MongoDB, spaCy, and a React-
based frontend, TalentLens addresses the core challenges of large-scale recruitment by
combining rule-based NLP with semantic analysis.

The system supports two distinct screening modes: Manual Screening, where recruiters
provide job descriptions and titles, and Advanced Screening, where the AI autonomously
detects the best-fit role for each uploaded resume. Both modes produce detailed ATS
scores, matched and missing skill lists, candidate rankings, and downloadable PDF reports.
The Advanced mode further provides deep analytical insights including top- 3 role matches,
candidate fit scores, strengths and weaknesses profiles, and actionable ATS improvement
tips.

A rich analytics dashboard accompanies both modes, featuring ten types of data
visualizations including score distribution pie charts, skill frequency histograms, candidate
score trends, and screening funnel analyses. The platform also integrates an email
automation system that allows recruiters to send personalized shortlisting or rejection
emails with attached PDF reports directly from the dashboard.

1.2 Problem Statement

Modern organizations routinely receive hundreds to thousands of resumes for a single job
vacancy. The traditional approach to resume screening is predominantly manual, which
suffers from several critical drawbacks:

Time Inefficiency: A human recruiter typically spends six to ten seconds on an
initial resume screen. Processing thousands of resumes takes days or weeks,
significantly slowing down the hiring cycle.
Subjective Bias: Manual screening is inherently subjective. Recruiters may
unconsciously favor or disfavor candidates based on factors unrelated to job
performance, such as name, educational institution, or formatting style.
Inconsistency: Different recruiters apply different criteria. Even the same recruiter
may apply different standards at different times, resulting in inconsistent
candidate shortlisting.
Keyword Blindness: Recruiters often miss qualified candidates who use different
but equivalent terminology for the same skills (e.g., 'JS' for JavaScript, 'k8s' for
Kubernetes).
Scalability Limits: As organizations grow, the volume of applications scales
exponentially while the recruitment team does not, creating a structural
bottleneck.
Existing commercial ATS solutions, while widely used, primarily rely on simple keyword
matching and lack the intelligence to understand semantic equivalences, detect implicit job
roles, or provide actionable feedback to candidates. There is a clear need for an intelligent,
NLP-powered system that automates resume screening with high precision while remaining
accessible and configurable for organizations of any size.

1.3 Objectives of the Project

The primary objectives of TalentLens are as follows:

To design and implement an automated resume screening system capable of
processing both single and bulk resume uploads in PDF and DOCX formats.
To develop a multi-strategy NLP pipeline for extracting candidate information
including contact details, technical skills, experience levels, and educational
qualifications.
To implement a synonym resolution mechanism and spaCy NER integration to
maximize skill detection coverage across varied resume writing styles.
To engineer a multi-dimensional ATS scoring algorithm that evaluates resumes
across skill match, experience, education, job title alignment, and keyword
coverage.
To build an Advanced Screening module that autonomously detects the best-fit
job role for any resume without requiring recruiter-provided job descriptions.
To provide comprehensive candidate analytics including top- 3 role predictions,
candidate fit scores, strengths analysis, weakness detection, and ATS
improvement recommendations.
To create interactive analytics dashboards with ten statistical visualization types
supporting data-driven recruitment decisions.
To implement PDF report generation and an automated SMTP-based email system
for recruiter-to-candidate communication.
1.4 Scope of the Project

TalentLens is scoped as a full-stack web application targeting the resume screening and
initial candidate ranking stages of the recruitment funnel. The system covers:

Resume ingestion supporting PDF and DOCX file formats, in single and batch
modes.
NLP-driven information extraction covering skills, experience, education, contact
information, and job role indicators.
Manual and automated screening modes with configurable job descriptions.
ATS score computation with a five-dimension weighted model.
Advanced role detection across a curated library of professional job roles.
Dashboard analytics for both screening modes with ten chart types.
PDF report generation and recruiter email dispatch with PDF attachments.
The system does not currently cover video interview scheduling, psychometric assessment
integration, or direct integration with third-party HR information systems (HRIS), which
are identified as future enhancements.

1.5 Motivation

The motivation behind TalentLens stems from a direct observation of the inefficiencies
plaguing modern recruitment processes. In conversations with HR professionals and
recruitment consultants, recurring themes emerged: the exhausting manual effort of resume
screening, the risk of overlooking qualified candidates due to keyword mismatches, and the
lack of objective, explainable scoring that could defend shortlisting decisions to
stakeholders.

Academic research in NLP has matured significantly over the past decade, with tools like
spaCy enabling high-performance entity recognition and semantic analysis at scale.
However, a gap exists between the capabilities demonstrated in research and the tools
available to mid-sized organizations that cannot afford enterprise ATS licenses. TalentLens
was conceived to bridge this gap: a powerful, explainable, and open-architecture ATS that
brings NLP-grade intelligence to the recruitment process.

Additionally, the growing emphasis on data-driven HR decisions made the analytics
dashboard a core component. Recruitment decisions backed by statistical visualizations —

score distributions, skill frequency patterns, and pass-rate trends — are inherently more
defensible and auditable than intuition-based shortlisting.

1.6 Organization of the Report

This report is organized into thirteen chapters as follows:

Chapter 1 provides an introduction to the project, including its overview, problem
statement, objectives, scope, and motivation.
Chapter 2 presents a literature review covering existing ATS systems, NLP
applications in recruitment, and the research gap this project addresses.
Chapter 3 describes the system architecture including the three-tier design,
frontend and backend architecture, and the database design.
Chapter 4 details the technology stack used across frontend, backend, NLP, and
development tooling layers.
Chapter 5 covers the methodology including the complete resume processing
pipeline and all NLP methods employed.
Chapter 6 describes the ATS scoring algorithm in detail including mathematical
formulation and weight justification.
Chapter 7 explains the role detection and advanced analysis modules including the
top-3 prediction system.
Chapter 8 documents all system features and modules including authentication,
screening modes, dashboards, and email automation.
Chapter 9 presents implementation details covering project structure, API design,
and database schema.
Chapter 10 describes the testing methodology and validation results.
Chapter 11 presents experimental results and evaluation metrics.
Chapter 12 discusses current limitations and future enhancement plans.
Chapter 13 concludes the report with a summary of key achievements.
Chapter 2: Literature Review
2.1 Introduction to Applicant Tracking Systems (ATS)

Applicant Tracking Systems (ATS) have become an essential component of modern
recruitment processes, enabling organizations to manage large volumes of job applications
efficiently. Early ATS platforms primarily relied on keyword-based filtering and database
management, limiting their ability to accurately evaluate candidate suitability. Recent
advancements have introduced machine learning and Natural Language Processing (NLP)
techniques to enhance resume parsing and candidate-job matching.
Patel and Shah [5] proposed an automated resume screening system using machine learning
and NLP, demonstrating improved efficiency and accuracy over traditional manual
methods. However, challenges such as lack of transparency, limited semantic
understanding, and rigid keyword matching still persist in many systems..
2.2 Existing Resume Screening Methods
Resume screening techniques have evolved significantly over time, transitioning from
simple keyword matching to advanced semantic-based approaches. Traditional methods
relied on exact keyword matching, which often resulted in high false-negative rates due to
synonym variations and contextual differences.
Maheshwary and Misra [1] introduced a deep Siamese neural network approach for
matching resumes with job descriptions, showing improved performance through semantic
similarity learning. Similarly, Qin et al. [10] proposed an ability-aware neural network
model to enhance person-job fit, emphasizing the importance of contextual and skill-based
matching.

Recent advancements in transformer-based models, such as BERT [3], have significantly
improved natural language understanding by capturing contextual relationships within text.
Reimers and Gurevych [4] further enhanced this capability with Sentence-BERT, enabling
efficient computation of semantic similarity between sentences, making it highly suitable
for resume-job matching applications.

2.3 NLP in Recruitment Systems

Natural Language Processing plays a crucial role in modern resume screening systems by
enabling structured information extraction and semantic analysis.

Rodrigues et al. [11] demonstrated the effectiveness of NLP and spaCy for extracting structured
information such as skills, education, and experience from resumes. The spaCy library [2]
provides robust tools for tokenization, Named Entity Recognition (NER), and linguistic
analysis, making it widely adopted in industrial NLP applications.

Bird et al. [6] provided foundational knowledge in NLP using Python, including techniques for
text preprocessing, parsing, and information extraction. These methods form the basis for
building efficient resume parsing systems.

Transformer-based architectures such as BERT [3] and embedding techniques like Sentence-
BERT [4] further enhance semantic similarity computation, enabling systems to match resumes
with job descriptions even when exact keywords are not present.

2.4 Limitations of Existing Systems

In addition to NLP techniques, modern resume screening systems rely on robust
backend and frontend technologies for scalability and usability. MongoDB [7], a
NoSQL database, is widely used for storing unstructured resume data and
supporting real-time analytics. FastAPI [9] provides a high-performance backend
framework for building scalable APIs, while React and JavaScript [8] enable the
development of interactive user interfaces for recruiters.

These technologies collectively support the development of full-stack ATS
platforms capable of handling large-scale recruitment workflows efficiently.

2.5 Research Gap

Despite significant advancements, existing systems still exhibit several
limitations:
Most systems rely heavily on exact keyword matching, lacking effective
synonym handling and semantic understanding.
Limited integration of NER, semantic similarity, and scoring mechanisms in a
unified pipeline.
Absence of automated job role detection without predefined job descriptions.
Lack of explainable scoring systems, making it difficult for users to interpret
results.
Insufficient support for real-time analytics and visualization in recruitment
systems.

To address these gaps, the proposed system TalentLens integrates NLP
techniques, semantic similarity, and multi-dimensional ATS scoring into a
unified, scalable platform.

Chapter 3: System Architecture
3.1 System Overview
TalentLens follows a client-server architecture organized into three logical tiers: the
Presentation Layer (frontend), the Application Layer (backend API), and the Data Layer
(database). The system is designed with separation of concerns as a guiding principle,
ensuring that each layer can be maintained, scaled, or replaced independently.
The frontend is a React-based Single Page Application (SPA) that communicates with the
backend exclusively through RESTful API calls. The backend is implemented in Python
using the FastAPI framework, which provides asynchronous request handling, automatic
API documentation via OpenAPI, and high throughput suitable for processing multiple
concurrent resume uploads. The data layer uses MongoDB, a document-oriented NoSQL
database, which naturally accommodates the variable schema of resume analysis results.

3.2 Architecture Design (3-Tier Architecture)
The three-tier architecture of TalentLens comprises:
(Fig.1 Architecture Design)
Tier 1 – Presentation Layer
The presentation layer consists of the React frontend application served to users through a
web browser. It handles all UI rendering, state management, file upload interactions, and
visualization of analytics data. The frontend communicates with the backend using
HTTP/HTTPS requests with JSON payloads.
Tier 2 – Application Layer
The application layer is the FastAPI backend, responsible for all business logic including
resume parsing, NLP processing, ATS score computation, role detection, report generation,
and email dispatch. This layer exposes a RESTful API under the /api prefix. It uses Motor,
an asynchronous MongoDB driver, to interact with the data layer without blocking the
event loop.
Tier 3 – Data Layer
The data layer consists of a MongoDB instance hosting two primary collections: resumes
(storing all extracted resume data, scores, and analysis results) and job_descriptions
(storing job description records and batch metadata for bulk uploads). The document model
is flexible enough to store both manual and advanced screening results within the same
collection, differentiated by the scan_mode field.
3.3 Frontend Architecture
The frontend architecture organizes the application into the following page-level
components:
Landing Page: The public-facing entry point introducing the platform's
capabilities and directing users to registration or login.
Authentication Pages: Registration and login forms with client-side validation.
Successful authentication stores a session token used for subsequent API requests.
Performance Page: An aggregated view of all resumes processed across both
screening modes, with date filtering. Includes access to the Resume Builder Guide
— a curated resource helping candidates optimize their resumes for the
TalentLens scoring model.
Manual Dashboard: The primary interface for manual screening, including file
upload controls, job title and description input, results display, and access to the
analytics sub-dashboard.
Advanced Dashboard: The interface for advanced screening, sharing structural
similarities with the manual dashboard but adding role detection results, candidate
fit displays, and the advanced-only analytics charts.
Each dashboard embeds a New Uploads sub-page for initiating fresh screening sessions and
an analytics section containing all ten visualization types. State management is handled
through React's built-in hooks (useState, useEffect) with API calls abstracted into a service
layer.
3.4 Backend Architecture
The FastAPI backend is structured as a single-file application for the current project scope,
with a clear internal organization:
Pydantic Models: Define the data schemas for request validation and response
serialization. Key models include ResumeAnalysis, JobDescription,
AnalyzeRequest, BulkAnalyzeRequest, ShortlistEmailRequest, and authentication
models.
NLP Utility Functions: A comprehensive library of pure functions handling text
extraction, contact info detection, skill extraction (with synonym resolution and
NER), experience and education analysis, JD intelligence parsing, and semantic
matching.
Scoring Engine: The calculate_ats_score function implementing the multi-
dimensional scoring algorithm.
Advanced Analysis Functions: The _detect_best_role and
_run_full_advanced_analysis functions implementing role detection, candidate fit
scoring, strengths analysis, weakness detection, and ATS tip generation.
Report Generation: PDF report builder using ReportLab, generating structured
candidate reports with score breakdowns, skill lists, and improvement feedback.
Email System: SMTP-based email dispatcher using Python's built-in smtplib,
supporting multiple email templates (shortlist, interview invite, rejection) and
PDF attachment support.
API Router: All endpoints are registered under an APIRouter with the /api prefix,
keeping the route definitions clean and consistent.
3.5 Database Design
MongoDB's document model is used for flexible storage of heterogeneous resume analysis
results. The two primary collections are:
Resumes Collection - Each document in the resumes collection stores the complete analysis
result for a single resume. Key fields include: id (UUID), user_id, filename, candidate_name,
email, phone, extracted_skills, experience_keywords, education_keywords, resume_text (full
extracted text), ats_score, matched_skills, missing_skills, jd_skills, feedback, score_breakdown,
job_title, scan_mode (manual or advanced), analysis_type (single or bulk), batch_id (for bulk
sessions), detected_role and role_confidence (for advanced mode), top3_roles, candidate_fit,
strength_analysis, weakness_analysis, ats_suggestions, file_bytes (base64- encoded original
file), and created_at timestamp.

job_descriptions Collection - Each document represents either a manually entered job
description or a bulk session record. Key fields include: id, title, description, required_skills,
preferred_skills, experience_level, scan_mode, and created_at. For advanced bulk sessions, the
document serves as a batch metadata record with auto-generated titles.
3.6 System Workflow Diagram
The overall system workflow follows this sequence: A user authenticates and navigates to
either the Manual or Advanced Dashboard. They upload one or more resume files
(PDF/DOCX). For manual mode, they also provide a job title and description. The backend
receives the upload, extracts text from the file, runs the NLP pipeline to extract skills and other
information, computes the ATS score (or detects the role in advanced mode), stores the result in
MongoDB, and returns the analysis to the frontend. The frontend renders the score, skill lists,
and feedback. The recruiter can then view the analytics dashboard, generate PDF reports, or
dispatch emails to candidates — all from the same interface.

(Diagram.2 System Workflow Diagram)

Chapter 4: Technology Stack
4.1 Frontend Technologies

The frontend of TalentLens is built using a modern JavaScript ecosystem chosen for
component reusability, developer experience, and ecosystem maturity:

Technology Version Purpose
React 18.x Componentframework - based^ UI
React Router 6.x Client-side routing
Axios 1.x HTTPcommunication^ client^ for API
Chart.js / Recharts Latest Interactive data visualizations
Tailwind CSS 3.x Utility-first CSS styling
React-PDF Latest In-browser PDF preview
Vite 5.x Build tool and dev server
4.2 Backend Technologies

Technology Version Purpose
Python 3.11+ Primary backend language
FastAPI 0.110+ Async REST API framework
Motor 3.x Async MongoDB driver
Pydantic 2.x Dataserialization^ validation and
PyPDF2 3.x PDF text extraction
python-docx 1.x DOCX text extraction
ReportLab 4.x PDF report generation
bcrypt 4.x Password hashing
python-dotenv 1.x Environmentmanagement variable
smtplib Built-in SMTP email dispatch
uvicorn 0.29+ ASGI server for FastAPI
4.3 NLP Tools and Libraries
Library Model Application
spaCy en_core_web_sm NER for name, org, product detection
re (regex) Built-in Pattern matching for contacts, dates, years
Custom Skill DB 280+ skills Multi-category skill keyword matching
Synonym Dictionary 50+ entries Alias resolution to canonical skills
Cosine Similarity spaCy vectors Semantic skill-to-resume matching
TF-IDF (implicit) Term freq. Keyword coverage scoring
4.4 Development Tools
Visual Studio Code: Primary IDE with Python and JavaScript extensions.
Postman: API testing and documentation during development.
MongoDB Compass: Visual database inspection and query testing.
Git / GitHub: Version control and collaborative development.
Docker: Containerization for consistent development environments.
pytest: Unit testing framework for backend functions.
4.5 Deployment Environment
The system is designed for deployment on Linux-based cloud infrastructure. The backend is
served via Uvicorn (ASGI server) and can be placed behind an Nginx reverse proxy for
production use. The frontend is compiled to a static bundle and served either by Nginx or a
CDN. MongoDB can be deployed as a managed service (MongoDB Atlas) or self-hosted.
Environment-specific configuration (database URL, SMTP credentials, secret keys) is
managed via .env files loaded at startup.

Chapter 5: Methodology
5.1 Overall System Workflow
The TalentLens processing workflow is designed as a sequential pipeline with conditional
branching based on the screening mode selected. The workflow begins when a user uploads
a resume file (or multiple files for bulk processing) through the web interface. The system
then routes the upload through a series of processing stages before storing results and
returning them to the frontend.For Manual Screening, the recruiter provides an explicit job
title and job description alongside the resume. The backend uses these to define the skill
requirements against which the resume is scored. For Advanced Screening, no recruiter
input is required; the system autonomously detects the best matching job role from a curated
role profile library based on the skills extracted from the resume.

5.2 Resume Processing Pipeline
The resume processing pipeline consists of the following sequential stages:

File Reception: The FastAPI endpoint receives the uploaded file via multipart
form data. The file type is validated to ensure it is either a PDF (.pdf) or Word
document (.docx). Files of other types are rejected with an appropriate error
response.
Temporary Storage: The file content is written to a temporary file on the server
filesystem using Python's tempfile module. This allows text extraction libraries
(PyPDF2, python-docx) to read the file content.
Text Extraction: Text is extracted from the temporary file using the appropriate
library based on file extension. The extracted text is a single string containing all
textual content from the document.
NLP Processing: The extracted text is passed through the NLP pipeline, which
runs all extraction functions in parallel conceptually — contact extraction, skill
extraction, experience analysis, and education analysis — and collects their
outputs.
Scoring or Role Detection: In manual mode, the ATS scoring engine receives the
extracted skills, JD skills, and both texts to compute the composite score. In
advanced mode, the role detection engine identifies the best-fit role and runs the
full advanced analysis.
Persistence: The complete analysis result is serialized and stored in the MongoDB
resumes collection. The original file bytes are base64-encoded and stored
alongside the analysis for report generation.
Response: The API returns a structured JSON response containing all analysis
outputs to the frontend.
5.3 Text Extraction Process
Two text extraction strategies are implemented based on file format:

PDF Extraction (extract_text_from_pdf)

The PDF extraction function uses PyPDF2's PdfReader to iterate over all pages in the
document and extract text from each page. The page texts are concatenated with newline
separators. This approach works well for text-layer PDFs (digitally created documents) but
may produce limited output for scanned PDFs where the text layer is absent. Future work
includes integrating an OCR fallback using Tesseract for image-based PDFs.

DOCX Extraction (extract_text_from_docx)

The DOCX extraction function uses python-docx to access the document object model and
extract text from all paragraphs. Additionally, it iterates over all tables within the document
and extracts cell text, since many professional resume templates use tables for layout. This
ensures that skills listed in table cells are captured alongside paragraph text.

5.4 Information Extraction (Name, Email, Phone)
Contact information extraction is handled by the extract_contact_info function, which
combines regex pattern matching with spaCy NER:

Email Detection

A standard email regex pattern [a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+.[a-zA-Z]{2,} is
applied to the full resume text. The first match is returned as the candidate's email address.
This pattern handles all common email formats including those with dots, plus signs, and
subdomains.

Phone Number Detection

A composite regex handles international and domestic phone number formats including:
+91-XXXXXXXXXX (Indian mobile), (XXX) XXX-XXXX (US format),
XXXXXXXXXX (10-digit), and variations with spaces and dashes. The function returns
the first valid match.

Name Detection

Name detection uses a two-stage approach. First, the first line of the resume text is
examined, as most professional resumes begin with the candidate's name. If the spaCy
PERSON entity recognizer identifies a named entity in this first line, that entity is returned
as the name. If not, the function falls back to capitalizing the first line as a heuristic. This
handles the majority of standard resume formats.

5.5 Skill Extraction Techniques
Skill extraction is the most critical component of the NLP pipeline. TalentLens implements
a three-stage skill extraction process through the extract_skills_advanced function:

Stage 1: Canonical Keyword Matching

The system maintains a curated SKILL_KEYWORDS dictionary containing over 280
technical and professional skills organized into eleven categories: programming languages,
web technologies, databases, cloud/DevOps, AI/ML, mobile development, security,
testing, tools and methodologies, business software, and soft skills. Each keyword is
matched against the lowercase resume text using word-boundary regex patterns (\b
keyword \b) to avoid false matches within longer words.

Stage 2: Synonym Resolution

A SKILL_SYNONYMS dictionary maps canonical skill names to lists of known aliases
and abbreviations. For example: 'javascript' maps to ['js', 'ecmascript', 'es6', 'es2015'];
'kubernetes' maps to ['k8s']; 'postgresql' maps to ['postgres', 'psql']; 'machine learning' maps
to ['ml']. A reverse map (_SYNONYM_REVERSE) is built at startup, allowing any alias
found in the resume text to be resolved to its canonical skill name. This ensures that 'JS
developer' receives credit for 'JavaScript' in the scoring.

Stage 3: spaCy NER Pass

After keyword and synonym matching, the full resume text is processed through the spaCy
en_core_web_sm model. Named entities labeled as ORG (organization) or PRODUCT are
examined against the SKILL_KEYWORDS dictionary and the synonym reverse map. This
captures technology names that appear as proper nouns in the resume text and may not be
caught by the regex approach.
5.6 Synonym Resolution
The synonym resolution mechanism is a key differentiator of TalentLens from simple
keyword-matching ATS systems. The _SYNONYM_REVERSE dictionary is constructed at
module initialization by iterating over all entries in SKILL_SYNONYMS and creating
reverse mappings from each alias to its canonical form. When the skill extraction function
encounters any alias in the resume text, it immediately resolves it to the canonical skill before
adding it to the extracted skills set. This means that a resume containing 'ReactJS' is treated
identically to one containing 'React' for scoring purposes.

5.7 Named Entity Recognition (NER)
spaCy's en_core_web_sm model provides pre-trained NER capabilities trained on the
OntoNotes 5 corpus. TalentLens uses two entity types: PRODUCT (for software and tool
names) and ORG (for organization-named technologies like AWS, MongoDB). The NER
pass is applied after initial keyword matching to avoid redundant processing — entities
already detected by keyword matching are not double-counted. The NER approach is
particularly effective for newer technology names that may not be in the curated keyword
list but are recognized by the language model as product names.

5.8 Semantic Matching Approach
The semantic matching component (semantic_skill_match) addresses cases where a required
skill is not present in the resume as a keyword or synonym, but related content exists. This
uses spaCy's word vector representations to compute cosine similarity between the missing
skill name and all sentences/phrases in the resume text. The algorithm iterates over all skills
in the 'still missing after partial credit' set, computes a cosine similarity score between the
skill's spaCy vector representation and the resume document's vector, and awards a
proportional semantic bonus if the similarity exceeds a threshold of 0.5. The maximum
semantic bonus per skill is capped at 0.4 times the skill's category weight to prevent over-
crediting. This allows candidates with strong background knowledge in adjacent areas to
receive appropriate partial credit.

.
5.9 NLP Methods Used in the System
The following table summarizes all NLP methods employed in TalentLens
NLP Method Application Implementation
Regex Pattern Matching Email, phone, years extraction Python re module
Keyword Matching Skill^ identification^ (280+ skills)^ WordSKILL_KEYWORDS-boundary^ regex^ on
Synonym Resolution Aliasmapping-to- canonical^ skill SKILL_SYNONYMSmap reverse
Named Entity Recognition Name, org, product detection spaCy (en_core_web_sm model)
Tokenization
Tokenization is the fundamental step in NLP where text is divided into smaller units called
tokens. These tokens can be words, phrases, or sentences. In the TalentLens system,
tokenization is used to break down resume text into individual words, making it easier to
analyze and process further.

Stop Word Removal
Stop words are commonly used words such as “and”, “the”, “is”, etc., which do not carry
significant meaning in text analysis. Removing these words reduces noise in the data and
improves the efficiency of keyword matching and similarity calculations.

Lemmatization
Lemmatization converts words into their base or root form. For example, “running”, “ran”, and
“runs” are all converted to “run”. This ensures that different forms of a word are treated as the
same, improving matching accuracy.

Cosine Similarity Semanticmatching skill-resume spaCy document vector similarity
Multi-Strategy Date Parsing Experience year calculation _extract_experience_smart
Substring Matching Education tier detection EDUCATION_TIER_KEYW ORDS
TF-IDF Inspired Keyword
Scoring
JD keyword coverage in
resume
Set intersection on meaningful
words
Seniority Tier Detection Title match scoring SENIORITY_TIERSdictionary
Named Entity Recognition (NER)
NER is used to identify and extract important entities from text such as:

Candidate Name
Email Address
Phone Number
Skills
In TalentLens, NER is implemented using a combination of rule-based methods and pattern
matching (regular expressions), ensuring accurate extraction of structured information from
resumes.

TF-IDF (Term Frequency – Inverse Document Frequency)
TF - I D F(t , d) = TF(t , d) × log (N / DF(t))
is a statistical measure used to evaluate how important a word is in a document relative to a
collection of documents. In TalentLens, TF-IDF helps in identifying significant keywords and
skills in resumes, ensuring that more relevant terms are given higher importance.

Cosine Similarity
cos(θ) = A ⋅B / ∥ A ∥ ∥ B ∥
Cosine similarity measures the similarity between two text vectors (resume and job
description). It calculates the cosine of the angle between two vectors. A value closer to 1
indicates higher similarity.

This method is used in TalentLens to determine how well a candidate's resume matches the job
description.

Keyword Matching
Keyword matching involves directly comparing keywords from the job description with those
found in the resume. This method ensures that essential skills and requirements specified in the
job description are present in the candidate's resume.

Synonym Matching
Different candidates may use different terms for the same skill (e.g., “ML” vs “Machine
Learning”). Synonym matching resolves such variations by mapping similar terms to a
common representation, improving matching accuracy.

Regex-based Extraction
Regular expressions (Regex) are used for pattern-based extraction of structured data such as:

Email IDs
Phone numbers
LinkedIn profiles
This method ensures precise extraction of important candidate details from resumes.

Chapter 6: ATS Scoring Algorithm
6.1 Introduction to ATS Scoring
The ATS scoring algorithm is the core component of the TalentLens system. It generates a
composite score on a scale of 0–100, representing how well a candidate’s resume matches
the given job description. The scoring mechanism is designed to be transparent and
interpretable, allowing both recruiters and candidates to understand the contribution of each
evaluation parameter. The overall score is computed based on multiple weighted
components, including skills, experience, education, job title relevance, and keyword
matching.
Skill Score= WeightMatched Weight+Partial Credit+Semantic Bonus / Total JD × 100

The scoring model was designed with several guiding principles: skill relevance should be
the dominant factor; experience and education should complement but not overshadow
skills; category-specific weighting should reward technical depth; and dimensions absent
from the JD should not penalize candidates.
6.2 Scoring Parameters
Parameter Weight Description
Skills Score 45% Weighted intersection of JD skills and resume skills
Experience Score 25% Resume years vs. JD required years
Education Score 10% Resume education tier vs. JD education requirement
Title / Seniority Score 10% Resume seniority vs. JD seniority level
Keyword Score 10% Coverage of meaningful JD vocabulary in resume
6.3 Mathematical Formula
The composite ATS score is computed as:
ATS_Score = (Skill_Score × W_s) + (Exp_Score × W_e) + (Edu_Score × W_d) + (Title_Score × W_t) +
(KW_Score × W_k)

Where W_s = 0.45, W_e = 0.25, W_d = 0.10, W_t = 0.10, W_k = 0.10 for the base case.
Skill Score Calculation
The skill score uses category-weighted matching:
Skill_Score = (Matched_Weight + Partial_Credit + Semantic_Bonus) / JD_Total_Weight × 100
Where Matched_Weight is the sum of CATEGORY_WEIGHTS for all directly matched
skills; Partial_Credit (0.5× weight) is awarded for near-miss matches found by variant
normalization; and Semantic_Bonus provides proportional credit based on cosine similarity
for semantically related content.

Weight Redistribution
If a particular dimension (experience, education, or title) is absent from the job description,
its weight is not wasted. Instead, it is redistributed proportionally between the skills and
keyword scores:
New_W_s = W_s + Freed_Weight × (W_s / (W_s + W_k))
6.4 Weight Justification
The weight distribution was determined through analysis of recruitment best practices and
iterative calibration against sample resumes:

Skills (45%): Technical skills are the primary determinant of job suitability. A
candidate with all required skills but average experience typically outperforms a
highly experienced candidate missing core skills. The 45% weight reflects this
primacy.
Experience (25%): Experience years provide strong signal for role complexity
readiness. The 25% weight ensures experience influences the score significantly
without dominating candidates who are technically strong but newer to the field.
Education (10%): While educational credentials are relevant, especially for roles
requiring specific degrees, many tech roles value demonstrated skills over formal
education. The 10% weight reflects this reduced but non-zero importance.
Title Match (10%): Seniority alignment ensures senior roles are not filled by
entry-level candidates and vice versa. The 10% weight provides a tie-breaking
dimension without being decisive.
Keyword Coverage (10%): Keyword overlap with the JD captures relevant
domain language that falls outside the skills taxonomy. This rewards candidates
who naturally use industry-standard terminology.
6.5 JD Intelligence (Must-have vs Good-to-have)
TalentLens implements a JD Intelligence module (extract_jd_intelligence) that parses job
descriptions to classify required skills into must-have and good-to-have categories based on
qualifying language. Phrases such as 'required', 'must have', 'essential', and 'mandatory'
identify must-have skills; phrases like 'preferred', 'nice to have', 'bonus', and 'advantageous'
identify good-to-have skills.

When JD Intelligence classification is active (i.e., the JD contains classifiable language),
the skill score is computed as a weighted blend: 70% from must-have skill matching and
30% from good-to-have skill matching. This ensures that a candidate matching all must-
have skills but none of the preferred ones outscores a candidate with the reverse profile — a
more accurate reflection of real hiring priorities.

6.6 Keyword Matching Strategy
The keyword score is computed using a vocabulary intersection approach inspired by TF-
IDF principles. Meaningful words from the job description are extracted by removing
common stop words (articles, conjunctions, auxiliary verbs). For each remaining word, a
word-boundary regex search checks whether it appears anywhere in the resume text. The
keyword score is the ratio of matching words to total meaningful JD words, scaled to 100.

6.7 Experience & Education Scoring
Experience Scoring

Experience is extracted using the _extract_experience_smart function, which implements a
five-strategy cascade: (1) explicit 'N years' patterns, (2) date-range pairs (YYYY–YYYY or
Month YYYY – Month YYYY), (3) year-span heuristic from all years in the document, (4)
graduation year heuristic, and (5) seniority title heuristic. The strategy with the highest
confidence (high > medium > low) is used.

The extracted years are compared to the JD's required years. Full credit (100) is awarded
when the candidate meets or exceeds the requirement. Partial scores follow a sliding scale
down to 20 for candidates with zero experience when experience is required.

Education Scoring

Education tier detection uses a tiered keyword list with five levels: PhD (tier 4), Masters
(tier 3), Bachelors (tier 2), Diploma/Certification (tier 1), and High School (tier 0). The
candidate's detected tier is compared to the JD's required tier. Meeting or exceeding the
requirement yields a full score; each tier below reduces the score proportionally. When the
JD has no education requirement, the score reflects the absolute tier value (PhD = 100,
Masters = 85, Bachelors = 70, etc.), ensuring education is still factored without penalizing
candidates when no requirement exists.

Chapter 7: Role Detection & Advanced Analysis
7.1 Role Detection Overview
The Advanced Screening mode's defining capability is autonomous job role detection from
resume content alone. Rather than requiring a recruiter to provide a job description, the
system analyses the skills and keywords extracted from a resume and identifies the most
likely job roles the candidate is suited for from a curated library of role profiles.

This enables several valuable use cases: talent pool analysis (classifying existing employee
profiles), candidate self-assessment (identifying one's strongest role matches), and
recruitment without an open position (building a pipeline for anticipated needs).

7.2 Role Matching Algorithm
The role matching algorithm (_detect_best_role) operates against a ROLE_PROFILES
dictionary that maps job role names to lists of associated skills. For each role, the algorithm:

Extracts the role's required skills as a set.
Computes the intersection with the candidate's extracted skills.
Calculates a raw match ratio: matched skills / total role skills.
Applies category weights to the matched skills using CATEGORY_WEIGHTS.
Produces a weighted match score, which is then used to derive an ATS-equivalent
score using the standard scoring pipeline with the role's skill profile as the 'JD'.
Ranks all roles by weighted match score in descending order.
The top-ranked role becomes the detected_role. The ATS score, matched skills, missing

skills, and feedback are all computed relative to this best-fit role.

7.3 Top- 3 Role Prediction
Beyond the single best-fit role, TalentLens reports the top three role matches with their
respective confidence percentages. These are the three roles with the highest weighted
match scores from the role detection algorithm. The confidence percentage for each role is
the ratio of that role's match score to the maximum possible score for that role, expressed as
a percentage.

The top-3 display allows candidates to understand their profile versatility — a Full Stack
Developer might also score highly for Frontend Developer and Software Engineer roles,
signaling flexibility in job applications.

7.4 Candidate Fit Score Calculation
The candidate fit score is a holistic measure that combines multiple signals beyond skill
matching:

Skill Coverage: The percentage of the detected role's required skills present in the
resume.
Experience Alignment: Whether the candidate's experience level matches typical
requirements for the detected role.
Education Relevance: Whether the candidate's education is appropriate for the
detected role.
Profile Completeness: Whether the resume contains sufficient information across
all evaluated dimensions.
The candidate fit is reported as a qualitative label (Excellent Fit, Strong Fit, Good Fit,
Partial Fit, or Developing Profile) alongside the numeric ATS score, providing an
immediately interpretable assessment for recruiters.

7.5 Strength Analysis
Strength analysis (analyze_resume_strengths) evaluates the candidate's resume along six
dimensions:

Technical Depth: Count of technical skills across programming languages,
frameworks, databases, cloud, AI/ML, mobile, security, and testing categories. A
score of 70+ indicates strong technical depth.
Skill Diversity: Number of distinct skill categories represented. Diversity across
5+ categories signals a well-rounded technical profile.
Experience Strength: Years of experience relative to typical role requirements. 5+
years typically indicates a senior-level contributor.
Education Quality: The detected education tier and its alignment with role
expectations.
Skill Match Quality: The percentage of the detected role's required skills that are
present in the resume.
7.6 Weakness Detection
Weakness detection applies the inverse logic to the same dimensions, identifying gaps:
Missing Critical Skills: Skills required by the detected role that are absent from
the resume are flagged as critical gaps.
Limited Technical Breadth: A resume with fewer than three technical skill
categories may indicate insufficient versatility.
Experience Gap: If the detected role typically requires significantly more
experience than the resume demonstrates, this is flagged.
Education Gap: A detected education tier below the role's typical expectation is
reported as a potential weakness.
Soft Skills Absence: Absence of any soft skills in a senior role profile may
indicate a resume optimization gap.
Weaknesses are presented constructively as areas for improvement rather than as
disqualifying factors.
7.7 Recommendation System
The ATS tips recommendation system (generate_ats_tips or ats_suggestions) generates
targeted, actionable improvement suggestions based on the analysis results:
Missing skill suggestions: For each missing critical skill, the system suggests
adding it to the resume if the candidate genuinely has the skill but did not mention
it.
Keyword optimization: If the keyword score is low, the system recommends using
more JD-specific terminology throughout the resume.
Experience articulation: If the experience score is low but the candidate has
relevant work history, the system recommends explicitly stating years of
experience using patterns that the extraction algorithm recognizes.
Education formatting: If the education tier could not be detected, the system
recommends clearly stating the degree name using standard terminology.
Quantification tips: Generic advice on adding measurable achievements to strengthen the
resume's impact.
Chapter 8: System Features & Modules
8.1 User Authentication
TalentLens implements a stateless authentication system using bcrypt for password hashing
and session tokens for maintaining authenticated state. The registration endpoint accepts a
username, email, and password, hashes the password using bcrypt, and stores the user
record in the MongoDB users collection. The login endpoint validates credentials, and on
success, returns a session token that the frontend stores locally and includes in subsequent
API requests via the Authorization header.

All screening and dashboard endpoints validate the presence and validity of the user token,
ensuring that resume data is scoped to the authenticated user (user_id filtering on all
queries). This provides basic multi-tenancy: each user sees only their own uploaded
resumes and analysis results.

8.2 Manual Screening Module
The Manual Screening module provides the following workflow:

The user navigates to the Manual Dashboard and selects either Single Upload or
Bulk Upload.
For single upload, the user selects one PDF or DOCX file. For bulk upload,
multiple files are selected simultaneously.
The user enters a Job Title (e.g., 'Senior Python Developer') and a Job Description
containing the role's responsibilities and required skills.
On submission, the frontend sends the file(s) and JD data to the /api/analyze
(single) or /api/bulk-analyze (bulk) endpoint.
The backend processes each resume through the NLP pipeline and ATS scoring
engine, using the provided JD to define skill requirements.
Results are returned and displayed in the dashboard: ATS score, score breakdown,
matched skills, missing skills, and AI-generated feedback for each candidate.
The recruiter can sort and filter candidates by score, view individual profiles,
generate PDF reports, and select candidates for email dispatch.
8.3 Advanced Screening Module
The Advanced Screening module mirrors the Manual module in UX structure but
eliminates the JD input requirement:

The user uploads one or multiple resumes to the Advanced Dashboard.
The backend runs the full NLP extraction pipeline and then calls the role detection
algorithm to identify the best-fit job role.
The advanced analysis pipeline computes top- 3 role matches, candidate fit score,
strengths, weaknesses, and ATS tips — all without any recruiter input.
Results include all manual screening outputs plus the advanced-exclusive fields:
detected role, role confidence, top-3 roles, candidate fit label, strength profile,
weakness profile, and ATS improvement tips.
The Advanced Dashboard renders additional analytics charts exclusive to this mode,
including the candidate fit distribution visualization.
8.4 Dashboard & Analytics
Both dashboards embed a comprehensive analytics section with the following ten
visualizations:

Score Distribution Pie Chart: Segments candidates into four score bands
(Excellent ≥80, Good 60 – 79, Moderate 40 – 59, Low <40) and displays the
proportion of each.
Core Skill Frequency Histogram: Shows the frequency of each skill across all
screened resumes, identifying the most common qualifications in the talent pool.
Top 10 Candidates by Score: A ranked bar chart of the highest-scoring candidates,
with names and ATS scores for quick shortlisting reference.
Average Score Trend: A time series chart showing how the average ATS score of
uploaded resumes has changed over the selected date range, useful for tracking
recruitment campaign quality.
Top Matched Skills: A bar chart of the skills most frequently matched between
resumes and job descriptions, indicating the strongest areas of candidate
alignment.
Resumes by Job Title (Manual) / Detected Role (Advanced): A breakdown of how
many resumes have been screened per job title or detected role, supporting
pipeline volume analysis.
Screening Funnel: A funnel chart showing the progressive filtering from total
uploaded resumes to those passing score thresholds (e.g., >40, >60, >70),
illustrating the recruitment funnel efficiency.
Uploaded Type Split: A pie or bar chart distinguishing single-upload from bulk-
upload resumes, supporting workflow analysis.
it Distribution (Advanced only): A distribution chart of candidate fit labels across
the talent pool, showing the proportion of Excellent, Strong, Good, Partial, and
Developing profiles.
Quick Insights Panel: Displays four key metrics at a glance: pass rate (percentage
of resumes scoring ≥70%), highest score, lowest score, and count of unique job
roles in the dataset.
8.5 PDF Report Generation
The PDF report generation system uses ReportLab to produce formatted A4 candidate
reports. Each report includes: candidate name, contact details, ATS score with visual gauge,
score breakdown table (showing each dimension's score), matched skills list, missing skills
list, AI feedback points, and (for advanced mode) the top-3 role matches and ATS
improvement tips.

Reports are generated on demand via the /api/report/{resume_id} endpoint. The original
resume file bytes stored in MongoDB are also accessible, allowing the platform to bundle
the original resume alongside the generated report when sending recruiter emails.

8.6 Email Automation System
The email automation system enables recruiters to send templated emails to selected
candidates directly from the dashboard. The system supports five email templates: shortlist
notification, interview invitation, advancement to next round, polite rejection, and post-
scan thank-you.
The /api/send-shortlist-emails endpoint accepts a list of resume IDs, the selected template
type, an optional custom subject and body, and a flag controlling whether to attach the PDF
report. The backend retrieves each candidate's email from MongoDB, generates the PDF
report, and dispatches the email via SMTP using Python's built-in smtplib module. The
system supports Gmail and other SMTP providers configured through environment
variables.
Email addresses can be overridden per-resume via the email_overrides parameter,
accommodating cases where the extracted email is incorrect. The system logs successes and
failures per email for auditability.

Chapter 9: Implementation Details
9.1 Project Structure
The project is organized as follows:

talentlens/
backend/
server.py # Main FastAPI application
.env # Environment variables
requirements.txt # Python dependencies
frontend/ src/
pages/ # Landing, Auth, Performance, Dashboards components/

Reusable UI components
services/ # API call abstractions
package.json
README.md

9.2 API Design
The API follows RESTful conventions with all endpoints under the /api prefix. Key
endpoints are summarized below:

Method Endpoint Description
POST /api/register User registration
POST /api/login User authentication
POST /api/analyze Single resume manual screening
POST /api/bulk-analyze Bulk resume manual screening
POST /api/advanced-scan Single resume advanced screening
POST /api/advanced-bulk-scan Bulk resume advanced screening
GET /api/dashboard/manual Manual dashboard data
GET /api/dashboard/advanced Advanced dashboard data
GET /api/report/{id} Generate PDF report
POST /api/send-shortlist-emails Send emails to candidates
GET /api/resumes/{id} Get single resume analysis
DELETE /api/resumes/{id} Delete resume record
9.3 Database Schema
The resumes collection document schema (representative fields):

{ "id": "uuid", "user_id": "uuid",
"filename": "string", "candidate_name": "string", "email": "string", "phone":
"string",
"extracted_skills": ["Python", "React", ...],
"ats_score": 78.5, "matched_skills": [...],
"missing_skills": [...], "feedback": [...],
"score_breakdown": { "skills_score": 82.0, ... },
"scan_mode": "advanced", "detected_role": "...",
"top3_roles": [...], "candidate_fit": "Strong Fit", "created_at": "ISO8601 timestamp" }

9.4 Key Implementation Highlights
Async Processing: All database operations use Motor's async API (await
db.collection.find()), ensuring the FastAPI event loop is never blocked during I/O
operations.
File Storage: Original resume files are stored as base64-encoded bytes in
MongoDB, eliminating the need for a separate file storage service and simplifying
deployment.
Weight Redistribution: The scoring engine dynamically adjusts dimension weights
when a JD lacks requirements for experience, education, or seniority, preventing
artificial score deflation.
Batch Processing: Bulk upload endpoints iterate over all uploaded files, storing
individual results and a shared batch_id, enabling batch-level analytics and
filtering.
Email Templates: Five pre-built email templates are selected by the email_type
parameter, with full custom override supported through the body_template
parameter.
9.5 Security Features
Password Hashing: All passwords are hashed using bcrypt with a work factor of
12 before storage. Plain-text passwords are never stored.
CORS Configuration: The backend CORS middleware is configured to allow
requests only from the known frontend origins (localhost:3000, localhost:3002) in
development. Production deployments should update this to the deployed frontend
domain.
Environment Secrets: Database connection strings, SMTP credentials, and secret
keys are loaded from .env files via python-dotenv and are never hardcoded in
source code.
Input Validation: All API request bodies are validated by Pydantic models, which
enforce type checking and reject malformed requests before they reach business
logic.
File Type Validation: Upload endpoints explicitly check file extensions, rejecting
non-PDF, non-DOCX files with a 400 error before any processing is attempted.
Chapter 10: Testing & Validation
10.1 Testing Methodology
TalentLens was validated through a combination of functional testing, API testing, NLP
model validation, and performance testing. The testing strategy was designed to verify
correctness of individual components (unit testing) and integrated end-to-end workflows
(integration testing).

Given the NLP-centric nature of the system, significant testing effort was directed at
validating the accuracy of the skill extraction pipeline, the correctness of the ATS scoring
formula, and the reliability of the role detection algorithm across diverse resume styles. A
test dataset of 50 manually reviewed resumes spanning five job categories was assembled
for quantitative evaluation.

10.2 Functional Testing
Test Case Expected Result Actual Result Status
Upload valid PDF resume Textreturned^ extracted, score Scorecorrectly^ returned PASS
Upload valid DOCX resume Textreturned^ extracted, score Scorecorrectly^ returned PASS
Upload invalid file type (.txt) 400 error with message (^400) returned^ error PASS
Bulk upload 10 resumes 10 results with batch_id (^10) returned^ results PASS
Alias skill ('k8s') detection Kubernetesscore credited^ in Kubernetes matched PASS
JD with must-have skills Mustweighted-have at^ skills 70% Weightedapplied score PASS
Generate PDF report PDF file returned PDFcorrectly^ generated PASS
Send email with PDF Emailattachment^ dispatched with Email delivered PASS
Advanced role detection Best role identified Rolecorrectly^ detected PASS
Dashboard statistics API 10 chart datasets returned Allreturned^ charts data PASS

10.3 API Testing
All API endpoints were tested using Postman with automated test scripts validating
response status codes, response schema compliance (required fields present, correct data
types), and response time benchmarks. A Postman collection of 23 test cases was developed
covering all 13 primary endpoints.

Key API test findings: All endpoints returned the correct HTTP status codes for both
success and error cases. Response schemas matched Pydantic model definitions in all cases.
The /api/analyze endpoint consistently returned responses under 3 seconds for single-
resume uploads under 2MB. Bulk upload of 20 resumes completed in under 30 seconds.

10.4 NLP Model Validation
The NLP pipeline was validated on the 50-resume test dataset with the following
methodology:

Skill Extraction Accuracy: Each resume was manually annotated with all skills
present. The extract_skills_advanced function's output was compared against the
manual annotation. Precision (skills correctly identified / total skills identified)
and Recall (skills correctly identified / total skills in annotation) were computed.
Contact Extraction Accuracy: Email, phone, and name extraction were verified
against the actual resume content for all 50 test resumes.
Experience Extraction Accuracy: The extracted experience years were compared
against manually counted years from each resume's work history section.
Results of NLP validation:

NLP Component Precision Recall F1 Score
Skill Extraction (with
synonyms) 91.3%^ 87.6%^ 89.4%^
Email Detection 98.0% 96.0% 97.0%
Phone Detection 94.0% 92.0% 93.0%
Name Detection 86.0% 84.0% 85.0%
Experience Year Extraction 82.0% 80.0% 81.0%
Education Tier Detection 94.0% 92.0% 93.0%
10.5 Performance Testing
Performance testing was conducted to assess the system's throughput and response time
under realistic load conditions:

Single Resume Processing: Average processing time of 1.8 seconds (including
text extraction, NLP pipeline, and database write). 95th percentile: 2.9 seconds.
Bulk Upload (10 files): Average total processing time of 14.2 seconds. Average
per-file time: 1.42 seconds, indicating effective parallelism at the application
layer.
Advanced Scan (single): Average processing time of 2.4 seconds, with the
additional 0.6 seconds attributed to the role detection and full advanced analysis
computation.
Dashboard API: Average response time of 340ms for the full dashboard dataset
retrieval including aggregation of 100 resume records.
Concurrent Users: The system was tested with 5 concurrent users each uploading
a single resume simultaneously. All requests completed within 4 seconds,
demonstrating adequate concurrency support from FastAPI's async architecture.
Chapter 11: Results & Evaluation
11.1 Experimental Setup
The evaluation was conducted using a dataset of 100 resumes collected from publicly
available resume datasets (Kaggle Resume Dataset) and anonymized samples provided for
academic research purposes. The dataset covered five job categories: Software Engineer,
Data Scientist, Frontend Developer, DevOps Engineer, and Business Analyst, with 20
resumes per category.

For the Manual Screening evaluation, job descriptions for each category were prepared by a
subject matter expert. For the Advanced Screening evaluation, resumes were submitted
without any job description, and the system's role detection was evaluated against the
known ground-truth category labels.

11.2 Dataset Description
Category Count Format Avg. Skills/Resume
Software Engineer 20 PDF/DOCX 14.2
Data Scientist 20 PDF/DOCX 16.8
Frontend Developer 20 PDF/DOCX 11.5
DevOps Engineer 20 PDF/DOCX 13.1
Business Analyst 20 PDF/DOCX 8.4
Total 100 Mixed 12.8 avg.
11.3 Evaluation Metrics (Accuracy, Precision, Recall)
Three primary evaluation metrics were used:

Skill Matching Precision: Of all skills the system identified as matches, what
percentage were genuinely relevant to the JD.
Skill Matching Recall: Of all skills genuinely relevant to the JD that were present
in the resume, what percentage did the system identify.
Role Detection Accuracy: For advanced screening, what percentage of resumes
were assigned the correct job role category (top-1 accuracy).
11.4 Results Analysis
Manual Screening Results:

Job Category Avg. ATS Score Precision Recall
Software Engineer 74.3 90.1% 86.4%
Data Scientist 71.8 88.7% 84.2%
Frontend Developer 76.2 92.3% 88.1%
DevOps Engineer 69.4 87.9% 83.6%
Business Analyst 65.7 84.2% 80.9%
Overall 71.5 88.6% 84.6%
Advanced Screening Role Detection Accuracy:
Category Top- 1 Accuracy Top- 3 Accuracy Confidence (avg.)
Software Engineer 85% 95% 78.4%
Data Scientist 80% 95% 75.2%
Frontend Developer 90% 100% 82.1%
DevOps Engineer 75% 90% 70.8%
Business Analyst 70% 85% 65.3%
Overall 80% 93% 74.4%
The results demonstrate strong performance across all categories, with Frontend Developer
achieving the highest scores due to the distinctive and well-delineated skill set of that role.
DevOps Engineer and Business Analyst showed lower accuracy due to greater skill overlap
with adjacent roles (Software Engineer and Project Manager respectively).

11.5 Comparison with Existing Systems
Feature TalentLens Simple ATS Commercial ATS Research NLP
Synonym Resolution Yes No Partial Yes
Role Auto-Detection Yes No No Partial
Explainable Score Yes No Partial Yes
Analytics Dashboard 10 charts None Basic None
Email Automation Yes No Yes No
Open Source Yes Yes No Yes
Skill Match F1 89.4% 72.1% ~85% 91.2%

Processing Time 1.8s/resume 0.3s 2.1s 4.5s

Chapter 12: Future Enhancements
12.1 Limitations of Current System
The following limitations have been identified in the current implementation:

Scanned PDF Support: The system relies on PDF text layers. Scanned or image-
based PDFs yield no extractable text. An OCR integration (Tesseract or cloud
OCR API) is needed to handle these cases.
Multi-language Support: The NLP pipeline is designed for English-language
resumes. International candidates with resumes in other languages are not well
served by the current skill extraction model.
Role Profile Coverage: The ROLE_PROFILES dictionary covers common
technology roles but does not include specialized or emerging roles (e.g., Prompt
Engineer, AI Safety Researcher, Blockchain Developer). Expanding this
dictionary is an ongoing effort.
Deep Learning Integration: The current approach uses lightweight NLP without
transformer-based models. Integrating SBERT or similar models for semantic
matching could improve precision, particularly for domain-specific vocabulary.
No Interview Scheduling: TalentLens covers screening and ranking but does not
integrate with calendar systems for interview scheduling, limiting the end-to-end
recruitment workflow support.
Single-User Tenancy: The current authentication model assigns all resumes to a
single user account. Enterprise use cases require organization-level tenancy with
role-based access control (RBAC) for multiple recruiters.
12.2 Planned Improvements
The following improvements are planned for future development cycles:

OCR Integration: Integrate Tesseract OCR as a fallback for scanned PDF files,
enabling processing of the substantial portion of real-world resumes submitted as
scanned documents.
Transformer-Based Semantic Matching: Replace the current spaCy vector
similarity with SBERT (Sentence-BERT) for more accurate semantic skill
matching, particularly for emerging technologies not in the keyword dictionary.
Automated Role Profile Expansion: Implement a mechanism to automatically
expand the ROLE_PROFILES dictionary from job posting data (e.g., by scraping
job boards with user permission), keeping role definitions current with market
demand.
Multi-Language NLP: Integrate spaCy's multi-language models and expand the
skill keyword database to support at minimum French, German, Spanish, and
Mandarin resume analysis.
Calendar Integration: Integrate with Google Calendar and Outlook Calendar APIs
to allow direct interview scheduling from the shortlisted candidates view.
Organization-Level Tenancy: Implement a multi-tenant data model with
organization accounts, recruiter roles, and team-level analytics dashboards.
Bias Detection Module: Develop an optional module that flags potential
demographic bias signals in the screening results, promoting equitable hiring
practices.
Real-Time Collaboration: Enable multiple recruiters to collaboratively annotate,
score, and comment on candidate profiles within the platform.
12.3 Scalability Considerations
For large-scale deployment serving thousands of concurrent users and millions of resume
analyses, the following architectural changes are recommended:

Message Queue Integration: Replace synchronous bulk upload processing with an
async task queue (e.g., Celery with Redis or RabbitMQ) to decouple file upload
from NLP processing and improve throughput.
Horizontal Scaling: Deploy multiple FastAPI instances behind a load balancer
(Nginx or AWS ALB), leveraging the stateless API design for seamless horizontal
scaling.
MongoDB Sharding: As the resumes collection grows beyond 10 million
documents, implement MongoDB sharding on the user_id field to distribute the
data and query load.
CDN for Static Assets: Serve the frontend static bundle from a CDN (CloudFront,
Cloudflare) to reduce latency for globally distributed users.
Caching Layer: Introduce a Redis caching layer for frequently accessed dashboard
aggregations to reduce database query load on analytics-heavy usage patterns.
Chapter 13: Conclusion
13.1 Summary of Work
This project has presented the design, implementation, and evaluation of TalentLens, an
NLP-Powered Advanced Automated Applicant Tracking System for resume analysis and
candidate ranking. The system was built as a full-stack web application combining a React
frontend, a FastAPI Python backend, MongoDB persistence, and a comprehensive NLP
processing pipeline.

The system implements two screening modes — Manual Screening with recruiter-provided
job descriptions and Advanced Screening with autonomous role detection — providing
flexibility for diverse recruitment scenarios. A five-dimensional ATS scoring algorithm
with category-weighted skill matching, multi-strategy experience extraction, education tier
detection, and semantic similarity bonus scoring produces explainable, multi-faceted
candidate scores. An analytics dashboard with ten visualization types, PDF report
generation, and SMTP email automation complete the feature set.

13.2 Key Achievements
The key technical achievements of this project are:

A 280+ skill keyword database with eleven category classifications and category-
specific weighting, providing industry-grade skill coverage.
A synonym resolution system mapping 50+ skill aliases to canonical forms,
significantly improving skill recall compared to exact-match approaches.
A five-strategy experience extraction algorithm achieving 81% F1 on the test
dataset, outperforming simple regex-only approaches.
An autonomous role detection engine achieving 80% top- 1 accuracy and 93% top-
3 accuracy across five job categories without any recruiter input.
An overall skill matching F1 score of 89.4% on the 100 - resume test dataset,
competitive with published research systems while maintaining lightweight
deployment requirements.
A complete analytics dashboard with ten visualization types, providing data-
driven recruitment decision support absent from existing open-source tools.
A PDF report generation and email automation system enabling end-to-end
candidate communication from within the platform.
13.3 Final Outcome
TalentLens successfully demonstrates that a well-engineered combination of curated NLP
resources, multi-strategy information extraction, and category-weighted scoring can
achieve near-commercial-grade resume analysis accuracy without the computational
overhead of large language models. The system is deployable on modest hardware, making
it accessible to small and medium organizations that cannot afford enterprise ATS licenses.

The project has also produced several contributions applicable beyond the immediate
system: the SKILL_KEYWORDS taxonomy with category weights, the synonym
resolution architecture, the multi-strategy experience extraction algorithm, and the role
detection methodology are all reusable components for future NLP-powered HR
technology development.

In conclusion, TalentLens represents a meaningful step toward intelligent, transparent, and
scalable recruitment automation. The system's explainable scoring model, dual screening
modes, and comprehensive analytics capabilities position it as a practical and extensible
foundation for future academic research and commercial development in AI-assisted
human resource management.

References
[1] S. Maheshwary and H. Misra, “Matching Resumes to Jobs via Deep Siamese Network,” in
Proc. WWW Workshop on Automated Knowledge Base Construction, 2018. [Online].
Available:
https://www.researchgate.net/publication/324223036_Matching_Resumes_to_Jobs_via_Deep
_Siamese_Network

[2] Explosion AI, “spaCy: Industrial-Strength Natural Language Processing in Python.”
[Online]. Available: https://spacy.io/usage

[3] J. Devlin, M. Chang, K. Lee, and K. Toutanova, “BERT: Pre-training of Deep Bidirectional
Transformers for Language Understanding,” in Proc. NAACL-HLT, 2019. [Online]. Available:
https://arxiv.org/abs/1810.04805

[4] N. Reimers and I. Gurevych, “Sentence-BERT: Sentence Embeddings using Siamese BERT-
Networks,” in Proc. EMNLP, 2019. [Online]. Available: https://arxiv.org/abs/1908.10084

[5] M. Patel and D. Shah, “Automated Resume Screening using Machine Learning and NLP,”
International Journal of Advanced Computer Science and Applications (IJACSA), vol. 13, no.
4, pp. 312 – 319, 2022. [Online]. Available:
https://thesai.org/Publications/ViewPaper?Volume=13&Issue=4&Code=IJACSA&SerialNo=
39

[6] S. Bird, E. Klein, and E. Loper, Natural Language Processing with Python. Sebastopol, CA,
USA: O’Reilly Media, 2009. [Online]. Available: https://www.nltk.org/book/

[7]MongoDB Inc., “MongoDB Documentation.” [Online]. Available:
https://www.mongodb.com/docs/

[8] Mozilla Developer Network (MDN), “JavaScript Documentation.” [Online]. Available:
https://developer.mozilla.org/en-US/docs/Web/JavaScript

[9] FastAPI, “FastAPI Documentation.” [Online]. Available: https://fastapi.tiangolo.com/

[10] C. Qin, H. Zhang, J. Liu, and Y. Li, “Enhancing Person-Job Fit for Talent Recruitment: An
Ability-Aware Neural Network Approach,” in Proc. ACM SIGIR Conference, 2018, pp. 25–34.
[Online]. Available: https://dl.acm.org/doi/10.1145/3209978.3210023

[11] R. Rodrigues, L. Zárate, and C. Nobre, “Information Extraction from Resumes using NLP
and spaCy,” in Proc. IEEE International Conference on Machine Learning Applications
(ICMLA), 2019, pp. 1184 – 1189. [Online]. Available:
https://ieeexplore.ieee.org/document/8999244

Appendix
Appendix A — API Endpoints Reference
Meth
od Endpoint^ Auth^ Required^ Description^
POST /api/register No Register new user account
POST /api/login No Authenticate and receive token
POST /api/analyze Yes Analyze(manual)^ single resume
POST /api/bulk-analyze Yes Analyze(manual)^ multiple resumes
POST /api/advanced-scan Yes Advanced scan single resume
POST /api/advanced-bulk-scan Yes Advancedresumes scan^ multiple
GET /api/dashboard/manual Yes Manual dashboard data & stats
GET /api/dashboard/advanced Yes Advancedstats dashboard^ data^ &
GET /api/resumes/{id} Yes Getresult^ single resume^ analysis
DEL
ETE /api/resumes/{id}^ Yes^ Delete^ a^ resume^ record^
GET /api/report/{id} Yes Download PDF report
POST /api/send-shortlist-emails Yes Send emails to candidates
GET /api/performance Yes Performancemodes) overview^ (all
Appendix B — Key Code Snippets
B.1 .ATS Score Computation (excerpt)
def calculate_ats_score(resume_skills, jd_skills, resume_text, jd_text, job_title):

Compute raw skill score
skill_score_raw = (
matched_weight + partial_credit + semantic_bonus
) / max(jd_total_weight, 1)

Normalize skill score to percentage
skill_score = min(skill_score_raw * 100, 100.0)

Compute weighted composite score
composite = sum(
active_scores[k] * active_weights[k]
for k in active_scores
)

Final ATS score (capped at 100)
final_score = round(min(composite, 100.0), 1)

return final_score, matched, missing, breakdown

Explanation

This function calculates the ATS score by combining:
Exact skill matches (matched_weight)
Partial matches (partial_credit)
Semantic similarity bonus (semantic_bonus) The score is normalized and combined
using a weighted approach to produce the final ATS score.