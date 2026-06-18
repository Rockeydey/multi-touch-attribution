# Multi-Touch Attribution (MTA) Model

This repository provides resources, dummy datasets, and an overview of popular frameworks for building and evaluating Multi-Touch Attribution models. It is designed for data scientists, marketers, and analysts who want to understand how to distribute conversion credit across multiple marketing touchpoints.

---

## 📊 Where to Get Dummy Data

To build and test an MTA model, you need a dataset that captures user-level interactions across multiple channels. The most accessible and widely used dummy dataset is available on Kaggle.

### Recommended Dataset

- **Dataset Link**: [Multi-Touch Attribution Dataset on Kaggle](https://www.kaggle.com/datasets/vivekparasharr/multi-touch-attribution)
- **Description**: This dataset contains **10,000 rows** of simulated marketing interaction data, including:
  - `User ID` – Unique identifier for each customer
  - `Timestamp` – Date and time of the interaction
  - `Channel` – Marketing channel (e.g., Email, Social, Paid Search)
  - `Campaign` – Campaign name
  - `Conversion` – Binary flag indicating whether the interaction led to a conversion
- **Use Case**: Ideal for learning data preprocessing, feature engineering, and implementing both rule-based and data-driven attribution models.

### Alternative Dataset

For those looking for a larger dataset, a version with **586,000 touchpoints** is also available and frequently referenced in MTA tutorials and notebooks on Kaggle. Search for "Multi-Touch Attribution" on Kaggle to find multiple variations.

---

## ⚙️ Popular MTA Frameworks

Multi-Touch Attribution models can be broadly categorized into **rule-based** (heuristic) and **data-driven** (probabilistic/machine learning) approaches. Below is a breakdown of the most commonly used frameworks.

### 1. Rule-Based Attribution Models

These models apply fixed, predefined rules to distribute credit across touchpoints. They are easy to implement and interpret but do not learn from data patterns.

| Model | Description | Credit Distribution |
|-------|-------------|----------------------|
| **Linear Attribution** | Assigns equal credit to every touchpoint in the customer journey. | Equal share across all interactions. |
| **Time Decay Attribution** | Gives more credit to touchpoints that occur closer to the conversion time. | Weighted by recency (exponential or logarithmic decay). |
| **U-Shaped (Position-Based) Attribution** | Emphasizes the first and last touchpoints. | 40% first touch, 40% last touch, 20% split among middle touches. |

### 2. Data-Driven (Probabilistic) Models

These models use statistical methods and machine learning to infer the true contribution of each channel based on observed conversion patterns.

#### 🔹 Markov Chain Attribution
- **Concept**: Models the customer journey as a sequence of states (channels). It calculates the **removal effect** – the drop in conversion probability if a given channel were removed from all journeys.
- **Advantage**: Captures the transition probabilities between channels and accounts for indirect influences.
- **Output**: Channel importance is measured by the difference in conversion rate with and without that channel.

#### 🔹 Shapley Value Attribution
- **Concept**: Borrowed from cooperative game theory. Evaluates the marginal contribution of each channel by considering all possible subsets (coalitions) of channels.
- **Advantage**: Provides a fair and axiomatic distribution of credit based on each channel's incremental impact.
- **Output**: Each channel receives credit proportional to its average marginal contribution across all coalitions.

#### 🔹 Algorithmic / Deep Learning Attribution
- **Concept**: Uses advanced machine learning models (e.g., Recurrent Neural Networks, Transformers with Attention mechanisms) to predict conversion probability and assign credit dynamically.
- **Example**: The **Deep Learning with Attention (DLAW)** model has shown superior performance on simulated datasets by learning non-linear relationships and temporal dependencies.
- **Advantage**: Captures complex interactions and sequences that simpler models miss.

---

## ⚠️ Important Limitations of MTA

While MTA is a powerful tool for tactical channel optimization, it comes with significant challenges that practitioners must keep in mind.

| Limitation | Description |
|------------|-------------|
| **Tracking Dependency** | MTA relies heavily on user-level tracking (cookies, device IDs, UTM parameters). This is becoming increasingly unreliable due to privacy regulations (GDPR, CCPA), browser restrictions, and the phase-out of third-party cookies. |
| **Offline Channel Blindness** | MTA cannot measure the impact of offline channels (e.g., TV, radio, print) because they lack digital touchpoints. This leads to underreporting their contribution. |
| **Short-Term Bias** | MTA models tend to overvalue bottom-of-the-funnel channels (e.g., branded search, retargeting) while undervaluing top-of-funnel awareness channels (e.g., display ads, social media). |
| **Data Fragmentation** | Cross-device and cross-platform user journeys are difficult to stitch together, leading to incomplete path data. |
| **Model Sensitivity** | The choice of attribution model can dramatically change channel credit distribution, making results model-dependent rather than objective. |

---

## 🧠 Strategic Recommendation

For **holistic budget planning and strategic decision-making**, many industry experts recommend complementing MTA with **Marketing Mix Modeling (MMM)**.

- **MMM** works at an aggregate (time-series) level and does not require user-level tracking, making it privacy-safe.
- It measures the incremental impact of all marketing activities, including offline channels, seasonality, and external factors.
- While MTA is best for **tactical optimization** (e.g., adjusting bids, creative allocation), MMM is better suited for **high-level budget allocation** across channels and geographies.

---

## 📁 Project Structure (Suggested)
