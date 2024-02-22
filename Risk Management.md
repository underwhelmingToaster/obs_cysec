
> [!TLDR] TLDR
> Risk management is used to develop and implement information
> security strategies to reduce risks to an acceptable level.

The process of risk managements includes:
- Identifying factors that could damage or disclose data
- evaluating those factors considering data value and countermeasure cost
- implementing cost-effective solutions for mitigating or reducing risk

## 1 Types of Risks
### 1.1 Risk
The possibility that something could damage, destroy, or disclose data or other
resources.

### 1.2 Realized Risk
When a risk has been exploited.

## 2 Risks Assessment
### 2.1 Methodologies
There are two risk assessment methodologies
- **Quantitative risk analysis**: assigns real dollar figures to the loss of an asset
- **Qualitative risk analysis**: assigns subjective and intangible values to the loss of an asset

### 2.2 Quantitative risk analysis
#### 2.2.1 Definitions
- **Asset Value (AV)**
- **Exposure Factor (EF):** Percentage of loss that an organization would experience if a _specific asset_ is violated by a realized risk.
- **Single Loss Expectancy (SLE):** The cost associated with a single realized risk against a _specific asset_
- **Annualized Rate of Occurrence (ARO):** The expected frequency with which a specific threat or risk will occur within a single year
- **Annualized Loss Expectancy (ALE):** possible yearly cost of all instances of a specific realized threat against a _specific asset_
- **Annual Cost of Safeguard (ACS)**

#### 2.2.2 Calculations
$\text{SLE}=\text{AV} * \text{EF}$
$\text{ALE}=\text{SLE}*\text{ARO}$
$\text{Value of safeguard}=(\text{ALE before Safeguard}-\text{ALE after Safeguard})-\text{ACS}$
