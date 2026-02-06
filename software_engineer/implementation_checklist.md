# Implementation Checklist

Use this checklist for every user story you implement. Complete all steps in order.

## Before Coding

- [ ] Read the user story and all acceptance criteria
- [ ] Read the relevant screen spec from [Screen Inventory](../ux_designer/screen_inventory_template.md)
- [ ] Read the relevant flow from [User Flows](../ux_designer/user_flows_template.md)
- [ ] Read the relevant API endpoint(s) from [API Contracts](../head_of_engineering/api_contracts_template.md)
- [ ] Read the relevant entity(ies) from [Data Models](../head_of_engineering/data_models_template.md)
- [ ] Confirm you have all the specs you need — if anything is missing, escalate NOW before starting
- [ ] Create a feature branch: `feature/US-XXX-XX-short-description`

## During Coding

### Backend (if applicable)
- [ ] Migration created for new/modified tables
- [ ] TypeScript interface created/updated in `src/models/`
- [ ] API route created matching contract exactly
- [ ] Controller implements all business logic
- [ ] Request validation in place
- [ ] Response shape matches API contract
- [ ] All error codes from contract handled
- [ ] Authentication/authorization applied where required

### Frontend (if applicable)
- [ ] Screen component created in `src/screens/`
- [ ] Layout matches UX screen spec
- [ ] All elements from spec implemented
- [ ] All states implemented: default, loading, empty, error, success
- [ ] Navigation wired up (comes from / goes to)
- [ ] API service created/updated in `src/services/`
- [ ] Error handling for all API calls
- [ ] No hardcoded strings

### General
- [ ] Naming conventions followed (see [Technical Standards](../head_of_engineering/technical_standards.md))
- [ ] No `any` types in TypeScript
- [ ] No console.log in code
- [ ] Functions under 30 lines where possible
- [ ] File under 300 lines

## After Coding

- [ ] All acceptance criteria verified manually
- [ ] PR checklist from [Technical Standards](../head_of_engineering/technical_standards.md) completed
- [ ] Commit message follows conventional format
- [ ] PR submitted with reference to user story ID
