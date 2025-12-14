# Agentic Field Compliance Engine

> **Agentic Governance Architecture:** A serverless reference pattern using AWS Bedrock and Guardrails to automate visual safety compliance and Human-in-the-Loop auditing for field operations.

## 📋 Executive Summary
This project demonstrates a **Governance-First AI Architecture** designed for Field Service operations. It moves beyond simple chatbots to create an **Action-Oriented Agent** capable of auditing hardware installations visually.

By leveraging **AWS Bedrock Agents** and **Guardrails**, this solution enforces deterministic safety policies (e.g., "Ground wire must be green") that cannot be overridden by hallucination, bridging the gap between Generative AI flexibility and Enterprise Compliance requirements.

## 🏗️ Architecture Design

The solution follows an **Event-Driven Serverless** pattern to minimize idle costs while maintaining high scalability.

```mermaid
graph LR
    User[Field Tech (Streamlit)] -->|Upload Photo| API[Boto3 / API Gateway]
    API -->|Invoke| Agent[AWS Bedrock Agent]
    Agent -->|Reasoning| Model[Claude 3.5 Sonnet]
    Agent -->|Validation| Lambda[AWS Lambda (Rules Engine)]
    Agent -->|Policy Check| Guard[Bedrock Guardrails]
    Guard -->|Approved/Blocked| User
