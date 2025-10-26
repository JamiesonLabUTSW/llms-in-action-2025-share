# LLM Platforms: A Quick Cheatsheet

This guide provides a high-level overview of the different LLM platforms you'll encounter. While we will primarily use Google AI Studio in this course, it's important to be aware of the landscape. Each platform has its own "personality," strengths, and weaknesses.

---

### 1. ChatGPT (from OpenAI)

- **Core Idea**: The "Apple" of LLMs—highly consumer-focused, polished, and designed for intuitive chat-first interaction.
- **Key Models (as of late 2025)**:
  - **GPT-4o**: The default, flagship model. Highly capable in text, voice, and vision tasks.
  - **o4-series (o4-mini, o4-mini-high)**: A newer series focused on providing advanced reasoning capabilities to all users.
  - **GPT-4.1**: Specialized for coding and handling extremely long contexts (up to 1 million tokens).
  - **o3-series (o3, o3-pro)**: High-reliability reasoning models for enterprise and critical tasks.
  - **GPT-3.5**: Legacy model available on the free tier for simpler conversational tasks.
- **Standout Features**:
  - **Data Analysis**: Successor to "Code Interpreter." Upload datasets (CSV, Excel) for cleaning, analysis, and visualization.
  - **Custom GPTs**: Create personalized AI assistants tailored for specific roles or tasks (e.g., a SQL debugger, a marketing copywriter).
  - **Memory & Custom Instructions**: Remembers context, user preferences, and instructions across conversations for a personalized experience.
  - **Shared Projects**: Allows for collaboration where chats, files, and instructions can be shared among a group.
  - **Deep Research**: Can perform thorough investigations across multiple sources and compile organized reports with citations.
- **Things to Note**:
  - The platform and model lineup evolve very rapidly.
  - Usage limits apply, even for paid "Pro" tiers.
- **Link**: [chat.openai.com](https://chat.openai.com/)

---

### 2. Claude (from Anthropic)

- **Core Idea**: A strong competitor to OpenAI with a focus on responsible AI, excellent for writing and handling large documents.
- **Key Models (as of late 2025)**:
  - **Claude 4 Series**: The latest generation of models.
    - **Opus 4.1**: The most powerful model, excelling at code generation, multimodal tasks, and complex reasoning.
    - **Sonnet 4.5**: A balanced model with excellent speed, intelligence, and performance on agentic tasks.
    - **Haiku 4.5**: A lightning-fast model ideal for real-time support and quick interactions.
- **Standout Features**:
  - **File Creation & Editing**: Can generate and edit reports, proposals, and other documents directly in the interface.
  - **Artifacts for No-Code Apps**: Can be prompted to build and share simple, no-code applications or workflows.
  - **Claude Skills**: Can load "skills" (folders with instructions and resources) to become an expert on a specialized task, like following brand guidelines or working with Excel.
  - **Automatic Memory & Personalization**: Retains project details, user preferences, and past interactions to provide tailored assistance.
  - **Massive Context Window**: Can process up to 200,000 tokens, making it ideal for analyzing large codebases or lengthy documents.
- **Things to Note**:
  - Built on a "Constitutional AI" philosophy to be helpful, harmless, and honest.
  - Can be expensive; it's easy to burn through paid credits with large projects.
- **Link**: [claude.ai](https://claude.ai/)

---

### 3. Google AI Studio (Primary Course Tool)

- **Core Idea**: A free, powerful, and developer-friendly platform that exposes more of the underlying model controls.
- **Key Models**:
  - **Gemini 1.5 Pro**: The primary model for this course; powerful, with excellent reasoning and a large context window.
  - **Gemini 1.5 Flash**: A faster, lighter version for less complex tasks.
- **Standout Features**:
  - **Parameter Control**: Easily adjust `Temperature`, `Top-P`, `Top-K`, and `Max output tokens` to see how they affect model output.
  - **Grounding**: Can connect to Google Search to ground its responses in real-time web data.
  - **Structured Outputs**: Tools to force the model to generate output in specific formats like JSON.
- **Things to Note**:
  - The interface is organized by "prompts" rather than a single continuous chat, which encourages experimentation.
- **Link**: [aistudio.google.com](https://aistudio.google.com/)

---

### 4. Grok (from xAI)

- **Core Idea**: An LLM with a distinct, often humorous personality, integrated directly with real-time data from X (formerly Twitter).
- **Standout Features**:
  - **Real-Time X Data**: Can provide summaries and insights based on current conversations happening on X.
  - **Unique Personality**: Designed to be more conversational and less filtered than other models.
  - **"Fun Mode" vs. "Regular Mode"**: Can switch between a more witty or a more straightforward personality.
- **Things to Note**:
  - Requires a premium X subscription to access.
- **Link**: [grok.x.ai](https://grok.x.ai/)

---

### 5. Local & Specialized Tools

#### Desktop & Cloud Tools

**LM Studio**
- **Core Idea**: A desktop application that lets you download and run open-source LLMs (like Llama, Mistral, Phi) directly on your own computer.
- **Why Use It?**:
  - **Privacy**: All processing is done locally; no data is sent to the cloud.
  - **Control**: Full control over model parameters and configurations.
  - **Offline Access**: Works without an internet connection.
- **Things to Note**:
  - Requires a powerful computer with sufficient RAM and a good GPU.
- **Link**: [lmstudio.ai](https://lmstudio.ai/)

**Cursor**
- **Core Idea**: An "AI-first" code editor built on top of VS Code, designed for pair programming with an AI.
- **Why Use It?**:
  - **Deep Codebase Integration**: The AI can understand your entire project, not just the open file.
  - **AI-Powered Edits**: Generate, refactor, and debug code with natural language prompts.
- **Link**: [cursor.sh](https://cursor.sh/)

**NotebookLM (from Google)**
- **Core Idea**: A research assistant. You provide the source material (PDFs, text files, Google Docs), and the AI becomes an expert in *your* documents.
- **Why Use It?**:
  - **Grounded Responses**: The AI answers questions based *only* on the sources you provide, reducing hallucinations.
  - **Automatic Summaries & Citations**: Generates summaries and points directly to the source location in your documents.
- **Link**: [notebooklm.google.com](https://notebooklm.google.com/)

---
#### CLI (Command-Line Interface) Tools

**Claude Code**
- **Core Idea**: An "agentic" coding assistant that lives in your terminal. You give it a task, and it can plan and execute the work, including editing files and running commands.
- **Why Use It?**:
    - **Automation**: Offload complex engineering tasks like writing tests, refactoring code, or debugging.
    - **Terminal-Native**: Stays within the developer's natural workflow.
- **Link**: [claude.ai/code](https://claude.ai/code)

**Gemini CLI**
- **Core Idea**: A lightweight command-line interface to access Google's Gemini models directly from your terminal.
- **Why Use It?**:
    - **Scripting & Automation**: Easily integrate Gemini into your shell scripts and development workflows.
    - **Quick Access**: Fast and efficient way to get answers or generate code without a GUI.
- **Link**: [github.com/google/gemini-cli](https://github.com/google/gemini-cli)
