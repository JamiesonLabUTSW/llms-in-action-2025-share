# RAG - Exercises #1

**Task**: Use an LLM to prepare a patient education document on the latest treatment guidelines for hypertension.

## Why RAG helps here?

* **Contextual Relevance**: Retrieves specific documents tailored to the query, ensuring responses are precise and on-topic
* **Current Knowledge**: Retrieves up-to-date information from a knowledge base, ensuring responses are based on the latest research
* **Scalability**: Leverages external databases, allowing the model to handle vast amounts of information without retraining

## Approach 1: Zero-Shot Knowledge 

### Set-up

1. Navigate to [Google AI Studio](https://aistudio.google.com)
2. On the left-hand side, click the "Chat" button.
3. On the right-hand side near the top, make sure "Gemini 2.5 Pro" is selected.
4. Make sure that "Grounding with Google Search" is turned off (It is on by default).
5. Just under the model on the right-hand side, click the **System Prompt** and use the following:

```markdown
## Instructions
You are a medical assistant that helps write thorough patient education documents that are provided to patients and their families after a diagnosis or in advance of a treatment or procedure.

You will be tasked with writing a one-page patient education document in response to the user's query. Make sure to include any data around (1) symptoms, (2) treatment options, (3) complications or side effects, and (4) any other relevant information.

## Guidelines
* Your responses should target an eighth-grade reading level.
* Your responses should be concise and easy to understand.
* Your responses should be factually correct and based on the latest research.
```


### User Query

Now, use the following as the initial query. Submit the request after adding.

```markdown
What are the latest treatment guidelines for hypertension?
```

### Observations

* Does the response achieve the goals for readability and clarity?
* Does the response reflect the latest treatment guidance?
* Figure out the model's knowledge cut-off


### Extensions
#### 1. Compare Model Outputs
In the toolbar, click on **Compare mode** button. Compare the responses from the three different models.

**Suggested Models**:
1. **Gemini 2.5 Flash Latest** A more recent, lightweight model
2. **Gemma 3 1B** A recent, small, open-weights language model

#### 2. Resample with different generation parameters
Resample the response with different generation parameters. Try using `Temperature` between 0 and 1. Try using `Top P` between 0.2 and 1.

## Approach 2: Add Manually Updated Context

1. Navigate to [Google AI Studio](https://aistudio.google.com)
2. On the left-hand side, click the "Chat" button.
3. On the right-hand side near the top, make sure "Gemini 2.5 Pro" is selected.
4. Make sure that "Grounding with Google Search" is turned off (It is on by default).
5. Just under the model on the right-hand side, click the **System Prompt** and use the following:

```markdown
## Instructions
You are a medical assistant that helps write thorough patient education documents that are provided to patients and their families after a diagnosis or in advance of a treatment or procedure.

You will be tasked with writing a one-page patient education document in response to the user's query. Make sure to include any data around (1) symptoms, (2) treatment options, (3) complications or side effects, and (4) any other relevant information.

The user will also provide a helpful context document that is targeted to a professional audience. Use this document to help inform your response.

## Guidelines
 * Your responses should target an eighth-grade reading level.
 * Your responses should be concise and easy to understand.
 * Your responses should be factually correct and based on the latest research.
 * Your responses should be based on the context document provided, but should be leveraged in a way that is easy for a patient and their family to understand.
 * If the user does not provide the context, tell the user "I do not have access to the context document. Please provide the context document before continuing."
```

### User Query

Now, use the following as the initial query. Do not submit yet.

```markdown
 What are the latest treatment guidelines for hypertension?
 ```

Next, navigate to a reputable, up-to-date source of information on hypertension treatment guidelines. One example is the AHA's [A Guideline for the Prevention, Detection, Evaluation and Management of High Blood Pressure in Adults: A Report of the American College of Cardiology/American Heart Association Joint Committee on Clinical Practice Guidelines](https://www.ahajournals.org/doi/pdf/10.1161/CIR.0000000000001356).

Once the page has loaded, download the PDF file to your desktop and when the file download has completed, upload it to the context by clicking the (+) button to the right of the "Run" button.

### Observations

* Does the response achieve the goals for readability and clarity?
* Does the response reflect the latest treatment guidance?
* What impact does the context have on the response?
* What did adding context do to the token count and response time?

### Extensions

#### 1. Other Sources
Find another reputable source of information on hypertension management guidelines and add the context as a file upload or paste it into the request.

#### 2. Bad Sources
Find a blatantly incorrect source of information on hypertension treatment guidelines and add it to the context as a file upload or within the request.

Also, test the responses using the bad source as the *only* context. Compare the responses.

#### 3. Unrelated Context
Navigate to a web page that is not related to hypertension treatment guidelines and paste it in the request as well.

One suggestion: [Which ‘Sex and the City’ character are you, really? Kristin Davis’ guide to figuring it out](https://www.today.com/popculture/tv/which-sex-and-the-city-character-are-you-quiz-rcna199315)

## Approach 3: Add Automatically Updated Context

### Set-up

1. Navigate to [Google AI Studio](https://aistudio.google.com)
2. On the left-hand side, click the "Chat" button.
3. On the right-hand side near the top, make sure "Gemini 2.5 Pro" is selected.
4. Make sure that "Grounding with Google Search" is turned ON for this round.
5. Just under the model on the right-hand side, click the **System Prompt** and use the following:

```markdown
 ## Instructions
You are a medical assistant that helps write thorough patient education documents that are provided to patients and their families after a diagnosis or in advance of a treatment or procedure.

 You will be tasked with writing a one-page patient education document in response to the user's query. Make sure to include any data around (1) symptoms, (2) treatment options, (3) complications or side effects, and (4) any other relevant information.

 You will have the ability to search the web for up-to-date information on the topic. Please use this ability to help inform your response.
 
To improve transparency and trust, please include a list of the sources you used in your response. Number each source at the end of the document and provide the URL. In the body of the document, use the reference numbers from the citation list at the end to refer to the source.

 ## Guidelines
 * Your responses should target an eighth-grade reading level.
 * Your responses should be concise and easy to understand.
 * Your responses should be factually correct and based on the latest research.
 * Your responses should be factually based on reputable sources.
 * Your response should cite the sources you used for each factually based claim.
```

### User Query

```markdown
What are the latest treatment guidelines for hypertension?
```

### Observations

* Does the response achieve the goals for readability and clarity?
* Does the response reflect the latest treatment guidance?
* How many sources did the model use?
* How would you describe the quality of the sources?
* How well-grounded are the claims in the response?

### Extensions

#### 1. Compare Model Outputs
In the top-right corner, click on **Compare**. Compare the responses from the three different models.

**Suggested Models**:
1. **Gemini 2.5 Pro Experimental 03-25** A more recent model
2. **Gemini 2.0 Flash** A smaller, faster, cheaper model
3. **Gemini 1.5 Flash-8B** An even smaller, faster, cheaper model

#### 2. Resample with different generation parameters
Resample the response with different generation parameters. Try using `Temperature` between 0 and 1. Try using `Top P` between 0.2 and 1. Also, you can experiment with the **Dynamic retrieval** option located in the sidebar once **Grounding with Google Search** is enabled by clicking the **Edit** button --  If the threshold value is 0, the response is always grounded with Google Search; if it's 1, it never is.

## Reflection

* What are the key takeaways from this exercise?
* How do each of the approaches compare?
* How might these tools be useful in your own work?

## Further Reading
* Zakka, C. et al. Almanac—Retrieval-Augmented Language Models for
Clinical Medicine. NEJM AI. [https://doi.org/10.1056/AIoa2300068](https://doi.org/10.1056/AIoa2300068) (2024).
* Yang, R., Ning, Y., Keppo, E. et al. Retrieval-augmented generation for generative artificial intelligence in health care. npj Health Syst. 2, 2 (2025). [https://doi.org/10.1038/s44401-024-00004-1](https://doi.org/10.1038/s44401-024-00004-1)
* Lewis, Patrick, et al. "Retrieval-augmented generation for knowledge-intensive nlp tasks." Advances in neural information processing systems 33 (2020): 9459-9474. [https://proceedings.neurips.cc/paper/2020/file/6b493230205f780e1bc26945df7481e5-Paper.pdf](https://proceedings.neurips.cc/paper/2020/file/6b493230205f780e1bc26945df7481e5-Paper.pdf)
* Build a Retrieval Augmented Generation (RAG) App: Part 1 [https://python.langchain.com/docs/tutorials/rag/](https://python.langchain.com/docs/tutorials/rag/)
