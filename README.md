# AI-Driven Supply Chain Disruption Propagation and Resilience Scoring

A graph-based AI pipeline for modelling how disruptions propagate through global supply chain networks, predicting resilience scores, classifying disruption severity, and providing IoT-driven early warning — built as research preparation for doctoral work in AI-driven supply chain risk management at Cranfield University.

---

## Overview

Global supply chains face escalating disruption risks from climate change, cyber attacks, geopolitical instability, and financial shocks. When a disruption strikes at one node — a supplier, manufacturer, or distributor — it does not stay there. It propagates downstream through the network in what researchers call the **ripple effect** or cascading failure: a single supplier disruption can halt production lines, empty retail shelves, and affect customer service levels across multiple tiers of the supply chain.

This project addresses that challenge by building a complete AI pipeline from supply chain network representation to interpretable, actionable resilience intelligence:

- **Network modelling** — represent the supply chain as a directed graph with realistic physical and financial properties
- **Disruption simulation** — propagate 300 disruption scenarios across the network, modelling ripple effects tier by tier
- **ML-driven resilience scoring** — predict resilience scores and classify disruption severity from network features
- **Explainable decision support** — identify which nodes, features, and disruption types most drive resilience loss
- **IoT early warning** — simulate Industry 4.0 sensor streams and detect anomalous behaviour before full disruption

---

## Motivation

This work is directly informed by Dr Abhijeet Ghadge's research programme at Cranfield University on supply chain risk, resilience, and Industry 4.0 applications. Dr Ghadge's work on disruption propagation (the ripple effect), systems thinking for supply chain risk, and IoT-based information integration provides the theoretical foundation for this pipeline.

The critical open challenge identified in this literature is moving from reactive risk management — responding after disruptions occur — to **proactive, AI-enabled risk intelligence** that predicts propagation paths, scores resilience, and triggers early warnings before disruptions reach critical nodes. This is what this project demonstrates.

---

## Pipeline

```
Supply chain network construction
(Directed graph: suppliers → manufacturers → distributors → retailers)
        ↓
Node property assignment
(Single-source dependency, financial vulnerability, geographic risk,
 lead time, inventory buffer — risk factors from the literature)
        ↓
Disruption scenario generation (n=300)
(Origin node, disruption type, initial severity)
        ↓
BFS disruption propagation simulation
(Ripple effect: severity × flow criticality × dependency − buffer dampening)
        ↓
Resilience score computation per scenario
        ↓
Gradient Boosting regression — resilience score prediction (R² > 0.90)
Random Forest classification — Low / Medium / High severity
        ↓
Permutation importance — explainability layer
        ↓
Four-panel decision support dashboard
        ↓
IoT sensor stream simulation — anomaly detection early warning
```

---

## Key Results

- Disruptions originating at **Tier 3 suppliers** propagate furthest and cause the highest total impact — consistent with Dr Ghadge's ripple effect research
- **Single-source dependency** and **initial severity** are the strongest predictors of resilience loss — nodes with no alternative suppliers are the most critical vulnerabilities
- **Climate and geopolitical disruptions** produce the lowest resilience scores on average
- ML resilience prediction achieves **R² > 0.90**, demonstrating that disruption propagation dynamics are learnable from network features
- **IoT anomaly detection** identifies throughput degradation 7-10 days before full disruption — enabling proactive intervention

---

## Supply Chain Network Structure

| Tier | Node type | Example nodes | Risk profile |
|---|---|---|---|
| Tier 3 | Raw material suppliers | S3_A (China), S3_B (India) | Highest geographic and geopolitical risk |
| Tier 2 | Component suppliers | S2_A (Germany), S2_B (Japan) | High single-source dependency |
| Tier 1 | Direct suppliers | S1_A (UK), S1_B (USA) | High financial vulnerability |
| 0 | Manufacturers | MFG_A, MFG_B | Critical propagation nodes |
| -1 | Distributors | DIST_A, DIST_B | Lead time amplification |
| -2 | Retailers | RET_A, RET_B, RET_C | End consumer impact |

