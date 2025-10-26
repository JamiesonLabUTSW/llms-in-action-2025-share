# LLM Platforms: A Quick Cheatsheet

This guide provides a high-level overview of the different LLM platforms you'll encounter. While we will primarily use Google AI Studio in this course, it's important to be aware of the landscape. Each platform has its own "personality," strengths, and weaknesses.

---

## Quick Comparison Table

| Platform | Best For | Free Tier | Paid Tier | Healthcare/PHI Safe? | Key Limitation |
|----------|----------|-----------|-----------|---------------------|----------------|
| **ChatGPT** | General use, data analysis | GPT-5 (limited msgs) | $20-30/mo+ | ❌ No (unless Enterprise) | Message caps even on paid |
| **Claude** | Long documents, writing | Very limited (time-based) | $20/mo+ | ❌ No (unless Enterprise) | Strict message limits |
| **Google AI Studio** | Development, learning | Very generous free tier | Pay-as-you-go API | ❌ No (use Vertex AI) | More technical interface |
| **Microsoft Copilot** | Microsoft 365 integration | Basic chat access | $20-30/mo | ⚠️ Yes (M365 Enterprise) | Requires Microsoft ecosystem |
| **Grok** | Real-time X data | None | $8/mo+ (X Premium) | ❌ No | Requires X subscription |
| **LM Studio** | Privacy, local control | Completely free | N/A (local) | ✅ Yes (all local) | Requires powerful hardware |
| **NotebookLM** | Document analysis, research | Free (with limits) | N/A | ❌ No (Google service) | Limited to provided sources |

**⚠️ Healthcare Data Warning**: Never input patient data, PHI, or sensitive medical information into consumer LLM platforms. Only use enterprise versions with signed BAAs or local solutions for protected health information.

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
- **Cost Structure**:
  - **Free**: Access to the base GPT-5 model with strict message limits that refresh every few hours.
  - **Plus**: $20/month - Higher message limits for GPT-5, access to GPT-4o, and priority access.
  - **Team/Pro**: $30/month+ per user - Highest limits, access to specialized models like GPT-5 Thinking, admin controls.
  - **Enterprise**: Custom pricing - HIPAA compliance available, unlimited usage, advanced security.
- **Things to Note**:
  - **Healthcare Warning**: Only the Enterprise tier with a signed BAA is appropriate for patient data.
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
- **Cost Structure**:
  - **Free**: Very limited - approximately 10-20 messages every 8 hours (varies by demand)
  - **Pro**: $20/month - 5x more messages (hundreds per day), priority access during high-traffic times
  - **Team**: $25/month per user (minimum 5 users) - Central billing, higher limits
  - **Enterprise**: Custom pricing - SSO, HIPAA compliance options, advanced security features
- **Things to Note**:
  - **Healthcare Warning**: Consumer tiers not suitable for PHI. Enterprise plans with BAA required for patient data.
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
- **Cost Structure**:
  - **Free Tier**: Very generous - 15 requests per minute (RPM), 1 million tokens per day, 1500 requests per day
  - **Pay-as-you-go API**: After free tier limits:
    - Gemini 2.5 Flash: ~$0.075 per 1M input tokens, ~$0.30 per 1M output tokens
    - Gemini 2.5 Pro: ~$1.25 per 1M input tokens, ~$5.00 per 1M output tokens
  - **Vertex AI (Enterprise)**: Custom pricing with enterprise features, SLAs, and compliance options
- **Things to Note**:
  - **Healthcare Warning**: Free tier not appropriate for PHI. Consider Google Cloud Healthcare API for HIPAA compliance.
  - The interface is organized by "prompts" but has been revamped to better support building and deploying full applications.
  - Free tier is extremely generous compared to other platforms - ideal for learning and experimentation.
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
- **Cost Structure**:
  - **No Free Tier**: Requires X Premium subscription
  - **X Premium**: $8/month (web) or $10/month (mobile) - Basic Grok access
  - **X Premium+**: $16/month (web) or $20/month (mobile) - Priority access, higher limits
- **Things to Note**:
  - **Healthcare Warning**: Not suitable for any patient data or medical use cases.
  - Requires a premium X subscription to access. Its personality can be more "spicy" or unfiltered than other models.
  - Best for real-time information and social media analysis rather than professional work.
