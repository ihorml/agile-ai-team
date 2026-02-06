# Test Cases

## Test Case Format

Every test case must follow this exact format. This ensures any QA engineer can execute the test without additional context.

```
### TC-[Story ID]-[Number]: [Test Name]

**Related Story**: US-XXX-XX
**Related Screen**: SCR-XXX
**Type**: Functional / UI / API / Edge Case / Error State / Boundary
**Priority**: Critical / High / Medium / Low

**Preconditions**:
- [What must be true before starting this test]
- [e.g., User is logged in, on Home screen, has no existing data]

**Test Steps**:
| Step | Action | Expected Result |
|---|---|---|
| 1 | [What to do] | [What should happen] |
| 2 | [What to do] | [What should happen] |
| 3 | [What to do] | [What should happen] |

**Expected Final State**:
[What the screen/system should look like after all steps]

**Actual Result**: [Fill during execution]
**Status**: Not Run / Pass / Fail / Blocked
**Bug ID** (if failed): BUG-XXX
**Tested On**: [Device, OS version, date]
**Notes**: [Any observations]
```

## Test Case Categories

### Happy Path Tests
Test the standard, expected user journey. One test per acceptance criterion.

### Error State Tests
Test every error scenario defined in the UX screen spec and API contract.

### Edge Case Tests
Test boundary conditions:
- Empty inputs
- Maximum length inputs
- Special characters
- Concurrent actions
- Slow/no network
- Session expiration during action

### UI Compliance Tests
Verify the implementation matches the UX screen spec:
- All elements present
- All states rendered correctly (default, loading, empty, error, success)
- Navigation works as specified
- Touch targets meet minimum sizes

### API Contract Tests
Verify API responses match the contract:
- Correct status codes
- Correct response body shape
- Correct error codes and messages
- Authentication enforcement

## Defined Test Cases

(Fill in as stories are implemented.)
