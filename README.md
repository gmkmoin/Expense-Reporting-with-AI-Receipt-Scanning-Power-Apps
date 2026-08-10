🧾 Expense Reporting with AI Receipt Scanning – Power Apps
📌 Project Overview

The Expense Reporting App is a Microsoft Power Apps Canvas application designed to simplify and automate the employee expense reporting and approval process.

The application allows employees to create expense reports, add multiple expense line items, upload receipts, extract receipt information using AI Builder, and submit completed expense reports for approval.

The approval process is automated using Power Automate, with the appropriate approver determined based on the selected Cost Center.

This project demonstrates how Microsoft Power Apps, Dataverse, AI Builder, and Power Automate can be combined to build an end-to-end business application.

🎯 Project Objectives

The main objectives of the application are:

🧾 Digitize the employee expense reporting process
🤖 Automate receipt data extraction using AI Builder
📝 Allow users to create expense reports with multiple line items
📷 Upload and process expense receipts
🗂️ Categorize individual expenses
🏢 Associate expenses with Cost Centers
👤 Dynamically determine the appropriate approver
🔄 Automate the expense approval process
📧 Notify approvers when expenses are submitted
📊 Track expenses based on their current status
🔒 Prevent modification of expenses after submission
🗃️ Maintain relationships between expense reports and their line items
✨ Key Features
🏠 Expense Dashboard

The application provides a centralized dashboard where employees can view and manage their expense reports.

Users can filter expenses based on their current status.

Typical status filters include:

📋 All
🟢 Open
🟡 Pending
✅ Approved
❌ Rejected

The dashboard provides an overview of the user's existing expense reports and their current state.

📝 Create Expense Report

Users can create a new expense report by entering the required information.

The expense report can contain details such as:

Expense Name
Start Date
End Date
Cost Center
Comments

After the expense is created, it is initially maintained in an editable state.

🆔 Expense Identification

Each expense report has a unique identifier that can be used to track the expense throughout its lifecycle.

The identifier allows the expense report to be associated with its individual expense line items.

✏️ Edit Expense Report

Expenses that are still in an editable state can be modified by the employee.

Users can:

Edit expense information
Add expense line items
Modify existing line items
Delete line items
Upload receipts
Review receipt information
Submit the completed expense

Once the expense enters the approval process, editing is restricted.

🧾 Expense Line Items

An expense report can contain multiple individual expense line items.

For example:

Expense Report
│
├── Lunch with Client
├── Taxi to Client Office
├── Hotel Stay
└── Parking Charges

Each line item can contain information such as:

📝 Expense Name
🗂️ Category
💰 Cost
📅 Transaction Date
📄 Description
📷 Receipt

This creates a one-to-many relationship between an Expense Report and its Line Items.

➕ Add Expense Line Item

Users can add multiple line items to a single expense report.

The application allows users to:

Add a new expense
Save an expense line item
Save and continue adding additional items
Edit existing line items
Delete line items
Attach receipts to individual expenses

This makes it possible to create a complete expense report containing multiple transactions.

🤖 AI Builder Receipt Processing

One of the main features of the application is AI-powered receipt processing.

The application uses AI Builder Receipt Processing to extract information from uploaded receipts.

📷 Receipt Processing Workflow
Upload Receipt
      ↓
AI Builder Receipt Processing
      ↓
Extract Receipt Information
      ↓
Populate Expense Fields
      ↓
User Reviews Information
      ↓
Save Line Item

AI Builder can extract information such as:

🏪 Merchant Name
💰 Total Amount
📅 Transaction Date

The extracted information is then used to populate the appropriate fields in the Power Apps form.

🔍 Review Extracted Receipt Information

After the receipt is processed, the extracted information is displayed to the user.

The user can review the extracted values and make corrections if required.

This provides a validation step before the expense is saved and submitted for approval.

📎 Receipt Management

Each expense line item can have its associated receipt.

The receipt provides supporting documentation for the expense and can be reviewed along with the expense details.

This helps maintain the relationship between the expense transaction and its supporting document.

🗂️ Expense Categories

