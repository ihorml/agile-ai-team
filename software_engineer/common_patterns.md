# Common Patterns Guide

This document provides step-by-step instructions for recurring implementation tasks. Any engineer should be able to follow these guides without additional context.

---

## Pattern 1: Adding a New Entity / Database Table

**When**: A new data model is defined in the Head of Engineering's data models spec.

### Steps:
1. Check the [Data Models](../head_of_engineering/data_models_template.md) doc for the entity definition.
2. Create a migration file: `migrations/[timestamp]_create_[table_name].sql`
3. Define the table with all columns, types, and constraints from the spec.
4. Add indexes as specified.
5. Create the TypeScript interface in `src/models/[EntityName].ts` matching the schema exactly.
6. Create the database model/ORM definition in `server/models/[EntityName].ts`.
7. Run the migration locally and verify.
8. Add seed data if required for development.

### Checklist:
- [ ] Column names match spec exactly (snake_case in DB)
- [ ] TypeScript interface matches (camelCase in code)
- [ ] All constraints applied (NOT NULL, UNIQUE, defaults)
- [ ] Indexes created
- [ ] Migration has both UP and DOWN scripts
- [ ] Seed data added if needed

---

## Pattern 2: Adding a New API Endpoint

**When**: A new endpoint is defined in the Head of Engineering's API contracts.

### Steps:
1. Check the [API Contracts](../head_of_engineering/api_contracts_template.md) for the endpoint spec.
2. Create the route in `server/routes/[resource].ts`.
3. Create the controller in `server/controllers/[resource]Controller.ts`.
4. Implement request validation (match the spec's request schema).
5. Implement the business logic in the controller.
6. Return the response matching the spec's response schema exactly.
7. Implement all error responses listed in the spec.
8. Add authentication middleware if the spec says "Auth Required: Yes".

### Checklist:
- [ ] Route path matches spec
- [ ] HTTP method matches spec
- [ ] Request body validated
- [ ] Response shape matches spec exactly
- [ ] All error codes from spec are handled
- [ ] Auth middleware applied if required
- [ ] No business logic in route file (controller only)

---

## Pattern 3: Building a New Screen

**When**: A new screen is defined in the UX Designer's screen inventory.

### Steps:
1. Check the [Screen Inventory](../ux_designer/screen_inventory_template.md) for the screen spec.
2. Create the screen file in `src/screens/[ScreenName].tsx`.
3. Build the layout following the spec's layout description (header, body, footer).
4. Add all elements listed in the spec's elements table.
5. Implement all states: default, loading, empty, error, success.
6. Wire up navigation (comes from / goes to) as specified.
7. Connect to the API using the service layer.
8. Handle all interaction behaviors listed in the spec.

### Checklist:
- [ ] All elements from spec present
- [ ] All 5 states implemented (default, loading, empty, error, success)
- [ ] Navigation matches spec
- [ ] Touch targets meet platform minimums (44pt iOS / 48dp Android)
- [ ] No hardcoded strings
- [ ] Error handling for API calls

---

## Pattern 4: Connecting to an API from the Client

### Steps:
1. Create or update the service file in `src/services/[resource]Service.ts`.
2. Define the function matching the API contract.
3. Include proper error handling with try/catch.
4. Parse the response and map to the TypeScript interface.
5. Handle all error codes defined in the API contract.

### Template:
```typescript
// src/services/exampleService.ts
import { apiClient } from './apiClient';
import { IExample } from '../models/Example';

export const getExamples = async (page: number = 1): Promise<IExample[]> => {
  try {
    const response = await apiClient.get(`/api/v1/examples?page=${page}`);
    return response.data;
  } catch (error) {
    // Handle specific error codes from API contract
    throw error;
  }
};
```

---

## Pattern 5: Fixing a Bug from QA

**When**: The QA Engineer reports a bug.

### Steps:
1. Read the bug report — understand reproduction steps, expected vs actual behavior.
2. Create a bugfix branch: `bugfix/US-XXX-XX-short-description`.
3. Reproduce the bug locally.
4. Identify the root cause.
5. Fix the code.
6. Verify the fix matches the expected behavior from the bug report.
7. Check that the fix doesn't break related acceptance criteria.
8. Submit PR with commit message: `fix(scope): description of fix`.
