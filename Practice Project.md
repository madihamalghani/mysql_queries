# ER Diagram and Normalization (4NF) of Lost and Found Portal to Create Tables Through Queries:

**Topic:** Lost and Found Portal for Campus

## **Abstract:**

A public sector educational institute faces challenges in managing lost and found items within the campus premises. Currently, the lost and found process is handled manually via notice boards and word-of-mouth, which often results in misplaced items not being reclaimed, delayed communication, and lack of a proper tracking system. To overcome these inefficiencies, we propose an **automated Lost and Found Portal for Campus**.

This portal will allow students, faculty, and staff to report lost or found items based on descriptive attributes such as item name, color, brand, location, and date. The system will allow easy matching of lost and found reports and maintain a clean, organized database for future reference.

The new system will enhance the recovery of lost items and streamline the communication process, ensuring faster and more efficient item return.

### 2. Project Objectives

The main objective of the Lost and Found Portal for Campus is to create a simple, efficient, and organized system that enables users to report and claim lost and found items electronically. Specifically, the new system will be able to perform the following tasks:

1. Allow users to **submit lost item** reports by filling in descriptive details.
2. Allow users to **submit found item** reports with detailed attributes.
3. Enable users to search for lost or found items using filters such as item type, color, location, and date.
4. Enable users to **submit a claim** stating that a listed found item belongs to them.
5. Allow admin to **track the claimer lost item history** and check if his lost item is same as found.
6. Show users the **status** of their reports (e.g., Active , Matched, Claimed and Returned) so they can check if a possible match has been found.
7. Allow administrators to review, edit, or delete item reports to keep the system accurate and clean.
8. Provide secure sign-up, login, and access control so that only verified campus members can post, edit, or manage reports based on their role.

## **3. Database requirements and business rules:**

Following are the detailed requirements of the application:

1. There will be three types of users of the application: **Administrator**, **Faculty/Staff**, and **Student**.
2. All users must **register** and **log in** securely through the portal. Only verified campus users will be allowed to access the system and perform actions based on their roles.
3. A **student** or **faculty/staff member** can:
a. Submit a **lost item report** by entering descriptive details such as item name, item type, color, brand (optional), location lost, and date lost.
    
    b. Submit a **found item report** with similar attributes like item name, item type, color, brand (optional), location found, and date found.
    
    c. Search for lost or found items using filters such as item type, color, location, and date.
    
    d. View the **status** of their reports — `Active`, `Matched`,  `Claimed` ,  `Returned`.
    
4. The **administrator** will manage the system and perform the following tasks through the admin portal:
a. Add, search, view, edit, and delete user accounts (students, faculty/staff).
    
    b. Search, review, update, or delete lost and found item reports to ensure system accuracy.
    
    c. Mark item reports as `Matched` or `Claimed` based on user descriptions.
    
    d. Maintain overall control of the system data and ensure its reliability.
    
5. Each item report will have a **status** field to track its progress:
    - `Active`: When the item has not yet been claimed.
    - `Claimed`: User says that found item is mine.
    - `Matched`: When that user’s lost item is potentially matched with a found item (admin-confirmed).
    - `Returned` :When the item has been returned to the owner.
6. **Claims** will be submitted by students or users, and:
    
    a. Admin will verify and either approve or reject submitted claims
    
    b. Once approved, the item will be marked as **"Returned"** or **"Claimed"** in the system.
    
7. The system will support:
a. Allowing multiple found reports to be submitted for a single lost item, so that different users can report items they believe match the same lost item.
    
    b. **Multiple lost reports linked to a single found item**, recognizing that multiple users might think the found item belongs to them.
    
    c. **Self-claiming**, where a user who both lost and found the item can submit and claim the item themselves without any restriction.
    
8. The database should be **cloud-hosted** and built using an **open-source DBMS such as MySQL** to create the physical structure of the database. The DBMS should be accessible to the Admin for backup purposes and secure storage in a remote location.

---

## Conceptual Diagram:

<img width="1920" height="1080" alt="Conceptual diagram" src="https://github.com/user-attachments/assets/88116031-7293-412a-a5f4-5861e132f7bc" />

---

## **5. Details of Entities and Attributes**

### **5.1 User:**

| Attribute | Description |
| --- | --- |
| User ID | A unique number to identify each user |
| Name | Full name of the user |
| Email | Unique email of the user (used as a login username as well) |
| Password | Encrypted password of the user |
| Role | Type of user: Student, Faculty, or Admin |
| Contact Number | Optional contact number of the user |
| Registration Date | The date on which the user created their account |

### **5.2 Lost_Item:**

| **Attribute** | **Description** |
| --- | --- |
| Lost Item ID | A unique number to identify each lost item report |
| User ID | Foreign key referring to the user who submitted the lost item report |
| Item Name | Name or title of the lost item |
| Item Description | Detailed description (e.g., color, brand, size) of the lost item |
| Category ID | Foreign key referring to the category of the item |
| Location Lost | Place where the item was lost |
| Date Lost | The actual date on which the item was lost |
| Status | Status of the report: Active (item not found yet),  Returned |
| Date Reported | The date on which the lost item report was created |

### **5.3 Found_Item:**

| **Attribute** | **Description** |
| --- | --- |
| Found Item ID | A unique number to identify each found item report |
| User ID | Foreign key referring to the user who submitted the found item report |
| Item Name | Name or title of the found item |
| Item Description | Detailed description (e.g., color, brand, size) of the found item |
| Category ID | Foreign key referring to the category of the item |
| Location Found | Place where the item was found |
| Date Found | The actual date on which the item was found |
| Status | Status of the report: Active (item not claimed yet), Returned |
| Date Reported | The date on which the found item report was created |

### **5.4 Category:**

| **Attribute** | **Description** |
| --- | --- |
| Category ID | A unique number to identify each item category |
| Category Name | Title or name of the category (e.g., Electronics, Documents, Clothing) |
| Category Description  | Description of the category |

### 5.5 Claim:

| Attribute | Description |
| --- | --- |
| Claim ID | Primary key |
| Claimer id | Who is claiming |
| Found Item ID | Foreign key referring founditem |
| Status | Pending, Approved, Rejected |
| Claim Date | Date on which claimer claimed |
| Admin Id | Who approved and handled the return |

---

### 5.6 Match Item

| **Attribute** | **Description** |
| --- | --- |
| **Match ID (PK)** | A unique identifier for each match |
| **Lost Item ID (FK)** | Foreign key referencing the lost item |
| **Found Item ID (FK)** | Foreign key referencing the found item |
| Status | Status of the match: **Match**  **Pending**, **Matched**, **Rejected**, **Claimed, Returned** |
| Matched By | Admin who confirmed the match |
| Match Date | Date when the match was created |

## 6. Table Displays:
<img width="850" height="832" alt="4th_normal_form (1)" src="https://github.com/user-attachments/assets/7178d29b-ad80-4cb1-9085-39d871f21a10" />

## 7. Database And Tables:
<img width="278" height="263" alt="Screenshot 2025-05-06 201857" src="https://github.com/user-attachments/assets/6a115ccd-483b-40cc-b996-b97c08ac9f32" />


