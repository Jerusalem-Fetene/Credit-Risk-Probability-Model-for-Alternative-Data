# Credit-Risk-Probability-Model-for-Alternative-Data
This repository is an End-to-End Implementation for Building, Deploying, and Automating a Credit Risk Model.
# Credit Scoring Business Understanding
Credit risk management is a cornerstone of financial stability for banking institutions. The ability to accurately assess and manage the risk of borrowers defaulting on their obligations is critical for maintaining healthy portfolios, ensuring capital adequacy, and fostering trust in the financial system. The Basel Accords, particularly Basel II, have significantly shaped how financial institutions approach risk measurement and model development in this domain.

# 1) How does the Basel II Accord’s emphasis on risk measurement influence our need for an interpretable and well-documented model?
The Basel II Capital Accord, introduced to enhance the stability and soundness of the international banking system, places a strong emphasis on robust risk measurement and management. It operates on three pillars:
<ul>
<li> <b> Pillar 1: Minimum Capital Requirements:</b> This pillar outlines how banks should calculate their minimum capital to cover credit, operational, and market risks. For credit risk, it introduces the Internal Ratings-Based (IRB) approach, which allows banks to use their own internal models to estimate risk parameters (like Probability of Default, PD; Loss Given Default, LGD; Exposure at Default, EAD).</li>

<li><b>Pillar 2: Supervisory Review Process:</b> This pillar requires banks to assess their capital adequacy in relation to their risk profile and mandates supervisors to intervene if risks are too high.</li>

<li> <b>Pillar 3: Market Discipline:</b> This pillar promotes transparency by requiring banks to disclose key information about their risk exposures, risk assessment processes, and capital adequacy. </li>
</ul>
This framework directly influences the need for interpretable and well-documented credit risk models:
<ul>
<li><b>Regulatory Compliance and Auditability:</b> Under Basel II, particularly with the IRB approach, banks must demonstrate to regulators that their internal models are sound, robust, and accurately reflect risk. This requires extensive documentation of the model's development, validation, and ongoing performance. Interpretability is crucial because regulators need to understand how a model arrives at its decisions, allowing them to audit the model's logic, identify potential flaws, and ensure fairness. A "black-box" model, where the decision-making process is opaque, would be unacceptable in this highly regulated environment.</li>

<li><b>Risk Management and Decision Justification:</b> An interpretable model allows risk managers and loan officers to understand the drivers of credit risk for individual borrowers. This understanding is vital for justifying credit decisions (e.g., approving or denying a loan, setting interest rates), explaining outcomes to customers, and ensuring consistent application of credit policies. If a model predicts a high probability of default, stakeholders need to know why based on specific factors.</li>
<li><b>Model Validation and Monitoring: </b> Well-documented and interpretable models are easier to validate, monitor for performance degradation, and update. Any unexpected behavior or bias can be traced back to specific model components, facilitating quicker diagnosis and resolution.</li>

<li><b>Trust and Accountability:</b> In a financial context, trust is paramount. An interpretable model fosters trust among internal stakeholders, regulators, and customers by making the decision-making process transparent and accountable. It helps in identifying and mitigating potential biases that could lead to discriminatory lending practices. </li>
</ul>
<b> 2) Since we lack a direct "default" label, why is creating a proxy variable necessary, and what are the potential business risks of making predictions based on this proxy?</b>

In many real-world credit scoring scenarios, a direct, universally defined, and readily available "default" label is often absent or difficult to obtain immediately. This can be due to several reasons:
<ul>
<li><b>Legal and Operational Definitions:</b> The precise definition of "default" can vary legally, contractually, and operationally across different financial products or institutions. </li>

<li><b>Time Lag:</b> A true default event (e.g., bankruptcy, charge-off) might occur long after early signs of financial distress, creating a significant time lag in data collection. </li>

<li><b>Data Availability:</b> Historic data might not have a clear flag for "default" or the event itself might be rare, making direct labeling challenging. </li>
Therefore, creating a proxy variable becomes necessary. A proxy variable is an indirect measure that serves as a substitute for the true "default" event when direct observation or clear labeling is unavailable. Common proxies for default in credit risk modeling include:
<li><b>Severe Delinquency:</b> For instance, a loan being overdue by 90 days or more (90+ DPD - Days Past Due).

<li><b>Charge-Off:</b> When a financial institution considers a debt unlikely to be collected and writes it off as a loss.

<li><b>Bankruptcy Filing: </b> A legal declaration of inability to repay debts.

<li><b>Restructuring of Debt:</b> Indicating financial difficulty requiring new terms.
</ul>
<b>Potential Business Risks of Making Predictions Based on a Proxy:</b>

While proxies are essential, their use introduces several business risks:
<ul>
<li>Inaccuracy and Misclassification: The primary risk is that the proxy may not perfectly align with the true definition of default. This can lead to: <ul>
<li>False Positives (Type I Error): Classifying a borrower as "at risk of default" (based on the proxy) when they would not have truly defaulted. This can lead to denying credit to creditworthy individuals, resulting in lost revenue opportunities and potential reputational damage.</li>
<li>False Negatives (Type II Error): Classifying a borrower as "low risk" (based on the proxy) when they are actually heading towards true default. This can lead to approving risky loans, resulting in increased non-performing loans, higher provisions for bad debts, and significant financial losses for the institution.</li> </ul>
<ul>
<li>Financial Impact: Incorrect predictions driven by an imperfect proxy can directly impact the bank's profitability and capital adequacy. Underestimating risk leads to insufficient capital allocation, while overestimating risk can lead to overly conservative lending and missed business opportunities.

<li>Reputational Damage: Inconsistent or unfair lending decisions resulting from a flawed proxy can damage the institution's reputation and lead to customer distrust.

<li>Regulatory Scrutiny: Regulators may scrutinize models built on proxies to ensure their robustness and alignment with regulatory expectations of default definitions, potentially leading to penalties or requirements for model recalibration if the proxy is deemed inadequate.

<li>Model Stability and Maintenance: If the relationship between the proxy and true default changes over time (e.g., due to changes in economic conditions or operational processes), the model's predictive power can degrade, requiring frequent re-evaluation and potential redefinition of the proxy. </li>
</ul>
<b>What are the key trade-offs between using a simple, interpretable model (like Logistic Regression with WoE) versus a complex, high-performance model (like Gradient Boosting) in a regulated financial context? </b>
The choice between simple and complex models in credit scoring involves significant trade-offs, especially within a regulated financial environment:
<ol> 
<li> Simple, Interpretable Models (e.g., Logistic Regression with Weight of Evidence - WoE):
</ol>