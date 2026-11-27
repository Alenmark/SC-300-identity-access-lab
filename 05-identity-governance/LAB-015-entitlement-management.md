LAB-015 — Entitlement Management: External Access Package
Overview
This lab demonstrates how Microsoft Entra ID Governance entitlement management can package resources and permissions into a governed access request for external users. The scenario uses Alenmac Consulting, a fictional organisation, and an external finance consultant who needs temporary access to finance resources.

Scenario: An external finance consultant requests access to Alenmac Consulting's expense-management application. The access package grants membership of the Finance security group and the Expense User application role. The request is subject to justification and approval, and the resulting assignment is time-limited and reviewed regularly.
Scope note: The access package was created and its configuration reviewed. 

Objectives
- Understand how entitlement management packages resources and access permissions.
- Create an access package in a catalog.
- Add group membership and an enterprise application role as package resources.
- Configure who can request the package and the approval workflow.
- Collect requestor information and justification.
- Configure assignment expiry, extensions, and access reviews.
- Understand how connected organisations support external-user access.
Environment
- Tenant: Alenmac Consulting
- Portal: Microsoft Entra admin center — Identity Governance
- Catalog: General
- Access package: AP-LAB-015-External-Finance-Access
- Enterprise application: APP-LAB-015-Alenmac-Expense-Management
- Group resource: SG-DEPT-Finance
Implementation
1. Access package creation
Created AP-LAB-015-External-Finance-Access in the existing General catalog.

Description: Provides approved external finance consultants with temporary access to Alenmac Consulting Finance resources.

A separate catalog was not created for this exercise. In a production design, catalogs can be used to delegate ownership and organise resources by department, project, or business function.
2. Resource roles
Added the following resources to the package:
Resource	Resource type	Assigned role
SG-DEPT-Finance	Security group	Member
APP-LAB-015-Alenmac-Expense-Management	Enterprise application	Expense User


The package therefore bundles group membership and an application role into one access request.

Design consideration: The Finance group is an existing departmental group. In a production environment, a dedicated group for external application users may provide tighter separation from internal Finance access. This lab retained SG-DEPT-Finance to focus on understanding the entitlement-management workflow and resource-role configuration.

The application role is an Entra assignment. The application must still implement and enforce its own authorisation logic; this lab did not test a live application.
3. Request policy
Configured the package to allow access requests from users in configured connected organisations.

The request policy was configured to allow:
- Self-service requests.
- Administrator assignment.
Requestors must provide justification. The review summary showed approval as required.

Connected organisation dependency: This policy relies on connected organisations being configured in the tenant. The existence and onboarding of a real partner organisation, and an external user's ability to discover and request the package, were not tested as part of this lab.
4. Approval workflow
Configured a single approval stage:
Setting	Configuration
Approval required	Yes
Approval stages	1
Approver	External sponsor
Fallback approver	David Morgan
Decision deadline	14 days
Approver justification	Required
Requestor justification	Required


The portal displayed a licensing notice indicating that using sponsors as approvers requires a Microsoft Entra ID Governance subscription. The workflow configuration was saved, but sponsor approval was not exercised with an external request.
5. Requestor information
Configured two required long-text questions:
1. What is the name of your consulting company?
2. Which Alenmac Finance project or engagement will you be supporting?
These questions collect business context to help reviewers understand who is requesting access and why it is needed.
6. Assignment lifecycle and access reviews
Configured the following lifecycle controls:
Setting	Configuration
Assignment expiry	90 days
Request a specific timeline	No
Allow users to extend access	Yes
Approval required for extension	Yes
Access reviews	Enabled
Review start date	27 November 2026
Review frequency	Monthly
Review duration	14 days
Reviewer	Manager
Fallback reviewer	David Morgan


This configuration combines automatic expiry with recurring review. An extension is possible, but it requires approval.

The access-review schedule was configured but no review cycle was run. The manager reviewer's ability to resolve a review and the fallback process were not tested.
7. Custom extensions
No custom extensions were configured.

Custom extensions can connect entitlement-management events to external workflows, such as Logic Apps or other supported automation. They were outside the scope of this lab and the portal indicated that a Microsoft Entra ID Governance subscription is required.
Verification
The following outcomes were confirmed:
Check	Result
Access package created	Confirmed
Finance security group added with Member role	Confirmed
Expense Management enterprise application added with Expense User role	Confirmed
Request policy configured for users in connected organisations	Confirmed in package configuration
Requestor justification required	Confirmed
Single-stage approval configured	Confirmed
External sponsor and fallback approver configured	Confirmed
Two required requestor questions configured	Confirmed
90-day assignment expiry configured	Confirmed
Monthly access reviews configured	Confirmed
Extension allowed with approval	Confirmed
Custom extensions	Not configured
External request submitted	Not tested
Approval completed	Not tested
Assignment created	Not tested


The Requests and Assignments pages were both empty after creation. This is expected because creating an access package does not itself create a request or grant access. A request must be submitted and approved (where required) before an assignment is created.
Security and design considerations
- Least privilege: Package only the resources and roles required for the engagement.
- Group design: Consider a dedicated external-user group rather than reusing a broad internal departmental group.
- Approval: Use an accountable sponsor or resource owner who can validate the business need.
- Request context: Require meaningful justification and collect project or engagement details.
- Time limitation: Set an expiry date appropriate to the engagement.
- Access reviews: Review external access regularly and remove assignments that are no longer required.
- Extensions: Require renewed approval before extending access.
- Connected organisations: Restrict external requests to trusted partner organisations and verify their configuration.
- Application authorisation: Entra assignment controls access eligibility; the application must enforce its own role permissions.
Outcome
Successfully created an external finance access package containing a Finance group membership and an Expense User application role. Configured request justification, one-stage sponsor approval, requestor questions, a 90-day assignment lifetime, approved extensions, and monthly access reviews.

The lab demonstrates the configuration and governance design of an access package. It does not claim to have tested an end-to-end external request, approval, provisioning, or access-removal lifecycle.
Evidence
Screenshots are stored in screenshots/LAB-015-entitlement-management/.
1. [Identity Governance overview](../screenshots/LAB-015-entitlement-management/LAB-015-01-identity-governance-overview.png)
2. [Access package basics](../screenshots/LAB-015-entitlement-management/LAB-015-02-access-package-basics.png)
3. [Resource roles selection](../screenshots/LAB-015-entitlement-management/LAB-015-03-resource-roles-selection.png)
4. [Resource role assignments](../screenshots/LAB-015-entitlement-management/LAB-015-04-resource-role-assignments.png)
5. [Request settings](../screenshots/LAB-015-entitlement-management/LAB-015-05-request-settings.png)
6. [Approval settings](../screenshots/LAB-015-entitlement-management/LAB-015-06-approval-settings.png)
7. [Lifecycle and access reviews](../screenshots/LAB-015-entitlement-management/LAB-015-07-lifecycle-and-access-reviews.png)
8. [Custom extensions](../screenshots/LAB-015-entitlement-management/LAB-015-08-custom-extensions.png)
9. [Review summary](../screenshots/LAB-015-entitlement-management/LAB-015-09-review-summary.png)
10. [Review details](../screenshots/LAB-015-entitlement-management/LAB-015-10-review-details.png)
11. [Access package created](../screenshots/LAB-015-entitlement-management/LAB-015-11-access-package-created.png)
