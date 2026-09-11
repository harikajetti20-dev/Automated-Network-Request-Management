
# Automated Network Request Management

A ServiceNow-based application designed to automate and streamline the end-to-end lifecycle of network service requests, from request submission and approval to task assignment, processing, tracking, and completion.

---

## 📌 Project Overview

In a traditional network service request process, users may need to submit requests manually, communicate through emails, wait for approvals, and depend on manual assignment to the appropriate IT teams.

This can lead to:

- Delays in request processing
- Manual errors
- Lack of request visibility
- Repetitive administrative work
- Difficulty tracking the request lifecycle

To overcome these challenges, **Automated Network Request Management** was developed using **ServiceNow**.

The application provides a structured **Service Catalog** form and uses ServiceNow automation to manage the complete request lifecycle efficiently.

---

## 🎯 Objectives

The main objectives of this project are:

- Automate network service request submission
- Reduce manual effort in request processing
- Implement an automated approval process
- Provide dynamic form behavior
- Capture requester and request information in a structured manner
- Automate task creation and assignment
- Provide email notifications
- Improve request tracking and visibility
- Standardize the network request management process

---

## 🛠️ Technologies & ServiceNow Features Used

- **ServiceNow**
- **Service Catalog**
- **Catalog Items**
- **Catalog Variables**
- **Variable Sets**
- **Catalog UI Policies**
- **Flow Designer**
- **Approval Automation**
- **Catalog Tasks**
- **Email Notifications**
- **Request (REQ)**
- **Requested Item (RITM)**

---

## 🏗️ Solution Architecture

The project follows an automated request lifecycle:

