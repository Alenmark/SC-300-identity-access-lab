# LAB-014 — Enterprise Application Access Management

## Overview

This lab demonstrates how Microsoft Entra ID can be used to configure an enterprise application and control access through application roles assigned to security groups.

**Scenario:** Alenmac Consulting is configuring a fictional internal expense-management application. Finance employees receive the standard expense-user role, Management employees receive an approver role, and IT employees receive an administrator role.

> **Scope note:** This lab demonstrates Entra application configuration and access assignments. It does not deploy a functioning expense-management application. Therefore, application sign-in, application functionality, and enforcement of the roles by application code were not tested.

## Objectives

- Register an application in Microsoft Entra ID.
- Identify the relationship between an app registration and its enterprise application (service principal).
- Create custom application roles.
- Require explicit assignment to the enterprise application.
- Assign departmental security groups to application roles.
- Review a user's group memberships against the configured assignments.

## Environment

- **Tenant:** Alenmac Consulting
- **Application:** `APP-LAB-015-Alenmac-Expense-Management`
- **Account type:** Accounts in this organisational directory only
- **Resource:** Microsoft Entra ID — App registrations and Enterprise applications

## Implementation

### 1. Application registration

Created `APP-LAB-015-Alenmac-Expense-Management` as a single-tenant application registration.

The corresponding enterprise application (service principal) was available in the tenant after registration.

### 2. Application roles

Created the following enabled application roles. Each role allows assignment to users and groups.

| Display name | Role value | Intended responsibility |
|---|---|---|
| Expense User | `Expense.User` | Submit and view own expenses |
| Expense Approver | `Expense.Approver` | Review and approve submitted expenses |
| Expense Administrator | `Expense.Admin` | Manage expense application settings and users |

Application roles define the role values that an application can use for authorisation. The application itself must be implemented to interpret and enforce these roles.

### 3. Enterprise application properties

Configured the enterprise application with:

| Property | Value |
|---|---|
| Enabled for users to sign in | Yes |
| Assignment required | Yes |
| Visible to users | Yes |

With assignment required enabled, users must be assigned to the enterprise application (directly or through an eligible group assignment) to be granted access through this application assignment configuration.

### 4. Group-to-role assignments

Assigned existing departmental security groups as follows:

| Entra security group | Assigned application role |
|---|---|
| `SG-DEPT-Finance` | Expense User |
| `SG-DEPT-Management` | Expense Approver |
| `SG-DEPT-IT` | Expense Administrator |

The Entra portal displayed a warning that group assignment applies to users directly in the group and does not cascade to nested groups. This is an important consideration when designing group-based application assignments.

## Verification

The following checks were completed:

| User | Department/group membership | Expected assignment outcome | Result |
|---|---|---|---|
| Thomas Walker | Sales (`SG-DEPT-Sales`) | Not included in the three assigned departmental groups | Confirmed |
| Charlotte Lewis | Finance (`SG-DEPT-Finance`) | Expense User | Confirmed |
| Sophie Williams | IT (`SG-DEPT-IT`) | Expense Administrator | Confirmed |
| James Anderson | Management (`SG-DEPT-Management`) | Expense Approver | Confirmed |

Thomas Walker's group-membership page was inspected and showed membership of `SG-DEPT-Sales`, `SG-LAB-007-MFA-Test`, and `SG-LAB-009-SSPR-Test`, as well as the tenant's Alenmac Consulting Microsoft 365 group. He was not shown as a member of the Finance, IT, or Management groups used for the application assignments.

The Finance, IT, and Management memberships for the other three test users were confirmed during the lab. Individual screenshots were not captured for those checks.

### Verification boundary

The checks establish the configured group assignments and the users' relevant group memberships. No live sign-in attempt against a running expense-management application was performed. Consequently, this lab does not claim to have demonstrated an actual blocked sign-in for Thomas or runtime enforcement of the application roles.

## Security and design considerations

- **Least privilege:** Assign each department only the role aligned to its business responsibility.
- **Group-based administration:** Use existing security groups to simplify assignment management rather than assigning every employee individually.
- **Assignment required:** Enable explicit assignment to reduce unintended access to the enterprise application.
- **Nested groups:** Do not assume nested group membership is included in an enterprise application group assignment; the portal warns that the assignment does not cascade.
- **Application enforcement:** Entra can issue application role information, but the application must validate and enforce the roles in its own authorisation logic.
- **Production readiness:** Review role definitions, group ownership, access approval, and periodic access reviews before using this pattern for a production application.

## Outcome

The application registration, three custom application roles, enterprise application assignment requirement, and three departmental group-to-role assignments were configured successfully. User group memberships were checked against the assignments.

This lab demonstrates practical Microsoft Entra enterprise application configuration and group-based application role assignment.

## Evidence

Screenshots are stored in the repository at `screenshots/LAB-014-enterprise-application-access/`.

1. [Application registration overview](../screenshots/LAB-014-enterprise-application-access/LAB-014-01-application-registration-overview.png)
2. [Configured application roles](../screenshots/LAB-014-enterprise-application-access/LAB-014-02-application-roles.png)
3. [Enterprise application properties](../screenshots/LAB-014-enterprise-application-access/LAB-014-03-enterprise-application-properties.png)
4. [Finance group role assignment](../screenshots/LAB-014-enterprise-application-access/LAB-014-04-finance-role-assignment.png)
5. [Department group role assignments](../screenshots/LAB-014-enterprise-application-access/LAB-014-05-department-group-role-assignments.png)
6. [Thomas Walker group memberships](../screenshots/LAB-014-enterprise-application-access/LAB-014-06-thomas-walker-group-memberships.png)
