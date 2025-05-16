# Extreme Programming (XP)

[1. {Scan} Which situation do we use Extreme Programming?](./Developing_Questions.md#extreme-programming-1)

- Extreme Programming is an Agile software-development framework that emphasizes close collaboration, frequent releases, and high code quality.
    - Framework for developing software with agility
    - High level quaity programming
- It embodies the four Agile values: communication, simplicity, feedback, and courage
- XP teams work in very short iterations (often one- to two-week “iterations”)
    - Deliver small increments of value, and embrace change even late in the cycle. 
    - By focusing on technical excellence and customer involvement, XP helps teams respond quickly to evolving requirements while maintaining a robust codebase.

## Pair Programming

[2. {Scan} Why we need Pair Programming?](./Developing_Questions.md#extreme-programming-2)

- 2 developers work together at one workstation. 
    1. Driver: code writing
    2. Navigator: leading the work

## Code review

[3. {Scan} What is advantage of Code review?](./Developing_Questions.md#extreme-programming-3)

- Code review is a systematic examination of someone’s code by one or more peers before merging it into the main codebase.
- Every code need to review before intergrating into Product

## Spike Solutions

[4. {Scan} How to deal with hard technical problem?](./Developing_Questions.md#extreme-programming-4)

- Deal with hard technical problem
1. Run small experiments outside main development
    - Isolation from main development effort
2. Test the theory
    - Mostly code doesn't have production quaity as expecting
    - Keep learning
    - Estimate requirement better

## You aren't gonna need it (YAGNI)


[5. {Scan} Why do we need to apply YAGNI?](./Developing_Questions.md#extreme-programming-5)

- Avoid adding functionality early on
- Lean thinking & guiding principle
- ⚠️ We should implement something only when we actually need it
- Never in anticipation

# Test-driven development (TDD)

[1. {Scan} When we need Test-driven development?](./Developing_Questions.md#tdd-1)

- Agile Software development practice.
- Business requirements = tranfer => test case before programming.
    - Understand interface of the code before doing it
    - Easy to refactor
- Changing requirements or Fixing bugs => FIRST changing tests => adapting the code
- Require higher quality of code.

## Unit testing code

[2. {Scan} What is the most basic level of test-driven development?](./Developing_Questions.md#tdd-2)

- Unit testing is the practice of writing automated tests for the smallest testable parts of an application (functions, classes, modules) 
    - Before (or immediately after) writing the corresponding production code. 
- Better understanding code = describe it with test case
    - No code is written without adding the associated tests

## Behavior-driven development (BDD)

[3. {Scan} How to develop a feature with native language?](./Developing_Questions.md#tdd-3)

- Agile Software development practice.
- Have conversations about Business requirement before programming.
- BDD use natural language constructs
    - Create sentences => describe Business requirement in term of Behavior & Expect outcome
    - Behavior ≈ manual test case
    - Share understanding between Business Analyst and Developer

### 1. Write the Gherkin Feature

```gherkin
Feature: Todo List                  // describes the high-level capability
  Scenario: Adding a new todo item  //  captures one behavior to drive out code
    Given the todo list is empty
    When I add a new todo with text "Buy milk"
    Then the list should contain an item "Buy milk"
```

## 2. Map Steps to Test Code

```jsx
import React from 'react';
import { defineFeature, loadFeature } from 'jest-cucumber';
import { render, fireEvent, screen } from '@testing-library/react';
import TodoList from '../src/TodoList';

const feature = loadFeature('./tests/features/add_todo.feature');

defineFeature(feature, test => {
  test('Adding a new todo item', ({ given, when, then }) => {
    given('the todo list is empty', () => {
      render(<TodoList />);
      expect(screen.queryByText('Buy milk')).toBeNull();
    });

    when(/^I add a new todo with text "(.*)"$/, (todoText) => {
      fireEvent.change(screen.getByPlaceholderText('Add new todo'), {
        target: { value: todoText }
      });
      fireEvent.click(screen.getByText('Add'));
    });

    then(/^the list should contain an item "(.*)"$/, (todoText) => {
      expect(screen.getByText(todoText)).toBeInTheDocument();
    });
  });
});
```

### 3. Implement the React Component

- Implement code after understanding business and writting test case

# DevOps

[1. {Scan} What does DevOps do in a project?](./Developing_Questions.md#devops-1)

- DevOps is a cultural and technical movement that unites development (Dev) and operations (Ops) into a single, continuous workflow. 
    - Traditionally, developers focus on building features and sysadmins on maintaining infrastructure. 
    - DevOps practitioners span both domains, taking responsibility for the full lifecycle of software—from code check-in through automated build, test, deployment, monitoring, and feedback loops. 
- Key DevOps pillars include:
    - Automation: build, test, and deployment pipelines (CI/CD) to eliminate manual hand-offs and reduce lead time for changes.
    - Infrastructure as Code (IaC): where servers, networks, and configuration are versioned and managed like application code.
    - Continuous Monitoring & Feedback: using telemetry and alerts to detect issues in production early and feed insights back into development.
    - Collaboration & Shared Ownership: breaking down barriers so that developers and operations jointly own uptime and performance
- Developer:
    - Build software
    - Add new feature
    - Know little: infrastructure of software
- SysAdmin:
    - Build & maintain the IT infrastructure
    - Know little: operating of software
- DevOps:
    - DevOps is set of practices => build successful product.
    - Automating Tasks: building & deploying software => CI/CD
    - Move with Agile