Individual expense line items can be assigned to an expense category.

Examples include:

🍔 Food & Beverage
🚕 Transportation
🏨 Accommodation
🅿️ Parking
✈️ Travel
📦 Other

The available categories can be customized according to organizational requirements.

🏢 Cost Center Management

The application uses a Cost Center table to associate expenses with the appropriate organizational unit.

The Cost Center information is also used to determine the approver for the expense.

A Cost Center can contain information such as:

Cost Center
     ↓
Approver Email

For example:

Cost Center: Finance
Approver: manager@company.com

This allows the approval process to dynamically identify the correct approver.

🔄 Automated Approval Workflow

Power Automate is used to automate the expense approval process.

The overall process is:

Employee Creates Expense
          ↓
Adds Expense Line Items
          ↓
Uploads Receipts
          ↓
AI Builder Processes Receipt
          ↓
Reviews Expense
          ↓
Submits Expense
          ↓
Status = Pending
          ↓
Determine Approver
          ↓
Send Approval Request
          ↓
Approver Reviews Expense
          ↓
       ┌───────────────┐
       │               │
    Approve          Reject
       │               │
       ↓               ↓
   Approved         Rejected
📤 Submit Expense for Approval

After completing the expense report and adding the required line items, the employee can submit the expense.

When the expense is submitted:

🔄 The status changes to Pending
🔒 The expense becomes read-only for the employee
⚡ Power Automate starts the approval workflow
👤 The appropriate approver is identified
📧 An approval notification is sent to the approver
👤 Dynamic Approver Selection

The approver is not hard-coded directly into the application.

Instead, the approver information is maintained against the Cost Center.

The approval process follows:

Expense
   ↓
Selected Cost Center
   ↓
Cost Center Table
   ↓
Approver Email
   ↓
Power Automate
   ↓
Approval Request

This makes the application easier to maintain because approver information can be changed in the backend without modifying the Canvas App.

📧 Approval Notification

Power Automate sends an approval request to the appropriate approver after the expense is submitted.

The approver can review the expense and select:

✅ Approve
❌ Reject

The approval response is then used to update the expense status.

🔄 Expense Status Lifecycle

The application follows a simple expense lifecycle:

Open
  ↓
Pending
  ↓
 ┌──────────────┐
 ↓              ↓
Approved      Rejected
🟢 Open

The expense is still being prepared and can be edited by the employee.

🟡 Pending

The expense has been submitted and is waiting for approval.

The employee can view the expense but cannot modify it.

✅ Approved

The expense has been approved by the assigned approver.

❌ Rejected

The expense has been rejected by the assigned approver.

🗑️ Delete Expense

Users can delete expenses while they are still in an editable state.

The application maintains the relationship between the main Expense record and its associated Line Items.

This allows the related expense information to be managed together.

🧩 Dataverse Data Model

Microsoft Dataverse is used as the backend database for the application.

The primary tables are:

┌──────────────────────┐
│       Expense        │
├──────────────────────┤
│ Expense ID           │
│ Name                 │
│ Start Date           │
│ End Date             │
│ Cost Center          │
│ Comments             │
│ Submitted Date       │
│ Status               │
└──────────┬───────────┘
           │
           │ 1:N
           │
           ▼
┌──────────────────────┐
│     Line Items       │
├──────────────────────┤
│ Name                 │
│ Category             │
│ Cost                 │
│ Transaction Date     │
│ Description          │
│ Receipt Image        │
│ Expense Relationship │
└──────────────────────┘


┌──────────────────────┐
│     Cost Center      │
├──────────────────────┤
│ Name                 │
│ Approver Email       │
└──────────────────────┘
🗃️ Expense Table

The Expense table represents the main expense report.

Typical fields include:

Field	Purpose
Expense ID	Unique expense reference
Name	Expense report name
Start Date	Beginning date of the expense
End Date	Ending date of the expense
Cost Center	Related Cost Center
Comments	Additional information
Submitted Date	Date the expense was submitted
Status	Current approval status
🧾 Line Items Table

The Line Items table stores individual transactions belonging to an Expense report.

