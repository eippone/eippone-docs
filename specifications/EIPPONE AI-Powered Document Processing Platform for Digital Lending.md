# EIPPONE AI-Powered Document Processing Platform for Digital Lending

**EIPPONE Simulation Dynamics Inc.**

> **Transforming paper-based lending into intelligent, automated, and auditable digital document processing.**

---

## 1. Project Overview

### Platform Name

**EIPPONE AI-Powered Document Processing Platform for Digital Lending**

### Purpose

The **EIPPONE AI-Powered Document Processing Platform** is an OCR-enabled **Document AI and information-extraction platform** designed to transform complex, paper-based loan applications and supporting documents into validated, structured, machine-readable data.

The platform combines:

- Optical Character Recognition (OCR)
- Document classification
- AI-powered information extraction
- Natural Language Processing (NLP)
- Structured data transformation
- Data normalization
- Rule-based and AI-powered validation
- Confidence scoring
- Cross-document consistency checking
- Machine-learning model evaluation
- Human-in-the-loop review
- AI recommendations
- Workflow automation
- Dataverse integration
- REST/API integration
- Web and portable application interfaces

The system is designed for complex lending scenarios where applicants may submit documents in different formats, including:

- Scanned paper documents
- Photographs of documents
- PDF documents
- Digitally generated PDFs
- Plain-text documents
- Semi-structured forms
- Financial statements
- Identification documents
- Employment and income documents
- Bank statements
- Supporting loan documentation

### Objective

Build a production-oriented **Document AI pipeline** capable of converting heterogeneous loan documents into reliable, validated structured information that can support automated and human-assisted lending workflows.

The primary objective is:

> **Convert unstructured and semi-structured loan documentation into accurate, validated, traceable, and decision-ready structured data.**

### Business Problem

Traditional loan-processing workflows frequently depend on manual data entry and document review.

This can result in:

- Long processing times
- Manual transcription errors
- Inconsistent data entry
- Difficulty processing handwritten or scanned documents
- Duplicate information
- Missing fields
- Inconsistent information across documents
- Limited traceability
- High operational costs
- Delayed lending decisions

EIPPONE addresses these challenges by introducing an intelligent document-processing layer between document ingestion and the lending workflow.

### Current Status

**In Development / MVP Architecture**

The project is being developed as a reusable EIPPONE Document AI platform with an initial focus on **digital loan application processing**.

---

# 2. CRISP-DM Methodology Alignment

The project follows the **CRISP-DM (Cross-Industry Standard Process for Data Mining)** lifecycle to ensure that the Document AI solution is developed systematically, evaluated objectively, and deployed in a reproducible manner.

| Phase | Description | Project Activity |
|---|---|---|
| **Business Understanding** | Define business objectives, operational requirements, and success criteria. | Define digital lending requirements, document-processing objectives, extraction requirements, processing SLAs, and human-review requirements. |
| **Data Understanding** | Identify, inspect, profile, and understand source documents and their characteristics. | Analyze loan applications, images, PDFs, text documents, document layouts, OCR quality, field distributions, and document variability. |
| **Data Preparation** | Clean, preprocess, normalize, and prepare documents and extracted information. | Image preprocessing, PDF processing, OCR, text normalization, document segmentation, field normalization, duplicate detection, and training-data preparation. |
| **Modeling** | Select, configure, train, or integrate AI/ML models. | OCR models, document classification, NLP/LLM extraction, entity recognition, field extraction, confidence scoring, and validation models. |
| **Evaluation** | Measure technical performance and business effectiveness. | OCR accuracy, Character Error Rate (CER), Word Error Rate (WER), extraction precision, recall, F1-score, classification accuracy, confidence calibration, and business-rule validation. |
| **Deployment** | Integrate the solution into operational workflows. | REST API, web application, portable application, Dataverse, Power Platform, workflow automation, employee review interface, and downstream lending systems. |

---

# 3. End-to-End Document AI Pipeline

The core architecture follows a modular processing pipeline:

```text
┌───────────────────────────────────────────────────────────────┐
│                    LOAN DOCUMENT SOURCES                      │
├────────────────┬────────────────┬─────────────────────────────┤
│     Images     │      PDFs      │          Text               │
│ JPG / PNG /    │ Scanned /      │ TXT / Structured /          │
│ TIFF / Photos  │ Digital PDFs   │ Semi-structured             │
└───────┬────────┴────────┬───────┴──────────────┬──────────────┘
        │                 │                      │
        └─────────────────┼──────────────────────┘
                          ▼
              ┌──────────────────────┐
              │ DOCUMENT INGESTION   │
              └──────────┬───────────┘
                         ▼
              ┌──────────────────────┐
              │ DOCUMENT PREPROCESSING│
              │                      │
              │ • Image enhancement  │
              │ • Deskewing          │
              │ • Noise reduction    │
              │ • Page segmentation  │
              └──────────┬───────────┘
                         ▼
              ┌──────────────────────┐
              │ OCR / TEXT EXTRACTION│
              │                      │
              │ Image/PDF → Text     │
              └──────────┬───────────┘
                         ▼
              ┌──────────────────────┐
              │ DOCUMENT             │
              │ CLASSIFICATION       │
              │                      │
              │ ID / Income / Bank   │
              │ Statement / Loan etc.│
              └──────────┬───────────┘
                         ▼
              ┌──────────────────────┐
              │ INFORMATION          │
              │ EXTRACTION           │
              │                      │
              │ Name                 │
              │ Address              │
              │ Income               │
              │ Dates                │
              │ Loan Amount          │
              │ Employment           │
              │ Financial Data       │
              └──────────┬───────────┘
                         ▼
              ┌──────────────────────┐
              │ NORMALIZATION        │
              │ & STRUCTURING        │
              │                      │
              │ JSON / Data Model    │
              │ Dataverse Schema     │
              └──────────┬───────────┘
                         ▼
              ┌──────────────────────┐
              │ AI + RULE VALIDATION │
              │                      │
              │ Missing Fields       │
              │ Format Validation    │
              │ Cross-document       │
              │ Consistency          │
              └──────────┬───────────┘
                         ▼
              ┌──────────────────────┐
              │ CONFIDENCE SCORING   │
              │ & QUALITY ASSESSMENT │
              └──────────┬───────────┘
                         ▼
              ┌──────────────────────┐
              │ HUMAN-IN-THE-LOOP    │
              │ REVIEW               │
              └──────────┬───────────┘
                         ▼
              ┌──────────────────────┐
              │ AI RECOMMENDATION    │
              │ & WORKFLOW           │
              └──────────┬───────────┘
                         ▼
       ┌─────────────────┴──────────────────┐
       ▼                                    ▼
┌────────────────────┐             ┌────────────────────┐
│ DATAVERSE /        │             │ REST API /         │
│ POWER PLATFORM     │             │ EXTERNAL SYSTEMS   │
└────────────────────┘             └────────────────────┘
```

---

# 4. Core Functional Components

## 4.1 Document Ingestion

The ingestion layer accepts documents from multiple sources.

Supported inputs include:

- JPG
- JPEG
- PNG
- TIFF
- PDF
- TXT
- JSON
- Other supported document formats

The ingestion process records:

- Document ID
- Application ID
- File name
- Document type
- Source
- Upload timestamp
- File format
- Processing status
- Processing version

---

## 4.2 OCR Engine

OCR is a fundamental component of the platform but **not the entire platform**.

The OCR layer converts visual documents into machine-readable text.

### OCR Responsibilities

- Text detection
- Character recognition
- Word recognition
- Line detection
- Layout detection
- Bounding-box extraction
- Confidence scoring
- Page-level processing
- Multi-page document processing

### OCR Quality Metrics

The platform evaluates OCR performance using:

- Character Error Rate (CER)
- Word Error Rate (WER)
- Character Accuracy
- Word Accuracy
- OCR confidence
- Page-level confidence

---

# 5. Document Classification

The classification layer determines the type of document submitted.

Example document classes:

```text
Loan Application
       │
       ├── Government ID
       ├── Passport
       ├── Driver's Licence
       ├── Employment Letter
       ├── Pay Stub
       ├── Bank Statement
       ├── Tax Document
       ├── Financial Statement
       ├── Proof of Address
       └── Supporting Document
```

Classification can use:

- Rule-based classification
- Machine-learning classification
- Transformer-based models
- LLM-assisted classification
- Metadata and file-type signals
- Layout characteristics

---

# 6. AI Information Extraction

The information-extraction layer transforms document text into structured business information.

### Example

Raw document:

```text
Applicant: John Smith
Annual Employment Income: $92,500
Loan Requested: $35,000
Employment Start Date: March 14, 2021
```

Structured output:

```json
{
  "applicant_name": "John Smith",
  "annual_income": 92500,
  "requested_loan_amount": 35000,
  "employment_start_date": "2021-03-14"
}
```

