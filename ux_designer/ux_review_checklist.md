# UX Review Checklist

Use this checklist to evaluate every screen and flow before handoff to engineering.

## Nielsen's 10 Usability Heuristics

### 1. Visibility of System Status
- [ ] Does the user always know where they are in the app?
- [ ] Are loading states clearly communicated?
- [ ] Is progress shown for multi-step processes?
- [ ] Are success/failure states clearly indicated?

### 2. Match Between System and Real World
- [ ] Is language familiar to the user (not technical jargon)?
- [ ] Do icons and metaphors match user expectations?
- [ ] Is information ordered logically (by user mental model)?

### 3. User Control and Freedom
- [ ] Can the user undo or go back from any action?
- [ ] Is there a clear exit from every flow?
- [ ] Are destructive actions (delete, cancel) confirmed before executing?

### 4. Consistency and Standards
- [ ] Are the same actions represented the same way across screens?
- [ ] Does the app follow platform conventions (iOS/Android)?
- [ ] Are fonts, colors, and spacing consistent?

### 5. Error Prevention
- [ ] Are form inputs validated before submission?
- [ ] Are destructive actions protected with confirmation?
- [ ] Are constraints communicated before the user encounters them?

### 6. Recognition Rather Than Recall
- [ ] Are options visible rather than requiring memory?
- [ ] Does the UI provide context (breadcrumbs, labels, hints)?
- [ ] Are recently used items easily accessible?

### 7. Flexibility and Efficiency of Use
- [ ] Can experienced users take shortcuts?
- [ ] Are common actions easily reachable (1-2 taps)?
- [ ] Is the information hierarchy prioritized by frequency of use?

### 8. Aesthetic and Minimalist Design
- [ ] Does every element serve a purpose?
- [ ] Is visual noise minimized?
- [ ] Is the most important action on each screen obvious?

### 9. Help Users Recognize, Diagnose, and Recover from Errors
- [ ] Are error messages written in plain language?
- [ ] Do error messages suggest a solution?
- [ ] Are errors shown near the relevant input field?

### 10. Help and Documentation
- [ ] Is onboarding provided for first-time users?
- [ ] Are tooltips or help available for complex features?
- [ ] Is help searchable and task-oriented?

## Accessibility Quick Check

- [ ] Touch targets are at least 44x44pt (iOS) / 48x48dp (Android)
- [ ] Color is not the only way to convey information
- [ ] Text contrast meets WCAG AA (4.5:1 for body text)
- [ ] Screen reader labels are defined for interactive elements
- [ ] Font sizes are scalable / support dynamic type
