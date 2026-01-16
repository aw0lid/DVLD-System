# 🚗 Driving & Vehicle Licensing Department (DVLD) System

A detailed desktop application designed to manage the full lifecycle of driving licenses, from initial application to issuance, renewal, and violations management. The system is built using **C#**, **.NET**, and **SQL Server**, implementing a strict **N-Tier Architecture** to maintain a clean separation between the user interface, business logic, and data access.

---

## 📁 1. Project Architecture & Organization

The system is structured into three main layers to ensure maintainability and scalability:

* **Presentation Layer (UI):** Developed using Windows Forms. It utilizes custom **User Controls** (e.g., Person Card, Driver License Info) to promote code reusability and maintain a consistent design across the application.
* **Business Logic Layer (BLL):** This layer acts as the system's engine. It enforces all legal requirements and business rules, such as age validation, prerequisite test checks, and fee calculations, before any data is passed to the storage layer.
* **Data Access Layer (DAL):** Responsible for all database communication using **ADO.NET**. It handles data retrieval, insertion, and updates through optimized SQL queries and command management.
* **Database (SQL Server):** A normalized relational database designed to store complex relationships between people, users, drivers, applications, and licenses.

---

## 🔄 2. The License Issuance Workflow

The system follows a mandatory sequence of stages that an applicant must complete to obtain a license:

### **Phase 1: Person Registration**
Every individual in the system must first be registered in the **Global People Registry**. This module captures personal details including National ID, contact information, and personal photos. The system strictly prevents duplicate National IDs to ensure data integrity.

### **Phase 2: The Application Process**
When a registered person applies for a license, the system initiates an **Application** record:
* **Class Selection:** Identifies the license category (e.g., Private, Motorcycle, Heavy Truck).
* **Age Verification:** Checks the applicant's age against the minimum requirement for the selected class.
* **Redundancy Check:** Ensures the applicant does not have an active application or a valid license of the same class.

### **Phase 3: The Multi-Stage Testing Pipeline**
Access to tests is governed by a strict prerequisite logic:
1.  **Vision Test:** The initial medical clearance required to proceed.
2.  **Theory (Written) Test:** Automatically unlocked only after the applicant passes the Vision Test.
3.  **Practical (Street) Test:** The final examination, unlocked only after successfully passing both the Vision and Theory tests.

* **Test Retakes:** In case of failure, the system allows scheduling a retake after a specific period and payment of the required "Retake Test" fees, while maintaining a complete history of all attempts.

### **Phase 4: License Issuance**
Upon passing the final practical test, the system promotes the person to a **Driver**, generates a unique Driver ID, and issues the official license.

---

## 🛠️ 3. Core Modules & Services

### **1. Local & International Licenses**
* **Local Licenses:** Handles the primary workflow for new domestic drivers.
* **International Licenses:** Facilitates the issuance of international permits for existing local license holders, valid for one year and linked to their local record.

### **2. License Lifecycle Management**
* **Renewals:** Manages the renewal process for expired licenses, automatically calculating new expiry dates based on the class validity (e.g., 10 years for private vehicles).
* **Replacements:** Provides workflows for issuing replacements for "Lost" or "Damaged" licenses, applying the appropriate legal fees for each case.

### **3. Detain & Release System**
A dedicated module for managing license violations:
* **Detain:** Allows authorized users to detain a license and record the fine amount.
* **Release:** Ensures a detained license is only marked as "Released" after the fine is paid and the release requirements are met.

---

## 🧠 4. System Business Rules

The application relies on automated logic to guide users and prevent errors:
* **Prerequisite Enforcement:** The system locks subsequent steps in any workflow until the current requirement is satisfied.
* **Comprehensive History:** Provides a 360-degree view of a driver's history, including all past applications, test results, and license statuses (Active, Expired, Detained).
* **Automated Status Updates:** Applications and licenses move through different states (New, Cancelled, Completed, Active) based on real-time actions within the system.

---

## ✅ 5. Technical Implementation Summary
* **N-Tier Architecture:** Complete decoupling of UI, Logic, and Data.
* **ADO.NET Integration:** Direct and efficient database interaction.
* **Data Integrity:** Enforcement of relational constraints and business-level validation.
* **Modular UI Components:** Use of User Controls to minimize code duplication.
