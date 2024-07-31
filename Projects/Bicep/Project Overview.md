
# Project v1.0

## Introduction
In recent months, I have learned a lot about the cloud and applied this knowledge to relatively small assignments. This will all come together in the next big assignment where I will improve and automate an existing architecture.

In the coming weeks, I will work on solutions for Azure.  This project was originally designed to be completed as part of a team but I decided that this would enhance my portfolio and showcase my skills, so I will be doing this project solo. 


### What do I expect to learn in this project?
- Gain and apply new knowledge with little to no guidance
- Understand the project at an abstract level
- Solve problems independently
- Engage in discussions about technical elements with my former learning coach at Techgrounds and one of my team members that did the Cloud Engineering course with me.
- Implement improvements at both code and project levels

## Requirements
- Your GitHub repository
- Project Templates
- Your cloud environment

## Assignment
You have been tasked with helping a company transition to the cloud. The company's infrastructure was analyzed by a previous team, and a diagram was created based on the current situation. You can find these diagrams in the attachments.

You will build the Infrastructure as Code app to bring this design to the cloud. It is intended that you use Azure's Bicep for this app. The following requirements are specified as necessary:
- All VM disks must be encrypted.
- The web server must be backed up daily. Backups must be retained for 7 days.
- The web server must be installed in an automated manner.
- The admin/management server must be accessible via a public IP.
- The admin/management server should only be accessible from trusted locations (office/admin’s home).
- The following IP ranges are used: `10.10.10.0/24` & `10.20.20.0/24`.
- All subnets must be protected by a subnet-level firewall.
- SSH or RDP connections to the web server may only be made from the admin server.

In developing the Bicep app, ensure you start small and add features incrementally. Make sure you always have a commit/branch you can fall back on with a working version of your application. You can label commits with Git Tags that are easily found in GitHub. Once your code meets the requirements mentioned above, you can use the tag 'v1.0'.

Most participants use about €30-40 for the entire project. There is an absolute maximum of €50 per participant. If you exceed this, the project will be stopped immediately.

## How will we work?
The project consists of two phases. The first phase lasts 5 weeks, during which you will work on v1.0 of the application while also learning to program in Python.
The second phase of the project will introduce a change in your architecture. This simulates a situation where a client introduces new requirements into your project and will be released later.

You will work individually on your own implementation. However, you will work in teams. The following agreements apply:
- A sprint is 2 weeks, except for the first sprint, which is 3 weeks.
- Every last Friday, there is a sprint retrospective.
  - In this, the team discusses the process of the past week and improvements.
  - These improvements will be noted in the retro document. These action points are new user stories for the next sprint.
- Every last Friday, there is a sprint demo where the teams present their progress to the product owners and explain how/why the sprint goal was or was not achieved. Note: The goal of a sprint is always to show working code. So, prefer 1 fully working feature over 3 features with bugs.
- On the last Friday of the project, everyone presents the entire project to each other and possibly to the career buddies. Here you share your experience, your design decisions, and the architecture of your project.
- Each team has one scrum master.
  - The scrum master chosen in the first week carries their role for the entire project.
  - The scrum master is the first point of contact for the team. Team members from different teams should not seek each other for help. This disrupts focus.
  - Every workday at 16:00, there is a scrum master meeting of max 15 minutes. The scrum masters discuss the progress of the teams. Help can be requested and offered here.
 
  
## Definition of Done
When is a user story finished?
- If the user story has a deliverable: when it is on GitHub.
- If the user story is about a piece of IaC: when it can be deployed in isolation without errors.
- When the documentation about the user story is updated on GitHub.

When is a version of the app finished?
- v1.0: When it meets all the requirements as stated in this document.
- v1.1: When it meets all the new requirements.

## Deliverables
The following deliverables are expected in your GitHub repository at the end of this project:
- A working Bicep app of the MVP
- Design Documentation
- Decision Documentation
- Time logs
- Final presentation

### Working application of the MVP
The working application must successfully complete a build and a deployment. A version of your MVP must be easy to identify. This can be done with a tag or a release. Additionally, your repository should contain documentation on how to use the application. This includes how to invoke the application, the required arguments, and the necessary permissions in AWS or Azure to deploy.

### Design Documentation
You will use the existing architecture. However, there are still details that need to be further developed. In this document, you will fill in the gaps and eventually mention the practical and technical information on GitHub. This document will contain information about your chosen (N)SG rules, as well as a visualization of what and in what order your application deploys in the cloud. In v1.1, you will also place your own diagrams here to substantiate the adjustments and improvements.
## Time Logs
This is a file where you systematically keep track of your days. You indicate in a single sentence what you worked on that day. Point by point, you will note the obstacles you encountered and the solutions you found.