### Example Extraction Fields

| Category | Fields |
|---|---|
| Applicant | First Name, Last Name, Date of Birth |
| Address | Street, City, Province, Postal Code |
| Employment | Employer, Position, Start Date |
| Income | Salary, Other Income, Frequency |
| Loan | Loan Amount, Loan Term, Loan Type |
| Financial | Assets, Liabilities, Account Balances |
| Document | Document Type, Document Date, Document Number |

---

# 7. Structured Data Layer

Extracted information is converted into standardized structures.

Primary representations include:

- JSON
- Python dictionaries/data classes
- Pandas DataFrames
- Dataverse records
- REST API payloads

Example:

```json
{
  "application_id": "APP-1002",
  "document_type": "Income Verification",
  "extraction_status": "Completed",
  "confidence_score": 0.94,
  "fields": {
    "applicant_name": {
      "value": "John Smith",
      "confidence": 0.98
    },
    "annual_income": {
      "value": 92500,
      "confidence": 0.95
    }
  }
}
```

---

# 8. Validation & Quality Control

The platform performs multiple levels of validation.

## 8.1 Field-Level Validation

Examples:

- Required-field validation
- Data-type validation
- Date validation
- Currency validation
- Postal-code validation
- Numeric-range validation

## 8.2 Cross-Document Validation

The system compares information across multiple documents.

Example:

```text
Pay Stub
   │
   │ Income = $92,500
   ▼
Employment Letter
   │
   │ Income = $92,500
   ▼
Loan Application
   │
   │ Income = $92,500
   ▼
          ✓ CONSISTENT
```

If values conflict:

```text
Pay Stub              $92,500
Employment Letter     $88,000
Loan Application      $92,500

          ↓

⚠ VALIDATION FINDING
Income discrepancy detected
```

---

# 9. Confidence Scoring

Each extracted field can receive an independent confidence score.

Example:

| Field | Value | Confidence |
|---|---|---:|
| Applicant Name | John Smith | 98% |
| Date of Birth | 1987-04-15 | 96% |
| Address | 123 Main Street | 93% |
| Annual Income | $92,500 | 95% |
| Loan Amount | $35,000 | 99% |

Low-confidence fields can automatically be routed to human review.

```text
Confidence ≥ 95%
        │
        ▼
   Auto-validated

90–94%
        │
        ▼
   Review recommended

< 90%
        │
        ▼
   Human review required
```

Thresholds are configurable and should be calibrated using validation data.

---

# 10. Human-in-the-Loop Review

The platform supports employee review of AI-generated results.

The employee can:

- View the original document
- View OCR output
- View extracted fields
- View confidence scores
- View validation findings
- Correct extracted values
- Accept/reject AI results
- Add review comments
- Approve processing
- Escalate exceptions

This creates a controlled **AI + Human** workflow rather than relying entirely on automated decisions.

---

# 11. AI Recommendation Layer

After document processing and validation, the platform can generate recommendations for downstream processing.

Examples:

```text
DOCUMENT PROCESSING
        │
        ▼
EXTRACTION
        │
        ▼
VALIDATION
        │
        ├── No issues
        │      ↓
        │   Continue
        │
        └── Issues detected
               ↓
          Human Review
               ↓
        Correct / Resolve
               ↓
          Recommendation
```

Recommendations may include:

- Proceed to underwriting
- Request additional documentation
- Request clarification
- Escalate for review
- Hold application
- Reject due to documentation requirements

**Important:** Recommendations are designed as decision-support functionality and should be governed according to the organization's lending policies and applicable regulatory requirements.

---

# 12. Dataverse Data Model

The Document AI platform integrates with the EIPPONE Digital Lending data model.

Core tables include:

```text
Customer
    │
    └── Loan Application
            │
            ├── Loan Document
            │       │
            │       └── AI Extraction Result
            │
            ├── Application Review
            │
            ├── Approval
            │
            ├── Application Status History
            │
            ├── AI Validation Finding
            │
            ├── AI Recommendation
            │
            └── AI Processing Log
```

### Core AI Tables

| Table | Purpose |
|---|---|
| **AI Extraction Result** | Stores extracted fields and AI results |
| **AI Validation Finding** | Stores validation errors and inconsistencies |
| **AI Recommendation** | Stores AI-generated recommendations |
| **AI Processing Log** | Provides processing traceability |
| **AI Configuration** | Stores model, threshold, and processing configuration |

---

# 13. Technical Stack & Dependencies

## Language

- Python 3.12+

## Core Data & ML Libraries

Potential components include:

- Pandas
- NumPy
- scikit-learn
- PyTorch
- Transformers
- OpenCV
- Pillow
- Pydantic

## OCR / Document Processing

The architecture is designed to support pluggable OCR/document-processing engines, including:

- Tesseract OCR
- Cloud OCR services
- Document AI services
- Transformer-based OCR models
- Custom OCR models

The OCR implementation should remain modular so that OCR engines can be evaluated and replaced without redesigning the entire platform.

## AI / NLP

Potential technologies include:

- Large Language Models
- Transformer models
- Named Entity Recognition
- Document classification models
- Embedding models
- Retrieval-Augmented Generation where appropriate

## Data Integration

- CSV
- JSON
- REST APIs
- Microsoft Dataverse
- Power Platform
- Power Automate
- Power BI

## Infrastructure

Potential deployment targets include:

- Local Windows environment
- Docker
- Cloud APIs
- AWS
- Microsoft Azure
- Microsoft Power Platform

---

# 14. Architecture Blueprint

## Logic Flow

```text
Input Document
      ↓
Ingestion
      ↓
Preprocessing
      ↓
OCR / Text Extraction
      ↓
Document Classification
      ↓
Information Extraction
      ↓
Normalization
      ↓
Validation
      ↓
Confidence Scoring
      ↓
Quality Evaluation
      ↓
Human Review
      ↓
AI Recommendation
      ↓
Dataverse / API
      ↓
Lending Workflow
```

## Data Layer

The data layer supports:

- Raw documents
- OCR output
- Extracted fields
- Normalized data
- Validation findings
- Model outputs
- Confidence scores
- Human corrections
- Processing logs
- Evaluation datasets

## Interface Layer

The platform is designed with **dual-delivery architecture**:

### 1. Portable / Downloadable Application

A locally deployable version providing a fully interactive UI/UX.

Potential technologies:

- Python application
- Streamlit
- Desktop wrapper
- Local API
- Docker

### 2. Web Application

An online version providing a fully interactive UI/UX.

Potential components:

- Web frontend
- REST API
- Cloud-hosted processing services
- Dataverse integration
- Authentication and authorization
- Monitoring

### Enterprise Interface

The solution can integrate with:

- Power Apps
- Power Automate
- Dataverse
- Power BI
- Enterprise APIs

---

# 15. Evaluation Framework

Model and system quality are evaluated using quantitative metrics.

## OCR Metrics

- Character Error Rate (CER)
- Word Error Rate (WER)
- Character Accuracy
- Word Accuracy

## Classification Metrics

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

## Information Extraction Metrics

- Field-level Accuracy
- Precision
- Recall
- F1-score
- Exact Match
- Partial Match

## Validation Metrics

- False Positive Rate
- False Negative Rate
- Validation Accuracy
- Exception Detection Rate

## Operational Metrics

- Processing Time
- Documents per Minute
- Average Cost per Document
- Human Review Rate
- Automation Rate
- Failure Rate

---

# 16. Machine Learning Evaluation

The platform supports systematic comparison of multiple models and processing strategies.

Example evaluation framework:

```text
                 Test Dataset
                      │
        ┌─────────────┼─────────────┐
        ▼             ▼             ▼
      Model A       Model B       Model C
        │             │             │
        ▼             ▼             ▼
      OCR /        OCR /         OCR /
    Extraction    Extraction    Extraction
        │             │             │
        └─────────────┼─────────────┘
                      ▼
               Evaluation Engine
                      │
        ┌─────────────┼──────────────┐
        ▼             ▼              ▼
     Accuracy        F1            CER/WER
        │             │              │
        └─────────────┼──────────────┘
                      ▼
              Model Comparison
                      │
                      ▼
               Model Selection
```

The evaluation framework should use representative test datasets and avoid evaluating models solely on the data used to develop them.

---

# 17. Implementation Roadmap — 18-Week Standard

## WKS 1–2: Business & Data Discovery

- Business requirements
- Lending workflow analysis
- Document inventory
- Document taxonomy
- Data-source assessment
- Success criteria
- Evaluation framework
- Security and governance requirements

**Primary outcome:** Business and data discovery baseline.

---

## WKS 3–5: Data Preparation & Prototyping

