
---

````markdown
# 🌐 Using the OpenAI API (Python)

OpenAI provides a powerful API that allows developers to interact with models like **GPT-4**, **GPT-3.5**, **Whisper**, **DALL·E**, and more.

This guide shows how to get started with **ChatCompletion**, which powers conversational AI apps.

---

## ✅ Step 1: Install the SDK

```bash
pip install openai
````

---

## ✅ Step 2: Set Your API Key

You’ll need an API key from [https://platform.openai.com/account/api-keys](https://platform.openai.com/account/api-keys)

```python
import openai

openai.api_key = "sk-..."  # ⚠️ Never share your key publicly
```

> 💡 You can also set it via environment variable:

```bash
export OPENAI_API_KEY=your-key
```

---

## 💬 Step 3: ChatCompletion (Chat with GPT)

```python
response = openai.ChatCompletion.create(
    model="gpt-4",  # or "gpt-3.5-turbo"
    messages=[
        {"role": "system", "content": "You are a helpful AI assistant."},
        {"role": "user", "content": "What is the capital of Italy?"}
    ],
    temperature=0.7,
    max_tokens=100
)

print(response['choices'][0]['message']['content'])
```

✅ Output:

```
The capital of Italy is Rome.
```

---

## 🛠️ ChatCompletion Parameters

| Parameter     | Description                                        |
| ------------- | -------------------------------------------------- |
| `model`       | Choose the engine (e.g., `gpt-4`, `gpt-3.5-turbo`) |
| `messages`    | List of chat turns (system, user, assistant)       |
| `temperature` | Randomness (0 = focused, 1 = creative)             |
| `max_tokens`  | Max words in the response                          |
| `stop`        | Optional stop sequences to end generation          |

---

## 🔁 Prompt Example with Conversation History

```python
messages = [
    {"role": "system", "content": "You are a travel guide."},
    {"role": "user", "content": "Where should I travel in summer?"},
    {"role": "assistant", "content": "You might enjoy Greece or Japan."},
    {"role": "user", "content": "Tell me more about Japan."}
]

response = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",
    messages=messages
)

print(response['choices'][0]['message']['content'])
```

---

## 📁 Other OpenAI APIs (Optional)

| API                 | Purpose                               |
| ------------------- | ------------------------------------- |
| `ChatCompletion`    | Chat interface (GPT models)           |
| `Completion`        | Legacy models like `text-davinci-003` |
| `Image.create`      | Generate images from text (DALL·E)    |
| `Audio.transcribe`  | Transcribe audio (Whisper)            |
| `Embedding.create`  | Generate text embeddings              |
| `Moderation.create` | Detect unsafe or toxic content        |

---

## 🧠 Tips for Best Results

* Use **system messages** to guide behavior.
* Keep **message history short** to avoid token limits.
* Use `temperature=0` for deterministic, factual results.
* Add retries or error handling in production apps.

---

## 🔐 Token Usage & Cost

* OpenAI charges per **1,000 tokens** (input + output).
* Use `response['usage']` to inspect token cost.

```python
print(response['usage'])
# {'prompt_tokens': 42, 'completion_tokens': 25, 'total_tokens': 67}
```

---

> 🧠 **Reminder**: You’re not “talking to a server” — you're sending structured text data to a powerful model trained on billions of documents.
