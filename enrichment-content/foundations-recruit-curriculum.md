# Foundations: Copilot Studio Recruit Curriculum

This document covers the foundational knowledge required before advancing to the Operative missions. The Recruit level establishes core concepts and environment setup for building AI agents with Microsoft Copilot Studio.

## Recruit Curriculum Overview

The Recruit track covers these essential topics:

| Module | Description |
|--------|-------------|
| Course Setup | Environment preparation and licensing |
| Introduction to Agents | Core concepts of AI agents |
| Copilot Studio Fundamentals | Platform navigation and key features |
| Create A Declarative Agent For Microsoft 365 Copilot | Building agents for M365 integration |
| Creating A Solution | Packaging and organising agent components |
| Using Prebuilt Agents | Leveraging existing agent templates |
| Create Agent From Conversation | Building agents from natural language |
| Add New Topic With Trigger | Defining conversation triggers and flows |
| Add Adaptive Cards | Rich UI components for agent responses |
| Add An Agent Flow | Backend automation with Power Automate |
| Add Event Triggers | Autonomous agent activation |
| Publish Your Agents | Deployment to production channels |
| Understanding Licensing | Copilot Studio and M365 licensing models |

Completing the Recruit curriculum earns the Recruit Badge and prepares you for the Operative level.

## Agent Academy Levels

| Level | Focus | Status |
|-------|-------|--------|
| **Recruit** | Fundamentals - building and publishing basic agents | Available |
| **Operative** | Advanced - multi-agent systems, orchestration, enterprise scenarios | Available |
| **Commander** | Expert - coming soon | Coming Soon |
| **Special Ops** | Specialist - coming soon | Coming Soon |

---

## Mission 00: Course Setup

**Codename:** Operation Deployment Ready
**Duration:** ~30 minutes

### Mission Brief

Before building your first AI agent, you need to establish a field-ready development environment. This mission outlines the systems, access credentials, and setup steps required to operate in the Microsoft 365 ecosystem.

### Objectives

- Getting a Microsoft 365 account
- Gaining access to Microsoft Copilot Studio
- (Optional) Securing a Microsoft 365 Copilot license for production publishing
- Creating a developer environment as your Copilot Studio environment
- Creating a SharePoint site to serve as a data source in later missions

### Prerequisites

- A work or school email address (personal @outlook.com, @gmail.com, etc., are not supported)
- Access to the internet and a modern browser (Edge, Chrome, or Firefox recommended)
- Basic familiarity with Microsoft 365 (signing into Office apps or Teams)
- (Optional) A credit card or billing method for paid licenses

---

### Step 1: Get a Microsoft 365 Account

Copilot Studio resides within Microsoft 365, so you need a Microsoft 365 account to access it.

**Options:**
- Use an existing work/school account
- Acquire a paid Microsoft 365 Business subscription

**For new subscriptions:**
1. Go to the Microsoft 365 Business Plans and Pricing Page
2. The cheapest option is Microsoft 365 Business Basic
3. Select "Try for free" and complete the subscription form
4. Login with your new account

**Important:** If you plan to publish agents into Microsoft 365 Copilot Chat or connect to organisational data (SharePoint, OneDrive, Dataverse), a Microsoft 365 Copilot license is required as an add-on.

---

### Step 2: Start a Copilot Studio Trial

Once you have your Microsoft 365 Tenant, get access to Copilot Studio with a free 30-day trial:

1. Navigate to aka.ms/TryCopilotStudio
2. Enter your Microsoft 365 email address and select Next
3. Sign in when prompted
4. Select "Start Free Trial"

**Trial Notes:**
- The free trial provides full Copilot Studio capabilities
- Email notifications sent about trial expiration
- Trial can be extended in 30-day increments (up to 90 days of agent runtime)
- If self-service sign-up is disabled, contact your Microsoft 365 admin

---

### Step 3: Create Developer Environment

Sign up for a Power Apps Developer Plan to create a free development environment for building and testing with Copilot Studio.

1. Sign up on the Power Apps Developer Plan website
2. Enter your email address
3. Tick the checkbox and select "Start free"
4. After signing up, you'll be redirected to Power Apps
5. The environment uses your name (e.g., "Adele Vance's environment")

**Use this developer environment in Copilot Studio when completing labs.**

**Note:** If using an existing Microsoft 365 account from your organisation, your IT administrator may have disabled the sign-up process. Contact your administrator or create a test tenant.

---

### Step 4: Create SharePoint Site

A SharePoint site serves as a data source for grounding agents in later missions.

1. Select the waffle icon in Microsoft Copilot Studio to view the menu
2. Select SharePoint from the menu
3. Select "+ Create site"
4. Choose "Team site"
5. Scroll down and select the "IT help desk" template
6. Select "Use template"

**Site Configuration Example:**

| Field | Value |
|-------|-------|
| Site name | Contoso IT |
| Site description | Copilot Studio for Beginners |
| Site address | ContosoIT |

7. Leave Language as English and select "Create site"
8. Optionally add other users
9. Select "Finish"
10. Copy the SharePoint site URL for future reference

**Template Contents:**
- Pages with sample data about IT policies
- Two sample lists: Tickets and Devices

---

### Step 5: Configure Devices SharePoint List

The Devices list is used in Mission 07. Configure it with sample data:

**Add Image Column:**
1. Scroll to the far right in the Devices list
2. Select "+ Add column"
3. Choose hyperlink type
4. Enter "Image" for the column name
5. Select "Add"

**Required Fields for Sample Data:**
- Device photo
- Title
- Status
- Manufacturer
- Model
- Asset Type
- Colour
- Serial Number
- Purchase Date
- Purchase Price
- Order #
- Image (hyperlink)

Add at least 4 sample device items (Surface Laptop 13, Surface Laptop 15, Surface Pro, Surface Studio).

---

### Mission Complete

After completing Mission 00, you have:

- Set up a Microsoft 365 dev environment
- Activated your Copilot Studio trial
- Created a SharePoint site for grounding agents
- Populated the Devices list for use in future missions

You're officially cleared to begin Recruit-level agent training.

---

## Key Concepts Introduced

### What is Copilot Studio?

Microsoft Copilot Studio is a low-code platform for building AI agents that can:
- Engage in natural language conversations
- Connect to organisational data sources
- Execute automated workflows
- Integrate with Microsoft 365 applications

### Environment Types

| Environment | Purpose |
|-------------|---------|
| Developer Environment | Free sandbox for building and testing |
| Production Environment | Live deployment for end users |
| Sandbox Environment | Testing before production |

### Data Sources for Agents

Agents can be grounded in various data sources:
- **SharePoint** - Documents, lists, and pages
- **Dataverse** - Structured business data
- **OneDrive** - Personal and shared files
- **External APIs** - Third-party systems via connectors

### Licensing Overview

| License | Capabilities |
|---------|--------------|
| Copilot Studio Trial | Full capabilities for 30-90 days |
| Copilot Studio Paid | Production agent deployment |
| Microsoft 365 Copilot | Required for M365 Copilot Chat publishing and organisational data access |

---

## Progression Path

```
Recruit (Foundations)
    ↓
Operative (Multi-Agent Systems)
    ↓
Commander (Coming Soon)
    ↓
Special Ops (Coming Soon)
```

The Recruit curriculum provides the essential foundation for understanding how agents work, how to build them in Copilot Studio, and how to deploy them. The Operative level builds on this by introducing multi-agent orchestration, advanced instructions, and enterprise-grade automation scenarios.

---

*Source: Microsoft Agent Academy - Recruit Curriculum*
