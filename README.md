# 🧠 Fair AI Hiring Analysis with Stack Overflow Developer Data

> **Analyzing and mitigating gender bias in job hiring predictions using real-world developer data.**

## 📊 About the Dataset

This project uses a cleaned and preprocessed version of the Stack Overflow Developer Survey dataset, containing over **70,000** responses from global developers.

📁 [Dataset on Kaggle](https://www.kaggle.com/datasets/nikailani/70k-job-applicants-data-processed)

The data includes:
- Demographics (Age, Gender, Country)
- Education level
- Professional experience
- Salary and computer skills
- Technologies/tools used (`HaveWorkedWith`)

---

## 🧹 Preprocessing Summary

- Removed unnecessary columns (e.g., `Unnamed: 0`) and duplicates
- Replaced missing values in `HaveWorkedWith` with `'None'`
- One-hot encoded categorical variables: `Age`, `Gender`, `Country`, `EdLevel`, `Accessibility`, `MentalHealth`, `MainBranch`
- Transformed `HaveWorkedWith` into multiple binary features (e.g., Python, SQL, JavaScript)
- Standardized numerical columns: `YearsCode`, `YearsCodePro`, `PreviousSalary`, `ComputerSkills`

---

## 📈 Dataset Overview

- 👥 **Respondents**: ~73,000
- 💼 **Employed**: ~64,800 (majority)
- 💻 **Avg. Computer Skills**: 13.43 (range: 0–107)
- 💵 **Avg. Previous Salary**: ~$67,751 (std: $49,488)
- ⌛ **Avg. Coding Experience**: 14 years (up to 50)
- 🌍 **Geography**: Global

---

## ⚖️ Bias Exploration

- **Gender imbalance**: 95% Men vs 5% Women
- **Age distribution**:
  - 65% of men < 35 years
  - 73% of women < 35 years
- **Salary gap**: Men earn significantly more across all brackets
- **Employment rate**:
  - Men: 54% employed
  - Women: 45% employed

---

## 🤖 Model Training

- Binary classification model to predict `Employed (1) vs Unemployed (0)`
- Initial accuracy: **71%**
- High false negative rate, especially for women — indicates gender bias

---

## 🛠 Bias Mitigation with IBM AIF360

Applied **Disparate Impact Remover** from IBM's [AIF360](https://aif360.mybluemix.net/) library:

- Protected attribute: `Gender` (`1 = Man`, `0 = Woman`)
- Favorable label: `Employed = 1`
- Repair level: `1.0` (maximum correction)

### 📊 Results After Debiasing

| Metric                        | Before      | After       |
|------------------------------|-------------|-------------|
| **Model Accuracy**           | 71%         | **77%**     |
| **Female Hiring Rate**       | 66.3%       | **81.6%**   |
| **Male Hiring Rate**         | 66.6%       | **53.8%**   |
| **False Negatives**          | 2,985       | **1,754**   |

✅ **Impact**: Post-correction, women were 28% more likely to be recommended by the model than before — indicating successful bias reduction.

---

## 📁 Project Structure

├── bias_fairness_analysis.ipynb # Main notebook: preprocessing, modeling, bias analysis
├── README.md


---

## 🧰 Tools & Libraries

- Python (Pandas, NumPy)
- Matplotlib & Seaborn
- Scikit-learn
- IBM AIF360 (Fairness toolkit)

---

## 📬 Contact

**Taha Bouhafa**  
Big Data & AI Engineering Student at ENSA Tétouan  
📧 [tahabouhafa1@gmail.com](mailto:tahabouhafa1@gmail.com)  

