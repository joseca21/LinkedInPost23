# Foundations: Copilot Studio Recruit Curriculum

---

## SECTION 1: SUMMARY

This section provides a condensed overview of the Recruit curriculum for quick reference.

### Recruit Curriculum Overview

The Recruit track is the foundational level of Microsoft's Agent Academy, covering 13 essential modules:

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

### Agent Academy Progression

| Level | Focus | Status |
|-------|-------|--------|
| **Recruit** | Fundamentals - building and publishing basic agents | Available |
| **Operative** | Advanced - multi-agent systems, orchestration, enterprise scenarios | Available |
| **Commander** | Expert | Coming Soon |
| **Special Ops** | Specialist | Coming Soon |

### Mission 00 Summary: Course Setup

**Codename:** Operation Deployment Ready
**Duration:** ~30 minutes

**Key Steps:**
1. Get a Microsoft 365 account (Business Basic minimum)
2. Start a Copilot Studio trial (30-day free, extendable to 90 days)
3. Create a developer environment via Power Apps Developer Plan
4. Create a SharePoint site using the IT help desk template
5. Configure the Devices list with sample data

**Key Concepts Introduced:**
- Copilot Studio as a low-code AI agent platform
- Environment types (Developer, Production, Sandbox)
- Data sources for grounding agents (SharePoint, Dataverse, OneDrive)
- Licensing tiers (Trial, Paid, M365 Copilot add-on)

**Prerequisites:**
- Work or school email (not personal accounts)
- Modern browser
- Basic Microsoft 365 familiarity

---

## SECTION 2: VERBATIM CONTENT

This section contains the original source material in its complete form.

---

### Recruit Curriculum Modules

Course Setup

Introduction to Agents

Copilot Studio Fundamentals

Create A Declarative Agent For Microsoft 365 Copilot

Creating A Solution

Using Prebuilt Agents

Create Agent From Conversation

Add New Topic With Trigger

Add Adaptive Cards

Add An Agent Flow

Add Event Triggers

Publish Your Agents

Understanding Licensing

Course Completion Badge Recruit

Operative
Commander (Coming Soon)

Special Ops (Coming Soon)

---

### 🚨 Mission 00: Course Setup

🕵️‍♂️ CODENAME: OPERATION DEPLOYMENT READY

⏱️ Operation Time Window: ~30 minutes

#### 🎯 Mission Brief

Welcome to the first mission of your training as a Copilot Studio Agent.
Before you can start building your first AI agent, you need to establish your field-ready development environment.

This briefing outlines the systems, access credentials, and setup steps required to successfully operate in the Microsoft 365 ecosystem.

#### 🔎 Objectives

Your mission includes:

- Getting a Microsoft 365 account
- Gaining access to Microsoft Copilot Studio
- (Optional) Securing a Microsoft 365 Copilot license for production publishing
- Creating a developer environment as your Copilot Studio environment to build in
- Creating a SharePoint site to serve as your data source in later missions

#### 🔍 Prerequisites

Before you begin, ensure you have:

- A work or school email address (personal @outlook.com, @gmail.com, etc., are not supported).
- Access to the internet and a modern browser (Edge, Chrome, or Firefox recommended).
- Basic familiarity with Microsoft 365 (for example, signing into Office apps or Teams).
- (Optional) A credit card or billing method if you plan to purchase paid licenses.

#### Step 1: Get a Microsoft 365 Account

Copilot Studio resides within Microsoft 365, so you need a Microsoft 365 account to access it. You can either use an existing account if you have one or follow these steps to get an appropriate license:

**Acquire a Paid Microsoft 365 Business Subscription**

Go to the Microsoft 365 Business Plans and Pricing Page
The cheapest option to get you started is the Microsoft 365 Business Basic plan. Select Try for free and walk through the guided form to fill in your subscription and account details and payment information.

Once you have your new account, login.

TIP: If you plan to publish agents into Microsoft 365 Copilot Chat or connect to organizational data (SharePoint, OneDrive, Dataverse), a Microsoft 365 Copilot license is required. This is an add-on license which you can learn more about on the licensing site

#### Step 2: Start a Copilot Studio Trial

Once you have your Microsoft 365 Tenant, you need to get access to Copilot Studio. You can get a free 30 day trial by following these steps:

