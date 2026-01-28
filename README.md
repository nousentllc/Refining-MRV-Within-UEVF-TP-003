# Refining MRV with UEVF
### Making Marginal Reliability Value (MRV) Decisively Locational, Risk-Aware, and Market-Consistent

[![Status](https://img.shields.io/badge/Status-Protocol_Active-success.svg)]()
[![License](https://img.shields.io/badge/License-MIT-green.svg)]()
[![Documentation](https://img.shields.io/badge/Docs-Whitepaper-blue.svg)]()

**Author:** Justin Candler  
**Contact:** [Uriel](mailto:your-email@example.com)  
**Date:** August 26, 2025  

## 📖 Abstract
Traditional capacity valuation often relies on system-wide averages that mask local scarcity and over-value constrained assets. This repository implements the **Refining MRV** framework, an operational upgrades package for the Unified Energy Valuation Framework (UEVF). It transforms Marginal Reliability Value (MRV) from a static planning metric into a dynamic, locational procurement signal.

Key innovations include:
1.  **Locational MRV:** Computing value by Load Resource Zone (LRZ) to reflect local scarcity.
2.  **Market-Consistent Stop Rule:** A "Buy/No-Buy" test equating MRV with the marginal cost of capacity from the VRR curve.
3.  **Probabilistic Accreditation:** Replacing binary "deliverable" flags with continuous probabilities for queue survival ($p_{surv}$) and deliverability.
4.  **Duration-Value Curves:** Valuing storage based on its ability to mitigate duration-specific tail risks (2-10h).

## 🚀 Key Features

### 1. The Locational MRV Formula
We implement the core valuation equation:
$$\widehat{MRV}_{i,z} = \left(-\frac{\partial EUE_z}{\partial MW_i}\right) \cdot VOLL_z \cdot p_{surv,i} \cdot ELCC^{RA}_{i,z}$$
* **Locational Relief:** $-\partial EUE_z / \partial MW_i$ captures local reliability benefits.
* **Risk weighting:** $p_{surv}$ and $ELCC^{RA}$ discount for attrition and deliverability risk.

### 2. Market-Consistent Stop Rule
To prevent over-procurement, the framework implements a rigorous stop rule:
> **Procure capacity in zone $z$ until $\widehat{MRV}_{i,z} = MC_z$.**

Where $MC_z$ is derived from the Variable Resource Requirement (VRR) curve (slope, cap, and floor).

### 3. Queue Survival v2
We deploy a gradient-boosted survival model to estimate $p_{surv}$ based on project attributes (study phase, TO, state, tech), going beyond simple upgrade-cost heuristics.

## Citation
If you use this framework, please cite:

Code snippet
@techreport{Candler2025_RefiningMRV,
  title={Refining MRV with UEVF: Making Marginal Reliability Value Decisively Locational, Risk-Aware, and Market-Consistent},
  author={Candler, Justin},
  year={2025},
  institution={Nous Energy},
  number={TP-003}
}
⚖️ License
This project is licensed under the MIT License - see the LICENSE file for details.

