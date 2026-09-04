# Patient Monitoring & Early Deterioration Detection System

An AI-assisted post-discharge patient monitoring platform designed to identify potential deterioration early through **personalized monitoring, multi-channel patient interaction, longitudinal data analysis, and risk assessment**.

The system is designed around one core principle:

> **Different ways of collecting patient information, one unified risk engine.**

---

## 1. Problem Statement

After hospital discharge, patients may experience changes in their condition that are not identified until they become serious.

Traditional follow-up methods often rely on:

* Scheduled hospital visits
* Manual phone calls
* Patient-initiated communication
* Generic monitoring instructions

These approaches may fail to detect subtle deterioration between hospital visits.

The proposed system provides **continuous, personalized post-discharge monitoring** based on the patient's condition, baseline, risk level, symptoms, and recovery trajectory.

---

# 2. Proposed Solution

The system begins with information provided by the hospital at discharge.

This includes:

* Discharge information
* Relevant medical history
* Baseline condition
* Patient risk level

Based on this information, the system generates a **personalized monitoring plan**.

The patient can then provide information through the interaction method most suitable for them:

* Smartphone application
* Voice / telephone interaction
* SMS
* Connected medical devices

All collected information is converted into a common data format and processed by the same **AI / Risk Engine**.

The system analyzes:

* Patient baseline
* Symptoms
* Changes in symptoms
* Vital-sign trends
* Longitudinal patient data
* Recovery trajectory

The resulting risk assessment determines whether the system should:

1. Continue normal monitoring
2. Increase monitoring and ask additional questions
3. Alert a doctor or nurse

---

# 3. Core System Principle

The system does **not** treat App, Voice, SMS, and Medical Devices as independent monitoring systems.

Instead, every channel feeds into a common data pipeline.

```text
APP ───────────────┐
                   │
VOICE / PHONE ─────┤
                   │
SMS ───────────────┼──► DATA NORMALIZATION
                   │           │
MEDICAL DEVICES ───┘           ▼
                       COMMON PATIENT DATA
                               │
                               ▼
                         RISK ENGINE
                               │
                               ▼
                       RISK ASSESSMENT
                               │
                               ▼
                       CLINICIAN ALERT
```

This allows information collected through different interaction methods to be analyzed together.

For example:

```text
Patient reports:
"I am more breathless today."

              +

SpO₂:
94% → 91%

              +

Previous observations:
Stable for 5 days

              +

Patient baseline:
Normal SpO₂ = 97–99%

              ↓

         RISK ENGINE

              ↓

    Potential Deterioration

              ↓

 Additional Questions /
 Increased Monitoring
```

---

# 4. Complete Architectural Flow

```text
                    ┌─────────────────────┐
                    │       HOSPITAL      │
                    │                     │
                    │ Discharge           │
                    │ Medical History     │
                    │ Baseline Condition  │
                    │ Risk Level          │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ MONITORING SERVICE  │
                    │                     │
                    │ Personalized        │
                    │ Monitoring Plan      │
                    └──────────┬──────────┘
                               │
                               ▼
              ┌────────────────────────────────┐
              │      PATIENT INTERACTION       │
              │                                │
              │  ┌──────┐ ┌───────┐ ┌──────┐ │
              │  │  APP │ │ VOICE │ │ SMS  │ │
              │  └──────┘ └───────┘ └──────┘ │
              │                                │
              │       Medical Devices          │
              └───────────────┬────────────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │   DATA NORMALIZATION │
                   │                      │
                   │ Symptoms             │
                   │ Patient Responses    │
                   │ BP / SpO₂            │
                   │ Other Measurements   │
                   │ Daily Changes        │
                   └──────────┬───────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │      RISK ENGINE     │
                   │                      │
                   │ Patient Baseline     │
                   │ Symptom Changes      │
                   │ Vital Sign Trends    │
                   │ Longitudinal Data    │
                   │ Recovery Trajectory  │
                   └──────────┬───────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │    RISK ASSESSMENT   │
                   │                      │
                   │ Normal / Low Risk    │
                   │ Potential Deterior.  │
                   │ High Risk            │
                   └──────────┬───────────┘
                              │
                    ┌─────────┴─────────┐
                    │                   │
                    ▼                   ▼
             ┌─────────────┐     ┌─────────────┐
             │   CONTINUE  │     │    ALERT    │
             │  MONITORING │     │ DOCTOR /    │
             │             │     │    NURSE    │
             └─────────────┘     └─────────────┘
```

