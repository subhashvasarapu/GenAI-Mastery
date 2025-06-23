
---

# 🧠 **AI-Powered Resume Builder from Job Descriptions**

---

````markdown
# 🧠 Smart Resume Generator from Job Descriptions using AI

This project scrapes job listings from career websites or LinkedIn and uses **LLMs (like GPT-4)** to **auto-generate a customized resume** based on job requirements, keywords, and industry patterns.

> Think of it like: "Scrape → Understand → Match → Auto-Generate Resume."

---

## 🎯 Project Goals

- 🔍 Scrape job descriptions from LinkedIn, Indeed, or company career pages
- 🧠 Use AI (GPT-4) to understand:
  - Required skills
  - Job responsibilities
  - Keywords
- 📄 Automatically generate a customized resume tailored to the job
- ✅ Allow user inputs to include:
  - Personal info (name, contact, education)
  - Past experiences (optional)
- 💾 Output resume in **PDF format**

---

## 🧱 Tech Stack

| Tool / Library        | Purpose                                      |
|------------------------|----------------------------------------------|
| `BeautifulSoup`, `Selenium`, `Playwright` | Web scraping job descriptions     |
| `OpenAI API`           | Text generation (GPT-4)                     |
| `Streamlit / Flask`    | UI for user interaction                     |
| `pdfkit / WeasyPrint`  | Generate resumes in PDF format              |
| `LangChain` (optional) | Better LLM control and prompt pipelines     |

---

## 📁 Folder Structure

```plaintext
resume-gen-from-jobs/
├── app.py
├── scrape/
│   └── linkedin_scraper.py
├── generator/
│   └── resume_writer.py
├── templates/
│   └── resume_template.html
├── utils/
│   └── clean_text.py
├── output/
│   └── resume.pdf
├── README.md
└── requirements.txt
````

---

## 🔄 Workflow Overview

```plaintext
[LinkedIn/Career Page URL] → [Scraper] → [Job Description Text]
→ [GPT Prompt with Resume Template] → [Generated Resume]
→ [PDF Export] → [Download]
```

---

## 🔧 Example Prompt to GPT

```text
You are a professional resume writer. Based on the following job description, generate a resume that highlights relevant skills, experience, and education for the role.

Job Description:
"""
[Paste scraped job description]
"""

User Info:
- Name: Aryan Subhash
- Education: B.Tech in Computer Science
- Experience: 3 years in Cloud Networking
- Skills: Azure, PowerShell, Terraform

Output the resume in clean, professional bullet-point format.
```

---

## 💻 Example Python Code (Core Logic)

```python
import openai

def generate_resume(job_desc, user_info):
    prompt = f"""
    You are a professional resume writer...

    Job Description:
    {job_desc}

    User Info:
    {user_info}

    Format the resume clearly with sections like Summary, Skills, Experience, Education.
    """
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}],
        temperature=0.4
    )
    return response.choices[0].message.content
```

---

## 🌐 Optional Streamlit UI

```python
import streamlit as st
from generator.resume_writer import generate_resume

st.title("🧠 Smart AI Resume Generator")

url = st.text_input("Paste Job Description URL (LinkedIn/Company Site)")
name = st.text_input("Your Name")
skills = st.text_area("Your Skills (comma-separated)")
experience = st.text_area("Your Past Experience")

if st.button("Generate Resume"):
    job_desc = scrape_job_description(url)  # Implement with BeautifulSoup
    resume = generate_resume(job_desc, {
        "name": name,
        "skills": skills,
        "experience": experience
    })
    st.text_area("Generated Resume", resume, height=500)
```

---

## 💾 PDF Export

Use `pdfkit` or `WeasyPrint` to convert resume HTML to PDF.

```bash
pip install pdfkit
```

```python
import pdfkit

def export_to_pdf(text, filename="resume.pdf"):
    html = f"<html><body><pre>{text}</pre></body></html>"
    pdfkit.from_string(html, filename)
```

---

## 📌 Real-World Applications

| Use Case       | Description                                         |
| -------------- | --------------------------------------------------- |
| Job Seekers    | Auto-create resumes for each application in seconds |
| Career Coaches | Help clients generate AI-optimized resumes          |
| Job Boards     | Resume generation based on listings                 |
| Freelancers    | Tailor proposals or profiles automatically          |

---

## 🧠 Bonus: Smart Resume Variants

* 🎯 Match score: Show how well resume matches JD (via semantic similarity)
* 🌐 LinkedIn Profile to Resume: Use scraped LinkedIn profile to feed GPT
* 🧾 Cover Letter: Add button to generate cover letter based on same JD

---

## ✅ Final Deliverables

| File                   | Description                  |
| ---------------------- | ---------------------------- |
| `app.py`               | Main app interface           |
| `linkedin_scraper.py`  | Scrapes JD text              |
| `resume_writer.py`     | GPT-powered resume generator |
| `resume_template.html` | Optional for PDF styling     |
| `output/resume.pdf`    | Final exported resume PDF    |

---

## 🏁 Summary

This AI project automates the resume-building process by scraping **live job descriptions** and dynamically tailoring resumes using **GPT-4**.

* Saves time
* Optimizes for ATS (if keywords matched)
* Feels personal and custom-written

---

> 🚀 A great fit for AI portfolios, HR Tech startups, or personal productivity tools.
