# LAB-011 — Microsoft Entra Conditional Access (Report-only)

## 1. Lab Overview

**Objective:** Configure and evaluate a Microsoft Entra Conditional Access policy requiring MFA for a dedicated test group, using Report-only mode.

**Environment:** Microsoft Entra ID  
**Organisation:** Alenmac Consulting  
**Test Group:** SG-LAB-007-MFA-Test  
**Excluded Group:** SG-Emergency-Access

## 2. Policy Configuration

Created the following Conditional Access policy:

**Policy name:** CA-LAB-007-Require-MFA-Test-Users

| Setting | Configuration |
|---|---|
| Users included | SG-LAB-007-MFA-Test |
| Users excluded | SG-Emergency-Access |
| Target resources | All resources |
| Grant control | Require multifactor authentication |
| Policy state | Report-only |

The policy was configured to evaluate sign-ins from the test group without enforcing the grant control.

## 3. Security Defaults

Security Defaults were confirmed as enabled in the tenant.

The existing protection was retained throughout the lab. Security Defaults were not disabled because doing so would require a planned replacement with Conditional Access baseline policies.

Consequently, the Conditional Access policy remained in Report-only mode.

## 4. Policy Impact and Sign-in Evaluation

The Conditional Access Policy Impact page was reviewed.

For 26 November 2026, the displayed results included:

- 7 Report-only success sign-ins (53.85%).
- 6 Report-only not applied sign-ins (46.15%).
- 13 sign-ins in total.

An individual sign-in was then inspected.

The Report-only evaluation showed:

- Policy: CA-LAB-007-Require-MFA-Test-Users
- Grant control: Require MFA
- Result: Report-only: Success

This confirms that Entra evaluated the policy and that the sign-in satisfied the MFA requirement.

Security Defaults provided the active baseline protection. The Conditional Access policy itself did not enforce MFA.

## 5. Key Learning Points

- Conditional Access policies can target specific users and groups.
- Policies can include exclusions, such as emergency-access accounts.
- Grant controls determine the access requirements applied by a policy.
- Report-only mode allows administrators to assess policy impact before enforcement.
- Sign-in logs provide individual policy evaluation results.
- Security Defaults and Conditional Access enforcement require careful planning when transitioning between the two approaches.

## 6. Limitations

- The Conditional Access policy was not enabled for enforcement.
- Security Defaults remained enabled.
- No enforced Conditional Access sign-in challenge was tested.
- Report-only success indicates that the policy requirements were satisfied; it does not prove that this policy independently enforced MFA.

## 7. Evidence

Screenshots are stored in the central repository evidence folder:
- [Conditional Access policies](../screenshots/LAB-011-conditional-access/LAB-011-01-conditional-access-policy.png)
- [Security Defaults enabled](../screenshots/LAB-011-conditional-access/LAB-011-02-security-defaults-enabled.png)
- [Policy impact overview](../screenshots/LAB-011-conditional-access/LAB-011-03-policy-impact-overview.png)
- [Daily policy impact — 26 November 2026](../screenshots/LAB-011-conditional-access/LAB-011-04-daily-policy-impact.png)
- [Individual sign-in Conditional Access results](../screenshots/LAB-011-conditional-access/LAB-011-05-sign-in-conditional-access.png)
- [Report-only policy evaluation](../screenshots/LAB-011-conditional-access/LAB-011-06-report-only-policy-evaluation.png)

## 8. Conclusion

Successfully configured and evaluated a Microsoft Entra Conditional Access policy in Report-only mode.

The exercise demonstrated policy targeting, exclusions, MFA grant controls, policy impact reporting and individual sign-in evaluation while retaining the tenant's existing Security Defaults protection.