---

# 5. System Workflow

## Step 1 — Hospital Discharge

The hospital provides relevant patient information:

```text
Discharge Information
        +
Relevant Medical History
        +
Baseline Condition
        +
Risk Level
```

This information becomes the foundation for personalized monitoring.

---

## Step 2 — Personalized Monitoring Plan

The system determines:

* What information should be collected
* Which symptoms should be monitored
* Which vital signs are relevant
* How frequently the patient should be monitored
* When additional questions should be asked

The monitoring plan is adapted according to the patient's risk.

---

## Step 3 — Patient Interaction

The patient can interact using the method most suitable for them:

```text
                PATIENT
                   │
       ┌───────────┼───────────┐
       ▼           ▼           ▼
   Smartphone     Voice       SMS
       │           │           │
       └───────────┼───────────┘
                   │
                   ▼
           Medical Devices
```

The system is designed to remain accessible even for patients who are not comfortable using smartphones or complex applications.

---

## Step 4 — Data Collection

The system collects information such as:

* Symptoms
* Patient responses
* Blood pressure
* SpO₂
* Other available measurements
* Changes compared with previous observations

---

## Step 5 — AI / Risk Engine

The Risk Engine combines the collected information with historical patient data.

It evaluates:

```text
Current Observation
        +
Patient Baseline
        +
Previous Observations
        +
Symptom Changes
        +
Vital-Sign Trends
        +
Recovery Trajectory
        ↓
   Risk Assessment
```

---

## Step 6 — Risk Assessment

The system categorizes the patient's current state.

### Normal / Low Risk

```text
Continue normal monitoring
```

### Potential Deterioration

```text
Increase monitoring
        +
Ask additional questions
```

### High Risk

```text
Generate alert
        ↓
Doctor / Nurse
```

---

# 6. Key Differentiator

The primary innovation is **not simply patient monitoring**.

The system combines two major capabilities:

### Personalized Deterioration Detection

The system does not use exactly the same monitoring process for every patient.

Instead, monitoring is based on:

* Individual baseline
* Risk level
* Symptoms
* Vital-sign trends
* Previous observations
* Recovery trajectory

### Accessible Patient Interaction

Patients can communicate through the method that is most accessible to them.

```text
Technology-comfortable patient
          ↓
      Smartphone

          OR

Less technology-comfortable patient
          ↓
      Voice / Phone

          OR

Simple communication required
          ↓
         SMS

          OR

Available measurements
          ↓
   Medical Devices
```

Regardless of the input method:

```text
Different Interaction Channels
              ↓
       Common Data Model
              ↓
        Same Risk Engine
```

This creates a unified monitoring system rather than multiple disconnected solutions.

---

# 7. Phase One — Folder Structure

The initial implementation focuses on establishing the core software architecture.

```text
patient-monitoring-system/
│
├── frontend/
│   ├── patient-app/
│   └── clinician-dashboard/
│
├── backend/
│   ├── server/
│   │   ├── routes/
│   │   ├── controllers/
│   │   ├── services/
│   │   │   ├── patient/
│   │   │   ├── monitoring/
│   │   │   ├── data/
│   │   │   ├── risk-engine/
│   │   │   └── alerts/
│   │   ├── models/
│   │   └── utils/
│   │
│   └── integrations/
│       ├── voice/
│       └── sms/
│
├── ai/
│   ├── symptom-analysis/
│   ├── risk-prediction/
│   └── prompts/
│
├── database/
│   ├── schema/
│   └── seed/
│
├── tests/
│
├── docs/
│
├── .env.example
├── .gitignore
├── docker-compose.yml
└── README.md
```

---

# 8. Directory Responsibilities

