# ITAI 2376 Project Specifications

[Note: The PDF contains many repeated sections and long instructions. This Markdown version is structured for copy/paste use. Diagrams and images are represented as placeholders where needed.]

## ITAI 2376 Deep Learning in Artificial Intelligence

### Midterm and Final Project Specifications

**Spring 2026**

Houston City College AI and Robotics Program

---

## At a Glance

- **Midterm:** AI Agent Blueprint
- **Due:** April 06, 2026
- **Weight:** 20% of your final grade
- **Final:** Build Your AI Agent
- **Due:** May 3, 2026
- **Weight:** 25% of your final grade
- **Format:** Individual or team, maximum 3 students
- The midterm plan builds directly into the final project.

---

# Midterm Project: AI Agent Blueprint

## Due April 06, 2026

## Weight: 20 of your final grade

### What Is This?

This is your game plan. Before you build anything, you need to think it through. The midterm is a design document where you plan the AI agent or multi-agent system you will build for your final project. Think of it like an architect drawing blueprints before construction starts.

### Important

This is not busy work. Your final project will be graded partly on how well you followed or intentionally improved upon this plan.

### Why a Plan Instead of a Build?

You have already built AI models in your other courses—classifiers in Computer Vision, sentiment analyzers in NLP, and predictors in Machine Learning. Building another standalone model would not push you forward. The next step in your AI career is learning to wrap those models into intelligent agents that can reason, use tools, and interact with users or other agents. This midterm forces you to study what agents are and design one before you code it.

---

## Choose Your Path

Either option is equally valid. Choose based on what interests you and what you want in your portfolio.

### Option A: Single AI Agent
Design one agent that uses a deep learning model and at least one tool to accomplish a task.

**Example:** A customer support agent that uses a text model to understand questions and searches a knowledge base.

### Option B: Multi-Agent System
Design two or more agents that collaborate to solve a bigger problem.

**Example:** A research team where one agent searches the web, another summarizes findings, and a third writes a report.

### Option A / Option B Examples

- A medical image screening agent that uses a CNN to analyze X-rays and generates a preliminary report.
- A content creation agent that uses a generative model and can browse the web for research.
- A quality control pipeline where one agent inspects images with a CNN, another logs defects, and a third generates alerts.
- A creative studio where one agent generates images, another critiques them, and a third refines based on feedback.

You must declare your option. Your blueprint must clearly state whether you are planning Option A single agent or Option B multi-agent system. This is your commitment for the final project. You can upgrade from A to B later. If you upgrade, you will explain what changed in your final write-up.

---

## Tips for Choosing Your Application

Choosing what to build is often the hardest part. Here are some tips to help you land on an idea that is both doable and meaningful.

- Start with what you know. Think about your domain knowledge, your job, your hobbies, or your other coursework.
- Solve a real annoyance. “I wish someone would just do this for me” is a great starting point.
- Do a little research first. Spend 30 minutes looking at AI agent demos on YouTube, browsing LangChain and CrewAI templates, and checking GitHub for example projects.
- Think about your portfolio. This project will go on your resume and GitHub.
- Keep it focused. An agent that does one thing really well is better than an agent that tries to do everything and breaks.
- Reach out early if you are stuck.

---

## What to Include in Your Blueprint

Keep it clear and organized. Your blueprint must cover all eight sections below. Each section has a description of what to write and a short example to guide you.

### 1. Problem Statement — 10 points
Describe the real-world problem your agent will solve. Answer three things:

- What is the problem?
- Who has this problem?
- Why does it matter or why is it worth automating?

**Example:** Small business owners spend hours every week answering the same customer questions by email. My agent will read a company FAQ document and automatically generate accurate answers to incoming customer emails. The target user is a small business owner with no technical background who wants to reduce time spent on repetitive support tasks.

### 2. Chosen Option — 5 points
State clearly whether you are choosing Option A single agent or Option B multi-agent system. Then explain in 2 to 3 sentences why that option fits your problem.

**Example Option A:** I am choosing Option A Single AI Agent. My problem only requires one agent to read the FAQ and generate a response. Adding more agents would overcomplicate a straightforward task and make debugging harder.

**Example Option B:** I am choosing Option B Multi-Agent System. My problem requires one agent to search the web for research, a second agent to summarize the results, and a third to write the final report. Each step is specialized enough to warrant its own agent.

