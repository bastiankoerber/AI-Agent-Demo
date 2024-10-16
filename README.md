# Travel Agent Demo (Autonomous Agent Showcase)

This repository demonstrates an autonomous travel agent that helps users book travel. It showcases how you can leverage Large Language Models (LLM) and Camunda to build task agents and multi-agent systems. Please note that this is a demo and uses mock services for the REST endpoints. The goal is to demonstrate the concept of task agents and multi-agent orchestration, not to provide a fully functioning travel booking service. To implement a working solution, real APIs, access tokens, and schemas would need to be integrated.

## Getting Started

### Steps:
1. **Download and Import**: Import all BPMN files and forms provided in this repository into your Camunda modeler.
2. **Explore Agents**: The demo includes three types of agents:
   - **Search Agent (Task Agent)**
   - **Booking Agent (Task Agent)**
   - **Travel Agent (Multi-Agent)**

### Sidenote:
- The demo calls mockup APIs. To build a fully functional agent, you must provide access tokens, real API endpoints, and schemas for integration with live search agents.

## Requirements

- **AWS Token** for AWS Bedrock
- **Camunda 8.6+ Cluster**
- **Running Camunda Connectors (we are using AWS Bedrock and Rest Connector)** (especially for the SM connector)

## Task Agents: Search & Book Agents

These agents represent simple task agents designed to handle specific tasks based on user input:
- **Search Agent**: Handles user input and translates it into the correct API payload for search services (e.g., flight, hotel, car).
- **Booking Agent**: Follows a similar flow, translating input into the appropriate payload for booking services.
  
The agents dynamically choose the correct API based on user input and execute actions through a Camunda Connector (in this demo, the REST Connector is used). Once the APIs are executed, the agents collect and aggregate the results.

## Travel Agent (Multi-Agent)

The Travel Agent is more complex, handling an end-to-end travel booking task:
1. **Information Gathering**: The agent first checks if all required information is provided. If any information is missing, it prompts the user to provide the necessary details.
2. **Search Execution**: Once all information is gathered, the Travel Agent calls the appropriate search agents. In this example, it has customized search agents for car, hotel, and flight bookings.
3. **Recommendation**: After the search agents return their results, the Travel Agent aggregates the data based on user preferences. It presents recommendations along with reasoning behind them.
4. **User Interaction**: The user can either accept the recommendation or request changes.
5. **Booking**: Upon acceptance, the Travel Agent triggers the action agents to perform the actual bookings.

## Repository Contents

- All necessary **BPMN files** and **forms** to run the demo.
  
## Setup

### To get started:
1. Import the BPMN files and forms into your Camunda Modeler.
2. Add the following secrets to your Camunda cluster:
   - `AI_AWS_BEDROCK_SECRET_KEY`
   - `AI_AWS_BEDROCK_ACCESS_KEY`

This setup will allow you to run the demo and showcase how autonomous agents work within a process orchestration framework.

---

Enjoy exploring the autonomous agent demo!