| Directory                      | Purpose                                      |
| ------------------------------ | -------------------------------------------- |
| `frontend/patient-app`         | Patient-facing application                   |
| `frontend/clinician-dashboard` | Doctor / nurse monitoring dashboard          |
| `backend/server`               | Core backend application                     |
| `backend/server/routes`        | API route definitions                        |
| `backend/server/controllers`   | Request handling                             |
| `backend/server/services`      | Core business logic                          |
| `services/patient`             | Patient management                           |
| `services/monitoring`          | Personalized monitoring plans                |
| `services/data`                | Data processing and normalization            |
| `services/risk-engine`         | Risk calculation and deterioration detection |
| `services/alerts`              | Clinician alert generation                   |
| `backend/integrations/voice`   | Voice / phone integration                    |
| `backend/integrations/sms`     | SMS integration                              |
| `ai/symptom-analysis`          | AI-based symptom interpretation              |
| `ai/risk-prediction`           | Risk prediction models                       |
| `ai/prompts`                   | AI prompts and interaction logic             |
| `database/schema`              | Database definitions                         |
| `database/seed`                | Initial / demonstration data                 |
| `tests`                        | Automated testing                            |
| `docs`                         | Technical documentation                      |

---

# 9. Phase One Development Goal

The first implementation should establish the following complete pipeline:

```text
Hospital Data
      ↓
Patient Baseline
      ↓
Risk Level
      ↓
Personalized Monitoring Plan
      ↓
Patient Interaction
      ↓
Data Collection
      ↓
Data Normalization
      ↓
Risk Engine
      ↓
Risk Assessment
      ↓
Doctor / Nurse Alert
```

The architecture should be modular so that additional AI models, interaction channels, medical measurements, and clinical workflows can be added later without redesigning the entire system.

---

# 10. Development Philosophy

The project follows these principles:

* **Patient-centric** — monitoring is personalized to the individual.
* **Multi-channel** — patients can interact through different communication methods.
* **Unified data pipeline** — all channels feed the same risk engine.
* **Longitudinal analysis** — changes over time are more important than isolated observations.
* **Baseline-aware** — patient-specific baselines are considered during assessment.
* **Risk-based monitoring** — monitoring intensity can change according to risk.
* **Clinician-in-the-loop** — the system assists doctors and nurses rather than replacing clinical judgment.
* **Modular architecture** — components can be independently expanded or replaced.
* **Privacy and security** — patient data must be handled using appropriate security and access controls.

---

# 11. Project Status

### Phase One

* [ ] Project structure
* [ ] Database schema
* [ ] Patient management
* [ ] Hospital discharge data
* [ ] Patient baseline creation
* [ ] Personalized monitoring plan
* [ ] Patient application
* [ ] Clinician dashboard
* [ ] Data normalization
* [ ] Initial risk engine
* [ ] Alert system

### Future Phases

* [ ] Voice-based interaction
* [ ] SMS-based interaction
* [ ] Medical device integrations
* [ ] Advanced AI risk prediction
* [ ] Recovery trajectory modeling
* [ ] Multilingual interaction
* [ ] Advanced analytics
* [ ] Production deployment

---

# 12. High-Level System Summary

```text
                 HOSPITAL
                    │
                    ▼
          Patient Baseline + Risk
                    │
                    ▼
       Personalized Monitoring Plan
                    │
                    ▼
       ┌────────────┼────────────┐
       │            │            │
      APP         VOICE         SMS
       │            │            │
       └────────────┼────────────┘
                    │
              MEDICAL DATA
                    │
                    ▼
          DATA NORMALIZATION
                    │
                    ▼
              RISK ENGINE
                    │
       ┌────────────┼────────────┐
       │            │            │
    Baseline     Symptoms     Trends
       │            │            │
       └────────────┼────────────┘
                    │
                    ▼
             RISK ASSESSMENT
                    │
          ┌─────────┼─────────┐
          │         │         │
          ▼         ▼         ▼
        LOW      POTENTIAL   HIGH
        RISK      RISK       RISK
          │         │         │
          ▼         ▼         ▼
       Continue   Increase   Alert
       Monitoring Monitoring Doctor
```

---

## Final Concept

> **Hospital knowledge establishes the patient's baseline.
> Personalized monitoring collects what matters.
> Multiple interaction channels make monitoring accessible.
> Longitudinal AI analysis identifies meaningful changes.
> Risk assessment determines when clinical attention is required.**

The goal is to move post-discharge monitoring from **generic follow-up** toward **personalized, continuous, accessible, and risk-aware monitoring**.