### 3. Agent Architecture and Diagram — 30 points
Draw a diagram that shows how information flows through your agent. Your diagram must include all four of the following boxes connected by labeled arrows:

- INPUT box
- DEEP LEARNING MODEL box
- AGENT BRAIN box
- TOOL box
- OUTPUT box

#### What each box means

- **INPUT box:** What the user sends to the agent.
- **DEEP LEARNING MODEL box:** The specific AI model that processes or analyzes the input.
- **AGENT BRAIN box:** This is always the LLM.
- **TOOL box:** An external resource the agent calls to get information or take an action.
- **OUTPUT box:** What the agent sends back to the user.

#### Arrow labels
Every arrow must have a short label that says what is being passed from one box to the next.

#### Example diagram text

```
INPUT Customer Email
   | sends email text for classification
   v
DEEP LEARNING MODEL BERT Text Classifier
   | identifies topic and intent
   v
AGENT BRAIN LLM GPT-4 / Claude / Gemini
   | reads topic, decides what to search, writes reply
   | searches FAQ for matching answer
   v
TOOL FAQ Database Search
   | finds best matching FAQ entry
   v
OUTPUT Email reply sent to the customer
```

Notice that the DEEP LEARNING MODEL box and the AGENT BRAIN box are two separate boxes. The BERT model does one specific job: classify the question. The LLM does the reasoning, decision-making, and writing. They work together but they are not the same thing.

If you are building Option B multi-agent, draw one complete set of boxes for each agent and add horizontal arrows between agents showing what one agent hands to the next.

### 4. Deep Learning Connection — 25 points
Name the deep learning model or models that will power your agent. You must connect at least two modules from this course to your design. Explain why each model fits the task, not just what it is.

**Example:** My agent uses two deep learning components. First, a fine-tuned BERT model from Module 05 Transformers to classify the customer’s question and find the most relevant FAQ entry. I chose BERT because it understands sentence meaning, not just keywords. Second, a GPT-based LLM as the reasoning brain from Module 10 Agentic AI to generate a natural-sounding reply using the FAQ answer as context. Together these two models cover understanding the question and writing the response.

### 5. Agent Framework — part of 15 points
Name the agent framework you plan to use for the final build. Explain why you chose it over the alternatives. Mention whether you have already tried it or if this will be your first time using it.

**Example:** I plan to use LangChain because it has strong built-in support for RAG pipelines and tool integration, which are exactly what my agent needs. I considered CrewAI, but decided against it because my project is a single agent, and LangChain is better suited for that. I have already run the LangChain quickstart tutorial and successfully built a basic question-answering chain.

### 6. Tools and Data — part of 15 points
List every tool or API your agent will call. For each one, explain why the agent needs it. Then describe what data your agent will work with and where you will get it.

**Example:**

- **Tool 1:** A vector database such as Chroma DB, free to store and search the FAQ document. The agent needs this to retrieve relevant answers without reading the whole document every time.
- **Tool 2:** An email-reading tool using the Gmail API free tier. The agent needs this to receive incoming customer emails automatically.

**Data:** I will create a sample FAQ document with 50 common questions for a fictional software company. This data is self-generated so there are no privacy or licensing concerns.

### 7. Build Plan — part of 10 points
Write a simple week-by-week timeline from the midterm deadline April 6 to the final deadline May 3. Be specific about what you will work on each week.

**Example:**

- **Week 1, April 6 to 13:** Set up LangChain environment in Colab, load the FAQ document into Chroma DB, and verify that basic search works.
- **Week 2, April 14 to 20:** Fine-tune the BERT classifier on sample question-answer pairs and connect it to the vector search tool.
- **Week 3, April 21 to 27:** Build the full agent loop: receive question, classify, search FAQ, generate reply. Test with at least 20 sample questions.
- **Week 4, April 28 to May 3:** Record the demo video, write the final write-up, and submit all files.

### 8. Expected Challenges — part of 10 points
Name at least two things that could go wrong or that you are unsure about. This is not a weakness in your plan—it shows that you are thinking like a real engineer.

**Example:**

- **Challenge 1:** The BERT classifier may not perform well on questions that are phrased very differently from the FAQ entries. I plan to test this early and may need to add synonym matching or use a more flexible embedding-based retrieval method instead.
- **Challenge 2:** The Gmail API requires OAuth authentication, which I have not set up before. If this takes too long to configure, I will use a simulated inbox with local text files as a fallback so the rest of the agent can still be demonstrated.

