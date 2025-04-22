# LLM's in Action: Introduction to Prompt-engineering (Demo)

This file contains a series of demos to practice and understand various prompt engineering techniques, such as role prompting, task specification, context specification, output constraints, zero-shot prompting, few-shot prompting etc.

## Demo 1

### Scenario

A patient has just been diagnosed with Type 2 Diabetes. Explain the condition to them.

**Practice the following prompting techniques**:

- Role prompting
- Task specification
- Context specification
- Output constraints
- Using delimiters for different sections

### Iter 0: Initial prompt

```markdown
Explain Type 2 diabetes in plain language.
```

### Iter 1: Improved prompt using role and context specification.

```markdown
## Role 
You are an experienced healthcare educator. Your primary goal is to inform and empower, not to overwhelm or scare.

### Task
Generate a clear explanation of Type 2 diabetes in plain language.

## Context 
You are speaking directly to a patient who has just been diagnosed with Type 2 Diabetes. They most likely have limited prior knowledge about the condition
```

### Iter 2. Specifying the output format to get a better response

```markdown
## Role
You are an experienced healthcare educator. Your primary goal is to inform and empower, not to overwhelm or scare.

## Task
Generate a clear explanation of Type 2 Diabetes in plain language.

## Context
You are speaking directly to a patient who has just been diagnosed with Type 2 Diabetes. They most likely have limited prior knowledge about the condition.

## Instructions
- Use a few lines of text or a short paragraph for easy readability.
- Avoid complex medical jargon. If a technical term is necessary, explain it simply.
- Maintain an empathetic and encouraging tone.
```

## Demo 2

### Scenario 2

You are an assistant at a clinic. One of your responsibilities is to classify incoming patient messages into predefined categories to help route them correctly. You would like to use AI to help you with this.

**Task:** Classify patient messages based on their primary intent.

**Intent Categories:**

- `Appointment Request`
- `Medication Query`
- `Urgent Concern`
- `Test Result Inquiry`
- `General Inquiry`

**Practice the following prompting techniques:**

- Priming the output
- Zero-shot prompting
- Few-shot prompting (Demonstrating improved accuracy, handling ambiguity, enforcing output format)
- Role Prompting
- Task Specification

### Iter 0: Initial prompt (Zero-shot)

```markdown
You are a helpful clinical assistant AI. 

Classify the following patient message into one of these categories:  
- Appointment Request
- Medication Query
- Urgent Concern
- Test Result Inquiry
- General Inquiry

Patient Message: "Hi, I'd like to make an appointment to see Dr. Smith next week, and also wanted to know if my blood test results from last Friday are available yet?"
```

### Iter 1: Priming the output (Zero-shot)

```markdown
## Role
You are a helpful clinical assistant AI. 

## Task
Classify the following patient message into one of these categories:  
- Appointment Request
- Medication Query
- Urgent Concern
- Test Result Inquiry
- General Inquiry

## Patient Message
"Hi, I'd like to make an appointment to see Dr. Smith next week, and also wanted to know if my blood test results from last Friday are available yet?"

Intent:
```

### Attempt 2: Few-Shot Prompt

This prompt uses examples to guide the model on handling ambiguity and desired output format.

```markdown
## Role
You are a helpful clinical assistant AI. 

## Task
Classify the following patient message into one of these categories:  
- Appointment Request
- Medication Query
- Urgent Concern
- Test Result Inquiry
- General Inquiry

## Examples

Patient Message: "Can I get a refill for my Lipitor prescription?"
Intent: Medication Query

Patient Message: "I woke up with severe back pain and can barely move."
Intent: Urgent Concern

Patient Message: "I need to reschedule my appointment for next Tuesday. Also, are my recent blood test results in?"
Intent: Appointment Request

Patient Message: "Feeling a bit more breathless today than usual, not sure if I should be worried."
Intent: Urgent Concern

Now, classify the following message:

## Patient Message
"Hi, I'd like to make an appointment to see Dr. Smith next week, and also wanted to know if my blood test results from last Friday are available yet?"

Intent:
```

## Demo 3

### Scenario 3: Generating Differential Diagnoses

You are a clinician and want to use an AI assistant to help brainstorm potential diagnoses for a complex patient presentation.

**Patient Case:**

45-year-old female presenting with:
*   Progressive fatigue for 2 months
*   10-pound unintentional weight loss
*   Night sweats occurring 3-4 times weekly
*   History of hypothyroidism (TSH now normal)
*   No fever or productive cough
*   No relevant travel history or known exposures

**Task:** Generate the 5 most likely differential diagnoses for this patient, along with the rationale for each.

**Practice the following prompting techniques:**

-   Role Prompting
-   Task Specification
-   Direct Prompting vs. Chain-of-Thought Prompting
-   Structured Output Formatting

### Iteration 0: Direct Prompt

This prompt asks directly for the output without requesting the reasoning process.

```markdown
## Role
You are a clinical assistant AI helping a physician generate differential diagnoses.

## Patient Information
45-year-old female presenting with:
* Progressive fatigue for 2 months
* 10-pound unintentional weight loss
* Night sweats occurring 3-4 times weekly
* History of hypothyroidism (TSH now normal)
* No fever or productive cough
* No relevant travel history or known exposures

## Task
Give me the five most likely diagnoses for this patient.
```

*(Potential LLM Output: Might list 5 plausible diagnoses (e.g., Lymphoma, Tuberculosis, Occult Malignancy, Hyperthyroidism [despite normal TSH], Chronic Infection), but without any explanation, making it difficult to assess the AI's reasoning or trust the suggestions.)*

### Iteration 1: Basic Chain-of-Thought (CoT)

This prompt asks the AI to think step-by-step and include its thought process before the final answer, using XML tags to delineate the thinking.

```markdown
## Role
You are a clinical assistant AI helping a physician generate differential diagnoses.

## Patient Information
45-year-old female presenting with:
* Progressive fatigue for 2 months
* 10-pound unintentional weight loss
* Night sweats occurring 3-4 times weekly
* History of hypothyroidism (TSH now normal)
* No fever or productive cough
* No relevant travel history or known exposures

## Task
Give me the 5 most likely diagnoses for this patient.

## Instructions
Think through this case step by step to generate the 5 most likely diagnoses. First, identify the key clinical patterns. Second, consider relevant systems. Third, evaluate potential diagnoses against the symptoms. Fourth, note diagnoses explaining multiple symptoms.

## Output
- Output your thinking process within `<think>` tags. 
- After the thinking process, provide your final answer as a numbered list of the top 5 diagnoses, each with a brief rationale.
```

*(Expected LLM Output: Will include a reasoning section within `<think>` tags, followed by the structured list of diagnoses and rationales. Example thinking might involve identifying B symptoms (weight loss, night sweats), considering malignancy, infection, endocrine causes, etc.)*


**Advantages shown by Chain-of-Thought:**

-   **Transparency & Trust:** Reasoning is visible, allowing clinicians to assess the AI's logic.
-   **Improved Reasoning:** Explicit steps guide the AI towards a more thorough analysis.
-   **Structured Output (Iter 2):** Clear instructions ensure the final output is consistently formatted and easy to use.
-   **Debugging:** Errors in logic are easier to spot within the reasoning steps.