---

## Disruption Types Modelled

| Disruption type | Characteristics | Real-world examples |
|---|---|---|
| Climate | Geographic, unpredictable, sustained | Flooding, drought, storms |
| Cyber | Instantaneous, spreads via digital links | Ransomware, data breach |
| Financial | Gradual, amplified by credit dependency | Supplier insolvency |
| Pandemic | Simultaneous multi-node, labour-driven | COVID-19 type events |
| Geopolitical | Trade policy, border closures | Tariffs, sanctions |

---

## Outputs

| File | Description |
|---|---|
| `supply_chain_network.png` | Network graph coloured by node type across all tiers |
| `supply_chain_resilience_dashboard.png` | Four-panel dashboard: feature importance, resilience by type/tier, node vulnerability ranking, prediction accuracy |
| `iot_early_warning.png` | IoT sensor time series with anomaly detection for two nodes |

---

## Requirements

```bash
pip install networkx matplotlib scikit-learn pandas numpy seaborn
```

| Library | Purpose |
|---|---|
| NetworkX | Supply chain graph construction and traversal |
| scikit-learn | ML models, preprocessing, explainability |
| Pandas / NumPy | Data handling and simulation |
| Matplotlib / Seaborn | Dashboard visualisation |

---

## Usage

```bash
jupyter notebook supply_chain_resilience.ipynb
```

All output figures saved automatically.

---

## Connection to PhD Research

This project is built as preparation for doctoral research in AI-driven supply chain risk and resilience management at Cranfield University, supervised by Dr Abhijeet Ghadge and Dr Nicky Yates.

**Ripple effect modelling:** The BFS disruption propagation algorithm directly implements the ripple effect / cascading failure dynamics central to Dr Ghadge's published research. The simulation shows how disruption severity decays across edges but amplifies at nodes with high single-source dependency — consistent with empirical findings in the supply chain risk literature.

**Industry 4.0 integration:** The IoT sensor stream simulation reflects Dr Ghadge and Dr Yates's 2025-2026 research on IoT-based information integration and supply chain performance. The early warning layer demonstrates how real-time sensor data can trigger proactive risk responses before disruptions propagate.

**AI-driven decision support:** The explainability layer (permutation importance) and four-panel dashboard translate ML outputs into actionable intelligence for supply chain managers — identifying which nodes are single points of failure, which disruption types are most dangerous, and which risk factors most drive resilience loss.

**Next steps toward the PhD:**

- Replace simulated network with real supply chain data from industry partners
- Implement Graph Neural Networks for learned disruption propagation representations
- Integrate digital twin simulation for real-time what-if scenario analysis
- Extend IoT layer with live sensor data and time-series anomaly detection models
- Incorporate climate risk projections (CMIP6) for long-term resilience planning
- Develop multi-objective optimisation for resilience-cost trade-off analysis

---

## References

Ghadge, A., Dani, S., & Kalawsky, R. (2012). Supply chain risk management: present and future scope. *International Journal of Logistics Management*, 23(3), 313-339.

Ivanov, D., Dolgui, A., & Sokolov, B. (2019). The impact of digital technology and Industry 4.0 on the ripple effect and supply chain risk analytics. *International Journal of Production Research*, 57(3), 829-846.

Xue, Y., Yates, N., & Ghadge, A. (2025). The relationship between IoT-based information integration, decision-making uncertainty, and supply chain performance. *International Journal of Logistics Research and Applications*.

Ghadge, A., & Mogale, D. G. (2023). Big Data Analytics and Its Applications in Supply Chain Management. Springer Nature Singapore.

---

## Author

**Kunal Kamble**
MSc Advanced Computer Science, University of Liverpool
[LinkedIn](https://linkedin.com/in/kunal-kamble19) | [Email](mailto:kamblekunal165@gmail.com) | [GitHub](https://github.com/kunal190399)

*Built in preparation for doctoral research in AI-driven supply chain risk and resilience at Cranfield University, supervised by Dr Abhijeet Ghadge and Dr Nicky Yates.*