You can use the following template:

# Log [date]

## Daily Summary (1 sentence)

## Obstacles

## Solutions

## Learnings

---

## Interim Presentations
At the end of each sprint, you will create a presentation of your progress. In this, you will cover what you have done in the past sprint. At the delivery, you will show a demo of your work.

## Final Presentation
On the last Friday of the project, everyone presents the entire project to each other. Here you share your experience, your design decisions, and the architecture of your project.

## User Stories
The Product Owners have already had a meeting and have prepared the following epics and backlog. You will work on these epics and user stories as a team.
If your team identifies user stories that need to be split into smaller stories, your team is free to do so.

### The following epics apply to the project:

#### Exploration
The exploration epic is intended to make decisions about the project. Once you have completed this epic, ensure that you do not need to revisit it. You have too little time to make major adjustments.

#### v1.0
Epic v1.0 is delivering the Infrastructure as Code and all required documentation to meet the requirements you discovered during the exploration.

#### v1.1
Version 1.1 is delivering the Infrastructure as Code and all required documentation to meet the requirements that become available later.

### Here are the user stories for the epics exploration, and v1.0:

#### As a team, we want to clearly understand the application's requirements
- **Epic**: Exploration
- **Description**: You have already received a lot of information. Some requirements are mentioned in this document, but this list may be incomplete or unclear. It is important to have clarified all ambiguities before undertaking major work.
- **Deliverable**: A point-by-point description of all requirements

#### As a team, we want a clear overview of the assumptions we have made
- **Epic**: Exploration
- **Description**: You have already received a lot of information. There may be questions that none of the stakeholders have been able to answer. Your team should produce an overview of the assumptions you make as a result.
- **Deliverable**: A point-by-point overview of all assumptions

#### As a team, we want a clear overview of the Cloud Infrastructure that the application needs
- **Epic**: Exploration
- **Description**: You have already received a lot of information and a design. However, the design is missing items like IAM/AD. Identify these additional services you will need and create an overview of all services.
- **Deliverable**: An overview of all services to be used

#### As a customer, I want a working application to deploy a secure network
- **Epic**: v1.0
- **Description**: The application must build a network that meets all requirements. An example of a stated requirement is that only traffic from trusted sources should be able to access the management server.
- **Deliverable**: IaC code for the network and all components

#### As a customer, I want a working application to deploy a working web server
- **Epic**: v1.0
- **Description**: The application must start a web server and make it available to the general public.
- **Deliverable**: IaC code for a web server and all necessary components

#### As a customer, I want a working application to deploy a working management server
- **Epic**: v1.0
- **Description**: The application must start a management server and make it available to a limited audience.
- **Deliverable**: IaC code for a management server and all necessary components

#### As a customer, I want a storage solution for storing bootstrap/post-deployment scripts
- **Epic**: v1.0
- **Description**: There should be a location where bootstrap scripts are available. These scripts should not be publicly accessible.
- **Deliverable**: IaC code for a storage solution for scripts

#### As a customer, I want all my data in the infrastructure to be encrypted
- **Epic**: v1.0
- **Description**: Data security is very important, both at rest and in motion. All data must be encrypted.
- **Deliverable**: IaC code for encryption provisions

#### As a customer, I want daily backups retained for 7 days
- **Epic**: v1.0
- **Description**: The customer wants a backup available to restore the servers to a previous state if needed. (Ensure the backup actually works)
- **Deliverable**: IaC code for backup provisions

#### As a customer, I want to know how to use the application
- **Epic**: v1.0
- **Description**: Ensure that the customer can understand how to use the application. Make it clear what the customer needs to configure before starting the deployment and what arguments the program needs.
- **Deliverable**: Documentation for using the application

#### As a customer, I want to deploy an MVP for testing
- **Epic**: v1.0
- **Description**: The customer wants to test your architecture internally before using the code in production. Ensure that configuration is available for the customer to deploy an MVP.
- **Deliverable**: Configuration for deploying an MVP
## Resources:
For designing your architecture: [Draw.io](https://www.draw.io)


### Azure Documentation:
- [Azure Bicep Documentation](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/)
- [Azure ARM Template Documentation](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/overview)
- [Azure ARM Resource Descriptions](https://docs.microsoft.com/en-us/azure/templates/)

  


