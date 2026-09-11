# Automated Network Request Management

A ServiceNow-based application designed to streamline and automate the end-to-end lifecycle of network-related service requests, including request submission, approval, task assignment, processing, tracking, and completion.

---

## 📌 Project Overview

In a traditional network request process, requests may involve manual submission, manual approval, communication through emails, and manual assignment to the appropriate IT teams. This can result in delays, human errors, lack of visibility, repetitive administrative work, and difficulty tracking the complete request lifecycle.

To overcome these challenges, **Automated Network Request Management** was developed using **ServiceNow**.

The project provides a structured Service Catalog interface for submitting network service requests and automates the backend request lifecycle using ServiceNow features such as Catalog Variables, Variable Sets, Catalog UI Policies, Flow Designer, approval automation, email notifications, and Catalog Tasks.

The complete request lifecycle can be managed within ServiceNow, from request submission through approval, processing, task assignment, tracking, and completion.

---

## 🎯 Objectives

The main objectives of this project are:

- Automate network service request submission
- Reduce manual effort in request processing
- Implement a structured approval process
- Provide dynamic and user-friendly form behavior
- Capture requester and request information in a structured manner
- Reduce unnecessary manual communication
- Automate request processing activities
- Generate and assign fulfillment tasks
- Provide email notifications
- Improve request tracking and visibility
- Standardize the network request management process
- Improve coordination between requesters, approvers, and fulfillment teams

---

## 🛠️ Technologies and ServiceNow Features Used

- ServiceNow
- Service Catalog
- Catalog Items
- Catalog Variables
- Variable Sets
- Catalog UI Policies
- Flow Designer
- Approval Automation
- Email Notifications
- Request Records (REQ)
- Requested Items (RITM)
- Catalog Tasks

---

# ⚙️ Project Implementation and Main Features

## 1. Network Request Catalog Item

A dedicated **Network Request** Catalog Item was created in ServiceNow specifically for managing network-related service requests.

The Catalog Item is configured with:

- Name: **Network Request**
- Short Description: **Network Services Request**
- Service Catalog availability
- Network Standard Changes category
- Catalog Variables
- Requester Information Variable Set
- Catalog UI Policy

The Catalog Item provides users with a structured and centralized interface for submitting network service requests.

---

## 2. Catalog Variables and Request Information

Catalog Variables are configured to collect the information required for processing a network request.

The form captures details such as:

- Requested For
- Opened On Behalf Of
- User Name
- Email ID
- Phone Number
- Mobile Number
- Type of Connection
- Existing Connection Details
- Total Amount
- Mode of Payment
- Address

These variables collect the required information in a structured format and make the submitted data available for further processing.

---

## 3. Reusable Requester Information Variable Set

A **Variable Set** was configured to organize common requester-related fields.

The Variable Set includes information such as:

- Opened On Behalf Of
- User Name
- Email ID
- Phone Number
- Mobile Number

Using a Variable Set improves the organization and reusability of common fields.

Some information can also be populated based on the selected user, helping reduce manual data entry and improving consistency.

---

## 4. Dynamic Form Behavior Using Catalog UI Policy

A **Catalog UI Policy** was implemented to provide dynamic behavior on the Network Request form.

The requester can select the **Type of Connection** as:

- New
- Existing

When the requester selects **Existing**, the corresponding Existing Connection field is displayed.

This ensures that users only see relevant fields based on their selection.

```text
Type of Connection
        │
        ├── New
        │
        └── Existing
                │
                ▼
       Existing Connection
          field displayed
```

This improves the usability of the form and avoids displaying unnecessary fields.

---

## 5. Network Services Request Form

The Network Services Request form is the user-facing entry point for the complete request management process.

A requester can:

1. Specify the user for whom the service is required.
2. Enter requester information.
3. Select the Type of Connection.
4. Provide existing connection information when applicable.
5. Enter the Total Amount.
6. Select the Mode of Payment, such as UPI or Card.
7. Enter the required Address.
8. Submit the request using **Order Now**.

Once submitted, the information collected through the Catalog Variables becomes available for the backend request and automation process.

---

## 6. Automated Request Creation

After the Network Request form is submitted, ServiceNow generates a unique **Request record (REQ)**.

Example:

```text
REQ0010003
```

The Request record provides centralized information about the submitted request, including:

- Requester
- Opened By
- Approval Status
- Request State
- Related Requested Items

The REQ record acts as the parent record for the submitted service request.

---

## 7. Requested Item (RITM) Creation

After the request is submitted, ServiceNow creates a **Requested Item (RITM)** for the specific Catalog Item.

Example:

```text
REQ0010003
      │
      ▼
RITM0010003
      │
      ▼
Network Request
```

The RITM represents the specific **Network Request Catalog Item** submitted by the requester.

The Requested Item contains the variables and information entered through the Service Catalog form.

This allows the submitted request information to be used throughout the request fulfillment process.

