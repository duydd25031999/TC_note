# Extreme Programming (XP)

- Extreme Programming is an Agile software-development framework that emphasizes close collaboration, frequent releases, and high code quality.
    - Framework for developing software with agility
    - High level quaity programming
- It embodies the four Agile values: communication, simplicity, feedback, and courage
- XP teams work in very short iterations (often one- to two-week “iterations”)
    - Deliver small increments of value, and embrace change even late in the cycle. 
    - By focusing on technical excellence and customer involvement, XP helps teams respond quickly to evolving requirements while maintaining a robust codebase.

## Pair Programming

- 2 developers work together at one workstation. 
    1. Driver: code writing
    2. Navigator: leading the work

## Code review

- Code review is a systematic examination of someone’s code by one or more peers before merging it into the main codebase.
- Every code need to review before intergrating into Product

## Spike Solutions

- Deal with hard technical problem
1. Run small experiments outside main development
    - Isolation from main development effort
2. Test the theory
    - Mostly code doesn't have production quaity as expecting
    - Keep learning
    - Estimate requirement better

## You aren't gonna need it (YAGNI)

- Avoid adding functionality early on
- Lean thinking & guiding principle
- ⚠️ We should implement something only when we actually need it
- Never in anticipation

# Test-driven development (TDD)

- Agile Software development practice.
- Business requirements = tranfer => test case before programming.
    - Understand interface of the code before doing it
    - Easy to refactor
- Changing requirements or Fixing bugs => FIRST changing tests => adapting the code
- Require higher quality of code.

## Unit testing code

- Unit testing is the practice of writing automated tests for the smallest testable parts of an application (functions, classes, modules) 
    - Before (or immediately after) writing the corresponding production code. 
- Better understanding code = describe it with test case
    - No code is written without adding the associated tests

## Behavior-driven development (BDD)

- Agile Software development practice.
- Have conversations about Business requirement before programming.
- BDD use natural language constructs
    - Create sentences => describe Business requirement in term of Behavior & Expect outcome
    - Behavior ≈ manual test case
    - Share understanding between Business Analyst and Developer

# DevOps

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