- Collect sample documents
- Create representative image/PDF/text datasets
- Document preprocessing
- OCR prototype
- Text normalization
- Initial document classification
- Initial information extraction
- Structured JSON output
- Initial evaluation dataset

**Primary outcome:** Functional Document AI prototype.

---

## WKS 6–8: Internal Review & Iteration

- OCR benchmarking
- Model comparison
- Extraction evaluation
- Validation rules
- Confidence scoring
- Error analysis
- Edge-case testing
- Stress testing
- Pipeline refactoring
- Human-review prototype

**Primary outcome:** Validated internal prototype.

---

## WKS 9–14: Deployment & Integration

- Production API
- Web interface
- Portable application
- Dataverse integration
- Power Apps integration
- Power Automate integration
- AI processing tables
- Employee review interface
- Workflow integration
- Logging and monitoring
- Security implementation

**Primary outcome:** Integrated operational solution.

---

## WKS 15–18: Final Assessment & Reporting

- End-to-end performance testing
- Model evaluation
- OCR evaluation
- Extraction accuracy assessment
- Operational performance assessment
- Business impact analysis
- Documentation
- Technical report
- Stakeholder presentation
- Deployment recommendations

**Primary outcome:** Production-readiness assessment and final project report.

---

# 18. Project Deliverables Matrix

| Deliverable | Description | Duration | Status |
|---|---|---:|---:|
| **Project Plan** | Scope, architecture, timeline, resources, and technical strategy | 2 Wks | 0% |
| **Business & Document Discovery** | Lending workflow, document taxonomy, requirements, and use cases | 2 Wks | 0% |
| **Project EDA** | Document profiling, OCR feasibility, data quality, and document variability analysis | 2 Wks | 0% |
| **Document Dataset** | Representative image, PDF, and text loan-document datasets | 2 Wks | 0% |
| **OCR Prototype** | OCR processing pipeline and benchmark framework | 2 Wks | 0% |
| **Document Classification** | Automated document-type classification | 2 Wks | 0% |
| **Information Extraction** | AI-powered structured field extraction | 3 Wks | 0% |
| **Validation Engine** | Business-rule and cross-document validation | 2 Wks | 0% |
| **Model Assessment** | Accuracy, precision, recall, F1, CER, WER, and confidence evaluation | 2 Wks | 0% |
| **Human Review Interface** | Employee review and correction workflow | 3 Wks | 0% |
| **Dataverse Integration** | Integration with EIPPONE Digital Lending data model | 3 Wks | 0% |
| **API Layer** | REST-based document processing interface | 3 Wks | 0% |
| **Portable Application** | Downloadable interactive application | 3 Wks | 0% |
| **Web Application** | Online interactive document-processing interface | 3 Wks | 0% |
| **Deployment** | Integration into operational workflow | 6 Wks | 0% |
| **Final Report** | Technical findings, performance results, and recommendations | 2 Wks | 0% |

---

# 19. Proposed Repository Structure

```text
eippone-ai-document-processing/
│
├── README.md
├── LICENSE
├── .gitignore
├── pyproject.toml
├── requirements.txt
├── .env.example
│
├── src/
│   └── eippone_document_ai/
│       │
│       ├── ingestion/
│       │   ├── image_ingestion.py
│       │   ├── pdf_ingestion.py
│       │   └── text_ingestion.py
│       │
│       ├── preprocessing/
│       │   ├── image_preprocessing.py
│       │   ├── pdf_preprocessing.py
│       │   └── text_preprocessing.py
│       │
│       ├── ocr/
│       │   ├── base.py
│       │   ├── tesseract_engine.py
│       │   └── ocr_pipeline.py
│       │
│       ├── classification/
│       │   ├── document_classifier.py
│       │   └── taxonomy.py
│       │
│       ├── extraction/
│       │   ├── field_extractor.py
│       │   ├── entity_extractor.py
│       │   └── schemas.py
│       │
│       ├── normalization/
│       │   └── normalizer.py
│       │
│       ├── validation/
│       │   ├── rules.py
│       │   ├── validator.py
│       │   └── cross_document.py
│       │
│       ├── recommendation/
│       │   └── recommendation_engine.py
│       │
│       ├── evaluation/
│       │   ├── ocr_metrics.py
│       │   ├── extraction_metrics.py
│       │   ├── classification_metrics.py
│       │   └── evaluation_runner.py
│       │
│       └── common/
│           ├── config.py
│           ├── logging.py
│           └── exceptions.py
│
├── api/
│   ├── main.py
│   └── routes/
│
├── app/
│   ├── web/
│   └── desktop/
│
├── data/
│   ├── raw/
│   │   ├── images/
│   │   ├── pdf/
│   │   └── text/
│   │
│   ├── processed/
│   ├── annotations/
│   └── evaluation/
│
├── models/
│
├── notebooks/
│   ├── 01_document_eda.ipynb
│   ├── 02_ocr_evaluation.ipynb
│   ├── 03_classification.ipynb
│   └── 04_extraction_evaluation.ipynb
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── evaluation/
│
├── deployment/
│   ├── docker/
│   ├── local/
│   └── cloud/
│
├── docs/
│   ├── architecture/
│   ├── api/
│   ├── data-model/
│   └── evaluation/
│
└── scripts/
    ├── run_ocr.py
    ├── process_documents.py
    ├── evaluate_models.py
    └── generate_test_data.py
```

# Implemen ted Structure