Typical fields include:

Field	Purpose
Name	Line item name
Category	Expense category
Cost	Expense amount
Transaction Date	Date of transaction
Description	Expense description
Receipt Image	Uploaded receipt
Expense	Related Expense record

The relationship allows one Expense report to contain multiple Line Items.

One Expense
     │
     ├── Line Item 1
     ├── Line Item 2
     ├── Line Item 3
     └── Line Item 4
🏢 Cost Center Table

The Cost Center table stores information used to determine the appropriate approver.

Typical fields include:

Field	Purpose
Name	Cost Center name
Approver Email	Person responsible for approval

This allows the approval workflow to dynamically determine the approver.

⚙️ Power Automate Workflow

Power Automate manages the automated approval process.

A simplified workflow is:

Expense Submitted
       ↓
Get Expense Details
       ↓
Get Cost Center Information
       ↓
Retrieve Approver
       ↓
Start Approval
       ↓
Wait for Approval Response
       ↓
Check Approval Outcome
       ↓
 ┌───────────────┐
 │               │
Approve        Reject
 │               │
 ↓               ↓
Update Status   Update Status
 │               │
 ↓               ↓
Approved       Rejected

The flow can also be extended to send notifications to the employee after the approval decision.

🧠 Power Apps Logic

The Canvas App uses Power Fx to control different parts of the application.

The project demonstrates:

🧭 Screen navigation
📝 Form behavior
💾 Record creation
✏️ Record editing
🗑️ Record deletion
👁️ Conditional visibility
🔄 Status-based controls
🔎 Data filtering
📷 Receipt processing
🔔 User notifications
⚠️ Validation
📊 Gallery filtering
🔐 Status-Based Access

The application uses the expense status to control what actions are available to the employee.

Example:

If Status = Open
    → Allow Edit
    → Allow Add Line Item
    → Allow Delete
    → Allow Submit

If Status = Pending
    → View Only

If Status = Approved
    → View Only

If Status = Rejected
    → View / Handle according to business rules

This prevents employees from modifying expenses after they have entered the approval process.

🔎 Expense Filtering

The dashboard allows users to filter their expense reports based on status.

Example:

All
Open
Pending
Approved
Rejected

This makes it easier for users to locate specific expense reports.

📱 Application Workflow

The complete user journey is:

                    ┌──────────────────┐
                    │   Open App       │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ Expense Dashboard│
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ Create Expense   │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ Enter Details    │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ Select Cost      │
                    │ Center           │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ Add Line Item    │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ Upload Receipt   │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ AI Builder       │
                    │ Receipt Scanning │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ Review Extracted │
                    │ Information      │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ Save Line Item   │
                    └────────┬─────────┘
                             ↓
                    ┌──────────────────┐
                    │ Add More Items?  │
                    └───────┬───┬──────┘
                            │   │
                           Yes  No
                            │   │
                            ↓   ↓
                       Add Item Submit
                                │
                                ↓
                         ┌──────────────┐
                         │ Status       │
                         │ Pending      │
                         └──────┬───────┘
                                ↓
                         ┌──────────────┐
                         │ Power        │
                         │ Automate     │
                         └──────┬───────┘
                                ↓
                         ┌──────────────┐
                         │ Determine    │
                         │ Approver     │
                         └──────┬───────┘
                                ↓
                         ┌──────────────┐
                         │ Approval     │
                         └──────┬───────┘
                                ↓
                         ┌──────┴──────┐
                         ↓             ↓
                     Approved       Rejected
🛠️ Technologies Used
Technology	Purpose
Microsoft Power Apps	Canvas application and user interface
Power Fx	Application logic and formulas
Microsoft Dataverse	Relational backend database
Power Automate	Approval and workflow automation
AI Builder	Receipt scanning and information extraction
Dataverse Relationships	Expense and Line Item relationship
Microsoft Teams / Approvals	Approval notification and response
Microsoft Power Platform	Overall application platform
⚙️ Power Platform Components

The project demonstrates the following Power Platform capabilities:

