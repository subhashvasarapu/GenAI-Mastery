
---

````markdown
# 🤗 Hugging Face Tutorial: Transformers, Datasets & Diffusers

**Hugging Face** is a hub for open-source models and tools to work with **transformers**, **text generation**, **diffusion models**, and more.

This tutorial introduces how to use their key libraries:  
- `transformers` → for LLMs like BERT, GPT-2, Falcon  
- `datasets` → for ML-ready corpora  
- `diffusers` → for image generation (like Stable Diffusion)

---

## 📦 1. Installation

```bash
pip install transformers datasets diffusers accelerate
````

Optional: Install PyTorch or TensorFlow based on your setup.

---

## 🤖 2. Using `transformers` for Text Generation

### 🔹 Load GPT-2 and Generate Text

```python
from transformers import pipeline

generator = pipeline("text-generation", model="gpt2")
result = generator("In a world where AI controls", max_length=50, do_sample=True)
print(result[0]['generated_text'])
```

### 🔹 Use a Conversational Model

```python
from transformers import AutoModelForCausalLM, AutoTokenizer
import torch

model_name = "microsoft/DialoGPT-small"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForCausalLM.from_pretrained(model_name)

input_ids = tokenizer.encode("Hello, who are you?", return_tensors="pt")
output = model.generate(input_ids, max_length=50, pad_token_id=tokenizer.eos_token_id)
print(tokenizer.decode(output[0], skip_special_tokens=True))
```

---

## 📚 3. Using `datasets`

```python
from datasets import load_dataset

dataset = load_dataset("imdb")  # Loads movie reviews
print(dataset["train"][0])
```

### 🔹 Other Popular Datasets:

* `"squad"` – QA dataset
* `"ag_news"` – News classification
* `"common_voice"` – Speech-to-text
* `"wiki40b"` – Clean Wikipedia text

---

## 🎨 4. Using `diffusers` for Image Generation

```python
from diffusers import StableDiffusionPipeline
import torch

pipe = StableDiffusionPipeline.from_pretrained(
    "CompVis/stable-diffusion-v1-4", torch_dtype=torch.float16
).to("cuda")

image = pipe("A futuristic cityscape at night, cyberpunk style").images[0]
image.save("generated_image.png")
```

> 🖼️ This generates a realistic image based on your prompt using **Stable Diffusion**.

---

## 🧪 Bonus: Inference with Hugging Face Hub

### 🔹 Load Any Model from `huggingface.co/models`

```python
from transformers import pipeline

qa_pipeline = pipeline("question-answering", model="deepset/roberta-base-squad2")
qa_pipeline({
    "question": "What is the capital of France?",
    "context": "France's capital city is Paris, known for the Eiffel Tower."
})
```

---

## 🧠 Summary

| Tool             | Purpose                                       |
| ---------------- | --------------------------------------------- |
| `transformers`   | Use LLMs like GPT, BERT, Falcon, LLaMA        |
| `datasets`       | Load, preprocess, and manage datasets         |
| `diffusers`      | Text-to-image models like Stable Diffusion    |
| Hugging Face Hub | Free public repository of models and datasets |

---

## 🌐 Useful Resources

* 🤗 [https://huggingface.co/models](https://huggingface.co/models)
* 📚 [https://huggingface.co/docs/transformers](https://huggingface.co/docs/transformers)
* 🧪 [https://huggingface.co/docs/diffusers](https://huggingface.co/docs/diffusers)
* 🔬 [https://huggingface.co/docs/datasets](https://huggingface.co/docs/datasets)

---

> 🧠 Hugging Face makes it easy to build, test, and deploy GenAI models — no need to train from scratch!