```text
(.venv) PS C:\EIPPONE\eippone-ai-document-processing> tree /F
Folder PATH listing for volume Acer
Volume serial number is 00000045 A8C8:81B5
C:.
│   .gitignore
│   pyproject.toml
│   README.md
│   requirements.txt
│
├───.venv
│   │   .gitignore
│   │   pyvenv.cfg
│   │
│   ├───Include
│   ├───Lib
│   │   └───site-packages
│   │       ├───pip
│   │       │   │   py.typed
│   │       │   │   __init__.py
│   │       │   │   __main__.py
│   │       │   │   __pip-runner__.py
│   │       │   │
│   │       │   ├───_internal
│   │       │   │   │   cache.py
│   │       │   │   │   configuration.py
│   │       │   │   │   exceptions.py
│   │       │   │   │   main.py
│   │       │   │   │   pyproject.py
│   │       │   │   │   self_outdated_check.py
│   │       │   │   │   wheel_builder.py
│   │       │   │   │   __init__.py
│   │       │   │   │
│   │       │   │   ├───build_env
│   │       │   │   │   │   base.py
│   │       │   │   │   │   installer.py
│   │       │   │   │   │   noop.py
│   │       │   │   │   │   venv.py
│   │       │   │   │   │   virtual.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           base.cpython-313.pyc
│   │       │   │   │           installer.cpython-313.pyc
│   │       │   │   │           noop.cpython-313.pyc
│   │       │   │   │           venv.cpython-313.pyc
│   │       │   │   │           virtual.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───cli
│   │       │   │   │   │   autocompletion.py
│   │       │   │   │   │   base_command.py
│   │       │   │   │   │   cmdoptions.py
│   │       │   │   │   │   command_context.py
│   │       │   │   │   │   index_command.py
│   │       │   │   │   │   main.py
│   │       │   │   │   │   main_parser.py
│   │       │   │   │   │   parser.py
│   │       │   │   │   │   progress_bars.py
│   │       │   │   │   │   req_command.py
│   │       │   │   │   │   spinners.py
│   │       │   │   │   │   status_codes.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           autocompletion.cpython-313.pyc
│   │       │   │   │           base_command.cpython-313.pyc
│   │       │   │   │           cmdoptions.cpython-313.pyc
│   │       │   │   │           command_context.cpython-313.pyc
│   │       │   │   │           index_command.cpython-313.pyc
│   │       │   │   │           main.cpython-313.pyc
│   │       │   │   │           main_parser.cpython-313.pyc
│   │       │   │   │           parser.cpython-313.pyc
│   │       │   │   │           progress_bars.cpython-313.pyc
│   │       │   │   │           req_command.cpython-313.pyc
│   │       │   │   │           spinners.cpython-313.pyc
│   │       │   │   │           status_codes.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───commands
│   │       │   │   │   │   cache.py
│   │       │   │   │   │   check.py
│   │       │   │   │   │   completion.py
│   │       │   │   │   │   configuration.py
│   │       │   │   │   │   debug.py
│   │       │   │   │   │   download.py
│   │       │   │   │   │   freeze.py
│   │       │   │   │   │   hash.py
│   │       │   │   │   │   help.py
│   │       │   │   │   │   index.py
│   │       │   │   │   │   inspect.py
│   │       │   │   │   │   install.py
│   │       │   │   │   │   list.py
│   │       │   │   │   │   lock.py
│   │       │   │   │   │   search.py
│   │       │   │   │   │   show.py
│   │       │   │   │   │   uninstall.py
│   │       │   │   │   │   wheel.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           cache.cpython-313.pyc
│   │       │   │   │           check.cpython-313.pyc
│   │       │   │   │           completion.cpython-313.pyc
│   │       │   │   │           configuration.cpython-313.pyc
│   │       │   │   │           debug.cpython-313.pyc
│   │       │   │   │           download.cpython-313.pyc
│   │       │   │   │           freeze.cpython-313.pyc
│   │       │   │   │           hash.cpython-313.pyc
│   │       │   │   │           help.cpython-313.pyc
│   │       │   │   │           index.cpython-313.pyc
│   │       │   │   │           inspect.cpython-313.pyc
│   │       │   │   │           install.cpython-313.pyc
│   │       │   │   │           list.cpython-313.pyc
│   │       │   │   │           lock.cpython-313.pyc
│   │       │   │   │           search.cpython-313.pyc
│   │       │   │   │           show.cpython-313.pyc
│   │       │   │   │           uninstall.cpython-313.pyc
│   │       │   │   │           wheel.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───distributions
│   │       │   │   │   │   base.py
│   │       │   │   │   │   installed.py
│   │       │   │   │   │   sdist.py
│   │       │   │   │   │   wheel.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           base.cpython-313.pyc
│   │       │   │   │           installed.cpython-313.pyc
│   │       │   │   │           sdist.cpython-313.pyc
│   │       │   │   │           wheel.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───index
│   │       │   │   │   │   collector.py
│   │       │   │   │   │   package_finder.py
│   │       │   │   │   │   sources.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           collector.cpython-313.pyc
│   │       │   │   │           package_finder.cpython-313.pyc
│   │       │   │   │           sources.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───locations
│   │       │   │   │   │   base.py
│   │       │   │   │   │   _distutils.py
│   │       │   │   │   │   _sysconfig.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           base.cpython-313.pyc
│   │       │   │   │           _distutils.cpython-313.pyc
│   │       │   │   │           _sysconfig.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───metadata
│   │       │   │   │   │   base.py
│   │       │   │   │   │   pkg_resources.py
│   │       │   │   │   │   _json.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   ├───importlib
│   │       │   │   │   │   │   _compat.py
│   │       │   │   │   │   │   _dists.py
│   │       │   │   │   │   │   _envs.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           _compat.cpython-313.pyc
│   │       │   │   │   │           _dists.cpython-313.pyc
│   │       │   │   │   │           _envs.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           base.cpython-313.pyc
│   │       │   │   │           pkg_resources.cpython-313.pyc
│   │       │   │   │           _json.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───models
│   │       │   │   │   │   candidate.py
│   │       │   │   │   │   direct_url.py
│   │       │   │   │   │   format_control.py
│   │       │   │   │   │   index.py
│   │       │   │   │   │   installation_report.py
│   │       │   │   │   │   link.py
│   │       │   │   │   │   release_control.py
│   │       │   │   │   │   scheme.py
│   │       │   │   │   │   search_scope.py
│   │       │   │   │   │   selection_prefs.py
│   │       │   │   │   │   target_python.py
│   │       │   │   │   │   wheel.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           candidate.cpython-313.pyc
│   │       │   │   │           direct_url.cpython-313.pyc
│   │       │   │   │           format_control.cpython-313.pyc
│   │       │   │   │           index.cpython-313.pyc
│   │       │   │   │           installation_report.cpython-313.pyc
│   │       │   │   │           link.cpython-313.pyc
│   │       │   │   │           release_control.cpython-313.pyc
│   │       │   │   │           scheme.cpython-313.pyc
│   │       │   │   │           search_scope.cpython-313.pyc
│   │       │   │   │           selection_prefs.cpython-313.pyc
│   │       │   │   │           target_python.cpython-313.pyc
│   │       │   │   │           wheel.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───network
│   │       │   │   │   │   auth.py
│   │       │   │   │   │   cache.py
│   │       │   │   │   │   download.py
│   │       │   │   │   │   lazy_wheel.py
│   │       │   │   │   │   session.py
│   │       │   │   │   │   utils.py
│   │       │   │   │   │   xmlrpc.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           auth.cpython-313.pyc
│   │       │   │   │           cache.cpython-313.pyc
│   │       │   │   │           download.cpython-313.pyc
│   │       │   │   │           lazy_wheel.cpython-313.pyc
│   │       │   │   │           session.cpython-313.pyc
│   │       │   │   │           utils.cpython-313.pyc
│   │       │   │   │           xmlrpc.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───operations
│   │       │   │   │   │   check.py
│   │       │   │   │   │   freeze.py
│   │       │   │   │   │   prepare.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   ├───build
│   │       │   │   │   │   │   build_tracker.py
│   │       │   │   │   │   │   metadata.py
│   │       │   │   │   │   │   metadata_editable.py
│   │       │   │   │   │   │   wheel.py
│   │       │   │   │   │   │   wheel_editable.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           build_tracker.cpython-313.pyc
│   │       │   │   │   │           metadata.cpython-313.pyc
│   │       │   │   │   │           metadata_editable.cpython-313.pyc
│   │       │   │   │   │           wheel.cpython-313.pyc
│   │       │   │   │   │           wheel_editable.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   ├───install
│   │       │   │   │   │   │   wheel.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           wheel.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           check.cpython-313.pyc
│   │       │   │   │           freeze.cpython-313.pyc
│   │       │   │   │           prepare.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───req
│   │       │   │   │   │   constructors.py
│   │       │   │   │   │   pep723.py
│   │       │   │   │   │   req_dependency_group.py
│   │       │   │   │   │   req_file.py
│   │       │   │   │   │   req_install.py
│   │       │   │   │   │   req_set.py
│   │       │   │   │   │   req_uninstall.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           constructors.cpython-313.pyc
│   │       │   │   │           pep723.cpython-313.pyc
│   │       │   │   │           req_dependency_group.cpython-313.pyc
│   │       │   │   │           req_file.cpython-313.pyc
│   │       │   │   │           req_install.cpython-313.pyc
│   │       │   │   │           req_set.cpython-313.pyc
│   │       │   │   │           req_uninstall.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───resolution
│   │       │   │   │   │   base.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   ├───legacy
│   │       │   │   │   │   │   resolver.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           resolver.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   ├───resolvelib
│   │       │   │   │   │   │   base.py
│   │       │   │   │   │   │   candidates.py
│   │       │   │   │   │   │   factory.py
│   │       │   │   │   │   │   found_candidates.py
│   │       │   │   │   │   │   provider.py
│   │       │   │   │   │   │   reporter.py
│   │       │   │   │   │   │   requirements.py
│   │       │   │   │   │   │   resolver.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           base.cpython-313.pyc
│   │       │   │   │   │           candidates.cpython-313.pyc
│   │       │   │   │   │           factory.cpython-313.pyc
│   │       │   │   │   │           found_candidates.cpython-313.pyc
│   │       │   │   │   │           provider.cpython-313.pyc
│   │       │   │   │   │           reporter.cpython-313.pyc
│   │       │   │   │   │           requirements.cpython-313.pyc
│   │       │   │   │   │           resolver.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           base.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───utils
│   │       │   │   │   │   appdirs.py
│   │       │   │   │   │   compat.py
│   │       │   │   │   │   compatibility_tags.py
│   │       │   │   │   │   datetime.py
│   │       │   │   │   │   deprecation.py
│   │       │   │   │   │   direct_url_helpers.py
│   │       │   │   │   │   egg_link.py
│   │       │   │   │   │   entrypoints.py
│   │       │   │   │   │   filesystem.py
│   │       │   │   │   │   filetypes.py
│   │       │   │   │   │   glibc.py
│   │       │   │   │   │   hashes.py
│   │       │   │   │   │   logging.py
│   │       │   │   │   │   misc.py
│   │       │   │   │   │   packaging.py
│   │       │   │   │   │   pylock.py
│   │       │   │   │   │   retry.py
│   │       │   │   │   │   subprocess.py
│   │       │   │   │   │   temp_dir.py
│   │       │   │   │   │   unpacking.py
│   │       │   │   │   │   urls.py
│   │       │   │   │   │   virtualenv.py
│   │       │   │   │   │   wheel.py
│   │       │   │   │   │   _jaraco_text.py
│   │       │   │   │   │   _log.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           appdirs.cpython-313.pyc
│   │       │   │   │           compat.cpython-313.pyc
│   │       │   │   │           compatibility_tags.cpython-313.pyc
│   │       │   │   │           datetime.cpython-313.pyc
│   │       │   │   │           deprecation.cpython-313.pyc
│   │       │   │   │           direct_url_helpers.cpython-313.pyc
│   │       │   │   │           egg_link.cpython-313.pyc
│   │       │   │   │           entrypoints.cpython-313.pyc
│   │       │   │   │           filesystem.cpython-313.pyc
│   │       │   │   │           filetypes.cpython-313.pyc
│   │       │   │   │           glibc.cpython-313.pyc
│   │       │   │   │           hashes.cpython-313.pyc
│   │       │   │   │           logging.cpython-313.pyc
│   │       │   │   │           misc.cpython-313.pyc
│   │       │   │   │           packaging.cpython-313.pyc
│   │       │   │   │           pylock.cpython-313.pyc
│   │       │   │   │           retry.cpython-313.pyc
│   │       │   │   │           subprocess.cpython-313.pyc
│   │       │   │   │           temp_dir.cpython-313.pyc
│   │       │   │   │           unpacking.cpython-313.pyc
│   │       │   │   │           urls.cpython-313.pyc
│   │       │   │   │           virtualenv.cpython-313.pyc
│   │       │   │   │           wheel.cpython-313.pyc
│   │       │   │   │           _jaraco_text.cpython-313.pyc
│   │       │   │   │           _log.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───vcs
│   │       │   │   │   │   bazaar.py
│   │       │   │   │   │   git.py
│   │       │   │   │   │   mercurial.py
│   │       │   │   │   │   subversion.py
│   │       │   │   │   │   versioncontrol.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           bazaar.cpython-313.pyc
│   │       │   │   │           git.cpython-313.pyc
│   │       │   │   │           mercurial.cpython-313.pyc
│   │       │   │   │           subversion.cpython-313.pyc
│   │       │   │   │           versioncontrol.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   └───__pycache__
│   │       │   │           cache.cpython-313.pyc
│   │       │   │           configuration.cpython-313.pyc
│   │       │   │           exceptions.cpython-313.pyc
│   │       │   │           main.cpython-313.pyc
│   │       │   │           pyproject.cpython-313.pyc
│   │       │   │           self_outdated_check.cpython-313.pyc
│   │       │   │           wheel_builder.cpython-313.pyc
│   │       │   │           __init__.cpython-313.pyc
│   │       │   │
│   │       │   ├───_vendor
│   │       │   │   │   bom.cdx.json
│   │       │   │   │   README.rst
│   │       │   │   │   vendor.txt
│   │       │   │   │   __init__.py
│   │       │   │   │
│   │       │   │   ├───cachecontrol
│   │       │   │   │   │   adapter.py
│   │       │   │   │   │   cache.py
│   │       │   │   │   │   controller.py
│   │       │   │   │   │   filewrapper.py
│   │       │   │   │   │   heuristics.py
│   │       │   │   │   │   LICENSE.txt
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   serialize.py
│   │       │   │   │   │   wrapper.py
│   │       │   │   │   │   _cmd.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   ├───caches
│   │       │   │   │   │   │   file_cache.py
│   │       │   │   │   │   │   redis_cache.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           file_cache.cpython-313.pyc
│   │       │   │   │   │           redis_cache.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           adapter.cpython-313.pyc
│   │       │   │   │           cache.cpython-313.pyc
│   │       │   │   │           controller.cpython-313.pyc
│   │       │   │   │           filewrapper.cpython-313.pyc
│   │       │   │   │           heuristics.cpython-313.pyc
│   │       │   │   │           serialize.cpython-313.pyc
│   │       │   │   │           wrapper.cpython-313.pyc
│   │       │   │   │           _cmd.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───certifi
│   │       │   │   │   │   cacert.pem
│   │       │   │   │   │   core.py
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │   __main__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           core.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │           __main__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───distlib
│   │       │   │   │   │   compat.py
│   │       │   │   │   │   LICENSE.txt
│   │       │   │   │   │   resources.py
│   │       │   │   │   │   scripts.py
│   │       │   │   │   │   t32.exe
│   │       │   │   │   │   t64-arm.exe
│   │       │   │   │   │   t64.exe
│   │       │   │   │   │   util.py
│   │       │   │   │   │   w32.exe
│   │       │   │   │   │   w64-arm.exe
│   │       │   │   │   │   w64.exe
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           compat.cpython-313.pyc
│   │       │   │   │           resources.cpython-313.pyc
│   │       │   │   │           scripts.cpython-313.pyc
│   │       │   │   │           util.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───distro
│   │       │   │   │   │   distro.py
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │   __main__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           distro.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │           __main__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───idna
│   │       │   │   │   │   cli.py
│   │       │   │   │   │   codec.py
│   │       │   │   │   │   compat.py
│   │       │   │   │   │   core.py
│   │       │   │   │   │   idnadata.py
│   │       │   │   │   │   intranges.py
│   │       │   │   │   │   LICENSE.md
│   │       │   │   │   │   package_data.py
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   uts46data.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │   __main__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           cli.cpython-313.pyc
│   │       │   │   │           codec.cpython-313.pyc
│   │       │   │   │           compat.cpython-313.pyc
│   │       │   │   │           core.cpython-313.pyc
│   │       │   │   │           idnadata.cpython-313.pyc
│   │       │   │   │           intranges.cpython-313.pyc
│   │       │   │   │           package_data.cpython-313.pyc
│   │       │   │   │           uts46data.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │           __main__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───msgpack
│   │       │   │   │   │   COPYING
│   │       │   │   │   │   exceptions.py
│   │       │   │   │   │   ext.py
│   │       │   │   │   │   fallback.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           exceptions.cpython-313.pyc
│   │       │   │   │           ext.cpython-313.pyc
│   │       │   │   │           fallback.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───packaging
│   │       │   │   │   │   dependency_groups.py
│   │       │   │   │   │   direct_url.py
│   │       │   │   │   │   errors.py
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   LICENSE.APACHE
│   │       │   │   │   │   LICENSE.BSD
│   │       │   │   │   │   markers.py
│   │       │   │   │   │   metadata.py
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   pylock.py
│   │       │   │   │   │   requirements.py
│   │       │   │   │   │   specifiers.py
│   │       │   │   │   │   tags.py
│   │       │   │   │   │   utils.py
│   │       │   │   │   │   version.py
│   │       │   │   │   │   _elffile.py
│   │       │   │   │   │   _manylinux.py
│   │       │   │   │   │   _musllinux.py
│   │       │   │   │   │   _parser.py
│   │       │   │   │   │   _structures.py
│   │       │   │   │   │   _tokenizer.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   ├───licenses
│   │       │   │   │   │   │   _spdx.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           _spdx.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           dependency_groups.cpython-313.pyc
│   │       │   │   │           direct_url.cpython-313.pyc
│   │       │   │   │           errors.cpython-313.pyc
│   │       │   │   │           markers.cpython-313.pyc
│   │       │   │   │           metadata.cpython-313.pyc
│   │       │   │   │           pylock.cpython-313.pyc
│   │       │   │   │           requirements.cpython-313.pyc
│   │       │   │   │           specifiers.cpython-313.pyc
│   │       │   │   │           tags.cpython-313.pyc
│   │       │   │   │           utils.cpython-313.pyc
│   │       │   │   │           version.cpython-313.pyc
│   │       │   │   │           _elffile.cpython-313.pyc
│   │       │   │   │           _manylinux.cpython-313.pyc
│   │       │   │   │           _musllinux.cpython-313.pyc
│   │       │   │   │           _parser.cpython-313.pyc
│   │       │   │   │           _structures.cpython-313.pyc
│   │       │   │   │           _tokenizer.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───pkg_resources
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───platformdirs
│   │       │   │   │   │   android.py
│   │       │   │   │   │   api.py
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   macos.py
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   unix.py
│   │       │   │   │   │   version.py
│   │       │   │   │   │   windows.py
│   │       │   │   │   │   _xdg.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │   __main__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           android.cpython-313.pyc
│   │       │   │   │           api.cpython-313.pyc
│   │       │   │   │           macos.cpython-313.pyc
│   │       │   │   │           unix.cpython-313.pyc
│   │       │   │   │           version.cpython-313.pyc
│   │       │   │   │           windows.cpython-313.pyc
│   │       │   │   │           _xdg.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │           __main__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───pygments
│   │       │   │   │   │   console.py
│   │       │   │   │   │   filter.py
│   │       │   │   │   │   formatter.py
│   │       │   │   │   │   lexer.py
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   modeline.py
│   │       │   │   │   │   plugin.py
│   │       │   │   │   │   regexopt.py
│   │       │   │   │   │   scanner.py
│   │       │   │   │   │   sphinxext.py
│   │       │   │   │   │   style.py
│   │       │   │   │   │   token.py
│   │       │   │   │   │   unistring.py
│   │       │   │   │   │   util.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │   __main__.py
│   │       │   │   │   │
│   │       │   │   │   ├───filters
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   ├───formatters
│   │       │   │   │   │   │   _mapping.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           _mapping.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   ├───lexers
│   │       │   │   │   │   │   python.py
│   │       │   │   │   │   │   _mapping.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           python.cpython-313.pyc
│   │       │   │   │   │           _mapping.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   ├───styles
│   │       │   │   │   │   │   _mapping.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           _mapping.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           console.cpython-313.pyc
│   │       │   │   │           filter.cpython-313.pyc
│   │       │   │   │           formatter.cpython-313.pyc
│   │       │   │   │           lexer.cpython-313.pyc
│   │       │   │   │           modeline.cpython-313.pyc
│   │       │   │   │           plugin.cpython-313.pyc
│   │       │   │   │           regexopt.cpython-313.pyc
│   │       │   │   │           scanner.cpython-313.pyc
│   │       │   │   │           sphinxext.cpython-313.pyc
│   │       │   │   │           style.cpython-313.pyc
│   │       │   │   │           token.cpython-313.pyc
│   │       │   │   │           unistring.cpython-313.pyc
│   │       │   │   │           util.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │           __main__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───pyproject_hooks
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   _impl.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   ├───_in_process
│   │       │   │   │   │   │   _in_process.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           _in_process.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           _impl.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───requests
│   │       │   │   │   │   adapters.py
│   │       │   │   │   │   api.py
│   │       │   │   │   │   auth.py
│   │       │   │   │   │   certs.py
│   │       │   │   │   │   compat.py
│   │       │   │   │   │   cookies.py
│   │       │   │   │   │   exceptions.py
│   │       │   │   │   │   help.py
│   │       │   │   │   │   hooks.py
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   models.py
│   │       │   │   │   │   packages.py
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   sessions.py
│   │       │   │   │   │   status_codes.py
│   │       │   │   │   │   structures.py
│   │       │   │   │   │   utils.py
│   │       │   │   │   │   _internal_utils.py
│   │       │   │   │   │   _types.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │   __version__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           adapters.cpython-313.pyc
│   │       │   │   │           api.cpython-313.pyc
│   │       │   │   │           auth.cpython-313.pyc
│   │       │   │   │           certs.cpython-313.pyc
│   │       │   │   │           compat.cpython-313.pyc
│   │       │   │   │           cookies.cpython-313.pyc
│   │       │   │   │           exceptions.cpython-313.pyc
│   │       │   │   │           help.cpython-313.pyc
│   │       │   │   │           hooks.cpython-313.pyc
│   │       │   │   │           models.cpython-313.pyc
│   │       │   │   │           packages.cpython-313.pyc
│   │       │   │   │           sessions.cpython-313.pyc
│   │       │   │   │           status_codes.cpython-313.pyc
│   │       │   │   │           structures.cpython-313.pyc
│   │       │   │   │           utils.cpython-313.pyc
│   │       │   │   │           _internal_utils.cpython-313.pyc
│   │       │   │   │           _types.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │           __version__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───resolvelib
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   providers.py
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   reporters.py
│   │       │   │   │   │   structs.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   ├───resolvers
│   │       │   │   │   │   │   abstract.py
│   │       │   │   │   │   │   criterion.py
│   │       │   │   │   │   │   exceptions.py
│   │       │   │   │   │   │   resolution.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           abstract.cpython-313.pyc
│   │       │   │   │   │           criterion.cpython-313.pyc
│   │       │   │   │   │           exceptions.cpython-313.pyc
│   │       │   │   │   │           resolution.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           providers.cpython-313.pyc
│   │       │   │   │           reporters.cpython-313.pyc
│   │       │   │   │           structs.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───rich
│   │       │   │   │   │   abc.py
│   │       │   │   │   │   align.py
│   │       │   │   │   │   ansi.py
│   │       │   │   │   │   bar.py
│   │       │   │   │   │   box.py
│   │       │   │   │   │   cells.py
│   │       │   │   │   │   color.py
│   │       │   │   │   │   color_triplet.py
│   │       │   │   │   │   columns.py
│   │       │   │   │   │   console.py
│   │       │   │   │   │   constrain.py
│   │       │   │   │   │   containers.py
│   │       │   │   │   │   control.py
│   │       │   │   │   │   default_styles.py
│   │       │   │   │   │   diagnose.py
│   │       │   │   │   │   emoji.py
│   │       │   │   │   │   errors.py
│   │       │   │   │   │   filesize.py
│   │       │   │   │   │   file_proxy.py
│   │       │   │   │   │   highlighter.py
│   │       │   │   │   │   json.py
│   │       │   │   │   │   jupyter.py
│   │       │   │   │   │   layout.py
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   live.py
│   │       │   │   │   │   live_render.py
│   │       │   │   │   │   logging.py
│   │       │   │   │   │   markup.py
│   │       │   │   │   │   measure.py
│   │       │   │   │   │   padding.py
│   │       │   │   │   │   pager.py
│   │       │   │   │   │   palette.py
│   │       │   │   │   │   panel.py
│   │       │   │   │   │   pretty.py
│   │       │   │   │   │   progress.py
│   │       │   │   │   │   progress_bar.py
│   │       │   │   │   │   prompt.py
│   │       │   │   │   │   protocol.py
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   region.py
│   │       │   │   │   │   repr.py
│   │       │   │   │   │   rule.py
│   │       │   │   │   │   scope.py
│   │       │   │   │   │   screen.py
│   │       │   │   │   │   segment.py
│   │       │   │   │   │   spinner.py
│   │       │   │   │   │   status.py
│   │       │   │   │   │   style.py
│   │       │   │   │   │   styled.py
│   │       │   │   │   │   syntax.py
│   │       │   │   │   │   table.py
│   │       │   │   │   │   terminal_theme.py
│   │       │   │   │   │   text.py
│   │       │   │   │   │   theme.py
│   │       │   │   │   │   themes.py
│   │       │   │   │   │   traceback.py
│   │       │   │   │   │   tree.py
│   │       │   │   │   │   _cell_widths.py
│   │       │   │   │   │   _emoji_codes.py
│   │       │   │   │   │   _emoji_replace.py
│   │       │   │   │   │   _export_format.py
│   │       │   │   │   │   _extension.py
│   │       │   │   │   │   _fileno.py
│   │       │   │   │   │   _inspect.py
│   │       │   │   │   │   _log_render.py
│   │       │   │   │   │   _loop.py
│   │       │   │   │   │   _null_file.py
│   │       │   │   │   │   _palettes.py
│   │       │   │   │   │   _pick.py
│   │       │   │   │   │   _ratio.py
│   │       │   │   │   │   _spinners.py
│   │       │   │   │   │   _stack.py
│   │       │   │   │   │   _timer.py
│   │       │   │   │   │   _win32_console.py
│   │       │   │   │   │   _windows.py
│   │       │   │   │   │   _windows_renderer.py
│   │       │   │   │   │   _wrap.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │   __main__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           abc.cpython-313.pyc
│   │       │   │   │           align.cpython-313.pyc
│   │       │   │   │           ansi.cpython-313.pyc
│   │       │   │   │           bar.cpython-313.pyc
│   │       │   │   │           box.cpython-313.pyc
│   │       │   │   │           cells.cpython-313.pyc
│   │       │   │   │           color.cpython-313.pyc
│   │       │   │   │           color_triplet.cpython-313.pyc
│   │       │   │   │           columns.cpython-313.pyc
│   │       │   │   │           console.cpython-313.pyc
│   │       │   │   │           constrain.cpython-313.pyc
│   │       │   │   │           containers.cpython-313.pyc
│   │       │   │   │           control.cpython-313.pyc
│   │       │   │   │           default_styles.cpython-313.pyc
│   │       │   │   │           diagnose.cpython-313.pyc
│   │       │   │   │           emoji.cpython-313.pyc
│   │       │   │   │           errors.cpython-313.pyc
│   │       │   │   │           filesize.cpython-313.pyc
│   │       │   │   │           file_proxy.cpython-313.pyc
│   │       │   │   │           highlighter.cpython-313.pyc
│   │       │   │   │           json.cpython-313.pyc
│   │       │   │   │           jupyter.cpython-313.pyc
│   │       │   │   │           layout.cpython-313.pyc
│   │       │   │   │           live.cpython-313.pyc
│   │       │   │   │           live_render.cpython-313.pyc
│   │       │   │   │           logging.cpython-313.pyc
│   │       │   │   │           markup.cpython-313.pyc
│   │       │   │   │           measure.cpython-313.pyc
│   │       │   │   │           padding.cpython-313.pyc
│   │       │   │   │           pager.cpython-313.pyc
│   │       │   │   │           palette.cpython-313.pyc
│   │       │   │   │           panel.cpython-313.pyc
│   │       │   │   │           pretty.cpython-313.pyc
│   │       │   │   │           progress.cpython-313.pyc
│   │       │   │   │           progress_bar.cpython-313.pyc
│   │       │   │   │           prompt.cpython-313.pyc
│   │       │   │   │           protocol.cpython-313.pyc
│   │       │   │   │           region.cpython-313.pyc
│   │       │   │   │           repr.cpython-313.pyc
│   │       │   │   │           rule.cpython-313.pyc
│   │       │   │   │           scope.cpython-313.pyc
│   │       │   │   │           screen.cpython-313.pyc
│   │       │   │   │           segment.cpython-313.pyc
│   │       │   │   │           spinner.cpython-313.pyc
│   │       │   │   │           status.cpython-313.pyc
│   │       │   │   │           style.cpython-313.pyc
│   │       │   │   │           styled.cpython-313.pyc
│   │       │   │   │           syntax.cpython-313.pyc
│   │       │   │   │           table.cpython-313.pyc
│   │       │   │   │           terminal_theme.cpython-313.pyc
│   │       │   │   │           text.cpython-313.pyc
│   │       │   │   │           theme.cpython-313.pyc
│   │       │   │   │           themes.cpython-313.pyc
│   │       │   │   │           traceback.cpython-313.pyc
│   │       │   │   │           tree.cpython-313.pyc
│   │       │   │   │           _cell_widths.cpython-313.pyc
│   │       │   │   │           _emoji_codes.cpython-313.pyc
│   │       │   │   │           _emoji_replace.cpython-313.pyc
│   │       │   │   │           _export_format.cpython-313.pyc
│   │       │   │   │           _extension.cpython-313.pyc
│   │       │   │   │           _fileno.cpython-313.pyc
│   │       │   │   │           _inspect.cpython-313.pyc
│   │       │   │   │           _log_render.cpython-313.pyc
│   │       │   │   │           _loop.cpython-313.pyc
│   │       │   │   │           _null_file.cpython-313.pyc
│   │       │   │   │           _palettes.cpython-313.pyc
│   │       │   │   │           _pick.cpython-313.pyc
│   │       │   │   │           _ratio.cpython-313.pyc
│   │       │   │   │           _spinners.cpython-313.pyc
│   │       │   │   │           _stack.cpython-313.pyc
│   │       │   │   │           _timer.cpython-313.pyc
│   │       │   │   │           _win32_console.cpython-313.pyc
│   │       │   │   │           _windows.cpython-313.pyc
│   │       │   │   │           _windows_renderer.cpython-313.pyc
│   │       │   │   │           _wrap.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │           __main__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───tomli
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   _parser.py
│   │       │   │   │   │   _re.py
│   │       │   │   │   │   _types.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           _parser.cpython-313.pyc
│   │       │   │   │           _re.cpython-313.pyc
│   │       │   │   │           _types.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───tomli_w
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   _writer.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           _writer.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───truststore
│   │       │   │   │   │   LICENSE
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   _api.py
│   │       │   │   │   │   _macos.py
│   │       │   │   │   │   _openssl.py
│   │       │   │   │   │   _ssl_constants.py
│   │       │   │   │   │   _windows.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           _api.cpython-313.pyc
│   │       │   │   │           _macos.cpython-313.pyc
│   │       │   │   │           _openssl.cpython-313.pyc
│   │       │   │   │           _ssl_constants.cpython-313.pyc
│   │       │   │   │           _windows.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   ├───urllib3
│   │       │   │   │   │   connection.py
│   │       │   │   │   │   connectionpool.py
│   │       │   │   │   │   exceptions.py
│   │       │   │   │   │   fields.py
│   │       │   │   │   │   filepost.py
│   │       │   │   │   │   LICENSE.txt
│   │       │   │   │   │   poolmanager.py
│   │       │   │   │   │   py.typed
│   │       │   │   │   │   response.py
│   │       │   │   │   │   _base_connection.py
│   │       │   │   │   │   _collections.py
│   │       │   │   │   │   _request_methods.py
│   │       │   │   │   │   _version.py
│   │       │   │   │   │   __init__.py
│   │       │   │   │   │
│   │       │   │   │   ├───contrib
│   │       │   │   │   │   │   pyopenssl.py
│   │       │   │   │   │   │   socks.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   ├───emscripten
│   │       │   │   │   │   │   │   connection.py
│   │       │   │   │   │   │   │   emscripten_fetch_worker.js
│   │       │   │   │   │   │   │   fetch.py
│   │       │   │   │   │   │   │   request.py
│   │       │   │   │   │   │   │   response.py
│   │       │   │   │   │   │   │   __init__.py
│   │       │   │   │   │   │   │
│   │       │   │   │   │   │   └───__pycache__
│   │       │   │   │   │   │           connection.cpython-313.pyc
│   │       │   │   │   │   │           fetch.cpython-313.pyc
│   │       │   │   │   │   │           request.cpython-313.pyc
│   │       │   │   │   │   │           response.cpython-313.pyc
│   │       │   │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           pyopenssl.cpython-313.pyc
│   │       │   │   │   │           socks.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   ├───http2
│   │       │   │   │   │   │   connection.py
│   │       │   │   │   │   │   probe.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           connection.cpython-313.pyc
│   │       │   │   │   │           probe.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   ├───util
│   │       │   │   │   │   │   connection.py
│   │       │   │   │   │   │   proxy.py
│   │       │   │   │   │   │   request.py
│   │       │   │   │   │   │   response.py
│   │       │   │   │   │   │   retry.py
│   │       │   │   │   │   │   ssltransport.py
│   │       │   │   │   │   │   ssl_.py
│   │       │   │   │   │   │   ssl_match_hostname.py
│   │       │   │   │   │   │   timeout.py
│   │       │   │   │   │   │   url.py
│   │       │   │   │   │   │   util.py
│   │       │   │   │   │   │   wait.py
│   │       │   │   │   │   │   __init__.py
│   │       │   │   │   │   │
│   │       │   │   │   │   └───__pycache__
│   │       │   │   │   │           connection.cpython-313.pyc
│   │       │   │   │   │           proxy.cpython-313.pyc
│   │       │   │   │   │           request.cpython-313.pyc
│   │       │   │   │   │           response.cpython-313.pyc
│   │       │   │   │   │           retry.cpython-313.pyc
│   │       │   │   │   │           ssltransport.cpython-313.pyc
│   │       │   │   │   │           ssl_.cpython-313.pyc
│   │       │   │   │   │           ssl_match_hostname.cpython-313.pyc
│   │       │   │   │   │           timeout.cpython-313.pyc
│   │       │   │   │   │           url.cpython-313.pyc
│   │       │   │   │   │           util.cpython-313.pyc
│   │       │   │   │   │           wait.cpython-313.pyc
│   │       │   │   │   │           __init__.cpython-313.pyc
│   │       │   │   │   │
│   │       │   │   │   └───__pycache__
│   │       │   │   │           connection.cpython-313.pyc
│   │       │   │   │           connectionpool.cpython-313.pyc
│   │       │   │   │           exceptions.cpython-313.pyc
│   │       │   │   │           fields.cpython-313.pyc
│   │       │   │   │           filepost.cpython-313.pyc
│   │       │   │   │           poolmanager.cpython-313.pyc
│   │       │   │   │           response.cpython-313.pyc
│   │       │   │   │           _base_connection.cpython-313.pyc
│   │       │   │   │           _collections.cpython-313.pyc
│   │       │   │   │           _request_methods.cpython-313.pyc
│   │       │   │   │           _version.cpython-313.pyc
│   │       │   │   │           __init__.cpython-313.pyc
│   │       │   │   │
│   │       │   │   └───__pycache__
│   │       │   │           __init__.cpython-313.pyc
│   │       │   │
│   │       │   └───__pycache__
│   │       │           __init__.cpython-313.pyc
│   │       │           __main__.cpython-313.pyc
│   │       │           __pip-runner__.cpython-313.pyc
│   │       │
│   │       └───pip-26.2.1.dist-info
│   │           │   entry_points.txt
│   │           │   INSTALLER
│   │           │   METADATA
│   │           │   RECORD
│   │           │   REQUESTED
│   │           │   WHEEL
│   │           │
│   │           └───licenses
│   │               │   AUTHORS.txt
│   │               │   LICENSE.txt
│   │               │
│   │               └───src
│   │                   └───pip
│   │                       └───_vendor
│   │                           ├───cachecontrol
│   │                           │       LICENSE.txt
│   │                           │
│   │                           ├───certifi
│   │                           │       LICENSE
│   │                           │
│   │                           ├───distlib
│   │                           │       LICENSE.txt
│   │                           │
│   │                           ├───distro
│   │                           │       LICENSE
│   │                           │
│   │                           ├───idna
│   │                           │       LICENSE.md
│   │                           │
│   │                           ├───msgpack
│   │                           │       COPYING
│   │                           │
│   │                           ├───packaging
│   │                           │       LICENSE
│   │                           │       LICENSE.APACHE
│   │                           │       LICENSE.BSD
│   │                           │
│   │                           ├───pkg_resources
│   │                           │       LICENSE
│   │                           │
│   │                           ├───platformdirs
│   │                           │       LICENSE
│   │                           │
│   │                           ├───pygments
│   │                           │       LICENSE
│   │                           │
│   │                           ├───pyproject_hooks
│   │                           │       LICENSE
│   │                           │
│   │                           ├───requests
│   │                           │       LICENSE
│   │                           │
│   │                           ├───resolvelib
│   │                           │       LICENSE
│   │                           │
│   │                           ├───rich
│   │                           │       LICENSE
│   │                           │
│   │                           ├───tomli
│   │                           │       LICENSE
│   │                           │
│   │                           ├───tomli_w
│   │                           │       LICENSE
│   │                           │
│   │                           ├───truststore
│   │                           │       LICENSE
│   │                           │
│   │                           └───urllib3
│   │                                   LICENSE.txt
│   │
│   └───Scripts
│           activate
│           activate.bat
│           activate.fish
│           Activate.ps1
│           deactivate.bat
│           pip.exe
│           pip3.13.exe
│           pip3.exe
│           python.exe
│           pythonw.exe
│
├───configs
│       config.yaml
│
├───data
│   ├───processed
│   ├───raw
│   └───samples
├───docs
│       architecture.md
│
├───notebooks
├───scripts
│       process_document.py
│       run_pipeline.py
│
├───src
│   └───eippone_document_ai
│       │   __init__.py
│       │
│       ├───api
│       │       main.py
│       │       routes.py
│       │       __init__.py
│       │
│       ├───classification
│       │       document_classifier.py
│       │       __init__.py
│       │
│       ├───evaluation
│       │       evaluator.py
│       │       metrics.py
│       │       __init__.py
│       │
│       ├───extraction
│       │       field_extractor.py
│       │       schemas.py
│       │       __init__.py
│       │
│       ├───ingestion
│       │       document_loader.py
│       │       file_detector.py
│       │       __init__.py
│       │
│       ├───ocr
│       │       image_preprocessor.py
│       │       ocr_engine.py
│       │       __init__.py
│       │
│       └───validation
│               confidence.py
│               field_validator.py
│               __init__.py
│
└───tests
        test_classification.py
        test_evaluation.py
        test_extraction.py
        test_ingestion.py
        test_ocr.py
        test_validation.py
        __init__.py
```
---

