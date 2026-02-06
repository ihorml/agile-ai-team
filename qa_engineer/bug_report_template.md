# Bug Reports

## Bug Report Format

Every bug must follow this exact format. The goal: any engineer should be able to reproduce the bug within 2 minutes of reading the report.

```
### BUG-[Number]: [Short descriptive title]

**Severity**: Critical / High / Medium / Low
**Status**: Open / In Progress / Fixed / Verified / Closed / Won't Fix
**Related Story**: US-XXX-XX
**Related Test Case**: TC-XXX-XX
**Found On**: [Device, OS, environment]
**Found By**: QA Engineer
**Date Found**: [Date]
**Assigned To**: Software Engineer

**Summary**:
One sentence describing the bug.

**Steps to Reproduce**:
1. [Exact step]
2. [Exact step]
3. [Exact step]

**Expected Result**:
[What should happen according to the spec]

**Actual Result**:
[What actually happened]

**Evidence**:
[Screenshots, error logs, network responses — describe what you captured]

**Frequency**: Always / Intermittent (X out of Y attempts) / Once

**Workaround**: [If any, describe. Otherwise: "None"]

**Additional Context**:
[Any other relevant information — related bugs, possible cause if obvious]
```

## Severity Definitions

| Severity | Definition | Example |
|---|---|---|
| **Critical** | App crashes, data loss, security issue, blocks entire feature | App crashes on login |
| **High** | Feature doesn't work as specified, major UX broken, no workaround | Cannot submit form, button unresponsive |
| **Medium** | Feature partially works, minor UX issue, workaround exists | Wrong error message shown, layout shifts on load |
| **Low** | Cosmetic issue, minor inconsistency, doesn't affect functionality | Typo in label, 1px alignment off, animation jank |

## Bug Lifecycle

```
Open → In Progress → Fixed → Verified → Closed
                  ↘ Won't Fix
         ↗ Reopened (if fix doesn't work)
```

- **Open**: Bug reported, not yet being worked on
- **In Progress**: Software Engineer is working on the fix
- **Fixed**: Engineer says it's fixed, awaiting QA verification
- **Verified**: QA confirmed the fix works
- **Closed**: Bug is resolved
- **Won't Fix**: Product Manager decided not to fix (with documented reason)
- **Reopened**: Fix didn't work or bug reappeared

## Active Bugs

(Fill in as bugs are found.)

| ID | Title | Severity | Status | Story | Assigned |
|---|---|---|---|---|---|
| BUG-001 | | | Open | | |
