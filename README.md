# Grounded Commercial Credit Risk Analyzer

An explainable AI pipeline designed to automate preliminary credit appraisals for commercial lending while enforcing strict institutional governance (RBI/BCBS 239 alignment).

---

## 1. Problem Statement
Traditional commercial credit underwriting requires hours of manual cross-verification across disparate data sources (MCA filings, bank statements, and operational market signals). Generic LLM deployments pose substantial operational and regulatory risk—namely hallucinations, bias, and uncontrolled decision-making—if permitted to approve credit autonomously.

---

## 2. Solution Architecture
* **Model:** Google Gemini 3 Flash / 1.5 Flash
* **Environment:** Google AI Studio (Playground)
* **Temperature:** 0.1 (Strict factual extraction, zero creative deviation)
* **Governance Framework:** Defensive UX with Human-in-the-Loop (HITL) sign-off gate.

---

## 3. System Prompt Guardrails
To prevent regulatory liability and inaccurate credit scoring, the pipeline operates under four foundational rules:
1. **Factual Grounding:** Evaluation is restricted exclusively to provided data points.
2. **Early Warning Signals (EWS):** Mandatory identification of leading indicators prior to default.
3. **Defensive Governance:** Autonomous decision-making is strictly prohibited; the model acts solely as an analytical assistant for a Human Credit Officer.
4. **Anti-Hallucination Fallback:** Missing fields are explicitly marked as "Data Not Available" rather than mathematically estimated.

---

## 4. Test Scenario: Sharma Logistics Pvt Ltd
* **Loan Request:** ₹1.5 Crore for fleet expansion
* **Financials Provided:** ₹12 Cr annual turnover, 4.2% net profit margin, ₹3 Cr existing debt, ~₹90 lakh monthly bank credits.
* **Unstructured Operational Signals:** 2 director resignations in 45 days, 60-day delay in diesel vendor payments.

---

## 5. Execution Results & Findings
* **Turnover Discrepancy:** The model cross-referenced monthly bank statements (~₹10.8 Cr annualized) against the declared turnover (₹12 Cr) and detected an unexplained ₹1.2 Cr variance.
* **Leading Indicators Identified:**
  * Governance risk flagged from sudden director exits.
  * Severe liquidity stress flagged from vendor payment delays for core operating expenses.
* **Missing Data Handling:** Debt Service Coverage Ratio (DSCR) and collateral availability were labeled "Data Not Available."
* **Final Sign-off Gate:** Execution halted automatically with: `Final Decision: Pending Human Credit Officer Sign-off`.