# 20. Security, Governance & Traceability

Because the platform processes potentially sensitive financial and personal information, the architecture should incorporate appropriate security and governance controls.

Key considerations include:

- Authentication
- Authorization
- Role-based access control
- Encryption
- Secure document storage
- Data retention policies
- Audit logging
- Processing traceability
- Model/version tracking
- Human-review tracking
- Data minimization
- Environment separation
- Secrets management

Each processing event should be traceable.

Example:

```text
Document
   ↓
Processing ID
   ↓
OCR Model Version
   ↓
Extraction Model Version
   ↓
Extracted Fields
   ↓
Confidence Scores
   ↓
Validation Findings
   ↓
Human Corrections
   ↓
Final Structured Data
```

---

# 21. Quality & Observability

The platform should provide operational visibility into the entire processing pipeline.

Key monitoring indicators include:

- Documents processed
- Successful processing rate
- OCR failure rate
- Classification failure rate
- Extraction failure rate
- Average confidence
- Human review rate
- Validation exception rate
- Processing latency
- API errors
- Model performance drift

---

# 22. Reproducibility

All experiments should be reproducible through controlled:

- Dataset versions
- Model versions
- Configuration versions
- Prompt versions
- Processing pipelines
- Evaluation datasets
- Experiment metadata

A processing result should be traceable to the exact configuration and model versions that generated it.

