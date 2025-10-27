# Tool Use with LLMs - Exercises #2

**Task**: Use an LLM to calculate a patient's 10-year risk for cardiovascular disease (ASCVD risk) using clinical data.

## Why Tool Use Helps Here?

* **Accuracy**: Ensures precision and reliability in complex calculations.
* **Consistency**: Applies standardized formulas uniformly.
* **Efficiency**: Quickly performs calculations, saving clinicians time.

---

## Approach 1: Zero-Shot Calculation (No Tools)

### Set-up

1. Navigate to [Google AI Studio](https://aistudio.google.com).
2. On the left-hand side, click the "Chat" button.
3. On the right-hand side near the top, make sure "Gemini 2.5 Pro" is selected.
4. Make sure that **Code Execution** is turned off.
5. Make sure that "Grounding with Google Search" is turned off (It is on by default).
6. Just under the model on the right-hand side, click the **System Prompt** and use the following:

```markdown
## Instructions
You are a medical assistant that helps support physicians perform various medical calculations.

You will be provided with a patient's clinical data and a query that asks for a calculation to be performed.

## Guidelines
* Your responses should be clinically accurate.
* Your responses should include the calculation logic and the result.
* Your responses should be mathematically correct.
* If you do not have all of the necessary information, you should immediately request missing elements from the user.

## Response Format
Any calculations you perform should be presented first but enclosed within <calculation></calculation> tags.

Your final answer will be presented last as only one sentence on a line by itself in the format of:
"The patient's [name of risk score] is [result]."
```

### User Query

```markdown
Calculate the 10-year ASCVD risk for a 55-year-old White male, current smoker, total cholesterol 230 mg/dL, HDL 50 mg/dL, LDL 140 mg/dL, untreated systolic blood pressure 140 mmHg, diastolic blood pressure 90 mmHg, no diabetes, not on hypertension treatment, not on a statin, and not on aspirin therapy.
```

### Calculation: DOUBLE-CHECK IT

Fill in the calculator located here for this patient to double check the model's outputs: [https://tools.acc.org/ASCVD-Risk-Estimator-Plus/#!/calculate/estimate/](https://tools.acc.org/ASCVD-Risk-Estimator-Plus/#!/calculate/estimate/)

### Observations

* Did the model accurately perform the calculation?
* Did the model explain the logic clearly?
* Identify potential inaccuracies or limitations.

---

## Approach 2: API Tool Call (Structured JSON)

### Set-up

1. Navigate to [Google AI Studio](https://aistudio.google.com).
2. On the left-hand side, click the "Chat" button.
3. On the right-hand side near the top, make sure "Gemini 2.5 Pro" is selected.
4. Make sure that **Code Execution** is turned off.
5. Make sure that "Grounding with Google Search" is turned off (It is on by default).
6. Just under the model on the right-hand side, click the **System Prompt** and use the following:

```markdown
## Instructions
You are a medical assistant tasked with calculating patient risk scores.

You have access to a structured JSON API that performs the calculation if provided with the necessary clinical data.

## Tool Call Function Schema in JSON

{
  "current_age": int,
  "sex": "Male" | "Female",
  "race": "White" | "African American" | "Other",
  "systolic_bp": int,
  "diastolic_bp": int,
  "total_cholesterol": int,
  "hdl_cholesterol": int,
  "ldl_cholesterol": int,
  "diabetes": bool,
  "smoker": "Current" | "Former" | "Never",
  "hypertension_treatment": bool,
  "statin": bool,
  "aspirin_therapy": bool
}

## Guidelines
* Your response should prepare the JSON API call with the necessary clinical data according to the schema.
* Assume that your response will be parsed and the API will be called with the provided data.
* Your responses should follow the schema exactly.
* Your responses should be accurate and grounded in the clinical data provided.
* If you do not have all of the necessary information, you should immediately request missing elements from the user.
```

### User Query

Use the same scenario, adding the following:

```markdown
Calculate the 10-year ASCVD risk for a 55-year-old White male, current smoker, total cholesterol 230 mg/dL, HDL 50 mg/dL, LDL 140 mg/dL, untreated  blood pressure 140 / 90, no diabetes, not on hypertension treatment, not on a statin, and not on aspirin therapy.
```

### Calculation: DOUBLE-CHECK IT

Double check the extracted values and fill in the calculator located here for this patient to double check the model's outputs: [https://tools.acc.org/ASCVD-Risk-Estimator-Plus/#!/calculate/estimate/](https://tools.acc.org/ASCVD-Risk-Estimator-Plus/#!/calculate/estimate/) to see if any extraction errors caused shifts in the risk estimate.


### Observations

* What impact did adding the simulated API call have on the model’s accuracy?
* Compare clarity and accuracy with **Approach 1**.
* What are the downsides of this approach?
* What might the benefits be for patient safety?

---

## Approach 3: API Tool Call (Native Function Call)

### Set-up

1. Navigate to [Google AI Studio](https://aistudio.google.com).
2. On the left-hand side, click the "Chat" button.
3. On the right-hand side near the top, make sure "Gemini 2.5 Pro" is selected.
4. Make sure that **Code Execution** is turned off.
5. Make sure that "Grounding with Google Search" is turned off (It is on by default).
6. Toggle on the **Function Calling** option.
7. Next to **Function Calling**, click **Edit**.
8. In the pop-up, enter the following function call schemas:

```json
[
    {
        "name": "ascvd_calculation",
        "description": "Calculates the 10-year ASCVD risk for a patient based on their clinical data.",
        "parameters": {
            "type": "object",
            "properties": {
                "current_age": {
                    "type": "integer",
                    "description": "The patient's current age in years."
                },
                "sex": {
                    "type": "string",
                    "description": "The patient's sex.",
                    "enum": ["Male", "Female"]
                },
                "race": {
                    "type": "string",
                    "description": "The patient's race.",
                    "enum": ["White", "African American", "Other"]
                },
                "systolic_bp": {
                    "type": "integer",
                    "description": "The patient's systolic blood pressure in mmHg."
                },
                "diastolic_bp": {
                    "type": "integer",
                    "description": "The patient's diastolic blood pressure in mmHg."
                },
                "total_cholesterol": {
                    "type": "integer",
                    "description": "The patient's total cholesterol in mg/dL."
                },
                "hdl_cholesterol": {
                    "type": "integer",
                    "description": "The patient's HDL cholesterol in mg/dL."
                },
                "ldl_cholesterol": {
                    "type": "integer",
                    "description": "The patient's LDL cholesterol in mg/dL."
                },
                "diabetes": {
                    "type": "boolean",
                    "description": "True if the patient has diabetes."
                },
                "smoker": {
                    "type": "string",
                    "description": "The patient's smoking status.",
                    "enum": ["Current", "Former", "Never"]
                },
                "hypertension_treatment": {
                    "type": "boolean",
                    "description": "True if the patient is on hypertension treatment."
                },
                "statin": {
                    "type": "boolean",
                    "description": "True if the patient is on a statin."
                },
                "aspirin_therapy": {
                    "type": "boolean",
                    "description": "True if the patient is on aspirin therapy."
                }
            },
            "required": [
                "current_age",
                "sex",
                "race",
                "systolic_bp",
                "diastolic_bp",
                "total_cholesterol",
                "hdl_cholesterol",
                "ldl_cholesterol",
                "diabetes",
                "smoker",
                "hypertension_treatment",
                "statin",
                "aspirin_therapy"
            ]
        }
    },
    {
        "name" : "gfr_calculator",
        "description": "Calculates the GFR for a patient based on their clinical data.",
        "parameters": {
            "type": "object",
            "properties": {
                "age": {
                    "type": "integer",
                    "description": "The patient's age in years."
                },
                "sex": {
                    "type": "string",
                    "description": "The patient's sex.",
                    "enum": ["Male", "Female"]
                },
                "creatinine": {
                    "type": "integer",
                    "description": "The patient's serum creatinine in mg/dL."
                }
            },
            "required": [
                "age",
                "sex",
                "creatinine"
            ]
        }
    }
]
```

7. Use the following **System Prompt**:

```markdown
## Instructions
You are a medical assistant tasked with calculating patient risk scores.

You have access to a set of calculators that perform the risk calculations if provided with the necessary clinical data.

## Guidelines
* Your responses should be factually correct and rely on the appropriate calculator.
* Your response should include the calculator used and the result.
* Ensure that the response is clear and easy to understand.
* Do not add text between the calculator output and the final result sentence.
* If you do not have all of the necessary information, you should immediately request missing elements from the user.

## Response Format
You will respond only with one sentence as follows:
"The patient's [name of risk score] is [result]."
```

### User Query

Use the same scenario, adding the following:

```markdown
Calculate the 10-year ASCVD risk for a 55-year-old White male, current smoker, total cholesterol 230 mg/dL, HDL 50 mg/dL, LDL 140 mg/dL, untreated systolic blood pressure 140 mmHg, diastolic blood pressure 90 mmHg, no diabetes, not on hypertension treatment, not on a statin, and not on aspirin therapy.
```

### Calculation

When prompted by the UI, enter the value "14.1" to simulate the response of the called function.

### Observations

* Compare clarity and accuracy with **Approach 1**
* Why would we choose **Approach 2** over **Approach 3**?
* Why would we choose **Approach 3** over **Approach 2**?

### Explorations

After you’ve completed the Observations for Approach 3, try feeding the model plain‑text patient narratives that are malformed or missing key details. Observe how the function‑calling layer reacts.

1. Missing smoking status

   ```
   Calculate the 10‑year ASCVD risk for a 55‑year‑old White male, total cholesterol 230 mg/dL, HDL 50 mg/dL, LDL 140 mg/dL, untreated systolic BP 140 mmHg, diastolic BP 90 mmHg, no diabetes, no hypertension treatment, not on a statin, and not on aspirin therapy.
   ```

   *What error or prompt does the model return when “smoker” is never mentioned?*

2. Ambiguous smoking description  
   
   ```
   Calculate the 10‑year ASCVD risk for a 55‑year‑old White male, current smoker (about 1 cigarette a day), total cholesterol 230 mg/dL, HDL 50 mg/dL, LDL 140 mg/dL, untreated systolic BP 140 mmHg, diastolic BP 90 mmHg, no diabetes, no hypertension treatment, not on a statin, and not on aspirin therapy.
   ```

   *Does the model map “about 1 cigarette a day” to a valid enum, or does it error?*

3. Out‑of‑range or missing age
   **Negative age**
   ```
   Calculate the 10‑year ASCVD risk for a −5‑year‑old White male, current smoker (about 1 cigarette a day), total cholesterol 230 mg/dL, HDL 50 mg/dL, LDL 140 mg/dL, untreated systolic BP 140 mmHg, diastolic BP 90 mmHg, no diabetes, no hypertension treatment, not on a statin, and not on aspirin therapy.
   ```

   **Missing age**
   ```
   Calculate the 10‑year ASCVD risk for a middle‑aged White male (age unknown), current smoker (about 1 cigarette a day), total cholesterol 230 mg/dL, HDL 50 mg/dL, LDL 140 mg/dL, untreated systolic BP 140 mmHg, diastolic BP 90 mmHg, no diabetes, no hypertension treatment, not on a statin, and not on aspirin therapy.
   ```

   *How does the function‑calling layer handle a negative age or the absence of any age?*

Reflect on which errors are caught, the clarity of the model’s error messages, and what this implies about building robust, user‑friendly clinical APIs.

---

## Approach 4: Enhanced Accuracy with Code Execution

### Set-up

1. Navigate to [Google AI Studio](https://aistudio.google.com).
2. On the left-hand side, click the "Chat" button.
3. On the right-hand side near the top, make sure "Gemini 2.5 Pro" is selected.
4. Make sure that "Grounding with Google Search" is turned off (It is on by default).
5. Toggle on the **Code Execution** option.
6. Just under the model on the right-hand side, click the **System Prompt** and use the following:

```markdown
## Instructions
You are a medical assistant helping clinicians calculate clinical risk scores accurately using executable Python code.

When given patient data and a description of a calculation, you must:
1. Translate the clinical decision-tree or calculation description into Python code.
2. Execute the Python code to obtain a precise numeric result.
3. Clearly display both the Python code and the result of the calculation.

## Guidelines
* Responses must include commented Python code demonstrating exactly how the calculation was performed.
* After execution, state clearly the calculated result.
* Your responses should be factually correct and based on the calculations.
* If you do not have all of the necessary information, you should immediately request missing elements from the user.

## Response Format

Your final answer will be presented last as only one sentence on a line by itself in the format of:
"The patient's [name of risk score] is [result]."

## Supporting Tables

<support>
# Table A. Equation Parameters of the Pooled Cohort Equations for Estimation of 10-Year Risk of Hard ASCVD\*  
## …and Specific Examples for Each Race and Sex Group

---

## **Women**  
**(Example: 55 years of age with total cholesterol 213 mg/dL, HDL-C 50 mg/dL, untreated systolic BP 120 mm Hg, nonsmoker, and without diabetes)**

| Variable                                       | White: Coefficient | White: Value | White: Coefficient × Value | African American: Coefficient | African American: Value | African American: Coefficient × Value |
|:-----------------------------------------------|:------------------:|:------------:|:--------------------------:|:----------------------------:|:-----------------------:|:--------------------------------------:|
| **Ln Age (y)**                                 | -29.799           | 4.01         | -119.41                   | 17.114                       | 4.01                    | 68.58                                |
| **Ln Age, Squared**                            | 4.884             | 16.06        | 78.44                     | N/A                          | N/A                     | N/A                                  |
| **Ln Total Cholesterol (mg/dL)**               | 13.540            | 5.36         | 72.59                     | 0.940                        | 5.36                    | 5.04                                 |
| **Ln Age × Ln Total Cholesterol**              | -3.114            | 21.48        | -66.91                    | N/A                          | N/A                     | N/A                                  |
| **Ln HDL-C (mg/dL)**                           | -13.578           | 3.91         | -53.12                    | -18.920                      | 3.91                    | -74.01                               |
| **Ln Age × Ln HDL-C**                          | 3.149             | 15.68        | 49.37                     | 4.475                        | 15.68                   | 70.15                                |
| **Ln Treated Systolic BP (mm Hg)**             | 2.019             | —            | —                         | 29.291                       | —                       | —                                    |
| **Ln Age × Ln Treated Systolic BP**            | N/A               | N/A          | N/A                       | -6.432                       | —                       | —                                    |
| **Ln Untreated Systolic BP (mm Hg)**           | 1.957             | 4.79         | 9.37                      | 27.820                       | 4.79                    | 133.19                               |
| **Ln Age × Ln Untreated Systolic BP**          | N/A               | N/A          | N/A                       | -6.087                       | 19.19                   | -116.79                              |
| **Current Smoker (1=Yes, 0=No)**               | 7.574             | 0            | 0                         | 0.691                        | 0                       | 0                                    |
| **Ln Age × Current Smoker**                    | -1.665            | 0            | 0                         | N/A                          | N/A                     | N/A                                  |
| **Diabetes (1=Yes, 0=No)**                     | 0.661             | 0            | 0                         | 0.874                        | 0                       | 0                                    |
| **Individual Sum**                             | —                 | —            | **-29.67**                | —                            | —                       | **86.16**                            |
| **Mean (Coefficient × Value)**                 | N/A               | N/A          | **-29.18**                | N/A                          | N/A                     | **86.61**                            |
| **Baseline Survival**                          | N/A               | N/A          | **0.9665**                | N/A                          | N/A                     | **0.9533**                           |
| **Estimated 10-y Risk of Hard ASCVD**          | N/A               | N/A          | **2.1%**                  | N/A                          | N/A                     | **3.0%**                             |

---

## **Men**  
**(Example: 55 years of age with total cholesterol 213 mg/dL, HDL-C 50 mg/dL, untreated systolic BP 120 mm Hg, nonsmoker, and without diabetes)**

| Variable                                       | White: Coefficient | White: Value | White: Coefficient × Value | African American: Coefficient | African American: Value | African American: Coefficient × Value |
|:-----------------------------------------------|:------------------:|:------------:|:--------------------------:|:----------------------------:|:-----------------------:|:--------------------------------------:|
| **Ln Age (y)**                                 | 12.344            | 4.01         | 49.47                     | 2.469                        | 4.01                    | 9.89                                 |
| **Ln Total Cholesterol (mg/dL)**               | 11.853            | 5.36         | 63.55                     | 0.302                        | 5.36                    | 1.62                                 |
| **Ln Age × Ln Total Cholesterol**              | -2.664            | 21.48        | -57.24                    | N/A                          | N/A                     | N/A                                  |
| **Ln HDL-C (mg/dL)**                           | -7.990            | 3.91         | -31.26                    | -0.307                       | 3.91                    | -1.20                                |
| **Ln Age × Ln HDL-C**                          | 1.769             | 15.68        | 27.73                     | N/A                          | N/A                     | N/A                                  |
| **Ln Treated Systolic BP (mm Hg)**             | 1.797             | —            | —                         | 1.916                        | —                       | —                                    |
| **Ln Untreated Systolic BP (mm Hg)**           | 1.764             | 4.79         | 8.45                      | 1.809                        | 4.79                    | 8.66                                 |
| **Current Smoker (1=Yes, 0=No)**               | 7.837             | 0            | 0                         | 0.549                        | 0                       | 0                                    |
| **Ln Age × Current Smoker**                    | -1.795            | 0            | 0                         | N/A                          | N/A                     | N/A                                  |
| **Diabetes (1=Yes, 0=No)**                     | 0.658             | 0            | 0                         | 0.645                        | 0                       | 0                                    |
| **Individual Sum**                             | —                 | —            | **60.69**                 | —                            | —                       | **18.97**                            |
| **Mean (Coefficient × Value)**                 | N/A               | N/A          | **61.18**                 | N/A                          | N/A                     | **19.54**                            |
| **Baseline Survival**                          | N/A               | N/A          | **0.9144**                | N/A                          | N/A                     | **0.8954**                           |
| **Estimated 10-y Risk of Hard ASCVD**          | N/A               | N/A          | **5.3%**                  | N/A                          | N/A                     | **6.1%**                             |

---

\*Defined as first occurrence of nonfatal myocardial infarction or CHD death, or fatal or nonfatal stroke.

\†Coefficient × Value: For age, lipids, and BP, defined as the natural log of the value multiplied by the parameter estimate. When an age interaction is present with  
lipids or BP, the natural log of age is multiplied by the natural log of the lipid or BP, and the result is multiplied by the parameter estimate.  
N/A indicates that the specific covariate was not included in the model for that sex–race group; — indicates that this value was not included in the example (e.g.,  
this example used untreated systolic BP, not treated systolic BP).

**Abbreviations**:  
- ASCVD = atherosclerotic cardiovascular disease  
- BP = blood pressure  
- CHD = coronary heart disease  
- HDL-C = high-density lipoprotein cholesterol  
- Ln = natural logarithm  
- N/A = not included  

---

# Table B. Estimating an Individual’s 10-Year Risk of Incident Hard ASCVD

The hypothetical profile provided in **Table A** (the “Individual Example Value” column) is identical for each race and sex group and is based on the overall sample mean. The profile assumes an individual **55 years of age** (for which the Ln(Age) = 4.01), with a total cholesterol of **213 mg/dL**, HDL-C of **50 mg/dL**, and an **untreated systolic BP of 120 mm Hg**. This individual is **not** a current smoker and does **not** have diabetes. For the equations, the values for age, lipids, and systolic BP are Ln transformed. Interactions between age and lipids or age and systolic BP use the natural log of each variable (e.g., Ln(Age) × Ln(Total Cholesterol)).

Calculation of the 10-year risk estimate for hard ASCVD can be described in a series of steps:

1. **Compute the natural log** of age, total cholesterol, HDL-C, and systolic BP (treated or untreated).  
2. **Compute any appropriate interaction terms** (e.g., Ln(Age) × Ln(Total Cholesterol)).  
3. **Multiply** each log-transformed variable (and interaction term) by the **coefficients** from the equation (“Coefficient” column in Table A) for the specific race-sex group.  
4. **Sum** these products to get the “Individual Sum” (shown as “Coefficient × Value” summed for the profile in Table A).  

The estimated 10-year risk of a first hard ASCVD event is formally calculated as:

\[
1 - \Bigl(S_{10}\Bigr)^{\bigl(\ln(dX'B) - \text{Mean}(X'B)\bigr)}
\]

Where \(S_{10}\) is the baseline survival rate at 10 years (the “Baseline Survival” in Table A), and \(\ln(dX'B)\) is the individual’s summed product of coefficients and values. The “Mean (Coefficient × Value)” is a race- and sex-specific overall mean of these sums.

Using **White men** as an example:

\[
1 - 0.9144^{(60.69 - 61.18)} \approx 5.3\%
\]

which equates to a **5.3%** probability of a first hard ASCVD event within 10 years.

---

**Abbreviations**:  
- ASCVD = atherosclerotic cardiovascular disease  
- BP = blood pressure  
- HDL-C = high-density lipoprotein cholesterol  
- Ln = natural logarithm  
</support>
```

### User Query

Use the same patient scenario, including:

```markdown
Calculate the 10-year ASCVD risk for a 55-year-old White male, current smoker, total cholesterol 230 mg/dL, HDL 50 mg/dL, LDL 140 mg/dL, untreated systolic blood pressure 140 mmHg, diastolic blood pressure 90 mmHg, no diabetes, not on hypertension treatment, not on a statin, and not on aspirin therapy.
```

### Observations

* Did the model accurately generate and execute Python code?
* Assess reproducibility and precision compared to previous approaches.
* How does tool-enabled code execution enhance clinical reliability?

---

## Reflection

* Summarize key advantages of integrating code execution into clinical workflows.
* Compare the reliability and clarity across all three approaches.
* Identify other clinical calculations or decision tools that might benefit from LLM-enabled code execution.

## Further Reading

* [Google AI Studio Documentation on Code Execution](https://ai.google.dev/gemini-api/docs/code-execution?lang=python)
* [Google AI Studio Documentation on Function Calling](https://ai.google.dev/gemini-api/docs/function-calling)
* [2013 ACC/AHA Guideline on the Assessment of Cardiovascular Risk A Report of the American College of Cardiology/American Heart Association Task Force on Practice Guidelines](https://www.ahajournals.org/doi/pdf/10.1161/01.cir.0000437741.48606.98)
* [Large language model agents can use tools to perform clinical calculations](https://www.nature.com/articles/s41746-025-01475-8)
