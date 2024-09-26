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

##  Getting stuck on step 2:
I had persistant difficulties getting past Step 2 as I couldn't get a trigger  to connect succesfully with Entra ID to create a new user.  I kept getting an error message that stated that I needed a work or school account to make the connection.

Steps I took to resolve this:
*  I tried to use different triggers.(HTTP, Gmail, Outlook)

*  I registered the Logic App in Entra ID, granting User.Read.Write.All and Admin Priveleges (see Includes for details)


Solutions:
After scrutinizing my app from start to finish, I realised that I was using an HTTP action instead of an HTTP Trigger as the first building block of my logic app.  

##  BedRequest Error:
After adding the next HTTP Action (1), I get getting a BadRequest error.  This seemed to have something to do with the way I structured the user information I entered in Postman and how that then gets interpreted by by the LogicApp.  

Here is the inputs from the HTTP 1 Action:

{
    "uri": "https://graph.microsoft.com/v1.0/users",
    "method": "POST",
    "headers": {
        "Authorization": "*sanitized*",
        "Content-Type": "application/json"
    },
    "body": {
        "accountEnabled": true,
        "displayName": "EsmeraldaWeatherwax",
        "mailNickname": "EsmeraldaWeatherwax",
        "userPrincipalName": "Esmeralda.Weatherwax@example.com",
        "passwordProfile": {
            "forceChangePasswordNextSignIn": true,
            "password": "DefaultPassword123!"
        }
    }
}

Solutions:
Firstly, I tried to clarify in my mind what the error was.  Using the JSON schemas from Postman and the LogicApp to compare was very useful here.

##  Forbidden Error
The BadRequest error sooned deteriorated into a Forbidden error, so I went back through to check the permissions provided earlier for my LogicApp in Entra ID.  Specifically, I wanted to check if I granted Group.ReadWrite.All and Directory.ReadWrite.All, as I know that I granted User.ReadWrite.All.

I found that I didn't previously assign anything apart from User.ReadWrite.All:

![image](https://github.com/user-attachments/assets/d57f7984-8038-4744-9323-1a0f280842d4)

But searching for Group.ReadWrite.All and Directory.ReadWrite.All didn't bring these options up.  So back to the drawing board.


## Outcomes

##  Summary of Steps:
###  HTTP Trigger (User data from Postman).

Here I set up the HTTP Trigger and added the details of the user I wanted to create in Postman:

![image](https://github.com/user-attachments/assets/f8a29f6d-4735-4da4-bbbe-47c2fec3e17a)




###  HTTP Action (Get access token from Azure AD).

This first HTTP action is used to connect to Entra ID and get the access token.

![image](https://github.com/user-attachments/assets/92461d63-f3e0-4085-bb52-1306fd8cb017)


###  Parse JSON (Extract access token).

The Parse JSON is used to get the access token from the body of the previous HTTP Acton 

![image](https://github.com/user-attachments/assets/cee072cb-9397-44d2-b1e7-5b9b02e4ec2f)



HTTP Action (Use Microsoft Graph API to create the user).

###  Here I set up the next HTTP action , using Microsoft Graph API to create the new user:

![image](https://github.com/user-attachments/assets/7fc528d5-b8c0-4a85-b419-5f7efd0948ec)