---

## How to Draw Your Architecture Diagram

A diagram might sound intimidating, but it is really just a simple map that shows how information flows through your agent. You do not need any special software. You can draw it by hand and take a photo, or use a free tool like Google Slides, Canva, or draw.io. Think of it as a flowchart with boxes and arrows.

### Every agent diagram needs to show four things

- What the agent receives as input.
- The deep learning model or logic the agent uses to think.
- Any tools the agent calls on to get information or take an action.
- What the agent sends back as output.

### Step-by-step example: Medical Image Screening Agent

Imagine you chose to build a medical image screening agent. A doctor uploads a chest X-ray image, and the agent analyzes it and produces a short preliminary report.

1. Draw a box on the left and label it `INPUT X-Ray Image uploaded by the doctor`.
2. Draw an arrow pointing right and label the arrow `sends image`.
3. Draw a second box and label it `AGENT BRAIN CNN Image Classifier`.
4. From the brain box, draw two arrows going out. One goes to a tool box labeled `TOOL Medical Knowledge Base Search`. Label that arrow `looks up matching conditions`.
5. Draw a final arrow from the tool box back to the brain box, and then one more arrow going right to `OUTPUT Preliminary Report sent to the doctor`. Label the last arrow `generates report`.

Your final diagram would read left to right like this:

`INPUT X-Ray Image -> AGENT BRAIN CNN Classifier -> TOOL Knowledge Base -> OUTPUT Report`

Label each box clearly, label each arrow with a short action phrase, and make sure someone who has never seen your project before could look at it and understand what your agent does.

If you are doing Option B, draw one box per agent and show arrows between them.

---

## Deliverables

1. Blueprint document in PDF or Word format.
2. Length: 3 to 6 pages, including your agent architecture diagram.

---

## Rubric

### 100 points

- **Problem Statement and Use Case — 10 points:** Clear, real-world problem. Makes sense as an agent task.
- **Option Choice and Justification — 5 points:** Clearly states Option A or B. Explains why it fits the problem.
- **Agent Architecture and Diagram — 30 points:** Shows inputs, reasoning, actions, and tools. Diagram is clear and labeled. The flow is easy to follow.
- **Deep Learning Connection — 25 points:** Connects at least 2 course modules. Explains why these models fit.
- **Agent Framework and Tools/Data — 15 points:** Names the chosen framework with reasoning. Data sources identified. Tools make sense.
- **Build Plan and Challenges — 10 points:** Week-by-week plan is specific. Challenges show honest thinking.
- **Professional Quality — 5 points:** Well-organized, readable, and correctly named files.

### File Naming Convention

- **Individual submissions:** `MDBlueprintLastNameFirstNameITAI2376.pdf`
- **Team submissions:** `MDBlueprintLastNameFirstNameGroupNameITAI2376.pdf`

**Examples:**

- `MDBlueprintGarciaMariaITAI2376.pdf`
- `MDBlueprintNguyenDavidAlphaTeamITAI2376.pdf`

Submit all files through Canvas. For team submissions, ONE team member submits on behalf of the whole group. Use the submitting member’s name in the file name. The cover page of your document must list the full names of all team members who worked on the project.

---

# Final Project: Build Your AI Agent

## Due May 3, 2026

## Weight: 25 of your final grade

### What Is This?

Now you build it. Take the blueprint you designed for the midterm and turn it into a working AI agent or multi-agent system. You can follow your original plan exactly, or you can pivot based on what you learned and the feedback you received. If you pivot, explain what changed and why in your final write-up. That explanation is part of the learning.

### Important: You Must Use an Agent Framework

Your final project must be built using an agent framework. Agent frameworks give your project structure, handle tool orchestration, manage agent memory, and reflect how agents are built in the real world.

You are free to choose any framework that works for you:

- LangChain or LangGraph
- CrewAI
- AutoGen by Microsoft
- Hugging Face smolagents
- OpenClaw or NemoClaw
- Other frameworks if acceptable

---

## Choose Your Final Option

### Option A: Single AI Agent
A working demo of one agent built with an agent framework. Your agent must:

- Use at least one deep learning model.
- Use at least one tool: web search, database, API, calculator, etc.
- Show visible reasoning, not just input going directly to output.

