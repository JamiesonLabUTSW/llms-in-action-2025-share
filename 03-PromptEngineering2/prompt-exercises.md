# Prompt Engineering Exercises

These exercises are designed to help you practice the prompting techniques discussed in the demo notebook (`prompt-demos.md`).

## Exercise 1: Extracting Structured Data from a Clinical Note

**Goal:** Practice creating prompts to extract specific information from semi-structured text and format it consistently.

**Background:** Clinical notes often contain valuable information, but the format can vary. They might use abbreviations, mix different types of information within sections, and lack perfect structure. Your task is to extract key data points from the provided clinical note (`note.txt`) into a structured JSON format.

**Instructions:**

1.  Review the contents of the `note.txt` file. Notice its structure, use of abbreviations, and how information is presented.
2.  Write a prompt that instructs an LLM to act as a clinical data extraction tool.
3.  Your prompt should ask the LLM to read the provided note text and extract the following information in tabular format:
    *   `patient_name`
    *   `mrn`
    *   `dob`
    *   `chief_complaint` (a brief summary of the main reason for the visit)
    *   `past_medical_history` (as a list of conditions)
    *   `medications` (as a list of medication names/dosages)
    *   `allergies` (as a list)
    *   `smoking_status` (e.g., "Current smoker", "Former smoker", "Non-smoker", including pack-years if available)
    *   `vitals` (an object containing BP, HR, RR, Temp, SpO2)
    *   `assessment_summary` (a brief summary of the clinician's assessment)
    *   `planned_labs` (as a list)
    *   `planned_imaging` (as a list)
4.  Consider using techniques like role prompting, clearly defining the desired output format and potentially providing instructions on how to handle dates, abbreviations or missing information.

---

## Exercise 2: AI-Powered Goal Planning

**Goal:** Practice using an LLM as a collaborative partner to brainstorm and structure a plan for achieving a personal health or wellness goal.

**Background:** Sometimes, the hardest part of achieving a goal is creating a realistic and actionable plan. LLMs can be excellent tools for brainstorming steps, identifying potential hurdles, and suggesting ways to stay motivated.

**Instructions:**

1.  Choose a personal health or wellness goal you have. Examples: 
    *  Run a 5k race in 3 months.
    *  Target a specific weight loss goal.
    *  Improve sleep quality (e.g., average 7-8 hours/night).
2.  Write a prompt that clearly states your goal and asks the LLM to help you create a feasible plan.


**Example Prompt:**

```markdown
Role: You are an encouraging and knowledgeable health coach.

My Goal: I want to consistently get better sleep. My goal is to average 7.5 hours of sleep per night within the next 8 weeks. Currently, I average about 6 hours and often feel tired.

Task: Help me create a detailed, actionable 8-week plan to achieve my sleep goal. Please include:

1.  **Weekly Focus:** Break down the 8 weeks, suggesting a specific focus for each week (e.g., Week 1: Establish a consistent bedtime, Week 2: Optimize sleep environment, etc.).
2.  **Actionable Steps:** For each week's focus, list 2-3 concrete actions I can take.
3.  **Potential Obstacles:** Identify common challenges people face when trying to improve sleep (e.g., difficulty winding down, inconsistent schedule on weekends, stress).
4.  **Overcoming Obstacles:** Provide practical tips or strategies to deal with the identified obstacles.
5.  **Progress Tracking:** Suggest simple ways I can track my sleep duration and quality (e.g., journal, app) and how to use this information to adjust the plan.
6.  **Motivation Tips:** Include a few ideas to help me stay motivated throughout the 8 weeks.

Please present the plan in a clear, organized format.
```

*(Run this prompt or your own modified version with your specific goal!)*