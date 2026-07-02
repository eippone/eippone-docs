┌─────────────────────────────────────────────────────────────────────────────┐
│                             END USERS                                       │
├─────────────────────────────────────────────────────────────────────────────┤
│  Executives │ SOC Analysts │ Risk Managers │ Data Scientists │ Customers    │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         MULTI-CHANNEL INTERFACE                             │
├─────────────────────────────────────────────────────────────────────────────┤
│  Web UI (Gradio)                                                            │
│  Enterprise Portal                                                          │
│  Teams / Slack                                                              │
│  Mobile App                                                                 │
│  API Gateway                                                                │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                    CONVERSATIONAL AI ORCHESTRATOR                           │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Session Manager                                                            │
│  Conversation Memory                                                        │
│  Context Manager                                                            │
│  User Profile Manager                                                       │
│  Prompt Manager                                                             │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                           GUARDRAILS LAYER                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│ Prompt Injection Detection                                                  │
│ Sensitive Information Protection                                            │
│ PII Detection                                                               │
│ Security Policies                                                           │
│ Access Control                                                              │
│ Role Based Restrictions                                                     │
│ Content Filtering                                                           │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                             AGENT ENGINE                                    │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│ Intent Detection                                                            │
│ Task Planning                                                               │
│ Tool Selection                                                              │
│ Function Calling                                                            │
│ Workflow Routing                                                            │
│ Multi-Agent Coordination                                                    │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
         ┌────────────────────────────┼─────────────────────────────┐
         ▼                            ▼                             ▼

┌───────────────────┐     ┌─────────────────────┐     ┌─────────────────────┐
│ Retrieval Agent   │     │ Analytics Agent     │     │ Executive Agent     │
├───────────────────┤     ├─────────────────────┤     ├─────────────────────┤
│ Semantic Search   │     │ Statistics          │     │ Business Story      │
│ Vector Search     │     │ Trend Analysis      │     │ Executive Summary   │
│ RAG               │     │ Forecasting         │     │ Risk Narrative      │
│ Knowledge Lookup  │     │ Anomaly Detection   │     │ Recommendations     │
└───────────────────┘     └─────────────────────┘     └─────────────────────┘

         │                            │                             │
         └────────────────────────────┼─────────────────────────────┘
                                      ▼

┌─────────────────────────────────────────────────────────────────────────────┐
│                             TOOL ECOSYSTEM                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│ Service 1: External APIs                                                    │
│   • Threat Intelligence APIs                                                │
│   • Fraud APIs                                                              │
│   • Asset APIs                                                              │
│   • Security APIs                                                           │
│                                                                             │
│ Service 2: Semantic Search                                                  │
│   • ChromaDB                                                                │
│   • FAISS                                                                   │
│   • Pinecone                                                                │
│                                                                             │
│ Service 3: Business Functions                                               │
│   • Risk Calculator                                                         │
│   • Fraud Scoring                                                           │
│   • Compliance Assessment                                                   │
│   • KPI/KRI Calculations                                                    │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼

┌─────────────────────────────────────────────────────────────────────────────┐
│                          KNOWLEDGE & DATA LAYER                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│ Structured Data                                                             │
│   • PostgreSQL                                                              │
│   • SQL Server                                                              │
│   • Snowflake                                                               │
│                                                                             │
│ Semi-Structured                                                             │
│   • CSV                                                                     │
│   • JSON                                                                    │
│   • Parquet                                                                  │
│                                                                             │
│ Unstructured                                                                │
│   • Reports                                                                 │
│   • PDFs                                                                     │
│   • Policies                                                                │
│   • Security Logs                                                           │
│                                                                             │
│ Vector Database                                                             │
│   • ChromaDB                                                                │
│   • Embeddings                                                              │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼

┌─────────────────────────────────────────────────────────────────────────────┐
│                      CYBERSECURITY DATA PIPELINE                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│ Synthetic Event Generator                                                   │
│ (Cybersecurity Data Generator)                                              │
│                                                                             │
│     Authentication Events                                                   │
│     Malware Events                                                          │
│     Network Events                                                          │
│     Insider Threat Events                                                   │
│     Data Exfiltration Events                                                │
│     Fraud Events                                                            │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼

┌─────────────────────────────────────────────────────────────────────────────┐
│                         ANALYTICS & AI LAYER                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│ Statistical Analysis                                                        │
│ Machine Learning                                                            │
│ Anomaly Detection                                                           │
│ Risk Scoring                                                                │
│ Fraud Detection                                                             │
│ Trend Analysis                                                              │
│ Predictive Analytics                                                        │
│ Digital Twin Simulation                                                     │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼

┌─────────────────────────────────────────────────────────────────────────────┐
│                         VISUALIZATION ENGINE                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│ Tables                                                                      │
│ Dashboards                                                                  │
│ Executive Reports                                                           │
│ Incident Summaries                                                          │
│ Heat Maps                                                                   │
│ Time Series                                                                 │
│ Risk Trends                                                                 │
│ Attack Trends                                                               │
│ Fraud Trends                                                                │
│ PDF Reports                                                                 │
│ PowerPoint Reports                                                          │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼

┌─────────────────────────────────────────────────────────────────────────────┐
│                         EXECUTIVE DECISION SUPPORT                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│ Key Risk Indicators (KRIs)                                                  │
│ Key Performance Indicators (KPIs)                                           │
│ Threat Intelligence Summary                                                 │
│ Fraud Exposure Assessment                                                   │
│ Risk Appetite Monitoring                                                    │
│ Strategic Recommendations                                                   │
│ Mitigation Prioritization                                                   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