### Option B: Multi-Agent System
A working demo of two or more agents that collaborate, built with an agent framework. Your system must:

- Have agents with distinct roles.
- Show agents communicating or passing work to each other.
- Integrate at least one deep learning model in the pipeline.

### Switching options
If you planned Option A in your midterm but want to upgrade to Option B or the reverse, that is fine. Just explain the change in your write-up.

---

## What You Need to Deliver

Three deliverables. That is it.

### 1. Working Code
Your agent must run and do what it is supposed to do. Submit all code files, notebook, scripts, configuration files organized in a folder or a GitHub repository. The project must use an agent framework.

If your agent requires API keys or paid services, include clear setup instructions so the instructor can understand how it works even if they cannot run it on their machine.

### 2. Working Demo
Show your agent in action. Choose one of the following:

- Live demo present in class or via Teams, 8 minutes maximum.
- Recorded video: a screen recording showing your agent working, with your voice narrating what is happening, 8 minutes maximum.

Upload to Canvas or share a link. The demo must show the agent actually running, not just slides about it.

### 3. Short Write-Up
A 2 to 4 page document covering:

- What your agent does.
- Which option you chose, A or B, and whether you upgraded from your midterm plan.
- What changed from your midterm blueprint and why.
- Which agent framework you used and why you chose it.
- Which deep learning models you integrated and how they fit into the agent.
- What worked, what did not work, and what you would improve with more time.
- One thing you learned about AI agents that surprised you.

---

## Rubric

### 100 points

- **Agent Functionality — 25 points:** Agent runs and performs its intended task. Reasoning and tool use are visible.
- **Deep Learning Integration — 15 points:** At least one deep learning model is meaningfully integrated, not just a wrapper around an API.
- **Agent Framework Usage — 10 points:** Built with a proper agent framework. Framework features such as tools, memory, and orchestration are used appropriately.
- **Working Demo Live or Video — 20 points:** Clear walkthrough of the agent actually running. I can see the agent thinking and acting. Within 8 minutes.
- **Write-Up and Reflection — 15 points:** Honest reflection on what changed, what worked, and what you learned.
- **Code Quality and Organization — 10 points:** Code is organized, commented, and includes a README with setup instructions.
- **Professional Quality — 5 points:** File naming, formatting, and overall presentation.

### File Naming Convention

- **Individual submissions:**
  - `FNCodeLastNameFirstNameITAI2376.zip`
  - `FNWriteUpLastNameFirstNameITAI2376.pdf`
  - `FNDemoLastNameFirstNameITAI2376.mp4`

- **Team submissions:**
  - `FNCodeLastNameFirstNameGroupNameITAI2376.zip`
  - `FNWriteUpLastNameFirstNameGroupNameITAI2376.pdf`
  - `FNDemoLastNameFirstNameGroupNameITAI2376.mp4`

**Examples:**

- `FNCodeGarciaMariaITAI2376.zip`
- `FNWriteUpGarciaMariaITAI2376.pdf`
- `FNDemoGarciaMariaITAI2376.mp4`

Submit all files through Canvas. For team submissions, ONE team member submits on behalf of the whole group. Use the submitting member’s name in the file name. The cover page of your document must list the full names of all team members who worked on the project.

If submitting code via GitHub instead of a zip file, include the GitHub repository link in your write-up and name your write-up and demo files using the convention above.

---

## How the Midterm and Final Connect

### MIDTERM
Design your agent.

### The Blueprint Feedback
5 weeks to build.

### FINAL
Build your agent.

### The Real Thing
Your midterm blueprint is the foundation for your final. You do not start from scratch in the final project. You already have a plan. The final is about executing that plan, adapting when things do not go as expected, and reflecting on what you learned.

Pivoting is okay. If your original idea turns out to be too complex or you discover a better approach, that is fine. In the real world, projects change. Just explain what changed and why in your write-up.

---

## Choosing How to Build

### Traditional Code, OpenClaw, or NemoClaw
You have real choices in how you build your agent. This section explains those choices honestly.

### What Are OpenClaw and NemoClaw?

OpenClaw is one of the fastest-growing open-source AI agent frameworks in history. It is not a chatbot. It is a complete runtime platform for building autonomous agents that run continuously, remember context across sessions, connect to messaging apps like Telegram, Slack, and WhatsApp, and take real actions: reading files, running shell commands, browsing the web, calling APIs, and more.

