# LAB-003: Security Group Management

## 1. Lab Overview

| Field | Details |
|---|---|
| Lab ID | LAB-003 |
| Title | Security Group Management |
| SC-300 Skill Area | Implement and manage user identities |
| Organisation | Alenmac Consulting (fictional organisation) |
| Status | Completed |

## 2. Business Scenario

Alenmac Consulting requires a structured approach to managing employee access across its departments.

Security groups provide a centralised way to organise users and manage access to resources according to departmental responsibilities.

## 3. Objectives

- Create departmental security groups.
- Apply a consistent group naming convention.
- Configure assigned membership.
- Add employees to their respective departmental groups.
- Understand the difference between security groups and Microsoft 365 groups.

## 4. Implementation

### Step 1: Establish a naming convention

Used the prefix `SG-DEPT` to identify departmental security groups.

### Step 2: Create departmental security groups

Created six security groups in Microsoft Entra ID.

| Group Name | Department | Membership Type |
|---|---|---|
| SG-DEPT-Finance | Finance | Assigned |
| SG-DEPT-HR | HR | Assigned |
| SG-DEPT-IT | IT | Assigned |
| SG-DEPT-Management | Management | Assigned |
| SG-DEPT-Operations | Operations | Assigned |
| SG-DEPT-Sales | Sales | Assigned |

### Step 3: Configure group membership

Added the 12 fictional employee accounts to their respective departmental security groups.

Each department has two employees.

Membership was configured as Assigned, meaning users are added and removed through administrative action rather than automatically through a rule.

### Step 4: Review groups

The departmental groups were created as Security groups, providing a separate structure for access management.

## 5. Testing and Results

| Test | Expected Result | Outcome |
|---|---|---|
| Create departmental groups | Six security groups available | Successful |
| Apply naming convention | Consistent SG-DEPT prefix | Successful |
| Configure membership | Assigned membership selected | Successful |
| Allocate employees | Employees added to relevant groups | Successful |

## 6. Lessons Learned

- Security groups simplify the administration of access for multiple users.
- Naming conventions make groups easier to identify and manage.
- Assigned membership requires administrators to manage membership manually.
- Microsoft 365 groups and Security groups serve different purposes.
- Group membership can provide the foundation for assigning access to applications and resources.

## 7. References

- [Microsoft Entra groups documentation](https://learn.microsoft.com/en-us/entra/fundamentals/concept-learn-about-groups)
- [Manage groups in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/groups-manage)

## 8. Evidence

See `screenshots/LAB-003-security-groups.png` for evidence of the departmental security groups and their membership types.
