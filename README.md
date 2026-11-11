# A Data-Grounded Conversational AI Agent for Integrated Home Environment Assessment and Outdoor Activity Recommendations

## Abstract

Indoor thermal comfort assessment requires consideration of environmental conditions, occupant preferences, and device operations rather than air temperature alone. However, outdoor forecasts differ from indoor measurements in spatial representativeness and temporal resolution, while air conditioning, dehumidification, and window opening can produce overlapping temperature–humidity patterns. These limitations complicate reliable interpretation of single-point measurements and the generation of actionable recommendations.

This paper proposes a **data-grounded conversational agent** that integrates indoor sensing, township-level weather forecasts, confirmed device states, and user feedback to support home environment assessment and outdoor activity recommendations. The proposed architecture employs **ESP32-based temperature–humidity sensing, MQTT messaging, SQLite storage, and a Python analytical engine**. A large language model coordinates data retrieval and analytical operations through **whitelisted tool calls**, while numerical calculations and classification are delegated to deterministic modules.

Indoor observations and outdoor forecasts are maintained as distinct data sources and aligned by location and time. Device states are obtained from operation records or explicit user confirmation rather than inferred directly from environmental changes. When evidence is insufficient, a clarification mechanism requests targeted information and communicates uncertainty instead of asserting unsupported causes.

A **two-week pilot study** is planned to collect environmental measurements, device-operation logs, and user-reported labels. A fixed-rule baseline and a shallow decision-tree classifier will be compared using chronological evaluation to reduce temporal leakage. Assessment will examine classification accuracy, macro-averaged F1 score, recommendation acceptance, evidence consistency, and clarification burden. An ablation analysis will investigate the incremental contribution of confirmed device states and user feedback.

The intended outcome is a demonstrable prototype and an evaluation framework for determining whether coordinated sensing, constrained language-model orchestration, and explicit uncertainty handling improve the traceability and practical utility of personalized environmental recommendations. **The pilot is designed to establish system feasibility rather than demonstrate population-level generalizability or causal attribution.**

**Index Terms:** Conversational agents · Indoor environmental monitoring · Internet of Things · Large language models · Thermal comfort · Tool orchestration · Uncertainty handling