---

# 23. Example End-to-End Loan Processing Scenario

### Input

A customer submits:

```text
1. Loan Application PDF
2. Driver's Licence Image
3. Employment Letter PDF
4. Pay Stub PDF
5. Bank Statement PDF
```

### Processing

```text
Documents
    ↓
Ingestion
    ↓
Preprocessing
    ↓
OCR
    ↓
Classification
    ↓
Information Extraction
    ↓
Normalization
    ↓
Cross-document Validation
    ↓
Confidence Scoring
    ↓
Human Review
    ↓
AI Recommendation
    ↓
Dataverse
    ↓
Loan Processing Workflow
```

### Example Output

```json
{
  "application_id": "APP-1002",
  "applicant": {
    "name": "John Smith",
    "address": "123 Main Street"
  },
  "loan": {
    "type": "Personal",
    "amount": 35000,
    "term_months": 60
  },
  "income": {
    "annual": 92500
  },
  "document_processing": {
    "status": "Completed",
    "overall_confidence": 0.95
  },
  "validation": {
    "status": "Passed",
    "findings": []
  },
  "recommendation": {
    "status": "Ready for Review"
  }
}
```

---

# 24. Success Criteria

The platform will be considered successful when it demonstrates measurable improvement over a manual document-processing workflow.

Key success criteria include:

