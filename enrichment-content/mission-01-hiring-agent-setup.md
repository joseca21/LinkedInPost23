# Mission 01: Get Started with the Hiring Agent

**Codename:** Operation Talent Scout
**Duration:** ~45 minutes

## Mission Brief

The first assignment is Operation Talent Scout - establishing the foundational infrastructure for an AI-powered recruitment system that will transform how organizations identify and hire top talent.

The mission is to deploy and configure a comprehensive hiring management system using Microsoft Copilot Studio. This involves importing a pre-built solution containing all the necessary data structures, then creating the first AI agent - the Hiring Agent - which will serve as the central orchestrator for all future recruitment operations.

This initial deployment establishes the solution that will be enhanced throughout the Agent Academy Operative course. This is the base of operations - the foundation upon which an entire network of specialized agents will be built in subsequent missions.

## Learning Objectives

- Understand the scenario and gain comprehensive knowledge of hiring automation challenges and solutions
- Successfully import and configure the fundamentals of a hiring management system
- Build a hiring agent that is the start of the scenario for the Agent Academy Operative track

## Prerequisites

- Copilot Studio license
- Access to a Microsoft Power Platform environment
- Administrative permissions to create solutions and agents

## Understanding the Hiring Automation Scenario

This scenario demonstrates how a company can use Microsoft Copilot Studio to improve and automate its hiring process. It introduces a system of agents that work together to handle tasks like reviewing resumes, recommending job roles, preparing interview materials, and evaluating candidates.

### Business Value

The solution helps HR teams save time and make better decisions by:

- Automatically processing resumes received via email
- Suggesting suitable job roles based on candidate profiles
- Creating job applications and interview guides tailored to each candidate
- Ensuring fair and compliant hiring practices through built-in safety and moderation features
- Collecting feedback to improve the solution

### How It Works

- A central **Hiring Agent** coordinates the process and stores data in Microsoft Dataverse
- An **Application Intake Agent** reads resumes and creates job applications
- An **Interview Prep Agent** generates interview questions and documents based on the candidate's background
- The system can be published to a demo website, allowing stakeholders to interact with it

This scenario is ideal for organizations looking to modernize their recruitment workflows using AI-powered automation, while maintaining transparency, fairness, and efficiency.

## Lab Overview

### Lab 1.1: Import Solution

1. Go to Copilot Studio
2. Select Solutions from the left navigation
3. Import the pre-configured solution containing Dataverse tables

**Components imported:**

| Display Name | Type | Description |
|--------------|------|-------------|
| Candidate | Table | Candidate information |
| Evaluation Criteria | Table | Evaluation criteria for the role |
| Hiring Hub | Model-Driven App | Application for managing the hiring process |
| Hiring Hub | Site Map | Navigation structure for the Hiring Hub app |
| Job Application | Table | Job applications |
| Job Role | Table | Job roles |
| Resume | Table | Resumes of the candidates |

### Lab 1.2: Import Sample Data

Import CSV files containing:
- Job roles data
- Evaluation criteria data

The evaluation criteria links to job roles via the Job Title field, demonstrating relational data structure in Dataverse.

### Lab 1.3: Create the Hiring Agent

1. Go to Copilot Studio
2. Select Agents > New Agent > Configure
3. Configure with:
   - **Name:** Hiring Agent
   - **Description:** Central orchestrator for all hiring activities
4. Associate with the Operative solution
5. Create the agent

## Skills Mastered

- **Scenario Understanding:** Comprehensive knowledge of hiring automation challenges and the solution architecture
- **Solution Deployment:** Successfully imported and configured the building blocks of the hiring management system
- **Agent Creation:** Built a hiring agent that serves as the central orchestrator

## Key Concepts

### Multi-Agent Architecture
The hiring system uses multiple specialized agents working together:
- Central orchestrator (Hiring Agent)
- Specialized task agents (Application Intake, Interview Prep)
- Shared data layer (Dataverse)

### Microsoft Dataverse
Used as the persistent storage layer for:
- Candidate profiles
- Job roles and requirements
- Applications and evaluations
- Resume data

### Copilot Studio Solutions
Solutions provide:
- Packaging for deployment
- Version control
- Environment portability
- Component organization

## Resources

- Microsoft Copilot Studio - Create an agent
- Microsoft Dataverse Documentation

---

*Source: Microsoft Agent Academy - Operative Curriculum, Mission 01*