- **Link**: [grok.x.ai](https://grok.x.ai/)

---

### 5. Microsoft Copilot (from Microsoft)

- **Core Idea**: Microsoft's AI assistant deeply integrated with the Microsoft 365 ecosystem, offering both consumer and enterprise versions.
- **Key Versions (as of late 2025)**:
  - **Copilot (Free)**: Basic chat interface with web access, powered by GPT models.
  - **Copilot Pro**: Advanced features for individual users with priority access and integration with Microsoft 365 apps.
  - **Copilot for Microsoft 365**: Enterprise version with deep Office integration, meeting transcription, and organizational data access.
- **Standout Features**:
  - **Office Integration**: Works directly inside Word, Excel, PowerPoint, Outlook, and Teams to draft documents, analyze data, and create presentations.
  - **Meeting Assistance**: Can join Teams meetings, take notes, and provide summaries.
  - **Organizational Knowledge**: Enterprise version can access your organization's SharePoint, OneDrive, and email data (with permissions).
  - **Excel Python Integration**: Can write and execute Python code directly in Excel for advanced data analysis.
- **Cost Structure**:
  - **Free**: Basic web chat at copilot.microsoft.com
  - **Copilot Pro**: $20/month per user (requires Microsoft 365 subscription for full features)
  - **Copilot for Microsoft 365**: $30/month per user (requires enterprise Microsoft 365 license)
- **Things to Note**:
  - **Healthcare Consideration**: Enterprise versions with proper Microsoft 365 healthcare configurations may be HIPAA compliant - check with your IT department.
  - Best value if you're already invested in the Microsoft ecosystem.
  - Consumer versions should not be used with sensitive data.
- **Link**: [copilot.microsoft.com](https://copilot.microsoft.com/)

---

### 6. Local & Specialized Tools

#### Desktop & Cloud Tools

**LM Studio**
- **Core Idea**: A desktop application that lets you download and run open-source LLMs (like Llama, Mistral, Phi) directly on your own computer.
- **Why Use It?**:
  - **Privacy**: All processing is done locally; no data is sent to the cloud.
  - **Control**: Full control over model parameters and configurations.
  - **Offline Access**: Works without an internet connection.
- **Cost**: **Completely Free** - No subscription, no API costs. Only cost is your hardware.
- **Things to Note**:
  - **Healthcare Note**: ✅ SAFE for PHI when properly configured - all data stays local on your machine.
  - Requires a powerful computer with sufficient RAM (16GB minimum, 32GB+ recommended) and a good GPU.
  - Model quality varies - test thoroughly before relying on outputs.
- **Link**: [lmstudio.ai](https://lmstudio.ai/)

**Cursor**
- **Core Idea**: An "autonomous AI agent platform" built on top of VS Code, designed to automate development tasks.
- **Why Use It?**:
  - **Background Agents**: Can run tasks independently in the cloud to debug issues or build features in parallel.
  - **Full Codebase Understanding**: Indexes your entire repository, allowing the AI to answer questions and make changes with multi-file context.
  - **BugBot**: An automated PR code reviewer that finds issues and suggests fixes before merging.
- **Cost**:
  - **Free**: Limited to 50 requests per month, basic features
  - **Pro**: $20/month - Unlimited requests, advanced models (GPT-4o, Claude Sonnet)
  - **Business**: $40/month per user - Team features, centralized billing, admin controls
- **Things to Note**:
  - **Healthcare Warning**: Not designed for clinical use. Code-focused tool only.
  - Great for developers but requires coding knowledge.
- **Link**: [cursor.sh](https://cursor.sh/)

**NotebookLM (from Google)**
- **Core Idea**: A research assistant. You provide the source material (PDFs, text files, Google Docs), and the AI becomes an expert in *your* documents.
- **Why Use It?**:
  - **Grounded Responses**: The AI answers questions based *only* on the sources you provide, reducing hallucinations.
  - **Automatic Summaries & Citations**: Generates summaries and points directly to the source location in your documents.
  - **Video Overviews & Mind Maps**: Can automatically create narrated video slideshows or interactive mind maps from your source documents to help visualize and understand complex topics.
- **Cost**: **Free** (with Google account) - Up to 50 sources per notebook, 500,000 words per source
- **Things to Note**:
  - **Healthcare Warning**: Not HIPAA compliant. Do not upload patient data or confidential medical records.
  - Excellent for literature reviews and research synthesis.
  - Audio overviews are particularly helpful for learning complex topics.
- **Link**: [notebooklm.google.com](https://notebooklm.google.com/)

---
#### CLI (Command-Line Interface) Tools

**Claude Code**
- **Core Idea**: An "agentic" coding assistant that lives in your terminal. You give it a task, and it can plan and execute the work, including editing files and running commands.
- **Why Use It?**:
    - **Automation**: Offload complex engineering tasks like writing tests, refactoring code, or debugging.
    - **Native VS Code Extension**: Offers a graphical experience directly within the VS Code editor.
    - **Checkpoints**: Automatically saves the code state before each change, allowing you to instantly rewind mistakes.
- **Cost**: Requires Claude Pro subscription ($20/month) or API keys with usage-based pricing
- **Things to Note**:
    - **Healthcare Warning**: Not for clinical use. Development tool only.
    - Powerful for coding tasks but requires command-line familiarity.
- **Link**: [claude.ai/code](https://claude.ai/code)

**Gemini CLI**
- **Core Idea**: A lightweight command-line interface to access Google's Gemini models directly from your terminal.
- **Why Use It?**:
    - **Interactive Shell**: Allows you to run commands like `vim` or `git` directly inside the AI session.
    - **Gemini CLI Extensions**: An open-source framework that lets the AI interact with external tools like databases, CI/CD systems, and APIs.
    - **Scripting & Automation**: Easily integrate Gemini into your shell scripts and development workflows.
- **Cost**: Free to use (uses your Google AI Studio API key with same generous free tier)
- **Things to Note**:
    - **Healthcare Warning**: Not for patient data. Development use only.
    - Requires API key setup and command-line knowledge.
- **Link**: [github.com/google/gemini-cli](https://github.com/google/gemini-cli)