---

## 8. Approval Automation

The project implements a structured approval process as part of the automated request lifecycle.

After submission, the request proceeds through the configured approval process.

The approval status is managed within ServiceNow, allowing the request to continue to the fulfillment stage based on the approval result.

This helps reduce manual follow-up and provides better visibility into the request status.

---

## 9. Flow Designer Automation

**Flow Designer** is used to automate the backend processing of the Network Request.

The flow connects the Service Catalog submission with the request processing lifecycle.

The automation handles activities such as:

- Processing submitted requests
- Handling approval activities
- Updating request information
- Sending email notifications
- Creating Catalog Tasks
- Supporting task assignment
- Managing the request lifecycle

This reduces manual intervention and helps provide a standardized and automated process.

---

## 10. Email Notifications

Email notifications are configured as part of the request automation process.

Notifications help keep relevant users informed about important activities and status changes during the request lifecycle.

This improves communication and visibility between:

- Requesters
- Approvers
- IT teams
- Fulfillment teams

---

## 11. Automated Catalog Task Creation

Catalog Tasks are generated as part of the request fulfillment process.

In the demonstrated implementation, two Catalog Tasks are created.

### Field Services Task

The first task is assigned to the **Field Services** group.

This task is used for assessment or scoping activities related to the network request.

### Software Task

The second task is assigned to the **Software** group.

This task supports the fulfillment of the requested service.

The task structure helps divide the work into appropriate activities and assign responsibilities to the relevant groups.

---

# 🔄 Complete Request Lifecycle

The complete automated workflow is shown below:

```text
Requester
    │
    ▼
Service Catalog
    │
    ▼
Network Request Catalog Item
    │
    ▼
Network Services Request Form
    │
    ▼
Enter Requester and Service Information
    │
    ▼
Select Type of Connection
    │
    ▼
Catalog UI Policy Displays Relevant Fields
    │
    ▼
Submit Request Using Order Now
    │
    ▼
Request Record Created (REQ)
    │
    ▼
Requested Item Created (RITM)
    │
    ▼
Flow Designer Automation
    │
    ├───────────────┬────────────────┐
    ▼               ▼                ▼
Approval      Email Notifications  Task Creation
                                       │
                              ┌────────┴────────┐
                              ▼                 ▼
                       Field Services        Software
                              │                 │
                              └────────┬────────┘
                                       ▼
                             Request Fulfillment
                                       │
                                       ▼
                              Request Tracking
                                       │
                                       ▼
                                   Completion
```

---

# 🏗️ Solution Architecture

```text
                         REQUESTER
                             │
                             ▼
                      SERVICE CATALOG
                             │
                             ▼
                  NETWORK REQUEST ITEM
                             │
                             ▼
                  NETWORK REQUEST FORM
                             │
          ┌──────────────────┼──────────────────┐
          ▼                  ▼                  ▼
     Requester          Connection          Payment and
     Information           Type              Address
                             │
                             ▼
                       SUBMIT REQUEST
                             │
                             ▼
                       REQUEST (REQ)
                             │
                             ▼
                  REQUESTED ITEM (RITM)
                             │
                             ▼
                  FLOW DESIGNER AUTOMATION
                             │
             ┌───────────────┼────────────────┐
             ▼               ▼                ▼
         APPROVAL       NOTIFICATIONS     TASK CREATION
                                               │
                                  ┌────────────┴────────────┐
                                  ▼                         ▼
                            FIELD SERVICES              SOFTWARE
                                  │                         │
                                  └────────────┬────────────┘
                                               ▼
                                     REQUEST FULFILLMENT
                                               │
                                               ▼
                                      REQUEST TRACKING
                                               │
                                               ▼
                                           COMPLETION
```

---

# 🧪 Testing

The application was tested to verify that the major functionalities of the automated request lifecycle work as expected.

The following functionalities were tested:

### 1. Catalog Item Availability

Verified that the **Network Request** Catalog Item is available in the configured Service Catalog and category.

### 2. Form Submission

Verified that users can enter the required information and successfully submit the Network Services Request form.

### 3. Requester Information

Verified that requester-related information is captured correctly through the configured Variable Set.

### 4. Dynamic Field Behavior

Verified the Catalog UI Policy behavior.

When **Existing** is selected as the Type of Connection, the Existing Connection field is displayed as expected.

### 5. Request Creation

Verified that a unique **Request (REQ)** record is generated after successful submission.

### 6. Requested Item Creation

Verified that a corresponding **Requested Item (RITM)** is created and linked to the parent Request.

### 7. Variable Data Availability

Verified that the information entered through the Service Catalog form is available in the Requested Item.

### 8. Approval Processing

Verified that the request follows the configured approval process.

### 9. Catalog Task Generation

Verified that Catalog Tasks are created as part of the request fulfillment process.

### 10. Task Assignment

Verified that the generated tasks are assigned to the appropriate groups:

