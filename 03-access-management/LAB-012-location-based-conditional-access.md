# LAB-012: Location-Based Conditional Access

## Overview

This lab demonstrates how Microsoft Entra Conditional Access uses named network locations to evaluate access requests based on a user's sign-in location.

A named location was created using an IPv4 address range and then used in a Conditional Access policy configured to block access when a sign-in originates from that location.

The policy was deliberately left in **Report-only** mode to test its evaluation without enforcing access restrictions or risking administrator lockout.

## Objectives

- Create a named location in Microsoft Entra ID.
- Configure an IP-based network location.
- Create a Conditional Access policy using the named location.
- Configure a Block access grant control.
- Evaluate the policy through sign-in logs.
- Understand the difference between Report-only evaluation and enforced access controls.

## Lab environment

| Setting | Configuration |
|---|---|
| Organisation | Alenmac Consulting |
| Platform | Microsoft Entra ID |
| Test account | Thomas Walker |
| Test group | SG-LAB-007-MFA-Test |
| Emergency access exclusion | SG-Emergency-Access |
| Named location | LOC-LAB-012-Home-Network |
| Policy | CA-LAB-012-Location-Based-Test |
| Policy state | Report-only |

## Implementation

### 1. Create a named location

Navigated to:

**Microsoft Entra ID → Conditional Access → Named locations**

Created the following named location:

- Name: `LOC-LAB-012-Home-Network`
- Location type: IP ranges
- IP range: Single IPv4 address (/32)
- Trusted location: No

The public IP address is intentionally redacted from the published evidence.

### 2. Create the Conditional Access policy

Created a policy named:

`CA-LAB-012-Location-Based-Test`

Configured the assignments as follows:

| Setting | Value |
|---|---|
| Users included | SG-LAB-007-MFA-Test |
| Users excluded | SG-Emergency-Access |
| Target resources | All resources |
| Network condition | LOC-LAB-012-Home-Network |
| Grant control | Block access |
| Policy state | Report-only |

Security Defaults remained enabled throughout the lab.

### 3. Test policy evaluation

Signed in as Thomas Walker using an incognito browser session after creating the policy.

Navigated to the sign-in logs and inspected the resulting sign-in event.

The Location tab confirmed that Microsoft Entra identified the sign-in as originating from:

`LOC-LAB-012-Home-Network`

The Report-only tab showed:

| Policy | Grant control | Result |
|---|---|---|
| CA-LAB-007-Require-MFA-Test-Users | MFA | Report-only: Success |
| CA-LAB-012-Location-Based-Test | Block | Report-only: Failure |

The Report-only Failure result demonstrates that the sign-in matched the location-based policy and would have been blocked if the policy were enforced.

**The sign-in was not actually blocked.** The policy remained in Report-only mode.

## Results

The lab successfully demonstrated:

- Creation of an IP-based named location.
- Association of a named location with a Conditional Access policy.
- Inclusion and exclusion of specific security groups.
- Use of the Block access grant control.
- Evaluation of the policy through Microsoft Entra sign-in logs.
- Identification of a sign-in matching the configured named location.
- Report-only evaluation without enforcing an access restriction.

## Security considerations

- Emergency access accounts were excluded from the test policy.
- Security Defaults remained enabled.
- The Conditional Access policy was not switched to On.
- The public IP address was redacted from published screenshot evidence.
- No production users or access restrictions were affected.

In a production environment, location-based policies should be designed carefully. IP addresses can change, and location alone should not be treated as a definitive indicator of trust.

## Evidence
Screenshots are stored in screenshots/LAB-012-location-based-conditional-access/.
1. [Named locations overview](../screenshots/LAB-012-location-based-conditional-access/LAB-012-01-named-locations-overview.png)
2. [Create home network named location](../screenshots/LAB-012-location-based-conditional-access/LAB-012-02-create-home-network-location.png)
3. [Named location created](../screenshots/LAB-012-location-based-conditional-access/LAB-012-03-named-location-created.png)
4. [Policy target resources](../screenshots/LAB-012-location-based-conditional-access/LAB-012-04-policy-target-resources.png)
5. [Emergency access group exclusion](../screenshots/LAB-012-location-based-conditional-access/LAB-012-05-policy-emergency-exclusion.png)
6. [Named location assigned as network condition](../screenshots/LAB-012-location-based-conditional-access/LAB-012-06-policy-network-condition.png)
7. [Block grant control and Report-only mode](../screenshots/LAB-012-location-based-conditional-access/LAB-012-07-policy-block-grant-report-only.png)
8. [Created policy details](../screenshots/LAB-012-location-based-conditional-access/LAB-012-08-policy-created-details.png)
9. [Sign-in Conditional Access tab](../screenshots/LAB-012-location-based-conditional-access/LAB-012-09-sign-in-conditional-access-tab.png)
10. [Report-only policy evaluation](../screenshots/LAB-012-location-based-conditional-access/LAB-012-10-sign-in-report-only-evaluation.png)
11. [Sign-in location with IP address redacted](../screenshots/LAB-012-location-based-conditional-access/LAB-012-11-sign-in-location-redacted.png)

## Conclusion

This lab demonstrated how Microsoft Entra Conditional Access can use named locations as part of access evaluation.

The test successfully matched a sign-in to the configured home network location and returned a Report-only Failure for the Block access control.

This provided practical experience with location-based access policies while maintaining the tenant's existing security protections.