```text
                    Requester
                        │
                        ▼
                Service Catalog
                        │
                        ▼
              Network Request Form
                        │
          ┌─────────────┼─────────────┐
          │             │             │
          ▼             ▼             ▼
      Requester    Connection      Payment &
      Information     Type          Address
                        │
                        ▼
                  Submit Request
                        │
                        ▼
                  Request (REQ)
                        │
                        ▼
              Requested Item (RITM)
                        │
                        ▼
              Flow Designer Automation
                        │
          ┌─────────────┼─────────────┐
          │             │             │
          ▼             ▼             ▼
      Approval      Notifications   Task Creation
                                        │
                              ┌─────────┴─────────┐
                              │                   │
                              ▼                   ▼
                       Field Services          Software
                              │                   │
                              └─────────┬─────────┘
                                        ▼
                              Request Fulfillment
                                        │
                                        ▼
                                 Request Tracking

⚙️ Main Features
1. Network Request Catalog Item

A dedicated Network Request Catalog Item was created in ServiceNow for managing network-related service requests.

The Catalog Item includes:

Name: Network Request
Short Description: Network Services Request
Catalog Variables
Variable Set
Catalog UI Policy

The item is organized under the appropriate Service Catalog category so that users can easily find and submit network service requests.

2. Requester Information

A reusable Variable Set was configured to organize common requester-related information.

The fields include:

Opened On Behalf Of
User Name
Email ID
Phone Number
Mobile Number

Some values can be automatically populated based on the selected user.

This reduces manual data entry and improves consistency in the submitted request.

3. Dynamic Form Behavior

A Catalog UI Policy was implemented to dynamically control the visibility of relevant fields.

For example, the requester can select the Type of Connection as:

New
Existing

When Existing is selected, the corresponding Existing Connection field is displayed.

Type of Connection
        │
        ├── New
        │
        └── Existing
                │
                ▼
       Existing Connection
          field displayed

This makes the form more user-friendly by displaying only the information relevant to the selected option.

4. Network Service Request Form

The user-facing form acts as the entry point for the request management process.

The form captures information such as:

Requested For
Opened On Behalf Of
User Name
Email ID
Phone Number
Mobile Number
Type of Connection
Existing Connection Details
Total Amount
Mode of Payment
Address

The requester enters the required information and submits the request using Order Now.

5. Automated Request Creation

After the requester submits the form, ServiceNow creates a unique Request (REQ) record.

Example:

REQ0010003

The request record contains important information such as:

Requester
Opened By
Approval Status
Request State

This provides a centralized record for tracking the submitted request.

6. Requested Item (RITM)

A Requested Item (RITM) is created for the submitted Catalog Item.

Example:

REQ0010003
     │
     ▼
RITM0010003
     │
     └── Network Request

The RITM contains the Network Request details and the variables entered through the Service Catalog form.

This connects the submitted request with the fulfillment process.

7. Automated Approval Process

The project includes an automated approval process for submitted network requests.

The approval status is managed as part of the request lifecycle, reducing the need for manual communication and providing a structured approval workflow.

The request can then proceed to fulfillment activities based on the approval result.

8. Automated Catalog Task Creation

Once the request reaches the fulfillment stage, Catalog Tasks are generated for the teams responsible for processing the request.

In the demonstrated implementation, two tasks are created:

Field Services

The Field Services group handles assessment or scoping activities related to the request.

Software

The Software group provides the requested service as part of the fulfillment process.

This division of tasks helps assign work to the appropriate teams.

9. Flow Designer Automation

Flow Designer is used to automate the request lifecycle.

The automation connects the Service Catalog submission with the backend request processing.

The flow manages activities such as:

Processing submitted requests
Approval handling
Request updates
Email notifications
Catalog Task creation
Task assignment
Request lifecycle management

This minimizes manual intervention and provides a standardized workflow.

10. Email Notifications

Email notifications are incorporated into the automated process to keep relevant users informed about request activities.

Notifications can be used to communicate important changes in the request lifecycle, helping improve visibility and communication between requesters, approvers, and fulfillment teams.

🔄 Complete Request Lifecycle

The complete process can be summarized as:

1. User opens Network Request Catalog Item
                    ↓
2. User enters requester information
                    ↓
3. User selects connection type
                    ↓
4. Relevant fields are displayed dynamically
                    ↓
5. User enters payment and address details
                    ↓
6. User submits the request
                    ↓
7. ServiceNow creates Request (REQ)
                    ↓
8. Requested Item (RITM) is created
                    ↓
9. Approval process is initiated
                    ↓
10. Email notifications are generated
                    ↓
11. Catalog Tasks are created
                    ↓
12. Tasks are assigned to appropriate groups
                    ↓
13. Fulfillment activities are performed
                    ↓
14. Request is tracked and completed
👩‍💻 Project Implementation

The project implementation includes the following ServiceNow configurations:

Service Catalog
Created the Network Request Catalog Item
Configured Catalog Variables
Configured Variable Set
Organized the Catalog Item under the appropriate category
Form Configuration
Implemented dynamic field behavior
Configured Catalog UI Policy
Collected requester and network request information
Captured payment and address details
Automation
Configured Flow Designer
Implemented approval automation
Configured request processing
Automated Catalog Task creation
Assigned tasks to appropriate groups
Configured email notifications
Request Management
Managed Request records
Managed Requested Items
Tracked request variables
Managed Catalog Tasks
Demonstrated the complete request lifecycle
🧪 Testing

The application was tested to verify the major functionalities of the automated request lifecycle.

Testing includes:

Catalog Item availability
Network Request form submission
Mandatory field validation
Dynamic field visibility
Request creation
Requested Item creation
Variable data transfer
Approval processing
Catalog Task generation
Task assignment
Email notification flow
Request tracking
📂 Project Documentation

The complete project documentation is organized into the following phases:

Automated-Network-Request-Management
│
├── 1. Ideation Phase
│
├── 2. Requirement Analysis
│
├── 3. Project Design Phase
│
├── 4. Project Planning Phase
│
├── 5. Project Development Phase
│
└── 6. Project Documentation

📸 Project Demonstration

The project demonstration covers the complete implementation:

1.Navigate to Service Catalog
2.Open the Network Request Catalog Item
3.Review the Catalog Item configuration
4.Review Catalog Variables and Variable Set
5.Demonstrate the Catalog UI Policy
6.Open the user-facing Network Services Request form
7.Enter sample requester information
8.Select the connection type
9.Demonstrate dynamic field behavior
10.Enter payment and address information
11.Submit the request
12.Review the generated Request (REQ)
13.Open the associated Requested Item (RITM)
14.Review the submitted variables
15.Review the generated Catalog Tasks
16.Demonstrate task assignment
17.Demonstrate the automation implemented using Flow Designer

🌟 Benefits

The solution provides several benefits:

Reduced Manual Effort

Automates repetitive request processing and fulfillment activities.

Improved Accuracy

Uses structured forms and automated processing to reduce manual errors.

Better Visibility

Provides centralized request and task tracking within ServiceNow.

Faster Processing

Reduces delays caused by manual communication, approval, and task assignment.

Standardized Workflow

Provides a consistent process for handling network service requests.

Better Team Coordination

Automatically creates and assigns fulfillment tasks to the appropriate groups.

Improved User Experience

Dynamic form behavior ensures that users see relevant fields based on their selections.

🚀 Future Enhancements

The project can be further enhanced with:

SLA monitoring and escalation
Advanced dashboards and reporting
Real-time request status tracking
Additional approval levels
Automated escalation rules
Integration with external network management systems
Automated request closure
AI-assisted request classification and routing
Additional notification and approval rules
🎓 Project Information

Project Name: Automated Network Request Management

Platform: ServiceNow

Domain: IT Service Management (ITSM)

Project Type: ServiceNow Application Development Project

👤 Author

Harika Jetti

Bachelor of Technology – Computer Science & Engineering

📌 Conclusion

Automated Network Request Management demonstrates how ServiceNow can transform a traditionally manual network service request process into a structured and automated workflow.

By using Service Catalog, Catalog Variables, Variable Sets, Catalog UI Policies, Flow Designer, approvals, notifications, Requests, Requested Items, and Catalog Tasks, the solution provides an efficient approach for submitting, approving, processing, assigning, and tracking network service requests.

The project helps reduce manual effort, improve visibility, standardize request processing, and provide a better overall service request experience within ServiceNow.
