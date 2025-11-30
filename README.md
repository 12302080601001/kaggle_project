# Real-Time Investment Advisor: AutoGen Data Streams 📈🤖



> **A Multi-Agent System that acts as a dynamic financial expert, refining investment strategies in real-time as market news streams in.**

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![AutoGen](https://img.shields.io/badge/Microsoft-AutoGen-purple)](https://microsoft.github.io/autogen/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

## 📖 Overview

Most Large Language Model (LLM) interactions are static: you ask a question, and you get an answer based on the current context. But in the real world—especially in finance—information is constantly flowing.

This project, built for the **Kaggle AI Agents Capstone**, demonstrates an **Agentic Workflow** that breaks the traditional "request-response" cycle. It uses **Microsoft AutoGen** to create a listening agent that continuously consumes an asynchronous stream of market news, proactively interrupting the user to update its investment advice based on new sentiment and data.

## ✨ Key Features

* **Asynchronous Data Injection:** Implements a custom event loop that injects external data (news) into an active conversation without breaking the chat context.
* **Multi-Agent Architecture:**
    * **UserProxy Agent:** Acts as the bridge between the news stream and the expert.
    * **Assistant Agent:** A "Financial Expert" persona that analyzes text and synthesizes strategies.
* **Dynamic Context Merging:** The agent doesn't just react to the *latest* news; it merges new findings with *previous* advice to create a holistic strategy.
* **Simulated Market Environment:** Includes a simulation engine to generate stock prices, news headlines, and sentiment scores for testing purposes.

## 🏗️ Architecture

The system utilizes a dual-agent setup wrapped in an asynchronous loop:

1.  **The Stream:** A background process simulates live market news (e.g., "Nvidia earnings report," "Deepfake regulations").
2.  **The Interceptor:** The `UserProxyAgent` checks this stream via a custom registered reply function.
3.  **The Synthesis:** When relevant news is detected, the `AssistantAgent` is triggered to re-evaluate the portfolio, explaining *why* the advice changed based on the new data.

## 🚀 Getting Started

### Prerequisites

* Python 3.8 or higher
* An OpenAI API Key (or compatible local LLM endpoint)

### Installation

  **Install dependencies:**
    ```bash
    pip install pyautogen pandas
    ```

### Configuration

You need to configure your LLM provider. Create a file named `OAI_CONFIG_LIST` or export your key as an environment variable:

```python
export OPENAI_API_KEY="sk-..."
