# LAB-002: User Provisioning and Identity Creation

## 1. Lab Overview

| Field | Details |
|---|---|
| Lab ID | LAB-002 |
| Title | User Provisioning and Identity Creation |
| SC-300 Skill Area | Implement and manage user identities |
| Organisation | Alenmac Consulting (fictional organisation) |
| Status | Completed |

## 2. Business Scenario

The objective is to establish a consistent approach to creating and managing employee accounts, including appropriate identity information and departmental allocation.

## 3. Objectives

- Create employee identities in Microsoft Entra ID.
- Apply a consistent username convention.
- Configure relevant user profile information.
- Allocate employees to their respective departments.
- Establish a foundation for access management through group membership.

## 4. Implementation

### Step 1: Define the employee directory

Created 12 fictional employee accounts across six departments.

| Employee | Job Title | Department |
|---|---|---|
| James Anderson | Managing Director | Management |
| Olivia Bennett | Operations Director | Management |
| Daniel Roberts | IT Manager | IT |
| Sophie Williams | IT Support Analyst | IT |
| Michael Thompson | HR Manager | HR |
| Emily Clarke | HR Officer | HR |
| David Morgan | Finance Manager | Finance |
| Charlotte Lewis | Accountant | Finance |
| Thomas Walker | Sales Manager | Sales |
| Grace Taylor | Sales Executive | Sales |
| Benjamin Harris | Operations Manager | Operations |
| Amelia White | Operations Coordinator | Operations |

### Step 2: Create user accounts

Created the 12 employee accounts in the Microsoft Entra admin centre.

A consistent username convention was used:

`firstname.lastname@organisation-domain`

### Step 3: Configure user accounts

User accounts were created using individual credentials and configured as standard employee identities.

The administrator account used to manage the lab was kept separate from the fictional employee accounts.

### Step 4: Allocate users to departments

Each employee was assigned to the appropriate departmental security group. This provides the foundation for managing access based on organisational responsibilities.

## 5. Testing and Results

| Test | Expected Result | Outcome |
|---|---|---|
| Create employee accounts | 12 accounts created | Successful |
| Apply naming convention | Consistent username format | Successful |
| Allocate employees to departments | Users assigned to relevant groups | Successful |
| Separate admin and employee identities | Employee accounts do not replace the admin account | Successful |

## 6. Lessons Learned

- User provisioning establishes the foundation of identity management.
- Consistent naming conventions make accounts easier to identify and administer.
- User profile information and group membership serve different purposes.
- Separating administrative identities from standard employee accounts supports better security practices.

## 7. References

- [Microsoft Entra ID documentation](https://learn.microsoft.com/en-us/entra/identity/)
- [Microsoft Learn: Add or delete users](https://learn.microsoft.com/en-us/entra/fundamentals/add-users)

## 8. Evidence

Screenshots demonstrating user creation and the employee directory will be stored in the repository's screenshots folder.

Sensitive tenant information, account identifiers and credentials must be excluded from published evidence.