1. Navigate to aka.ms/TryCopilotStudio.
2. Enter the email address from the new account you configured in the previous step and select Next.
3. It should recognize your account. Select Sign In.
4. Select Start Free Trial.

**Trial Notes**

- The free trial provides full Copilot Studio capabilities.
- You will receive email notifications about your trial expiration. You can extend the trial in 30-day increments (up to 90 days of agent runtime).
- If your tenant administrator disabled self-service sign-up, you'll see an error—contact your Microsoft 365 admin to re-enable it.

#### Step 3: Create new developer environment

**Sign up for a Power Apps Developer Plan**

Using the same Microsoft 365 tenant in Step 1, sign up for a Power Apps Developer Plan to create a free development environment to build and test with Copilot Studio.

1. Sign up on the Power Apps Developer Plan website.
2. Enter your email address
3. Tick the checkbox
4. Select Start free

After signing up for the Developer Plan, you'll be redirected to Power Apps. The environment uses your name, for example Adele Vance's environment. If there's already an environment with that name, the developer new environment is named Adele Vance's (1) environment.

Use this developer environment in Copilot Studio when completing the labs.

NOTE: If you are using an existing Microsoft 365 account and did not create one in Step 1, for example - using your own account in your work organization, your IT administrator (or the equivalent) team who manages your tenant/environments might have turned off the sign up process. In this case, please contact your administrator, or create a test tenant as per Step 1.

#### Step 4: Create new SharePoint site

A new SharePoint site needs to be created which will be used in Lesson 06.

1. Select the waffle icon on the top left hand side of Microsoft Copilot Studio to view the menu. Select SharePoint from the menu.
2. SharePoint will load. Select + Create site to create a new SharePoint site.
3. A dialog will appear to guide you in creating a new SharePoint site. Select Team site.
4. In the next step, a list of Microsoft templates will load by default. Scroll down and select the IT help desk template.
5. Select Use template to create a new SharePoint site using the IT help desk template.

Enter information for your site. The following is an example:

| Field | Value |
|-------|-------|
| Site name | Contoso IT |
| Site description | Copilot Studio for Beginners |
| Site address | ContosoIT |

6. In the final step, a language can be selected for the SharePoint site. By default it will be English. Leave the Language as English and select Create site.
7. The SharePoint site will provision for the next few seconds. In the mean time, you can choose to add other users to your site by entering their email address in the Add members field. When completed, select Finish.
8. The SharePoint site home page will next load. Copy the SharePoint site URL.

This template provides pages with sample data about various IT policies and two sample lists (Tickets and Devices).

#### Use Devices SharePoint list

We will use the Devices list for in Mission 07.

**Add new column**

Scroll to the far right in the list and select the + Add column button. Choose the hyperlink type, enter Image for the column name, and select add.

**Create sample data in Devices SharePoint list**

You need to make sure you fill in this list with at least 4 sample data items and add one additional column to this list.

When adding sample data, make sure that the following fields are filled out:

- Device photo - use the images from the device images folder
- Title
- Status
- Manufacturer
- Model
- Asset Type
- Color
- Serial Number
- Purchase Date
- Purchase Price
- Order #
- Image - use the following links

| Device | URL |
|--------|-----|
| Surface Laptop 13 | https://raw.githubusercontent.com/microsoft/agent-academy/refs/heads/main/docs/recruit/00-course-setup/images/device-images/Surface-Laptop-13.png |
| Surface Laptop 15 | https://raw.githubusercontent.com/microsoft/agent-academy/refs/heads/main/docs/recruit/00-course-setup/images/device-images/Surface-Laptop-15.png |
| Surface Pro | https://raw.githubusercontent.com/microsoft/agent-academy/refs/heads/main/docs/recruit/00-course-setup/images/device-images/Surface-Pro-12.png |
| Surface Studio | https://raw.githubusercontent.com/microsoft/agent-academy/refs/heads/main/docs/recruit/00-course-setup/images/device-images/Surface-Studio.png |

#### ✅ Mission Complete

You've successfully:

- Set up a Microsoft 365 dev environment
- Activated your Copilot Studio trial
- Created a SharePoint site for grounding agents
- Populated the Devices list for use in future missions

You're officially cleared to begin your Recruit-level agent training in Lesson 01.

---

*Source: Microsoft Agent Academy - Recruit Curriculum*
