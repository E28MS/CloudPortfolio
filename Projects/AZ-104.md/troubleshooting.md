Step 2:

I researched to see if SharePoint was the best trigger to use for my use case and after reading the information below, decided to replace the SharePoint trigger with a Googlemail trigger instead. I learnt that there are multiple ways to trigger the LogicApp:

Alternatives to SharePoint for Triggering a Logic App
Microsoft Logic Apps offers a wide range of connectors and triggers that can be used in place of SharePoint:

Email Triggers:

Outlook.com: You can use a trigger like "When a new email arrives" in your Outlook.com inbox. If you receive an email with specific details (like a new employee hire), it can trigger the Logic App workflow.
Gmail: Similar to Outlook, you can use a Gmail trigger if you prefer Google services.
Forms and Surveys:

Microsoft Forms: Create a form where you can manually input employee information. A new form submission can trigger the Logic App.
Google Forms: Similarly, Google Forms can be used to collect data, and responses can trigger actions via a webhook.
Manual Triggers:

Manual HTTP Request: You can create an HTTP trigger in your Logic App, which you can manually invoke whenever you need to start the workflow. This is useful if you want full control over when the workflow starts.
Button in Power Automate: You can use Power Automate's button feature to manually trigger a Logic App workflow.
File Creation/Modification:

OneDrive: Use the "When a file is created" or "When a file is modified" trigger in a specific OneDrive folder. If you save a file with employee information, this can trigger your Logic App.
Task Management Tools:

Trello: If you use Trello for task management, a new card creation can serve as a trigger.
Todoist: Adding a new task with specific labels or titles can trigger the Logic App.
Database or Spreadsheet Updates:

Google Sheets: You can set up a trigger based on changes or additions to a Google Sheet.
Excel Online (Business): If you have a Microsoft 365 subscription, you can use Excel Online, where new rows added to a spreadsheet can trigger your workflow.

### Unable to connect Outlook email account as it requires a work or school account.  

Once I've researched the problem to understand it in more details, I decided to use a Gmail trigger but this only got me to the end of step 2.  When I tried adding the Create User action through the Entra ID Connector in the LogicApp, I got the same error message stating that I couldn't log in with a personal account when I tried to create a connection between 
