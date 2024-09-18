###  Project Outline

## Onboard Automator (AZ-104 Module 1: Manage Azure identities and governance)
Streamline and automate the process of onboarding a new employee into Entra ID and assigning necessary Azure resources.

- **Programming required?**: ❌
- **Azure Services Used:**
  - Entra ID
  - Azure Logic Apps
  - Azure Email Service (part of Logic Apps connector)
  - Azure Resource Manager
  
- **Steps**:
   1. **Entra ID Setup**:
        - Set up a new Entra ID instance (if not already present) using the Azure portal.
   
   2. **Logic App Workflow Design**:
        - Design a Logic App workflow triggered by an event (like an entry in a SharePoint list or an email to a specific mailbox) indicating a new employee hire.
   
   3. **Azure AD User Creation**:
        - Use the Azure AD connector in Logic Apps to automatically create a new user in Azure AD based on the trigger event's details.
   
   4. **Role and Group Assignment**:
        - Assign predefined roles and groups to the new user based on the job position or department indicated in the trigger.
   
   5. **Resource Provisioning**:
        - Use the Azure Resource Manager connector in Logic Apps to provision any necessary Azure resources for the user (like VMs or specific permissions).
   
   6. **Welcome Email**:
        - Leverage the Email connector in Logic Apps to send a welcome email to the new hire with instructions and necessary access details.
   
   7. **Monitoring and Review**:
        - Monitor and review the onboarding process through Logic Apps runs history and Azure AD logs to ensure smooth operations.
     


###  Resources

[Learn Microsoft Process Data with Logic Apps](https://learn.microsoft.com/en-us/training/modules/route-and-process-data-logic-apps/1-introduction)

###  Difficulties and Troubleshooting

I had persistant difficulties getting past Step 2 as I couldn't get a trigger  to connect succesfully with Entra ID to create a new user.  I kept getting an error message that stated that I needed a work or school account to make the connection.

Steps I took to resolve this:
*  I tried to use different triggers.(HTTP, Gmail, Outlook)

*  I registered the Logic App in Entra ID, granting User.Read.Write.All and Admin Priveleges (see Includes for details)


Solutions:
After scrutinizing my app from start to finish, I realised that I was using an HTTP action instead of an HTTP Trigger as the first building block of my logic app.  

