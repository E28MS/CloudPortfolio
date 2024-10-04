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

[Workflow Expression Functions in Azure Logic Apps and Power Automate](https://learn.microsoft.com/en-us/azure/logic-apps/workflow-definition-language-functions-reference)

###  Learning and Reflection

Throughout this excercise, as I gained more knowledge about Azure LogicApps and understood my project better through attempting to build the onboarder, I was more and more able to challenge the directions or solutions provided to me by ChatGPT.  For instance, every time there was a piece of information that needed to be added, ChatGPT recommended updating the final building block, my HTTP Action 1.  I realised that this is non-sensical as this would mean that every time I wanted to create a new user, I would need to go to this step and manually adjust the information.  Instead, I build my onboarder so that all the information could be added in Postman and from there on be made available and used throughout the LogicApp.  This realisation really boosted my confidence and pushed me to explore further.

I learned that for each operation that involves creating or assigning something in Entra ID, I need to make a seperate Graph API call to Entra ID. 

I learned that instead of creating seperate HTTP actions for the above, I could batch my requests into a single HTTP action.

###  Difficulties and Troubleshooting

##  Getting stuck on step 2:
I had persistant difficulties getting past Step 2 as I couldn't get a trigger  to connect succesfully with Entra ID to create a new user.  I kept getting an error message that stated that I needed a work or school account to make the connection.

Steps I took to resolve this:
*  I tried to use different triggers.(HTTP, Gmail, Outlook)

*  I registered the Logic App in Entra ID, granting User.Read.Write.All and Admin Priveleges (see Includes for details)


Solutions:
After scrutinizing my app from start to finish, I realised that I was using an HTTP action instead of an HTTP Trigger as the first building block of my logic app.  

##  BadRequest Error:
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

When I added the permsissions above, and included  Group.Create, I got the following information in the Status of the API Permissions:

![image](https://github.com/user-attachments/assets/e9b4dc2a-dd58-4f57-81cf-3efc1ce853a5)

Which I resolved by Granting Admin Permissions:

![image](https://github.com/user-attachments/assets/d354d82f-0bd3-493e-be00-22b62d3c3432)

Then I was back to the BadError message and I spent some time until I established the following:

The issue you're encountering in the code is that the body part of your HTTP action is being treated as a string, and the dynamic expressions like @{triggerBody()...} are not being interpreted properly. These expressions should be outside of the quotation marks to allow Logic Apps to parse them.

Fixing the code allowed me to progress and get back to the Forbidden error, which turned out be because I had granted my User.ReadWrite.All permission as Delegated instead of Application.  

After I resolved this, the next error was this:  userPrincipalName (UPN) you are trying to assign to the new user is not valid because it does not belong to a verified domain in your Azure Active Directory (AAD).

###  Domain Name issues
Another error I encountered lead me to realise that in order to create the user, they needed to be linked to my domain name.


Solutions:
I resolved this by ensuring that their email account was linked to my domain name and this resolved the error.

###  Unauthorised error

In order to create the new user with their groups and roles incuded from the beginning, I built another LogicApp for a different user.  This allowed me to really understand the process, the errors and how everything fits together.  This went smoothly until the final HTTP action, where I got an Unauthorised error.  This seems to be linked to the token I got in Step 2, so I focussed my troubleshooting on how to resolve this. 



## Outcomes

Here I created a new user, using my Automatic Onboarder:




Here are the details of the new user, which raises an issue as her groups don't seem to have been created:

![image](https://github.com/user-attachments/assets/ffcf6a99-4b0c-400b-a7c5-ae0001ce5346)



##  Summary of Steps:
###  HTTP Trigger (User data from Postman).

Here I set up the HTTP Trigger and added the details of the user I wanted to create in Postman:

![image](https://github.com/user-attachments/assets/f8a29f6d-4735-4da4-bbbe-47c2fec3e17a)

The payload from Postman then populates the body of the HTTP Trigger when an HTTP request is received.  So I copied the URL from the HTTP Trigger and used this for Postman to send its payload to the trigger, thereby passing the payload to the body of the HTTP trigger.

###  Parse JSON
In order to parse the JSON from Postman so the information could be used, next I added a Parse JSON action.  Here is the Schema that I used:

{
  "type": "object",
  "properties": {
    "userName": {
      "type": "string"
    },
    "displayName": {
      "type": "string"
    },
    "userEmail": {
      "type": "string"
    },
    "userRoles": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "userGroups": {
      "type": "array",
      "items": {
        "type": "string"
      }
    }
  }
}
 




###  HTTP Action (Get access token from Azure AD).

This first HTTP action is used to connect to Entra ID and get the access token.

![image](https://github.com/user-attachments/assets/92461d63-f3e0-4085-bb52-1306fd8cb017)


###  Parse JSON (Extract access token).

The Parse JSON is used to get the access token from the body of the previous HTTP Acton 

![image](https://github.com/user-attachments/assets/cee072cb-9397-44d2-b1e7-5b9b02e4ec2f)



HTTP Action (Use Microsoft Graph API to create the user).

###  Here I set up the next HTTP action , using Microsoft Graph API to create the new user:

![image](https://github.com/user-attachments/assets/7fc528d5-b8c0-4a85-b419-5f7efd0948ec)


In order to complete the above, I had to register my app in Graph Api to grant permissions to my app and also to get the Client ID and Secret that I will require later:

![image](https://github.com/user-attachments/assets/7c43945b-e82c-406b-95c0-91b73240e666)