### Technical

- Reliable document ingestion
- High OCR accuracy
- High document-classification accuracy
- High field-extraction accuracy
- Robust validation
- Reliable confidence scoring
- Reproducible evaluation

### Operational

- Reduced manual data entry
- Reduced document-processing time
- Reduced transcription errors
- Increased automation rate
- Efficient exception handling

### Business

- Faster loan application processing
- Improved data quality
- Better employee productivity
- Improved document traceability
- Improved customer experience

---

# 25. Future Expansion

The architecture is intentionally designed as a reusable **EIPPONE Document AI platform**, rather than a loan-specific OCR script.

Potential future applications include:

- Mortgage processing
- Insurance claims
- Banking documents
- KYC document processing
- Financial statement analysis
- Tax document processing
- Contract processing
- Compliance documentation
- Procurement documents
- Government forms
- Healthcare administrative documents

The lending use case provides the initial reference implementation.

---

# 26. EIPPONE Platform Positioning

The project fits within the broader EIPPONE AI and Digital Transformation portfolio.

```text
                    EIPPONE
                       │
        ┌──────────────┼──────────────┐
        │              │              │
        ▼              ▼              ▼
   Simulation       AI / Data      Digital
   Platforms        Intelligence   Transformation
        │              │              │
        │              │              │
        │       Document AI           │
        │              │              │
        │              ▼              │
        │      Digital Lending        │
        │      Document Processing    │
        │              │              │
        └──────────────┼──────────────┘
                       ▼
             Intelligent Enterprise
```