🎨 Canvas Apps
🗃️ Microsoft Dataverse
🔄 Power Automate
🤖 AI Builder
🧮 Power Fx
🔗 Dataverse Relationships
📝 Forms
📋 Galleries
🔍 Filtering
🔐 Conditional access
📧 Automated notifications
✅ Approval workflows
🧠 Power Apps Concepts Demonstrated

This project demonstrates:

Canvas App development
Screen navigation
Forms
Galleries
Dataverse integration
Dataverse lookups
One-to-many relationships
Power Fx
Variables
Collections
Conditional visibility
Conditional formatting
Record creation
Record editing
Record deletion
Filtering
Form validation
Status-based UI
Image controls
Receipt/image upload
AI Builder integration
Error handling
User notifications
🤖 AI Builder Concepts Demonstrated

The application demonstrates how AI Builder can be integrated into a Canvas App.

The receipt processing workflow extracts information from an uploaded receipt and uses the extracted values to populate application fields.

Receipt Image
      ↓
AI Builder
      ↓
Receipt Processing
      ↓
Merchant Name
Total Amount
Transaction Date
      ↓
Power Apps Fields

The user can review and modify the extracted values before submitting the expense.

🔄 How the Application Works
1. 👤 User Opens the Application

The user opens the Canvas App and is presented with the expense dashboard.

Existing expenses can be filtered according to their status.

2. 📝 User Creates an Expense

The user creates a new expense and enters the required information such as:

Expense Name
Start Date
End Date
Cost Center
Comments
3. 💾 Expense Is Created

The expense is stored in Dataverse and remains in an editable state.

4. ➕ User Adds Line Items

The user adds individual transactions to the expense report.

Each transaction is stored as a separate Line Item related to the main Expense record.

5. 📷 User Uploads Receipt

The user uploads the receipt associated with the expense line item.

6. 🤖 AI Extracts Information

AI Builder processes the receipt and extracts relevant information such as:

Merchant
Amount
Transaction Date
7. ✏️ User Reviews Information

The user reviews the extracted information and corrects any values if required.

Additional information such as category and description can also be provided.

8. 💾 User Saves the Line Item

The line item is saved and associated with the main expense.

The employee can continue adding additional line items.

9. 📤 User Submits Expense

After completing the expense report, the employee submits it for approval.

The expense status changes to Pending.

10. 🔄 Power Automate Starts

Power Automate retrieves the expense and Cost Center information and identifies the appropriate approver.

11. 👤 Approver Receives Notification

The approver receives an approval request containing the relevant expense information.

12. ✅ Approver Makes Decision

The approver can:

Approve
   OR
Reject
13. 🔄 Expense Status Is Updated

Power Automate updates the Dataverse record based on the approval decision.

Approve → Approved

Reject → Rejected
📊 Example Business Scenario

Consider an employee who attends a customer meeting.

The employee creates an expense report:

Expense Name:
Meeting with Client A

Cost Center:
Microsoft

Start Date:
01-Aug-2026

End Date:
01-Aug-2026

The employee then adds multiple line items:

Line Item 1
Food & Beverage
₹1,500
Lunch with Customer
Receipt Attached

Line Item 2
Transportation
₹800
Taxi to Customer Office
Receipt Attached

AI Builder processes the receipts and extracts the relevant information.

After reviewing the information, the employee submits the expense.

Power Automate identifies the approver associated with the selected Cost Center and sends the approval request.

The approver reviews the expense and approves it.

The expense status is then updated to:

Approved
📂 Solution Components

The application consists of the following major components:

Expense Reporting Solution
│
├── Canvas App
│   ├── Home / Dashboard
│   ├── Expense Screen
│   ├── Expense Form
│   ├── Line Item Screen
│   ├── Receipt Processing
│   └── View / Edit Screens
│
├── Dataverse
│   ├── Expense Table
│   ├── Line Items Table
│   └── Cost Center Table
│
├── AI Builder
│   └── Receipt Processing
│
└── Power Automate
    └── Expense Approval Flow
📁 Data Relationship

The application uses relational data modeling.

