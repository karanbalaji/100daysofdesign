---
title: "Day 2/100: Revolutionizing AI Agents with A2UI and Interactions API"
seoTitle: "Day 2/100: Google's A2UI & Interactions API Revolution"
seoDescription: "Discover Google's latest A2UI protocol for agent-driven UIs and Interactions API for Gemini agents. Implementation guides"
datePublished: Mon Dec 22 2025 22:39:59 GMT+0000 (Coordinated Universal Time)
cuid: cmjhqo7yx000002jlgyzs0114
slug: day-2100-revolutionizing-ai-agents-with-a2ui-and-interactions-api
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766443128103/77f5da7d-ad7f-4948-af3d-32d99fe3de64.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766443120744/05d6e978-3dd2-45f9-ae42-cc240b3c2d21.png
tags: ai, artificial-intelligence, web-development

---

In this installment of the #100DaysOfAi series, we dive into two groundbreaking advancements from Google that are reshaping how AI agents interact with users and developers. A2UI, an open-source protocol for agent-driven user interfaces, and the Interactions API, a unified foundation for models and agents, represent key steps toward more dynamic, secure, and efficient AI systems. Drawing from recent announcements and developments as of December 2025, we'll explore these technologies through their core concepts, implementation strategies, and broader significance.

## What These Concepts Are About

A2UI stands for Agent to UI, a declarative protocol designed to let AI agents generate rich, interactive user interfaces without executing arbitrary code. Launched by Google with contributions from the open-source community, including CopilotKit, it addresses a core challenge in AI: safely transmitting complex UIs across trust boundaries. Instead of plain text responses or risky code, agents send structured JSON descriptions of components, which clients render natively on web, mobile, or desktop platforms. Currently in version 0.8 and public preview, A2UI is Apache 2.0 licensed and hosted on GitHub. It emphasizes security by using pre-approved component catalogs, preventing UI injection attacks, and supports progressive rendering for real-time updates.

The Interactions API, introduced by Google DeepMind on December 11, 2025, provides a single RESTful endpoint for seamless access to Gemini models like Gemini 3 Pro and agents such as Gemini Deep Research. Available in public beta via the Gemini API in Google AI Studio, it evolves beyond simple request-response interactions. Key elements include server-side state management to handle conversation histories, background execution for long-running tasks, and support for tools like Model Context Protocol (MCP) servers. This API unifies model and agent interactions, making it easier to build agentic applications that involve thinking, tool calls, and complex histories.

Together, these tools highlight Google's push toward agentic AI, where agents not only process information but also create intuitive interfaces and manage intricate workflows. Recent developments, such as integrations with the Agent Development Kit (ADK) and expansions to more built-in agents, underscore their rapid evolution.

### Key Features of A2UI

A2UI's design focuses on LLM-friendliness with a flat, streaming JSON format, framework-agnostic rendering (e.g., via Angular or Flutter), and custom components like interactive charts or maps.

### Key Features of Interactions API

It offers interpretable data models for debugging, optional server-side caching to reduce costs, and composability for manipulating agent histories.

## How to Implement Them with Practical Examples and Use Cases

Implementing A2UI starts with integrating its protocol into an AI agent workflow. Developers can clone the GitHub repository and use provided renderers for client-side implementation. For instance, in a web app built with React, you define a component catalog and parse incoming A2UI JSON messages to render elements like buttons or forms.

A practical example is the Landscape Architect Demo: Upload a photo to an agent powered by Gemini, which analyzes it and streams A2UI messages to generate an interactive UI with design suggestions, sliders for adjustments, and real-time previews. In code, this involves the agent generating a JSON structure like {"component": "slider", "props": {"min": 0, "max": 100}} and the client rendering it natively.

Use cases include enterprise applications where agents guide users through complex tasks, such as data visualization in business dashboards or interactive tutorials in educational tools. For mobile apps, Flutter integration allows the same A2UI descriptions to render on iOS and Android, ensuring consistency.

For the Interactions API, access begins with a Gemini API key from Google AI Studio. Use the /interactions endpoint in your code, specifying either a model or agent parameter.

In Python, a simple implementation for a model query might look like this:

```python
import google.generativeai as genai

client = genai.GenerativeModel('gemini-3-pro-preview')
interaction = client.interactions.create(
    model="gemini-3-pro-preview",
    input="Who won the last Euro?",
    tools=[{"type": "google_search"}]
)
print(interaction)
```

For agents, enable background execution for research tasks:

```python
interaction = client.interactions.create(
    agent="deep-research-pro-preview-12-2025",
    input="Research the history of Google TPUs.",
    background=True
)
```

Poll for results later, ideal for apps handling long-horizon tasks without keeping connections open.

Use cases span developer tools, such as embedding Gemini Deep Research in custom apps for automated report generation on topics like quantum computing or market analysis. In production, it simplifies state management for chatbots or virtual assistants, reducing errors and costs through caching.

Combining both: Use Interactions API to orchestrate an agent that outputs A2UI messages, enabling end-to-end agentic UIs. For example, a travel planning app could research destinations via the API and render interactive maps via A2UI.

## Why These Are Important

A2UI and the Interactions API are pivotal because they bridge gaps in current AI ecosystems. A2UI enhances user experience by moving beyond text walls to interactive, secure UIs, fostering trust in agent-driven systems. This is crucial as AI agents proliferate in sensitive areas like healthcare or finance, where security and usability are paramount.

The Interactions API streamlines development for agentic apps, addressing limitations in stateless models by handling complexity on the server. With AI shifting toward autonomous agents capable of multi-step reasoning, this API lowers barriers for developers, potentially accelerating innovations like personalized education or advanced research tools.

In the broader AI landscape, these advancements promote open standards and collaboration, as seen in A2UI's community contributions and the API's integration with protocols like A2A. As of late 2025, with Gemini's expansions into products like Google Search and NotebookLM, they signal a future where AI agents become integral infrastructure, driving efficiency and creativity across industries.

Sources:

* A2UI Official Site: [https://a2ui.org/](https://a2ui.org/)
    
* Google Interactions API Blog: [https://blog.google/technology/developers/interactions-api/](https://blog.google/technology/developers/interactions-api/)
    
* A2UI GitHub Repository: [https://github.com/google/A2UI](https://github.com/google/A2UI)
    
* Gemini API Documentation: [https://ai.google.dev/gemini-api/docs/interactions](https://ai.google.dev/gemini-api/docs/interactions)
    
* Building Agents with ADK and Interactions API: [https://developers.googleblog.com/building-agents-with-the-adk-and-the-new-interactions-api/](https://developers.googleblog.com/building-agents-with-the-adk-and-the-new-interactions-api/)