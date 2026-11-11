# A Data-Grounded Conversational AI Agent for Integrated Home Environment Assessment and Outdoor Activity Recommendations

> **Project:** DietSense — 居家環境與外出建議代理人  
> **Status:** Research proposal / pilot study planned

## Abstract

Indoor thermal comfort assessment requires consideration of environmental conditions, occupant preferences, and device operations rather than air temperature alone. However, outdoor forecasts differ from indoor measurements in spatial representativeness and temporal resolution, while air conditioning, dehumidification, and window opening can produce overlapping temperature–humidity patterns. These limitations complicate reliable interpretation of single-point measurements and the generation of actionable recommendations.

This paper proposes a **data-grounded conversational agent** that integrates indoor sensing, township-level weather forecasts, confirmed device states, and user feedback to support home environment assessment and outdoor activity recommendations. The proposed architecture employs **ESP32-based temperature–humidity sensing, MQTT messaging, SQLite storage, and a Python analytical engine**. A large language model coordinates data retrieval and analytical operations through **whitelisted tool calls**, while numerical calculations and classification are delegated to deterministic modules.

Indoor observations and outdoor forecasts are maintained as distinct data sources and aligned by location and time. Device states are obtained from operation records or explicit user confirmation rather than inferred directly from environmental changes. When evidence is insufficient, a clarification mechanism requests targeted information and communicates uncertainty instead of asserting unsupported causes.

A **two-week pilot study** is planned to collect environmental measurements, device-operation logs, and user-reported labels. A fixed-rule baseline and a shallow decision-tree classifier will be compared using chronological evaluation to reduce temporal leakage. Assessment will examine classification accuracy, macro-averaged F1 score, recommendation acceptance, evidence consistency, and clarification burden. An ablation analysis will investigate the incremental contribution of confirmed device states and user feedback.

The intended outcome is a demonstrable prototype and an evaluation framework for determining whether coordinated sensing, constrained language-model orchestration, and explicit uncertainty handling improve the traceability and practical utility of personalized environmental recommendations. **The pilot is designed to establish system feasibility rather than demonstrate population-level generalizability or causal attribution.**

**Index Terms:** Conversational agents · Indoor environmental monitoring · Internet of Things · Large language models · Thermal comfort · Tool orchestration · Uncertainty handling

---

## 01. Research Motivation and Problem

Temperature alone does not capture indoor comfort. Occupant preferences, indoor humidity, and recent device operations all affect interpretation. At the same time, township-level outdoor forecasts cannot be treated as direct indoor observations. Similar temperature–humidity patterns may arise from air conditioning, dehumidification, window opening, or other conditions.

**Research objective:** Provide evidence-grounded, actionable home-environment and outdoor-activity recommendations without assigning unsupported causes to ambiguous sensor changes.

## 02. Proposed System

| Layer | Planned component | Role |
| --- | --- | --- |
| Indoor sensing | ESP32 temperature–humidity sensor | Collect indoor environmental observations |
| Messaging | MQTT | Transport sensor measurements |
| Persistence | SQLite | Store measurements, operation records, and feedback |
| Outdoor context | Township-level weather forecast | Supply location- and time-aligned external context |
| Analysis | Python deterministic modules | Perform numerical calculations, features, and classification |
| Conversation | LLM with whitelisted tool calls | Coordinate retrieval, analysis, clarification, and responses |
| Human input | Device-operation records and explicit confirmation | Establish device-state evidence instead of guessing from sensor patterns |

### Evidence-grounded reasoning flow

```text
Indoor observations (ESP32 → MQTT) ─┐
Township weather forecasts ─────────┤
Device-operation records ───────────┼──> SQLite / data retrieval
User feedback & confirmations ──────┘             │
                                                  ▼
                                     Python analytical modules
                                                  │
                                                  ▼
                                   LLM (whitelisted tool calls)
                                                  │
                            ┌─────────────────────┴──────────────────┐
                            ▼                                        ▼
                  Evidence sufficient?                         Evidence missing?
                            │                                        │
                            ▼                                        ▼
                Grounded recommendation                  Targeted clarification
                                                               + uncertainty
```

Indoor observations and outdoor forecasts remain distinct sources. Location and time alignment are required before producing integrated recommendations.

## 03. Planned Evaluation

**Pilot duration:** Two weeks of environmental sensing, device-operation logging, and user-reported labels.

| Evaluation dimension | Planned approach |
| --- | --- |
| Classification methods | Fixed-rule baseline vs. shallow decision tree |
| Data splitting | Chronological evaluation to limit temporal leakage |
| Classification measures | Accuracy and macro-averaged F1 |
| Practical usefulness | Recommendation acceptance |
| Response reliability | Evidence consistency |
| Interaction overhead | Clarification burden |
| Component contribution | Ablation of confirmed device states and user feedback |

> **Research status:** The pilot study, comparisons, and ablations are proposed evaluation activities. No empirical improvements or study results are claimed here.

## 04. Scope and Intended Outcome

The project aims to deliver a **demonstrable conversational-agent prototype** and a **reproducible evaluation framework** for home-environment assessment and outdoor-activity guidance. The study focuses on system feasibility, traceable evidence use, constrained tool orchestration, and explicit handling of uncertain observations. It does **not** claim population-level generalizability or causal attribution from single-point temperature–humidity measurements.

---

## Keywords

`Conversational Agents` · `Indoor Environmental Monitoring` · `IoT` · `LLM` · `Thermal Comfort` · `Tool Orchestration` · `Uncertainty Handling`
