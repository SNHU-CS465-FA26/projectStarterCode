# DESIGN.md

## Tools

tools and technologies you expect to use

## Data/Services

what data and services will the project require &amp; how will you obtain them?

## Architecture

initial software architecture

## Plan

development plan

### Work

who will do what?

### Milestones

what are your milestones? How will you know if you're on schedule to finish by Dec 15th?

### Order

work sequence

*Legend:*
- `[ ]` Not Started
- `[/]` In Progress
- `[x]` Completed / Verified

***EXAMPLE follows - replace it with your project work sequence***

#### Phase 1: Core System Architecture & Database

- [x] **Task 1.1:** Initialize project repository and configure ESLint/Prettier code styling. *(Completed: 2026-11-02)*
- [x] **Task 1.2:** Design Prisma schema defining `User`, `Task`, and `Subtask` models with constraints. *(Completed: 2026-11-04)*
- [ ] **Task 1.3:** Setup local PostgreSQL Docker instance and execute initial database migrations.

#### Phase 2: Core API Implementation

- [/] **Task 2.1:** Implement API middleware for global JWT authentication & rate limiting.
- [ ] **Task 2.2:** Build `POST /tasks` and `GET /tasks` endpoints with strict schema validation.
- [ ] **Task 2.3:** Implement `PATCH /tasks/:id/status` endpoint safeguarding business logic invariants.

#### Phase 3: Testing & Quality Assurance

- [ ] **Task 3.1:** Write unit test suites achieving >90% line coverage on service layers.
- [ ] **Task 3.2:** Develop end-to-end integration tests simulating invalid failure paths.

---