---

# 27. Implementation Note for Stakeholders

### Adaptability

The platform is designed as a modular Document AI architecture. OCR, classification, extraction, validation, and recommendation components can be independently upgraded or replaced.

This enables the solution to adapt to:

- New document types
- New lending products
- New OCR engines
- New AI models
- New enterprise systems
- New business rules

### Evaluation

The **Evaluation** phase is particularly important because Document AI performance must be measured at multiple levels:

```text
OCR
 ↓
Classification
 ↓
Extraction
 ↓
Validation
 ↓
Business Outcome
```

A system with excellent OCR accuracy may still perform poorly if information extraction or validation is unreliable.

Therefore, the project evaluates the **complete processing pipeline**, rather than evaluating OCR in isolation.

### Human-in-the-Loop

Low-confidence or conflicting results should be routed to employees for review.

This creates a controlled workflow:

```text
AI Processing
     ↓
Confidence Assessment
     ↓
 ┌───┴────┐
 │        │
High     Low
 │        │
 ▼        ▼
Auto     Human
Process  Review
 │        │
 └───┬────┘
     ▼
Final Validated Data
```

### Dual Delivery Architecture

The EIPPONE platform is designed from the beginning for two deployment models:

**Portable / Downloadable**

A self-contained version capable of running in a local environment.

**Online / Web**

A browser-based version capable of integrating with cloud infrastructure and enterprise services.

Both versions should provide a **fully interactive UI/UX** rather than being limited to command-line execution.

---

# 28. Project Vision

The long-term vision is to create an intelligent document-processing platform that transforms documents from:

> **Unstructured → Machine-readable → Structured → Validated → Decision-ready**

The EIPPONE AI-Powered Document Processing Platform therefore goes beyond traditional OCR.

It combines:

**OCR + Document AI + NLP + Machine Learning + Validation + Human-in-the-Loop + Workflow Automation**

to create an intelligent foundation for modern digital lending.

---

## EIPPONE Simulation Dynamics Inc.

**AI Transformation • Data Intelligence • Simulation • Digital Operations**

*Building intelligent systems for complex enterprise decision-making.*
