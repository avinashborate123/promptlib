## Meta Information

title: Code Review
persona: Senior Developer
seniority: Senior
activity: Code Review
sdlc_phase: Testing
language: Angular
version: 1.0
tags: [senior-developer, code-review, angular, mfe, copilot, quality]

## Prompt

Perform an advanced **peer code review** for the Angular component currently open in the editor, specifically designed for a **Micro Frontend (MFE) architecture**.

## Additional Context

This component is part of a **Micro Frontend (MFE) architecture** using Angular and Module Federation. It communicates across multiple MFEs using `CustomEvent`, `sessionStorage`, and sharedservices (`globalEvent`, `AuthorizationService`). The component may run in **embedded or standalone modes** and requires testing under different environments (local, dev, APT). Testing must consider **cross-MFE data flows, environment-based behaviors, and workbench integration contexts** to ensure robust UT coverage.

## Prompt Library1

✅ Ensure **100% coverage** on:
- All **public methods, properties, and lifecycle hooks**
- Positive, negative, and edge cases
- Conditional branches and error handling
- **MFE-specific scenarios**: cross-application communication, embedded mode detection

✅ **MFE-Specific Test Requirements:**
- Mock **custom events** (`CustomEvent`) and `window.addEventListener` scenarios
- Test **sessionStorage** interactions and data persistence across microfrontends
- Verify **globalEvent** service communication patterns
- Mock **environment-based** behavior (dev, localhost, apt modes)
- Test **embedded mode** (`IsEmbeddedMode`) vs standalone scenarios
- Validate **cross-MFE data flow** through EventEmitters and custom events

✅ **Context-Aware Mocking:**
- Mock **AuthorizationService** with realistic response structures
- Create **Router/Location** mocks for navigation testing
- Mock **Globals** service with proper MFE state management
- Simulate **workbench integration** scenarios (WorkBenchUId, EnterpriseId)

✅ **Angular + MFE Best Practices:**
- Use `TestBed` configuration with **module federation** considerations
- Mock **external MFE dependencies** and shared services
- Test **ViewChild** elements and DOM interactions
- Validate **Input/Output** properties for inter-component communication
- Test **async operations** with proper `fakeAsync/tick` usage

✅ **Test Structure:**
- Group tests by **functionality** (account management, navigation, events)
- Include **integration-style** tests for MFE communication flows
- Test **error scenarios** specific to cross-application boundaries
- Validate **cleanup** of event listeners and memory leaks

✅  Edge Cases for MFE:
- Network failures during cross-MFE communication
- Missing or corrupted sessionStorage data
- Invalid account/role data from external systems
- Race conditions in async MFE interactions

✅ Ensure:
- Tests are **ready to run** in the MFE build pipeline
- **Consistent mocking** patterns across the MFE ecosystem
- **Performance-conscious** testing (no real network calls)
- Tests that validate **MFE isolation** and proper encapsulation

## format review as