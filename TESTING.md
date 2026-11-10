***THIS IS AN EXAMPLE -- USE IT ONLY AS A GUIDE TO BUILD YOURS***

# Full-Stack Application Test Plan: Project Dunderfoof

## 1. Test Strategy & Objectives

This document establishes the testing lifecycle for the full-stack application, ensuring API data integrity, front-end user experience, and overall system security.

### Testing Principles

- **Automation-First:** All API and structural component tests must be automated.
- **Database Isolation:** Integration tests must run against an isolated test database container.
- **Gatekeeping:** A test suite failure blocks deployment to the staging environment.

---

## 2. Test Environment Configuration

### Testing setup

Test tools used, how they are setup, etc.

### Networking setup

...

### Data/Database Configuration

...

---

## 3. Test Suite Progress & Execution Tracking

### Status Code Legend

- `[ ]` = **Not Started**
- `[/]` = **Underway**
- `[x]` = **Finished**

### Phase 1: Backend API Logic & Constraints

- [x] **Test 1.1:** Assert JWT verification blocks requests missing valid Bearer headers.
- [x] **Test 1.2:** Verify input payload sanitization throws 400 Bad Request on invalid data shapes.
- [/] **Test 1.3:** Validate business rule: Block closing a task if child subtasks are open.
 [ ] **Test 1.4:** Execute concurrency testing on status transition endpoints to check for race conditions.

### Phase 2: Frontend Component & State Tests

- [x] **Test 2.1:** Verify authentication state hooks redirect unauthenticated routes to `/login`.
- [/] **Test 2.2:** Assert Kanban board column rendering accurately reflects mock API data payloads.
- [ ] **Test 2.3:** Confirm client-side validation displays real-time inline errors for character limits.

### Phase 3: Full End-to-End (E2E) & Integration Flows

- [ ] **Test 3.1:** Execute complete user journey: Registration -> Login -> Project Creation -> Task Management.
- [ ] **Test 3.2:** Simulate network dropouts and assert clean client-side offline error banner UI.

---

## 4. Test Case Definitions & Execution Steps

### Test 1.3: Prevent Task Closure with Open Subtasks

1. **Setup:** Insert a dummy Task row linked to two active Subtask rows into the isolated database.
2. **Execution:** Dispatch a authenticated `PATCH /tasks/123/status` request payload containing `{"status": "Completed"}`.
3. **Expected Output:** Assert server intercepts request, rejects database execution, and responds with `HTTP 422`:

    ```json
    {
      "error": "UNRESOLVED_BLOCKERS",
      "message": "Cannot close a task while subtasks are still active."
    }
    ```

### Test 2.2: Frontend Column Population

1. **Setup:** Initialize Playwright browser environment and intercept network traffic using MSW returning three tasks.
2. **Execution:** Mount `<KanbanBoard />` component and query DOM layout elements.
3. **Expected Output:** Confirm `.kanban-column-todo` contains exactly three distinct card child nodes.

---

## 5. Deployment Criteria & Success Matrix

### Performance & Target Coverage Boundaries

- **Backend Service Coverage:** Minimum 90% statement/line test coverage required.
- **Frontend Component Coverage:** Minimum 75% coverage tracking key UI user-interactions.

***THIS WAS AN EXAMPLE -- USE IT ONLY AS A GUIDE TO BUILD YOURS***