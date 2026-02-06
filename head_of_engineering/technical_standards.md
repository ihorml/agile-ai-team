# Technical Standards

This document defines the coding conventions, project structure, and development process that the Software Engineer MUST follow. No deviations without Head of Engineering approval.

## 1. Folder Structure

```
project-root/
├── src/
│   ├── app/                    # App entry point, navigation
│   ├── components/             # Reusable UI components
│   │   ├── common/             # Buttons, inputs, cards
│   │   └── [feature]/          # Feature-specific components
│   ├── screens/                # Screen-level components (one per screen in inventory)
│   ├── services/               # API calls, external service integrations
│   ├── store/                  # State management
│   ├── models/                 # TypeScript types/interfaces matching data models
│   ├── utils/                  # Helper functions, formatters, validators
│   ├── hooks/                  # Custom React hooks
│   ├── constants/              # App-wide constants, config
│   └── assets/                 # Images, fonts, static files
├── server/                     # Backend (if monorepo)
│   ├── routes/                 # API route definitions
│   ├── controllers/            # Business logic
│   ├── middleware/              # Auth, validation, error handling
│   ├── models/                 # Database models
│   ├── services/               # External service integrations
│   └── utils/                  # Server-side helpers
├── tests/                      # Test files mirror src/ structure
├── docs/                       # Documentation
└── scripts/                    # Build, deploy, seed scripts
```

## 2. Naming Conventions

| Item | Convention | Example |
|---|---|---|
| Files (components) | PascalCase | `UserProfile.tsx` |
| Files (utilities) | camelCase | `formatDate.ts` |
| Files (constants) | camelCase | `appConfig.ts` |
| Variables | camelCase | `userName` |
| Constants | UPPER_SNAKE_CASE | `MAX_RETRY_COUNT` |
| Functions | camelCase (verb-first) | `getUserById()` |
| Components | PascalCase | `UserProfileCard` |
| Database tables | snake_case (plural) | `user_profiles` |
| Database columns | snake_case | `first_name` |
| API routes | kebab-case | `/api/v1/user-profiles` |
| CSS classes | kebab-case or Tailwind | `user-card` |
| TypeScript interfaces | PascalCase with "I" prefix | `IUserProfile` |
| TypeScript types | PascalCase | `UserRole` |
| Enums | PascalCase (members UPPER_SNAKE) | `UserRole.ADMIN` |

## 3. Git & Branching

### Branch Naming
- `main` — production-ready code
- `develop` — integration branch
- `feature/US-XXX-XX-short-description` — feature branches
- `bugfix/US-XXX-XX-short-description` — bug fixes
- `hotfix/description` — production emergency fixes

### Commit Messages
Follow conventional commits:
```
type(scope): description

feat(auth): add login with email
fix(profile): resolve avatar upload crash
docs(api): update endpoint documentation
refactor(utils): simplify date formatter
test(auth): add login flow unit tests
```

### PR Process
1. Branch from `develop`
2. Implement feature (one story per PR when possible)
3. Self-review using the PR checklist
4. Request review
5. Address feedback
6. Squash merge into `develop`

## 4. Code Quality Rules

- No `any` type in TypeScript — always define proper types
- No hardcoded strings — use constants or config
- No business logic in UI components — extract to hooks or services
- Every API call must have error handling
- Every user-facing string must be extractable for localization
- No console.log in committed code — use proper logger
- Functions should do one thing and be under 30 lines when possible
- Maximum file length: 300 lines (split if larger)

## 5. PR Checklist

Before submitting a PR, the Software Engineer must verify:

- [ ] Code follows naming conventions above
- [ ] No TypeScript errors or warnings
- [ ] No hardcoded values
- [ ] Error handling in place for all API calls
- [ ] Loading and error states implemented for all async operations
- [ ] Matches the UX screen spec (all states: default, loading, empty, error)
- [ ] Related user story acceptance criteria are met
- [ ] No console.log or debugging code
- [ ] Types/interfaces match the data model spec
