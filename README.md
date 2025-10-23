# Advanced CLI Chatbot

A multi-topic conversational AI chatbot with memory, factual knowledge, Wikipedia integration, and transformer-based response generation. Built using Flan-T5 Large, it can engage in general conversation, answer factual queries, tell jokes, and maintain context across multiple topics.

# Features

Multi-topic memory: Tracks and summarizes conversations per topic.

Knowledge base: Quick answers for capitals, AI/ML facts, and general knowledge.

Fuzzy matching: Handles typos in countries or keywords.

Fun & personality responses: Jokes and friendly interactions.

Wikipedia fallback: Provides answers for unknown queries.

Transformer-based response generation: Uses Flan-T5 for intelligent, human-like answers.

# Project Structure
advanced-cli-chatbot/
│
├── chatbot.py           # Main script to run CLI chatbot
├── README.md            # Project documentation
├── requirements.txt     # Python dependencies
└── assets/    

# Installation
Google Colab (Recommended for Large Models)
!pip install transformers sentencepiece wikipedia --quiet

Local Setup (VS Code or IDE)

Python 3.9+

PyTorch with GPU support for faster model inference

Install dependencies:

pip install transformers sentencepiece wikipedia

# Usage
Run Chatbot
from chatbot import run_chatbot  # or your main script name

run_chatbot()

Commands

/exit → Exit the chatbot

Type your questions, greetings, or requests to interact

# Code Overview
1. Model Loader

Loads Flan-T5 Large for response generation.

Handles prompts and generates answers.

model = ModelLoader()
model.generate("Explain AI in simple words.")

2. Multi-Topic Memory

Tracks conversations per topic and summarizes old turns.

memory = MultiTopicMemory(model)
memory.add_turn("What is Python?", "Python is a programming language.")

3. Knowledge Base

Quick access to facts and capitals.

FACTS["machine learning"]
# Output: "Machine Learning (ML) is a branch of AI ..."
CAPITALS["france"]
# Output: "Paris"

4. Helper Functions

Detect greetings, jokes, or personality questions.

Handle fuzzy matching for typos.

detect_greeting("Hello!")
fuzzy_country_lookup("Uited Stattes")  # Returns "usa"

5. Query Handling

Handles factual queries, follow-ups, and Wikipedia fallback.

query_fact("What is the capital of India?", memory)
# Output: "The capital of India is New Delhi."

6. Bot Response

Combines memory, knowledge base, fun responses, and model generation.

bot_response = get_bot_response("Tell me a joke", model, memory)

7. CLI Loop

Interactive command-line interface.

You: Hi
Bot: Hello! How can I help you today?

💡 Example Conversations

Greeting

You: Hi
Bot: Hello! How can I help you today?


Fact Query

You: Tell me about Python
Bot: Python is a versatile programming language widely used for AI, machine learning, web development, and automation.


Capital Query

You: What is the capital of Italy?
Bot: The capital of Italy is Rome.


Follow-up Question

You: And what about Germany?
Bot: The capital of Germany is Berlin.


Fun / Joke

You: Tell me a joke
Bot: Why did the AI cross the road? To optimize its loss function!


Wikipedia + AI

You: Who is Ada Lovelace?
Bot: Ada Lovelace was a 19th-century mathematician and writer, known for her work on Charles Babbage's early mechanical general-purpose computer, the Analytical Engine...

# Why Google Colab?

Free GPU/TPU support for faster model inference

Handles large models like Flan-T5 without memory issues

Easy package installation and collaboration

VS Code is better for production or app deployment, Colab is better for experimentation

