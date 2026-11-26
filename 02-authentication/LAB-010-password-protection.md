# LAB-010 — Microsoft Entra Password Protection

## 1. Objective

Explore Microsoft Entra Password Protection and understand how the platform helps protect user accounts against weak, commonly used and organisation-specific passwords.

The lab covers password protection configuration, Smart Lockout settings and a practical password rejection test.

## 2. Environment

- **Tenant:** Alenmac Consulting
- **Platform:** Microsoft Entra ID
- **Test account:** Thomas Walker
- **Environment type:** Cloud-only test tenant

## 3. Configuration

The following settings were reviewed and configured in:

**Entra ID → Authentication methods → Password protection**

| Setting | Configuration |
|---|---|
| Smart Lockout threshold | 10 attempts |
| Smart Lockout duration | 60 seconds |
| Enforce custom banned password list | Enabled |
| Custom banned password terms | Alenmac, Alenmac2026, Consulting, WelcomeAlenmac |
| Windows Server AD password protection | Enabled |
| Windows Server AD mode | Audit |

The custom banned password list was enabled and populated with organisation-specific terms.

Windows Server Active Directory password protection was left in Audit mode. No hybrid Active Directory testing was performed.

## 4. Practical Testing

### Test 1 — Password rejection

A password change was attempted using a password considered too common or easy to guess.

**Observed result:**

Microsoft rejected the password and displayed:

"We've seen that password too many times before. Choose something harder to guess."

The troubleshooting panel displayed error code `120018`.

This demonstrates that Microsoft Entra rejected the attempted password. However, the error message does not establish whether the rejection came from Microsoft's global banned password list or the organisation's custom banned password list.

### Test 2 — Smart Lockout configuration review

The Smart Lockout configuration was inspected.

- Threshold: 10 failed attempts
- Duration: 60 seconds

No deliberate account lockout test was performed.

## 5. Results

- Reviewed Microsoft Entra Password Protection settings.
- Enabled the organisation-specific custom banned password list.
- Added four fictional organisation-specific terms.
- Observed a password rejection during a password change.
- Reviewed Smart Lockout configuration.
- Left Windows Server AD password protection in Audit mode.

## 6. Limitations

- The password rejection was observed, but the specific source of the rejection was not confirmed.
- Smart Lockout was reviewed but not practically tested.
- No hybrid Active Directory environment was available for testing.
- No production users or privileged accounts were used for password testing.

## 7. Key Learning Points

- Microsoft Entra Password Protection helps prevent users from choosing weak or commonly used passwords.
- The global banned password list is supplemented by an organisation-specific custom banned password list.
- Smart Lockout helps protect accounts against repeated password guessing attempts.
- Hybrid environments can use password protection for on-premises Active Directory through additional configuration.

## 8. Evidence
Screenshots are stored in the central repository evidence folder:
- [Password Protection configuration, Smart Lockout settings and custom banned list](../screenshots/LAB-010-password-protection/LAB-010-01-password-protection-settings.png)
- [Password rejection and troubleshooting error 120018](../screenshots/LAB-010-password-protection/LAB-010-02-password-rejection-error.png)

## 9. Conclusion

This lab demonstrated the configuration of Microsoft Entra Password Protection, including an organisation-specific banned password list and Smart Lockout settings.

A password rejection was successfully observed. The test provided practical experience of password protection behaviour, while the limitations of the available cloud-only environment were documented.
