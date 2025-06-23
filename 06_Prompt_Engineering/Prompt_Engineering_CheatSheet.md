
---

````markdown
# 🧾 Prompt Engineering Cheat Sheet

Prompt engineering is the art of writing effective instructions to guide large language models (LLMs) like ChatGPT, GPT-4, Claude, or Gemini to produce accurate, relevant, and useful outputs.

Use this cheat sheet as a quick reference to craft powerful prompts.

---

## 🛠️ Core Tips

### ✅ 1. Use Clear Instructions
- Be direct and specific.
- Avoid vague language.
```text
❌ Tell me something about physics  
✅ Explain Newton’s 3 laws in simple terms
````

---

### ✅ 2. Provide Examples

* Show what kind of output you want.
* Models learn from pattern in prompt.

```text
Prompt:
Explain a concept using this format:
Concept: [Name]  
Explanation: [Layman’s terms]  
Analogy: [Real-world comparison]

Concept: Black Hole  
→ Output will follow your format
```

---

### ✅ 3. Use Delimiters for Structure

* Separate input sections using quotes, backticks, or triple quotes.

```text
Summarize the following text:
"""
Artificial Intelligence is a field of computer science...
"""
```

---

## ✨ Extra Techniques

### 🎭 4. Specify a Role

```text
You are a fitness coach. Create a beginner workout plan.
```

### 🧠 5. Ask Step-by-Step

```text
Explain how to build a website in 5 simple steps.
```

### 🧪 6. Force Reasoning (Chain-of-Thought)

```text
Let’s think step by step.
```

### 🔢 7. Set Format

```text
List 5 strategies with bullet points.
```

### 📦 8. Limit Output

```text
Give me 3 possible email subject lines.
```

---

## 🧱 Prompt Frameworks

### 🔤 P.R.O.M.P.T. Acronym

| Element      | Description                          |
| ------------ | ------------------------------------ |
| **P**urpose  | What's the task or goal?             |
| **R**ole     | Who is the AI acting as?             |
| **O**utput   | What format is expected?             |
| **M**arkers  | Keywords, steps, or delimiters       |
| **P**atterns | Example structure of expected result |
| **T**one     | Formal, funny, concise, etc.         |

---

## 🧠 Prompt Templates

### 📘 Template: Teach Like a Tutor

```text
You are a math tutor. Explain [concept] to a 10-year-old using a real-world analogy.
```

### 🧪 Template: ELI5 Format

```text
Explain [complex topic] like I'm 5 years old.
```

### 🔗 Template: Comparison

```text
Compare [Concept A] vs [Concept B] in a table with pros and cons.
```

---

## 🧩 Prompt Design Patterns

| Pattern             | Use Case                    |
| ------------------- | --------------------------- |
| Role-based          | Domain-specific responses   |
| Chain-of-thought    | Encourage logical reasoning |
| Input/Output format | Predictable structure       |
| Few-shot examples   | Show samples to mimic       |
| Step-by-step        | Break down complex problems |

---

## 🧠 Bonus: Prompt Fail Fixes

| Issue                 | Try This                             |
| --------------------- | ------------------------------------ |
| Too generic           | Add details and constraints          |
| Output too long       | Specify word or bullet count         |
| Misunderstood context | Use delimiters and structure clearly |
| Lacks reasoning       | Add "think step by step"             |

---

> 💬 Prompting is like programming in natural language — clarity, structure, and intent are everything.

