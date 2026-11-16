# Week 2 – Provider-Agnostic LLM Client

## 1. Objective

Build a provider-agnostic LLM client that uses a single common interface to connect two LLM providers:

- **Gemini:** Hosted cloud API.
- **Ollama:** Local Llama 3.2 model.

The application allows users to switch between providers without changing the common client code.

## 2. Technologies Used

- Python
- Google Gemini API
- Ollama
- Llama 3.2
- Requests
- Python-dotenv
- Unittest

## 3. Project Structure

```text
week-2/
│
├── llm_client.py
├── main.py
├── test_client.py
├── requirements.txt
├── .env
├── .gitignore
└── README.md
```

## 4. Installation and Setup

### Step 1: Install Ollama

Download Ollama from:

https://ollama.com/download

Install it and verify:

```bash
ollama --version
```

### Step 2: Download Llama 3.2

```bash
ollama pull llama3.2
```

Test the model:

```bash
ollama run llama3.2
```

### Step 3: Create a Virtual Environment

```bash
python -m venv .venv
```

Activate the environment in Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

### Step 4: Install Dependencies

Create `requirements.txt`:

```text
python-dotenv
pytest
google-genai
requests
```

Install packages:

```bash
pip install -r requirements.txt
```

## 5. Source Code

### File 1: llm_client.py

This file defines the common interface and implements Gemini and Ollama providers.

```python
from abc import ABC, abstractmethod
from google import genai
import requests


# Common interface
class LLMProvider(ABC):

    @abstractmethod
    def generate(self, prompt):
        pass


# Gemini cloud provider
class GeminiProvider(LLMProvider):

    def __init__(self, api_key):
        self.client = genai.Client(api_key=api_key)

    def generate(self, prompt):
        response = self.client.models.generate_content(
            model="gemini-3.8-flash",
            contents=prompt
        )
        return response.text


# Ollama local provider
class OllamaProvider(LLMProvider):

    def __init__(self, model="llama3.2"):
        self.model = model
        self.url = "http://localhost:11434/api/generate"

    def generate(self, prompt):
        response = requests.post(
            self.url,
            json={
                "model": self.model,
                "prompt": prompt,
                "stream": False
            },
            timeout=120
        )

        response.raise_for_status()
        return response.json()["response"]


# Common client
class LLMClient:

    def __init__(self, provider):
        self.provider = provider

    def generate(self, prompt):
        return self.provider.generate(prompt)
```

### File 2: main.py

This is the main execution file. It allows users to select a provider and enter a prompt.

```python
import os
from dotenv import load_dotenv

from llm_client import (
    GeminiProvider,
    OllamaProvider,
    LLMClient
)

load_dotenv(override=True)

provider_name = input(
    "Choose provider (gemini/ollama): "
).strip().lower()

if provider_name == "gemini":

    api_key = os.getenv("GEMINI_API_KEY")

    if not api_key:
        raise ValueError("Gemini API key not found in .env")

    provider = GeminiProvider(api_key)

elif provider_name == "ollama":

    provider = OllamaProvider("llama3.2")

else:
    raise ValueError("Invalid provider selected")

client = LLMClient(provider)

prompt = input("Enter your question: ")

answer = client.generate(prompt)

print("\nLLM Response:")
print(answer)
```

### File 3: test_client.py

This file tests the common LLM client using a fake provider.

```python
import unittest
from llm_client import LLMClient


# Fake provider for testing
class FakeProvider:

    def generate(self, prompt):
        return "AI stands for Artificial Intelligence."


class TestLLMClient(unittest.TestCase):

    def test_generate(self):

        provider = FakeProvider()
        client = LLMClient(provider)

        result = client.generate("Explain AI")

        self.assertEqual(
            result,
            "AI stands for Artificial Intelligence."
        )


if __name__ == "__main__":
    unittest.main()
```

### File 4: .env

Create a `.env` file and add your Gemini API key.

```env
GEMINI_API_KEY="YOUR_API_KEY_HERE"
```

Get your API key from:

https://aistudio.google.com/apikey

**Note:** Never upload your actual API key to GitHub.

### File 5: .gitignore

```text
.venv/
.env
__pycache__/
*.pyc
```

## 6. Run the Application

### Run Unit Tests

```bash
python -m unittest test_client -v
```

Expected output:

```text
test_generate ... ok

Ran 1 test

OK
```

### Run with Ollama

```bash
python main.py
```

Select:

```text
Choose provider (gemini/ollama): ollama
```

Enter a prompt:

```text
Explain Artificial Intelligence in simple words.
```

The response is generated using the local Llama 3.2 model.

### Run with Gemini

```bash
python main.py
```

Select:

```text
Choose provider (gemini/ollama): gemini
```

Enter a prompt:

```text
What is Cloud Computing?
```

The response is generated using the Gemini cloud API.

## 7. Working Architecture

```text
             Python Application
                    |
                    |
                 LLMClient
                    |
                    |
               LLMProvider
                    |
           -------------------
           |                 |
     GeminiProvider    OllamaProvider
           |                 |
      Gemini API        Llama 3.2
      (Cloud)            (Local)
```

## 8. Expected Outcome

The application successfully connects to both Gemini and Ollama through a common interface.

Users can select either provider and generate responses by entering prompts.

## 9. Conclusion

This project demonstrates the implementation of a provider-agnostic LLM client using Python. It uses abstraction and a common interface to support multiple LLM providers, making the application flexible and easier to extend.
