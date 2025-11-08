# AdaptCV

**AdaptCV** is an advanced AI-powered system that uses **LlamaIndex Agent Workflows** and the **Gemini LLM** to automatically tailor a user's resume for a specific job application. By intelligently analyzing the job posting and strategically updating an existing resume, the tool ensures maximum relevance and highlights the most crucial skills and experiences.

The core of the project is to create a **customized resume** using a LlamaIndex Workflow, adapting it specifically for targeted job applications.

---

## ✨ Features

* **Intelligent Job Scraping:** Utilizes a dedicated agent (`JobResearchAgent`) and a scraping tool (`scrape_url`) to retrieve and analyze content from a given job posting URL.
* **Resume Tailoring:** A specialized agent (`ResumeUpdaterAgent`) refines the user's existing resume by updating the summary, work experience, skills, and education sections to perfectly align with the job requirements.
* **HTML Generation:** The final markdown resume content is automatically rendered into a professional, styled HTML resume using a template (`html_resume_template/`) and a precise `apply_diff` tool for content injection.
* **Modular Architecture:** Built using LlamaIndex's `AgentWorkflow` for a structured and observable execution path.

---

## 🧠 Core Architecture (Agent Workflows)

The **AdaptCV** project is structured around two primary workflows:

1.  **`UpdateResumeWorkflow`**
    * **Goal:** Tailor the resume content, saving the result to (`updated_resume.md`).
    * **Agents:**
        * **`JobResearchAgent`:** Extracts and categorizes key job requirements (skills, qualifications, experiences).
        * **`ResumeUpdaterAgent`:** Generates the new, tailored resume content in markdown format based on job requirements and the existing resume.

2.  **`RenderResumeWorkflow`**
    * **Goal:** Create the final, professionally styled HTML resume (`html_resume/resume.html`).
    * **Tools:** This workflow uses tools like `read_resume_markdown`, `read_file`, and the critical `apply_diff` tool to perform precise code replacement within the HTML or CSS template.

---

## 💻 Setup and Installation

### Prerequisites

* **Python:** Requires Python version **3.12.9**.
* **API Key:** A **Gemini API Key** must be set up as an environment variable (e.g., in a `.env` file) for the agents to access the `models/gemini-2.0-flash` LLM.

### Dependencies

The project relies on a number of `llama-index` packages for its agent and workflow functionality:

```toml
[project]
dependencies = [
    "llama-index==0.12.28",
    "llama-index-core==0.12.28",
    "llama-index-llms-gemini==0.4.14",
    # ... other LlamaIndex dependencies ...
    "python-dotenv==1.1.0",
    "unstructured>=0.17.2",
]

To install all dependencies:
uv sync
```

## Run the Project

```sh
uv run main.py
```

## Usage
* Provide your existing resume file and the job posting URL directly in the chat interface.
* Open the `resume.html` file in your browser to view the rendered resume.