- Field Services
- Software

### 11. Email Notification Flow

Verified the notification process for relevant request activities and updates.

### 12. Request Tracking

Verified that the Request, Requested Item, and related Catalog Tasks can be tracked within ServiceNow.

---

# 📊 Testing Summary

```text
Catalog Item Availability        ✓ Verified
Form Submission                  ✓ Verified
Requester Information            ✓ Verified
Dynamic UI Policy                ✓ Verified
Request (REQ) Creation           ✓ Verified
Requested Item (RITM) Creation   ✓ Verified
Variable Data Transfer           ✓ Verified
Approval Processing              ✓ Verified
Catalog Task Generation          ✓ Verified
Task Assignment                  ✓ Verified
Email Notifications              ✓ Verified
Request Tracking                 ✓ Verified
```

---

# 📸 Project Demonstration

The complete project demonstration includes the following steps:

1. Navigate to **Application Navigator**.
2. Search for **Service Catalog**.
3. Open **Maintain Items**.
4. Open the **Network Request** Catalog Item.
5. Review the basic Catalog Item configuration.
6. Review the configured Catalog Variables.
7. Review the Requester Information Variable Set.
8. Review the Catalog UI Policy.
9. Click **Try It** to open the Network Services Request form.
10. Enter the requester information.
11. Select the Type of Connection.
12. Demonstrate the dynamic behavior for an Existing Connection.
13. Enter the Total Amount.
14. Select the Mode of Payment.
15. Enter the required Address.
16. Submit the request using **Order Now**.
17. Review the generated Request record.
18. Review the Request number, requester, approval status, and request state.
19. Open the associated Requested Item.
20. Review the variables entered through the Catalog form.
21. Review the generated Catalog Tasks.
22. Verify the Field Services task.
23. Verify the Software task.
24. Demonstrate the automated backend process using Flow Designer.

---

# 👩‍💻 My Contribution

I designed and implemented the ServiceNow-based **Automated Network Request Management** solution.

My contributions include:

- Creating the Network Request Catalog Item
- Configuring the Catalog Item category and details
- Creating Catalog Variables
- Creating and configuring a reusable Variable Set
- Configuring requester-related fields
- Implementing dynamic form behavior using Catalog UI Policies
- Configuring the Network Services Request form
- Implementing the approval process
- Configuring Flow Designer automation
- Configuring email notifications
- Automating Catalog Task creation
- Supporting task assignment to appropriate groups
- Testing the complete request lifecycle
- Documenting the project through different project phases

---

# 📂 Project Documentation

The complete project documentation is organized into the following phases:

```text
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
```

The repository contains documentation related to ideation, requirement analysis, project design, planning, development, testing, and final project documentation.

---

# 🌟 Benefits

## Reduced Manual Effort

The automation reduces repetitive manual activities involved in request processing, approval, communication, and task management.

## Improved Accuracy

Structured forms and automated processing help reduce manual errors and improve consistency.

## Better Visibility

Requests, Requested Items, approval status, and Catalog Tasks can be tracked within ServiceNow.

## Faster Processing

Automation helps reduce delays caused by manual communication, approval, and assignment activities.

## Standardized Workflow

The solution provides a consistent and structured process for managing network service requests.

## Better Team Coordination

Catalog Tasks help divide the request into fulfillment activities and assign work to the appropriate groups.

## Improved User Experience

Dynamic form behavior ensures that requesters see relevant fields based on their selections.

---

# 🚀 Future Enhancements

The project can be further enhanced by implementing:

- SLA monitoring and escalation
- Advanced dashboards and reports
- Real-time request status tracking
- Multiple approval levels based on request type
- Automated escalation rules
- Integration with external network management systems
- Automated request closure after task completion
- Additional notification rules
- Advanced task routing
- AI-assisted request classification and routing

---

# 🎓 Project Information

**Project Name:** Automated Network Request Management

**Platform:** ServiceNow

**Domain:** IT Service Management (ITSM)

**Project Type:** ServiceNow Application Development Project

---

# 👤 Author

**Harika Jetti**

Bachelor of Technology – Computer Science and Engineering

---

# 📌 Conclusion

**Automated Network Request Management** demonstrates how ServiceNow can transform a traditionally manual network service request process into a structured and automated workflow.

The project provides a centralized process for submitting network service requests through the Service Catalog, collecting information through Catalog Variables and Variable Sets, dynamically managing the form using Catalog UI Policies, processing requests through Flow Designer automation, handling approvals, sending notifications, and generating Catalog Tasks for fulfillment.

The automated workflow creates a clear connection between the **Request (REQ)**, **Requested Item (RITM)**, approval process, and fulfillment tasks, allowing the complete lifecycle to be managed and tracked within ServiceNow.

By reducing manual effort, improving visibility, standardizing request processing, and supporting better coordination between teams, the solution demonstrates the practical use of ServiceNow automation for efficient network service request management.
