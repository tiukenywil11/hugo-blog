---
title: "Project Idea 2 (AI Model): CRUD API"
date: 2025-02-15T16:55:01+08:00
tags: ["ai model", "full stack", "cursor", "python", "project idea"]
description: "Exploring the development of a simple AI model related to nutrition using an AI-powered IDE."
author: "Kenywil Tiu"
---

## **How I Started This Project Using Cursor**

As a developer constantly looking for efficient ways to speed up development, I recently started using **Cursor**, an AI-powered coding assistant, to help me streamline my backend projects. I wanted to build a **CRUD API for food profiles** using **FastAPI** while following **clean architecture principles**. Additionally, I needed **Docker support** to ensure smooth deployment and testing.

To track the development process, I recorded key timestamps and prompts, which I’ll outline below.

![Cursor IDE Intro](/img/project-idea-2-part-1/cursor-ide-intro.png)

---

## **Development Steps**

**🕒 Start Time:** 4:05 PM

📌 **Bitbucket Repository:** [nutri-sim-be](https://github.com/tiukenywil11/nutri-sim-be)

### **Step 1: FastAPI CRUD Boilerplate with Clean Architecture**
Prompt:  
`Create a CRUD FastAPI boilerplate using clean architecture for food profile.`

Cursor quickly generated a **well-structured FastAPI boilerplate**, separating concerns with:  
✅ **Routers** for API endpoints  
✅ **Services** for business logic  
✅ **Repositories** for database interactions  
✅ **Schemas** using Pydantic models  

![FastAPI CRUD Boilerplate](/img/project-idea-2-part-1/cursor-ide-prompt-1-result.png)

---

### **Step 2: Dockerizing the Application**
Prompt:  
`Create Dockerfile and docker-compose file to make startup, testing, and deployment easier.`

To ensure **consistency across environments**, I needed **Docker support**. Cursor generated a **Dockerfile** and **docker-compose.yaml**, allowing me to:
- Build a lightweight FastAPI container
- Set up a **PostgreSQL** database service
- Easily spin up the entire stack with `docker-compose up`

![Docker Setup](/img/project-idea-2-part-1/cursor-ide-prompt-2-result-2.png)

---

### **Step 3: Fixing Postgres Version Incompatibility**
Prompt:  
`Can you fix the following errors? [Postgres version incompatibility error]`

I ran into a **Postgres version mismatch** between my local environment and the Docker container. Cursor helped me adjust the **PostgreSQL version** in `docker-compose.yaml` and modify environment variables to ensure compatibility.

![Postgres Error Fix](/img/project-idea-2-part-1/cursor-ide-prompt-3-result-4.png)

---

### **Step 4: Debugging Internal Server Error (Database Issue)**
Prompt:  
`What does this error mean, can you fix it? [Internal server error, database issue]`

After running migrations, I encountered an **Internal Server Error** due to misconfigured database settings. Cursor identified the issue, suggesting:
- Updating **SQLAlchemy connection strings**
- Adjusting **Alembic migration settings**

After applying the fixes, database connections worked smoothly. 🚀

![Database Error Fix](/img/project-idea-2-part-1/cursor-ide-prompt-4-result-2.png)

---

### **Step 5: Creating a Postman Collection**
Prompt:  
`Create a Postman collection to test all endpoints.`

To simplify API testing, Cursor generated a **Postman collection** with:
- CRUD requests for the **food profile endpoints**
- Environment variables for API base URL
- Pre-configured authentication headers

This made testing much faster! ✅

![Postman Collection](/img/project-idea-2-part-1/cursor-ide-prompt-5-result-2.png)

---

### **Step 6: Fixing Type Errors in Food Profile Creation**
Prompt:  
`Can you fix this type error? [TypeError upon creating food]`

Upon testing, I encountered a **TypeError** due to incorrect data validation. Cursor helped:
- Adjust **Pydantic models** to properly parse input types
- Add **request validation handlers** to return clearer error messages

Once fixed, the API accepted and stored food profiles correctly. 🥗

![Type Error Fix](/img/project-idea-2-part-1/cursor-ide-prompt-6-result-1.png)

---

## **Final Outcome**

**🕒 End Time:** 4:47 PM  
**Total Duration:** **42 minutes** ⏳

In just **under an hour**, I successfully:
✅ Built a **FastAPI CRUD application** with clean architecture  
✅ **Dockerized** the setup for easy deployment  
✅ Resolved **database compatibility issues**  
✅ Fixed **server errors and type validation bugs**  
✅ Created a **Postman collection** for streamlined testing  

---

## **Conclusion**

Using **Cursor** significantly **accelerated my development process**, allowing me to build and debug a fully functional **FastAPI backend** in record time. Instead of manually fixing errors and writing boilerplate code, I could focus on **refining the architecture and improving performance**.

Stay tuned for more updates! 🚀

