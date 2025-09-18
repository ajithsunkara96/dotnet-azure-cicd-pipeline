.NET Web App CI/CD on Azure

## 📌 Aim
Implement a CI/CD pipeline using **Azure DevOps** to build, test, package, and deploy a .NET 8 web application into **three environments** (Dev, Staging, Prod) on **Azure App Service**.

---

## 🎯 Objectives
- Provision three Resource Groups and App Services (`mywebapp-dev`, `mywebapp-stg`, `mywebapp-prd`).
- Store application code in **Azure Repos** (migrated here to GitHub).
- Configure an Azure DevOps **Service Connection** (App Registration in Entra ID).
- Build a multi-stage **YAML pipeline**:
  - **CI Stage:** Restore, Build, Test, Publish artifact
  - **CD Stages:** Deploy artifact sequentially to Dev → Stg → Prod
- Verify deployment via App Service endpoints and monitor with Azure metrics.

---

## 🛠 Technologies Used
- **Azure DevOps Repos** – source control (migrated to GitHub)  
- **Azure DevOps Pipelines** – multi-stage YAML pipeline  
- **Azure App Service** – PaaS hosting for .NET apps  
- **.NET 8 SDK** – application framework  
- **Azure Entra ID App Registration** – service principal authentication  

---

## 📖 Terminology
- **CI (Continuous Integration):** Build, restore packages, run tests, publish artifacts.  
- **CD (Continuous Deployment):** Automated deployments to Dev, Stg, and Prod App Services.  
- **Service Connection:** Secure credential object for Azure in DevOps.  
- **Artifact:** ZIP package of the published web project.  
- **Azure App Service:** Fully managed hosting environment for web apps.  

---

## 🚀 Pipeline Workflow
1. **Code Commit** → Triggers CI on the `main` branch.  
2. **CI Stage**:
   - Use .NET SDK 8.x
   - Restore NuGet packages
   - Build the solution
   - Run unit tests
   - Publish web project
   - Package output into a ZIP artifact
3. **Artifact Published** → Passed to CD stages.  
4. **CD Stages**:
   - Deploy to **Dev** App Service
   - Deploy to **Stg** App Service
   - Deploy to **Prod** App Service
5. **Verification**:
   - Open endpoint URLs for Dev, Stg, Prod
   - Check Azure Portal → Metrics (Requests, Response Time, Errors)

---

## 📂 Repository Structure
```text
├── src/
│   └── DotNetWebApp/
│       ├── DotNetWebApp.csproj
│       ├── Pages/
│       ├── Services/
│       └── Program.cs
├── tests/
│   └── DotNetWebApp.Tests/
│       └── GreetingServiceTests.cs
├── .gitignore
├── DotNetWebApp.sln
├── azure-pipelines.yml
└── README.md
```
Credits:

Original reference materials and code came from the following repositories:
luckysuie/Pipelines – Pipeline-15
luckysuie/dotnetwebapp

I adapted and extended these resources to implement a full CI/CD pipeline with Azure DevOps for my own learning and practice.
