# LAB-009 — Self-Service Password Reset (SSPR)

## 1. Lab Overview

**Objective:** Configure and test Microsoft Entra Self-Service Password Reset (SSPR), allowing users to securely reset their passwords without administrator intervention.

**Environment:** Microsoft Entra ID  
**Organisation:** Alenmac Consulting  
**Test User:** Thomas Walker  
**Test Group:** SG-LAB-009-SSPR-Test

## 2. Configuration

SSPR was enabled for a dedicated test group rather than all users.

| Setting | Configuration |
|---|---|
| SSPR enabled | Selected users |
| Target group | SG-LAB-009-SSPR-Test |
| Methods required for reset | 2 |
| Security questions | Disabled |
| User registration required at sign-in | Yes |
| Reconfirmation interval | 180 days |
| Notify users after password reset | Yes |
| Notify admins of other admin password resets | No |

## 3. Authentication Methods

Two authentication methods were configured and registered for the test user.

| Authentication method | Configuration |
|---|---|
| Microsoft Authenticator | Registered and available |
| SMS | Enabled for SG-LAB-009-SSPR-Test and registered for Thomas Walker |

The SMS authentication policy was restricted to the SSPR test group.

The Temporary Access Pass previously used in LAB-008 was no longer usable and was not counted as an available authentication method.

## 4. Implementation Steps

1. Created the security group SG-LAB-009-SSPR-Test.
2. Added Thomas Walker to the group.
3. Changed SSPR targeting from All users to Selected users.
4. Configured the selected group as the SSPR target.
5. Set the number of authentication methods required to two.
6. Kept security questions disabled.
7. Reviewed registration and notification settings.
8. Enabled SMS authentication for the test group.
9. Registered a phone number for Thomas Walker.
10. Confirmed that Microsoft Authenticator and SMS were available.
11. Accessed the Microsoft SSPR portal as Thomas Walker.

## 5. Testing and Results

| Test | Expected result | Actual result |
|---|---|---|
| SSPR group targeting | Only selected group enabled | Successful |
| SMS verification | User receives and enters verification code | Successful |
| Authenticator verification | User completes second verification | Successful |
| Password reset | User can set a new password | Successful |
| Final sign-in | User can sign in using the new password | Successful |

Thomas successfully completed both verification steps:

- First verification: SMS.
- Second verification: Microsoft Authenticator.

Microsoft then allowed Thomas to choose a new password and displayed the confirmation message:

**Your password has been reset.**

A subsequent sign-in using the new password was also successful.

## 6. Key Learning Points

- SSPR can be scoped to selected security groups rather than enabled tenant-wide.
- Entra administrators can require multiple authentication methods before allowing a password reset.
- Users must have the required authentication methods registered before attempting SSPR.
- Registration and notification settings help maintain accurate recovery information and user awareness.
- Microsoft Authenticator and SMS can be combined to demonstrate two-step verification for password reset.
- Successful completion of the reset process should be followed by a sign-in test using the new password.

## 7. Considerations and Limitations

During configuration, the Entra portal displayed a warning that Microsoft-provided SMS and voice authentication is scheduled for retirement on 1 February 2027.

SMS was used for this practical lab because it was available in the test tenant. It should not be treated as the preferred long-term authentication approach.

Security questions were left disabled. The portal also displayed a notice that security questions are scheduled to retire in March 2027.

## 8. Evidence

Screenshots are stored in the central repository evidence folder.

### Configuration evidence

- [SSPR test group membership](../screenshots/LAB-009-self-service-password-reset/LAB-009-01-sspr-test-group-members.png)
- [SSPR policy scope](../screenshots/LAB-009-self-service-password-reset/LAB-009-02-sspr-policy-scope.png)
- [Two authentication methods required](../screenshots/LAB-009-self-service-password-reset/LAB-009-03-two-methods-required.png)
- [Registration settings](../screenshots/LAB-009-self-service-password-reset/LAB-009-04-registration-settings.png)
- [Notification settings](../screenshots/LAB-009-self-service-password-reset/LAB-009-05-notification-settings.png)
- [SMS authentication policy scope](../screenshots/LAB-009-self-service-password-reset/LAB-009-06-sms-policy-scope.png)
- [Thomas Walker's registered authentication methods](../screenshots/LAB-009-self-service-password-reset/LAB-009-07-user-authentication-methods.png)

### Testing evidence

- [First verification — SMS](../screenshots/LAB-009-self-service-password-reset/LAB-009-08-first-verification-sms.png)
- [Second verification — Microsoft Authenticator](../screenshots/LAB-009-self-service-password-reset/LAB-009-09-second-verification-authenticator.png)
- [New password screen](../screenshots/LAB-009-self-service-password-reset/LAB-009-10-new-password-screen.png)
- [Successful password reset confirmation](../screenshots/LAB-009-self-service-password-reset/LAB-009-11-password-reset-success.png)

## 9. Conclusion

Successfully configured and tested Microsoft Entra Self-Service Password Reset using a dedicated security group.

The test user completed SMS and Microsoft Authenticator verification, successfully reset their password and signed in using the new credentials.

This lab demonstrates how to configure controlled SSPR access, register authentication methods and validate the complete password recovery process.
