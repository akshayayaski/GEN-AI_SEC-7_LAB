# Week-3: LLM Monitoring with MongoDB

This project focuses on monitoring Large Language Model (LLM) applications using Python and MongoDB. It extends the provider-independent LLM client by integrating Google Gemini and Ollama to track token usage, response time, estimated API costs, and request status.

The application stores LLM usage details in MongoDB Atlas and implements timeout handling and automatic retries to improve reliability. It also supports unit testing to verify the functionality of the common LLM client.

**Technologies Used:** Python, Google Gemini API, Ollama, MongoDB Atlas, PyMongo, Requests, and Python-dotenv.

**Key Features:**
- Integration with Gemini and Ollama.
- Input and output token tracking.
- Response latency measurement.
- Estimated API cost calculation.
- MongoDB usage logging.
- Request timeout and retry handling.
- Unit testing.

**Objective:** To build a reliable LLM monitoring application that tracks model performance, token consumption, estimated costs, and request failures.
