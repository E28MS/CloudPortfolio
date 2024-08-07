
# Project v1.0

## Introduction
In recent months, I have learned a lot about the cloud and applied this knowledge to relatively small assignments. This will all come together in the next big assignment where I will improve and automate an existing architecture.

In the coming weeks, I will work on solutions for Azure.  This project was originally designed to be completed as part of a team but not included in our Techgrounds Cloud Engineering course.  I decided that this would enhance my portfolio and showcase my skills, so I will be doing this project solo. 


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

# Additional Requirements

The customer wants to utilize more features of the cloud. Additionally, the customer has indicated that they would like to adhere to more security best practices that are not yet implemented in the current version. Together with the consultant, the customer has outlined the following:

- The web server should no longer be accessible "naked" on the internet. Ideally, the customer wants a proxy in between. Also, the server should no longer have a public IP address.
- If a user connects to the load balancer via HTTP, the connection should automatically be upgraded to HTTPS.
- The connection must be secured with at least TLS 1.2 or higher.
- The web server must undergo regular health checks.
- If the web server fails this health check, the server should be automatically restored.
- If the web server comes under sustained load, a temporary extra server should be started. The customer believes that no more than 3 servers will ever be needed given the number of users in the past.

**Note:** Because we do not want to purchase a domain name for everyone, it is difficult to establish an HTTPS connection correctly. You may use a self-signed certificate for this purpose. You will get a warning in your browser, but the connection will be encrypted.

# Deliverables

The following items must be delivered for version 1.1 of your application:

- Updated versions of the following documents:
  - Architecture diagram
  - The justification for the new services used in the design document
  - An MVP of version 1.1

- Ongoing:
- 
Most participants use about €30-40 for the entire project. There is an absolute maximum of €50 per participant. If you exceed this, the project will be stopped immediately.

## How will I work?
During the original 
 
  
## Definition of Done
When is a user story finished?
- If the user story has a deliverable: when it is on GitHub.
- If the user story is about a piece of IaC: when it can be deployed in isolation without errors.
- When the documentation about the user story is updated on GitHub.

When is a version of the app finished?
- v1.0: When it meets all the requirements as stated in this document.
- v1.1: When it meets all the new requirements.

## Deliverables
I will produce the following deliverables in my GitHub repository at the end of this project:
- A working Bicep app of the MVP
- Design Documentation
- Decision Documentation
- Time logs

### Working application of the MVP
The working application must successfully complete a build and a deployment. A version of your MVP must be easy to identify. This can be done with a tag or a release. Additionally, your repository should contain documentation on how to use the application. This includes how to invoke the application, the required arguments, and the necessary permissions in Azure to deploy.

### Design Documentation
You will use the existing architecture. However, there are still details that need to be further developed. In this document, you will fill in the gaps and eventually mention the practical and technical information on GitHub. This document will contain information about your chosen (N)SG rules, as well as a visualization of what and in what order your application deploys in the cloud. In v1.1, you will also place your own diagrams here to substantiate the adjustments and improvements.

## Time Logs
This is a file where I systematically keep track of my days. I will indicate in a single sentence what I worked on that day. Point by point, I will note the obstacles I encountered and the solutions I found. 

##  Existing Architecture diagrams

[Existing Architecture](C:\Users\elmar\OneDrive\Cloud Engineering Course 2024\Additional Projects\Infrastructure diagrams  from Techground Project\AzureArchitecture.png)

[Architecture Diagram](C:\Users\elmar\OneDrive\Cloud Engineering Course 2024\Additional Projects\Infrastructure diagrams  from Techground Project\AzureArchitecture.png)




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

  


