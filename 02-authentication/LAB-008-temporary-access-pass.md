# LAB-008 — Temporary Access Pass (TAP)

## 1. Lab Overview

**Objective:** Configure and test Microsoft Entra Temporary Access Pass (TAP) to understand how it can provide temporary access for users to register or bootstrap authentication.

**Environment:** Microsoft Entra ID  
**Organisation:** Alenmac Consulting  
**Test User:** Thomas Walker  
**Test Group:** SG-LAB-007-MFA-Test

## 2. Configuration

The existing TAP authentication method policy was reviewed and updated.

| Setting | Configuration |
|---|---|
| TAP enabled | Yes |
| Target | SG-LAB-007-MFA-Test |
| Minimum lifetime | 1 hour |
| Maximum lifetime | 8 hours |
| Default lifetime | 1 hour |
| One-time use | Yes |
| Passcode length | 8 characters |

TAP was restricted to the dedicated test group rather than being available to all users.

## 3. Implementation Steps

1. Enabled Temporary Access Pass under Authentication methods.
2. Restricted the policy to SG-LAB-007-MFA-Test.
3. Configured one-time use.
4. Retained the existing lifetime settings.
5. Opened Thomas Walker's user account.
6. Navigated to Authentication methods.
7. Created a Temporary Access Pass with a one-hour activation duration.
8. Used the TAP to sign in as Thomas Walker.

## 4. Testing and Results

| Test | Expected result | Actual result |
|---|---|---|
| Create TAP | TAP generated successfully | Successful |
| First sign-in | User authenticates using TAP | Successful |
| Reuse TAP | Previously consumed TAP unavailable | TAP was no longer offered as a sign-in option |

The first sign-in completed successfully without an additional prompt to register another authentication method.

On the subsequent sign-in attempt, the TAP option was no longer offered and Microsoft returned the user to the password sign-in screen.

**Note:** An explicit invalid-code error was not observed. The result is recorded as the TAP no longer being offered after its initial use.

## 5. Key Learning Points

- Temporary Access Pass provides time-limited access for authentication setup and account recovery scenarios.
- Administrators can control which users or groups can use TAP.
- TAP lifetime and one-time-use settings are controlled by the authentication method policy.
- One-time TAPs are useful for limiting the exposure of temporary credentials.
- TAP codes must be handled securely and must never be included in screenshots or published documentation.

## 6. Evidence

Screenshots are stored in the central repository evidence folder:

## Evidence

Screenshots are stored in the central repository evidence folder:

- [TAP policy scope](../screenshots/LAB-008-temporary-access-pass/LAB-008-01-tap-policy-scope.png)
- [TAP lifetime settings](../screenshots/LAB-008-temporary-access-pass/LAB-008-02-tap-lifetime-settings.png)
- [TAP creation settings](../screenshots/LAB-008-temporary-access-pass/LAB-008-03-tap-creation-settings.png)
- [Sign-in options after TAP use](../screenshots/LAB-008-temporary-access-pass/LAB-008-04-sign-in-options-after-use.png)
- [TAP no longer offered after use](../screenshots/LAB-008-temporary-access-pass/LAB-008-05-tap-no-longer-offered.png)
## 7. Conclusion

Successfully configured and tested Microsoft Entra Temporary Access Pass using a dedicated test group. Verified the initial TAP sign-in and observed that the one-time TAP was no longer offered during the subsequent sign-in attempt.