OpenClaw is built around two core ideas:

- The **Gateway**, a persistent server that stays running and connects your agents to the outside world through whatever channels you choose.
- The **Skills system**, where every capability your agent has comes from a skill.

A skill is a directory containing a `SKILL.md` file that describes what the tool does and how the agent should use it, plus any supporting code.

NemoClaw is NVIDIA’s enterprise-grade version of OpenClaw. It adds security guardrails, the OpenShell runtime, sandboxed execution, policy-based privacy controls, and integration with NVIDIA’s Nemotron open models.

### Why this matters for your career
OpenClaw and NemoClaw represent a genuine shift in how AI agents are deployed in the real world. Knowing how to configure, extend, and deploy on these platforms is a real workforce skill.

---

## Your Three Framework Paths

### Path 1: Traditional Code
Write your agent in Python using LangChain, CrewAI, AutoGen, smolagents, or similar. Recommended for Option A single agent. You write every agent step, every tool call, every decision.

### Path 2: OpenClaw or NemoClaw
Configure and extend OpenClaw or NemoClaw by writing your own skills, defining your own agents, and wiring your own workflows. Recommended for Option B multi-agent.

### Path 3: Other Frameworks
Any established agent framework is acceptable: LangGraph, Agno, Google ADK, Semantic Kernel, and others.

---

## How OpenClaw Fits This Course

You may use OpenClaw for Option A or Option B. For many students, OpenClaw is especially useful in multi-agent work because it helps organize agents, skills, memory, and workflows. For a simpler single agent, traditional code may still be easier to understand and debug.

The key standard in this course is not whether you typed every line by hand. The key standard is whether you understand what is inside your system.

---

## If You Choose OpenClaw or NemoClaw

### What You Must Do

- Write your own skills from scratch.
- Define your own agents and subagents.
- Understand the ReAct loop under the hood.
- Connect a deep learning model meaningfully.
- Demonstrate full understanding in your demo.

### Using AI and Agent Platforms Responsibly
You may use AI-assisted development tools, including OpenClaw, to help build or assemble your system. However, you may not submit a system that you cannot explain clearly.

### Core expectations
You must be able to explain:

- What your overall agent system is designed to do.
- Why you chose a single agent or multi-agent design.
- What each agent or subagent does.
- How memory, shared state, or handoffs work.
- What the framework is doing for you.
- What would break if a skill, agent, memory component, or tool were removed.

---

## Using OpenClaw with Limited Compute

You do not need a powerful machine to use OpenClaw. The Gateway runs locally or in a free cloud instance, while reasoning happens in the cloud through an API call to whichever LLM you choose.

### Free tier options

- Gemini API
- Anthropic API
- OpenAI API
- HuggingFace Inference API
- Google Colab
- Railway or Render free tier

### Writing 1 to 2 skills from scratch
A skill is just a directory with a `SKILL.md` file plus a small script. Example skills can include:

- A skill that reads a local file and returns its contents.
- A skill that calls a free public API.
- A skill that runs a small pre-trained model via a HuggingFace endpoint.
- A skill that formats and saves output to a file.

---

## What to Include in Your Blueprint for OpenClaw

If you choose OpenClaw or NemoClaw, your blueprint must include:

1. Framework declaration.
2. Compute disclosure.
3. Agent and subagent design.
4. Two custom skills planned, not yet built.
5. LLM choice and free tier plan.
6. POC scope statement.

---

## Running Your Agent Online and Local Options

### Option 1: Run Online
Use Google Colab. It runs in your browser, requires no installation, and gives you free access to a Python environment with GPU support.

### Option 2: Run Locally with Docker
Docker lets you package your entire agent and all its dependencies into a container that runs the same way on any computer.

### Docker steps

1. Install Docker Desktop.
2. Organize your project folder.
3. Create `requirements.txt`.
4. Create your `Dockerfile`.
5. Store API keys safely in `.env`.
6. Build your Docker container.
7. Run your agent with Docker.
8. Record your demo from the terminal.

---

## Blueprint Amendment

If you already submitted an early blueprint, your original blueprint still counts. You are not starting over. You may stay the course or adjust your plan if needed.

---

## File Naming and Submission

Submit all files through Canvas. For team submissions, one team member submits on behalf of the whole group. Use the submitting member’s name in the file name.

---

## End of Document
