# LAB-013: Microsoft Entra Identity Protection and Risk Monitoring

## 1. Lab Overview

**Objective:** Explore Microsoft Entra Identity Protection, review identity risk monitoring capabilities, and understand how risky users and sign-ins are identified and monitored.

**Environment:** Alenmac Consulting – Microsoft Entra ID

**Lab type:** Practical configuration review and monitoring assessment

## 2. Lab Objectives

- Navigate the Microsoft Entra Identity Protection dashboard.
- Review risky users and understand risk levels.
- Inspect risk detection events.
- Review risky sign-in activity.
- Examine the relationship between Identity Protection and Conditional Access.
- Identify the limitations of testing risk-based protection in the current lab tenant.

## 3. Environment and Configuration

The following Identity Protection areas were reviewed:

| Area | Purpose |
|---|---|
| Identity Protection dashboard | Overview of identity risk and protection activity |
| Risky users | Review users identified as potentially compromised |
| Risk detections | Review detected risk events and associated details |
| Risky sign-ins | Review sign-ins identified as potentially suspicious |
| Conditional Access | Review policies and their current enforcement state |

## 4. Implementation and Testing

### 4.1 Identity Protection Dashboard

Navigated to the Identity Protection dashboard and reviewed the available security metrics.

**Observed results:**
- 0 attacks blocked in the previous 12 months.
- 0 users protected, according to the dashboard metric.
- No agents flagged for risk.
- No high-risk users recorded in the dashboard metrics.

These results reflect the current tenant data and do not demonstrate that all possible identity threats have been tested.

### 4.2 Risky Users

Opened the Risky users section and reviewed the risk-level distribution.

**Observed results:**
- 17 users were displayed in the risk distribution.
- All displayed users were classified as No Risk.
- No high-, medium-, or low-risk user activity was identified in the displayed overview.

### 4.3 Risk Detections

Reviewed the Risk detections page using the available last-month reporting period.

**Observed result:** No risk events were found.

This confirms that the tenant had no recorded risk detection events in the selected reporting period.

### 4.4 Risky Sign-ins

Reviewed the Risky sign-ins page using the available last-month reporting period.

**Observed result:** No results were returned.

No risky sign-in events were available to investigate during this review.

### 4.5 Conditional Access Review

Reviewed the existing Conditional Access configuration to understand how identity risk controls could be applied.

The tenant contained two user-created policies:

| Policy | Purpose | State |
|---|---|---|
| CA-LAB-007-Require-MFA-Test-Users | Test MFA requirements for a test group | Report-only |
| CA-LAB-012-Location-Based-Test | Test location-based access restrictions | Report-only |

No enabled Conditional Access policies were present at the time of review.

The existing policies were deliberately left in Report-only mode. Security Defaults remained enabled, and no tenant-wide security settings were changed.

## 5. Results and Findings

The lab demonstrated how Microsoft Entra Identity Protection provides visibility into identity risk through its dashboard, risky user reporting, risk detections and risky sign-in monitoring.

The review also established that Conditional Access can be used to apply access controls based on identity risk. However, this lab did not configure or enforce a risk-based Conditional Access policy.

No genuine risky sign-in or risk detection event was available in the tenant to demonstrate investigation or remediation.

## 6. Limitations

The following activities were not performed:

- Generating a genuine risky sign-in event.
- Testing automatic remediation of a risky user.
- Enforcing a user-risk or sign-in-risk Conditional Access policy.
- Testing risk-based access controls against a real detected threat.

These activities were excluded to avoid introducing unnecessary security risks or changing the tenant's existing protection settings.

## 7. Key Learning Outcomes

Through this lab, I gained practical familiarity with:

- The Microsoft Entra Identity Protection dashboard.
- Risky user and risky sign-in monitoring.
- Risk detection reporting.
- The relationship between Identity Protection and Conditional Access.
- The importance of reviewing policy impact before enabling security controls.
- The distinction between monitoring identity risk and actively enforcing risk-based remediation.

## 8. Evidence

1. [Identity Protection Dashboard](../screenshots/LAB-013-identity-protection/LAB-013-01-identity-protection-dashboard.png)
2. [Risky Users Overview](../screenshots/LAB-013-identity-protection/LAB-013-02-risky-users.png)
3. [Risk Detections](../screenshots/LAB-013-identity-protection/LAB-013-03-risk-detections.png)
4. [Risky Sign-ins](../screenshots/LAB-013-identity-protection/LAB-013-04-risky-sign-ins.png)
5. [Conditional Access Overview](../screenshots/LAB-013-identity-protection/LAB-013-05-conditional-access-overview.png)
6. [Conditional Access Policies](../screenshots/LAB-013-identity-protection/LAB-013-06-conditional-access-policies.png)

---

**Lab status:** Completed – monitoring and configuration review.

