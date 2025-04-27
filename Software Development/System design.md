# System Design Concept

### Questions

[1. What are the key design challenges you must solve when building a large-scale distributed system?](./Developing_Questions.md#system-design-process-1)

[2. In a distributed system, what are the primary reasons for choosing a distributed architecture over a centralized one?](./Developing_Questions.md#system-design-process-2)

[3. Why are design patterns important in system design, especially for distributed systems?](./Developing_Questions.md#system-design-process-3)

[4. Can you walk me through the general flow you follow when starting a system design from scratch?](./Developing_Questions.md#system-design-process-4)

[5. How would you design a system to be fault-tolerant, and why is it critical in distributed systems?](./Developing_Questions.md#system-design-process-5)

[6. What practices would you apply to make a system easily extensible for future changes?](./Developing_Questions.md#system-design-process-6)

[7. What aspects would you focus on when testing a newly designed system?](./Developing_Questions.md#system-design-process-7)

[8. What is a non-functional requirement, and how is it different from a functional requirement?](./Developing_Questions.md#system-design-process-8)

[9. How do you ensure non-functional requirements are properly addressed during system design?](./Developing_Questions.md#system-design-process-9)


## Large scale distributed systems

### Large scale

- Use a lot or intensive in terms of computer or data or any computer engineering principle
1. Have a lot of data
1. Used by a lot of people
1. Updated frequently
1. A lot of performance expectations

### Distributed systems

- The server or the code that is actually executing this program is not in one place.

## Design patterns

- A software design pattern is a general, reusable solution to a commonly occurring problem within a given context in software design
- Design patterns are particular practices, principles, or processes which are used by engineers to build these systems.
- Design patterns are common solutions for common problems

## System Design flow

1. Define requirements from the user's perspective.
    - Well document
    - Business banked document
    - Most important feature
2. Reduce these features to data definitions.
    1. Product requirement doc
    2. Features/abstract concepts
    3. Data definitions
    4. Object
    5. Database
3. Endpoint
    - API

## Fault Tolerance

- Usually a product requirement document does not define optional or good to have features. 
- These are all core features which are required in the document.
- The good to have features will be probably picked up in the next document
    - Don't need to think of which features are optional

## Extensibility

- How easy it is to change that solution.
- Build a system that can Scale & Extend as and when requirement change

## Testing

- Design should be tested

## Non-functional Requirement

- Non-functional Requirement above Feature of Product
    - Secure
    - Responsive
    - Performance
    - User experience
- Non-functional Requirement can be written in `User Story` with specific acceptance criteria.
- Non-functional Requirement is used to define `Definition of Done`
- Non-functional Requirements have many technical aspects.

# Functional Requirement

## User story

### Questions

[1. In a distributed system with rapidly changing requirements, how would you define and manage user stories to ensure consistent understanding among all team members?](./Developing_Questions.md#functional-requirement-1)

[2. How do you ensure that acceptance criteria are comprehensive and adaptable when dealing with evolving client requirements?](./Developing_Questions.md#functional-requirement-2)

[3. What challenges might occur during backlog refinement when sizing user stories, and how would you address them?](./Developing_Questions.md#functional-requirement-3)

[4. When creating a user story statement, how do you determine the correct level of abstraction to avoid overgeneralization?](./Developing_Questions.md#functional-requirement-4)

### Concept

- A user story or just story is basically the smallest unit of work
- From the client perspective user stories define project or business functions, and delivered in a particular sprint. {Q1}
- Represent a software function that is to be developed.
- Is a sub feature or a situation of a Epic.
- Explained from perspective of user with 3C (3 step process) 

1. Card
    - Description of User Story (main idea)
    - Not clean features ⇒ free adapt
2. Conversation
    - `Card` = brief ⇒ `Point` = reminder ⇒ `What to done`
    - No need detail specification ⇒ Need everyone have same understand
3. Confirmation
    - Acceptance Criteria

### Template

- As a/an `type of user`, I want `some goal`, so that `some reason`
    - As a `manager`, I would like to `learn about JIRA` so that `I can use it to manage project susing agile workflows`
- Background information
    - Reason for User Story - Background of stakeholder
- Acceptance Criteria
    - List of items needed for this story

### Acceptance Criteria

- Test acceptance
- List of items needed for this story
- Acceptance Criteria is for >= 1 function only
- Describe when an item is completed
    - Create by `Product Owner`
    - Commitment for PBI (a part of it also)
- Release PBI only when it meets "Acceptance Criteria" & "Definition of Done"

### Process

1. `Product Owner` define 1 Product Backlog Item as User Story
2. `Product Owner` discuss it with `Scrum Team`
    - Make sense the order
    - Get an estimate (sizing)
        -  Estimate (sizing) = a guess effort necessary ⇒ given task
        - ⚠️ NOT commitment || NOT promise => Uncertainty
    - Use `Product Backlog Refinement`
3. Use “planning poker” technique ⇒ explain why & discuss
    - ⚠️ “Planning poker” point = relative sizing
        - NOT absolute meaning
    - Just point of User Story
        - Complex point

### User story statement

1. Dựa vào User Journey => Actor => `Who`
1. Với 1 step => nhiều actions => `What`
    - Có thẻ step quá abtract => nhiều trường hợp có thể xảy ra || nhiều actions cần thực hiện => nhiều user story
1. Dựa vào thứ tự của action => Purpose => `Why`

```
As a [Who], 
I want to [What], 
So that I can [Why].
```

### Use case detail

- Phát triển từ US statement

I. Description

1. Navigation
    - Đường dẫn tới UC đó (link) 
    - Đường dẫn từ User Journey
2. Design & Diagram
    - Có sẵn Design hoặc Wireframe 
    - Workflow Diagram hoặc cái gì đó có sẵn
3. Business Rules
    - Validation
4. Screen's element liên quan
5. Message, labels, content 

II. Acceptance Criteria

(!) Scenario - Gherkin format
    - Bằng 1 Use case

1. Given
    - Precondition
    - Các step khác cuối
2. When
    - Bước cuối
3. Then
    - Kết quả

## Epic

### Questions

[1. What criteria would you use to decide when a group of user stories should be promoted into an epic?](./Developing_Questions.md#functional-requirement-5)

[2. How would you create a comprehensive user journey to identify potential gaps for writing complete user stories?](./Developing_Questions.md#functional-requirement-6)

### Concept

- Epic is large work wanted to do = group PBIs
    - Significant (Đáng kể) in size
    - Doesn't fit in a sprint
- Epic is Specific feature = can't done 1 print => need few sprints {Q3}
    - Break into many User Story
- ⚠️ Epic not in Product Backlog
    - Group của User stories
    - A big software feature in the product backlog is known as epic.
    - Larger body of work
- 💡 A work is hard to be completed in a sprint - a given iteration.
    - It usually gets broken into multiple user stories.
    - Epics are sub-divided into stories ⇒ `Story = sub-epic`

### User Journey

- Hành trình của 1 end user thực hiện các steps trên ứng dụng

1. Xác định mục tiêu chính
1. Xác định End User


# High-level Design

- Example: Live Streaming System Design

## 1. Analysising the ideas

## 2. Summarizing core requirements

- Ex: Streaming video
- Brainstorm what it's going to work
- Issues of it

## 3. Diagramming the approaches

- Sơ đồ hóa cách tiếp cận core features
- Hoàn thiện theo mức độ quan trọng
    - Bắt đầu từ core features 

## 4. Designing use case (API)

- Các việc cần làm của hệ thống
- Các bước của nó
- Các vấn đề có thể gặp phải
- Solution có các vấn đề

## 5. Designing Database

- Từ Use case => Object cần cho nó => Database

## 6. Choicing technique solution

# Low-Level Design 

- Louis design
- Take small chunks of the system and you try to elaborate on each chunk.
- Chia nhỏ hệ thống và cụ thể hóa mỗi phần 
- What are the actions that a user can perform
    - Các bước có thể hoạt động
    - Các hành động có thể xảy ra 

## 1. Engineering requirements

- Mục tiêu chất lượng mà Product cần đàm bảo

## 2. Use case - UML diagram

1. Actor
2. `actor should do` tree
3. Use case diagram
4. Use case document
    - PRD: Product Requirement Document

## 3. Service diagram

1. List service cần thiết
2. List các API tương ứng với mỗi UC từ service

![UseCaseToService](./image/UseCaseToService.png)

## 4. Class UML Diagram

1. Dựa vào Service Diagram => Class diagram (Class Name only)
2. Define action & data (abstract)
3. Define method & property (more detail - optional)

## Sequence UML Diagram

- Từ UC document + Service diagram => Workflow