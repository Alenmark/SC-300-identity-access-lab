# LAB-007: MFA and Authentication Methods

## 1. Lab Overview

| Field | Details |
|---|---|
| Lab ID | LAB-007 |
| Title | MFA and Authentication Methods |
| SC-300 Skill Area | Plan and implement authentication |
| Environment | Microsoft Entra ID |
| Organisation | Alenmac Consulting (fictional) |
| Status | Completed |
| Test Account | Thomas Walker (fictional user) |

## 2. Business Scenario

Alenmac Consulting wants to strengthen its identity security by introducing multifactor authentication (MFA) and modern authentication methods.

The organisation needs to ensure that users can register and use Microsoft Authenticator to approve sign-in requests. It also wants to evaluate a Conditional Access policy that requires MFA for a defined group of users.

A controlled test group is used to validate the configuration without immediately applying changes across the entire organisation.

## 3. Objectives

- Review and configure Microsoft Entra authentication method policies.
- Enable Microsoft Authenticator for users.
- Understand number matching for push notifications.
- Register Microsoft Authenticator for a test user.
- Configure a Conditional Access policy requiring MFA.
- Exclude emergency access accounts from the test policy.
- Validate the Authenticator registration and sign-in experience.
- Understand the difference between Report-only and enforced Conditional Access policies.

## 4. Implementation

### 4.1 Review Authentication Method Policies

Navigated to:

**Microsoft Entra admin centre → Authentication methods → Policies**

Reviewed the available authentication methods and their configuration.

The following methods were observed:

| Authentication method | Configuration observed |
|---|---|
| Passkey (FIDO2) | Enabled |
| Microsoft Authenticator | Enabled |
| SMS | Disabled |
| Temporary Access Pass | Enabled |
| Hardware OATH tokens | Disabled |
| Software OATH tokens | Enabled |
| Voice call | Disabled |
| Password | Enabled |
| Email OTP | Enabled |
| Certificate-based authentication | Disabled |
| Verified ID | Disabled |

Microsoft Authenticator was enabled and targeted to all users.

### 4.2 Review Microsoft Authenticator Configuration

Opened the Microsoft Authenticator policy and reviewed its settings.

The following configuration was observed:

- Microsoft Authenticator enabled.
- Target: All users.
- Registration: Optional.
- Authentication mode: Any.
- Microsoft Authenticator one-time password (OTP): Allowed.
- Number matching for push notifications: Enabled.
- Number matching target: All users.

Number matching helps protect against accidental approval of unexpected authentication requests.

### 4.3 Create MFA Test Group

Created the following security group:

`SG-LAB-007-MFA-Test`

Added the fictional test user Thomas Walker to the group.

The group provides a controlled scope for evaluating the Conditional Access configuration.

### 4.4 Configure Conditional Access Policy

Navigated to:

**Microsoft Entra ID → Conditional Access → Policies**

Created the following policy:

`CA-LAB-007-Require-MFA-Test-Users`

Configuration:

| Setting | Configuration |
|---|---|
| Policy name | CA-LAB-007-Require-MFA-Test-Users |
| Included users and groups | SG-LAB-007-MFA-Test |
| Excluded users and groups | SG-Emergency-Access |
| Target resources | All resources |
| Network conditions | Not configured |
| Conditions | None selected |
| Grant control | Require multifactor authentication |
| Policy state | Report-only |

The emergency access group was excluded to reduce the risk of an emergency administrator account being affected by the test policy.

**Important:** The policy was deliberately left in Report-only mode. The Entra admin centre indicated that Security Defaults were enabled and needed to be disabled before enabling a Conditional Access policy.

Security Defaults were therefore left unchanged to avoid compromising access to the tenant.

Report-only mode evaluates the policy without enforcing its access controls.

### 4.5 Register Microsoft Authenticator

Signed in as the test user, Thomas Walker, using a private browser session.

The registration process involved:

1. Starting the Microsoft Authenticator registration process.
2. Scanning the displayed QR code using Microsoft Authenticator.
3. Responding to the number-matching authentication challenge.
4. Successfully completing the registration process.
5. Confirming that Microsoft Authenticator was added as the default sign-in method.

The registration confirmation displayed a successful Authenticator setup.

### 4.6 Validate MFA Sign-in

Performed a subsequent sign-in using the test account.

Microsoft Authenticator was used to approve the sign-in request through number matching.

The test user successfully completed the authentication process.

This confirmed that Microsoft Authenticator registration and the number-matching sign-in experience were operational.

**Testing limitation:** The Conditional Access policy remained in Report-only mode. The successful MFA sign-in therefore demonstrates the Authenticator experience, but does not establish that the newly created Conditional Access policy enforced the challenge.

## 5. Screenshots and Evidence

Evidence is stored in:

`screenshots/LAB-007-mfa-and-authentication/`

| Evidence | Description |
|---|---|
| LAB-007-01-authentication-method-policies.png | Authentication methods and enabled/disabled settings |
| LAB-007-02-microsoft-authenticator-settings.png | Authenticator targeting and configuration |
| LAB-007-03-mfa-test-group-members.png | Test group membership |
| LAB-007-04-conditional-access-report-only.png | Conditional Access policy and Report-only state |
| LAB-007-05-emergency-access-exclusion.png | Emergency access group exclusion |
| LAB-007-06-number-matching-challenge.png | Authenticator number-matching challenge |
| LAB-007-07-authenticator-registration-success.png | Successful Authenticator registration |

Registration QR codes and other temporary authentication secrets are excluded from the public evidence.

## 6. Testing and Results

| Test | Expected result | Actual result |
|---|---|---|
| Microsoft Authenticator policy review | Authenticator enabled | Passed |
| Number matching configuration | Enabled | Passed |
| Test group configuration | Test user included | Passed |
| Emergency access exclusion | Emergency access group excluded | Passed |
| Conditional Access configuration | MFA grant control configured | Passed |
| Conditional Access enforcement | Policy remains in Report-only mode | Not tested |
| Authenticator registration | User successfully registers Authenticator | Passed |
| Number-matching challenge | User receives and approves challenge | Passed |
| Subsequent test sign-in | User successfully authenticates | Passed |

## 7. Lessons Learned

- Microsoft Entra supports several authentication methods, each with different security and usability characteristics.
- Microsoft Authenticator provides push notification approval and one-time password functionality.
- Number matching provides additional protection against accidental approval of authentication requests.
- Authentication method policies determine which methods users can register and use.
- Conditional Access can be configured to require MFA for specific users or groups.
- Report-only mode allows administrators to evaluate a Conditional Access policy before enforcement.
- Emergency access accounts should be considered when designing Conditional Access policies.
- Security Defaults and Conditional Access need to be considered carefully when planning tenant-wide authentication security.

## 8. Conclusion

This lab demonstrated the configuration and practical testing of Microsoft Authenticator within Microsoft Entra ID.

A dedicated MFA test group and a Conditional Access policy requiring MFA were created. The policy was retained in Report-only mode while Microsoft Authenticator registration and number-matching sign-in were successfully tested using a fictional employee account.

The exercise provided practical experience in authentication method administration, MFA registration, number matching and Conditional Access policy configuration.

## 9. References

- [Microsoft Learn – Authentication methods in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-methods)
- [Microsoft Learn – Microsoft Authenticator authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-authenticator-app)
- [Microsoft Learn – Conditional Access overview](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
- [Microsoft Learn – Conditional Access report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only)
- [Microsoft Learn – Security Defaults](https://learn.microsoft.com/en-us/entra/fundamentals/security-defaults)
