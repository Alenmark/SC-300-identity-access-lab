# LAB-006: Delegated Administration with Microsoft Entra PIM

## 1. Lab Overview

| Field | Details |
|---|---|
| Lab ID | LAB-006 |
| Title | Delegated Administration with Microsoft Entra PIM |
| SC-300 Skill Area | Identity and Access Management |
| Platform | Microsoft Entra ID |
| Organisation | Alenmac Consulting (fictional) |
| Status | Completed |

## 2. Business Scenario

Alenmac Consulting wants to delegate day-to-day group administration to an IT support administrator without granting that individual permanent Global Administrator privileges.

The objective is to apply the principle of least privilege by using Microsoft Entra Privileged Identity Management (PIM) to provide eligible access to the Groups Administrator role.

## 3. Objectives

- Create a test security group for delegated administration.
- Assign the Groups Administrator role to a test administrator as an eligible assignment.
- Activate the role through PIM.
- Verify that the administrator can manage group membership.
- Check whether the administrator can initiate a Global Administrator role assignment.

## 4. Implementation

### Step 1 – Create a test security group

Created a security group named `SG-LAB-006-Test`.

- Group type: Security
- Membership type: Assigned
- Purpose: Testing delegated group administration.

### Step 2 – Assign the Groups Administrator role

Assigned the Groups Administrator role to the test administrator, Noah Patel, through Microsoft Entra Privileged Identity Management.

Configuration:

- Assignment type: Eligible
- Membership: Direct
- Duration: Permanent eligibility

This allows the administrator to activate the role when required rather than having it continuously active.

### Step 3 – Activate the eligible role

Signed in as Noah Patel and activated the eligible Groups Administrator assignment through PIM.

The role appeared under Active assignments after activation.

### Step 4 – Test delegated group management

Accessed `SG-LAB-006-Test` while signed in as Noah Patel and successfully managed its membership.

The group membership view confirmed that Emily Clarke and Sophie Williams were members.

### Step 5 – Check privileged role administration

Navigated to the Global Administrator role assignments page while signed in as Noah Patel.

The existing Global Administrator assignment was visible, but the **Add assignments** action was unavailable (greyed out) in the tested interface.

No existing privileged role assignments were modified.

## 5. Screenshots and Evidence

The following evidence is stored in:

`screenshots/LAB-006-delegated-administration/`

| Evidence | Screenshot |
|---|---|
| Eligible Groups Administrator assignment | `LAB-006-03-groups-administrator-eligible.png` |
| Successful delegated group membership change | `LAB-006-04-delegated-group-membership.png` |
| Global Administrator assignment restriction view | `LAB-006-05-global-admin-assignment-restriction.png` |

Include the role activation screenshot as additional evidence if available.

## 6. Testing and Results

| Test | Expected Result | Actual Result |
|---|---|---|
| Assign Groups Administrator role as eligible | Eligible assignment created | Successful |
| Activate eligible role through PIM | Role becomes active | Successful |
| Access test security group | Group is accessible | Successful |
| Manage group membership | Membership can be managed | Successful |
| Initiate Global Administrator assignment | Assignment action unavailable to test administrator | Add assignments was greyed out in the tested interface |

## 7. Lessons Learned

- Microsoft Entra PIM supports just-in-time activation of privileged roles.
- Eligible role assignments reduce the need for continuously active administrative permissions.
- The Groups Administrator role supports delegated group management.
- Administrative responsibilities should be separated to reduce unnecessary privilege.
- Access should be tested after role activation to confirm that the intended permissions are available.

**Security consideration:** The unavailable Add assignments action is evidence from the tested interface. It does not, by itself, establish that every possible method of privileged role assignment is blocked.

## 8. Conclusion

This lab demonstrated how Microsoft Entra PIM can be used to delegate group administration without assigning the test administrator permanent Global Administrator privileges.

The test administrator successfully activated the Groups Administrator role and managed group membership. The Global Administrator assignment interface did not provide the Add assignments action during the final test.

The exercise demonstrates practical experience with privileged role assignments, role activation, delegated administration and least-privilege principles.

## References

- [Microsoft Learn – What is Privileged Identity Management?](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure)
- [Microsoft Learn – Assign Microsoft Entra roles in PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-how-to-add-role-to-user)