Cost Center
     │
     │
     ▼
 Expense
     │
     │ 1 : Many
     ▼
 Line Items

For example:

Microsoft Cost Center
        │
        ▼
Meeting with Client
        │
        ├── Lunch Receipt
        ├── Taxi Receipt
        └── Parking Receipt
🚀 Benefits

The application provides several business benefits:

⏱️ Reduces manual expense entry
🤖 Automates receipt data extraction
📷 Reduces repetitive receipt data entry
🔄 Automates approval workflows
📧 Automates approver notifications
🗃️ Centralizes expense information
🔎 Makes expenses easier to track
🔒 Prevents unauthorized modification after submission
📊 Provides clear expense status tracking
🏢 Supports Cost Center-based approval routing
📈 Can be extended for enterprise expense management
💡 Challenges Solved
❌ Manual Receipt Entry

Employees traditionally need to manually enter merchant, amount, and transaction date.

✅ Solution

AI Builder extracts important information directly from uploaded receipts.

❌ Manual Approval Process

Expense requests can require emails and manual tracking.

✅ Solution

Power Automate automates the approval workflow.

❌ Hard-Coded Approvers

Hard-coding approvers makes applications difficult to maintain.

✅ Solution

Approvers are maintained against Cost Centers.

❌ Scattered Expense Information

Receipts and expense information can become difficult to track.

✅ Solution

Expenses and their supporting information are managed within a centralized Dataverse solution.

❌ Modification After Submission

Employees should not be able to modify an expense while it is being reviewed.

✅ Solution

The application uses status-based logic to make Pending expenses read-only.

📚 Learning Outcomes

This project demonstrates how to:

Build a business application using Power Apps
Design Canvas App interfaces
Work with Microsoft Dataverse
Create relational Dataverse tables
Create one-to-many relationships
Build forms and galleries
Use Power Fx for business logic
Implement status-based UI behavior
Upload and display images
Integrate AI Builder with Power Apps
Extract receipt information using AI
Build Power Automate workflows
Implement automated approval processes
Dynamically determine approvers
Update Dataverse records from Power Automate
Build an end-to-end Power Platform solution
🔮 Potential Enhancements

The application can be further extended with:

💬 Microsoft Teams approval notifications
📱 Responsive mobile layout
📊 Power BI expense analytics
💰 Expense limits and validation
🏦 Reimbursement tracking
👥 Multiple approval levels
🔔 Employee approval/rejection notifications
📧 Automated reimbursement emails
📎 Multiple receipt attachments
📈 Department-wise expense reporting
🗓️ Monthly and yearly expense summaries
🔍 Advanced search and filtering
🔐 Role-based security
🧾 Automated expense report generation
💱 Multi-currency support
🌍 International expense management
🤖 AI-based expense categorization
🚨 Duplicate receipt detection
🎯 Potential Use Cases

The architecture can be adapted for:

💼 Employee Expense Claims
✈️ Business Travel Expenses
🍽️ Client Entertainment Expenses
🚕 Transportation Claims
🏨 Hotel Reimbursements
🧾 Receipt Management
💳 Corporate Card Expenses
🏢 Department Expense Management
💰 Reimbursement Management
📊 Finance Operations
🧑‍💼 Employee Business Expenses
🏆 Project Highlights
🎨 Canvas App
        +
🗃️ Dataverse
        +
🤖 AI Builder
        +
🔄 Power Automate
        +
✅ Approval Workflow
        =
🚀 End-to-End Expense Management Solution

The project demonstrates how multiple Microsoft Power Platform services can be combined to create an intelligent, automated, and maintainable business application.

📌 Project Summary

The Expense Reporting App is an end-to-end Power Platform solution that enables employees to create expense reports, add multiple transactions, upload receipts, automatically extract receipt information using AI Builder, and submit expenses for automated approval.

The solution combines:

Microsoft Power Apps for the application interface
Microsoft Dataverse for relational data storage
AI Builder for receipt processing
Power Automate for workflow automation and approvals

The result is a centralized expense management application that reduces manual data entry, improves approval efficiency, and provides better visibility into the employee expense lifecycle.
