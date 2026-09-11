
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
