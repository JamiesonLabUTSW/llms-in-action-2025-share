# LLM Platforms: A Quick Cheatsheet

This guide provides a high-level overview of the different LLM platforms you'll encounter. While we will primarily use Google AI Studio in this course, it's important to be aware of the landscape. Each platform has its own "personality," strengths, and weaknesses.

---

### 1. ChatGPT (from OpenAI)

- **Core Idea**: The "Apple" of LLMs—highly consumer-focused, polished, and designed for intuitive chat-first interaction.
- **Key Models (as of late 2025)**:
  - **GPT-5**: The new default model for all users, with more powerful versions like **GPT-5 Thinking** available for paid subscribers.
  - **GPT-4o**: Reintroduced for paid subscribers after initial removal, remains a powerful multimodal option.
  - **GPT-4o mini**: A fast and capable model that has replaced the older GPT-3.5 for most standard interface tasks.
- **Standout Features**:
  - **Data Analysis**: Successor to "Code Interpreter." Upload datasets (CSV, Excel) for cleaning, analysis, and visualization.
  - **Custom GPTs**: Create personalized AI assistants tailored for specific roles or tasks (e.g., a SQL debugger, a marketing copywriter).
  - **Memory & Custom Instructions**: Remembers context, user preferences, and instructions across conversations for a personalized experience.
  - **Shared Projects**: Allows for collaboration where chats, files, and instructions can be shared among a group.
  - **Deep Research**: Can perform thorough investigations across multiple sources and compile organized reports with citations.
- **Things to Note**:
  - **Subscription Tiers (Pro, Team, etc.)**: Paid tiers offer significantly higher usage limits, faster responses, and access to the most powerful models (like GPT-5 Thinking) and advanced features. The free tier has stricter limits and may use less powerful models during peak times.
  - The platform and model lineup evolve very rapidly.
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
  - **Subscription Tiers (Pro)**: The free version has strict message limits that reset every few hours. The Pro tier offers at least 5x more usage, which is essential for heavy use (e.g., analyzing large documents). This is where costs can add up.
  - Built on a "Constitutional AI" philosophy to be helpful, harmless, and honest.
- **Link**: [claude.ai](https://claude.ai/)

---

### 3. Google AI Studio (Primary Course Tool)

- **Core Idea**: A free, powerful, and developer-friendly platform that exposes more of the underlying model controls and is designed for a fast path from prompt to production.
- **Key Models (as of late 2025)**:
  - **Gemini 2.5 Pro**: The primary model for this course; powerful, with excellent reasoning and a large context window.
  - **Gemini 2.5 Flash**: An updated, faster, lighter option optimized for speed and efficiency.
- **Standout Features**:
  - **One-click Cloud Run publishing**: Easily deploy AI applications directly from the studio.
  - **Google Maps Grounding**: Allows the model to integrate live, real-world data from Google Maps into its responses.
  - **Playground Overhaul**: Features a unified UI and a "Compare Mode" for testing models side-by-side.
  - **Parameter Control**: Easily adjust `Temperature`, `Top-P`, `Top-K`, and `Max output tokens` to see how they affect model output.
- **Things to Note**:
  - The interface is organized by "prompts" but has been revamped to better support building and deploying full applications.
- **Link**: [aistudio.google.com](https://aistudio.google.com/)

---

### 4. Grok (from xAI)

- **Core Idea**: An LLM with a distinct, often humorous personality, integrated directly with real-time data from the X platform.
- **Key Models (as of late 2025)**:
  - **Grok 4**: The flagship model, with variants like **Grok 4 Heavy** for complex reasoning and **Grok 4 Fast** for speed.
- **Standout Features**:
  - **Real-Time X Data**: Can provide summaries and insights based on current conversations happening on X.
  - **Text-to-Video Generation**: Can generate short videos (6-15 seconds) with synchronized audio from text prompts.
  - **Customizable AI Companions**: Offers a range of AI personalities that users can interact with.
- **Things to Note**:
  - Requires a premium X subscription to access. Its personality can be more "spicy" or unfiltered than other models.
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
