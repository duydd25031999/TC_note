# System Design Concept

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

## System Design

1. Define requirements from the user's perspective.
    - Well document
    - Business banked document
    - Most important feature
2. Reduce these features to data definitions.
    1. Product requirement doc
    2. Features/ abstract concepts
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

# Functional Requirement

## User story

### User Journey

- Hành trình của 1 end user thực hiện các steps trên ứng dụng

1. Xác định mục tiêu chính
1. Xác định End User

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

### Epic

- Group của User stories

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

# High-level Design

- Example: Live Streaming System Design

## 1. Summarizing the requirements

## 2. Core requirement - Streaming video

- Brainstorm what it's going to work
- Issues of it

## 3. Diagramming the approaches

- Sơ đồ hóa cách tiếp cận core features
- Hoàn thiện theo mức độ quan trọng
    - Bắt đầu từ core features 

## 4. Use case - API Design

- Các việc cần làm của hệ thống
- Các bước của nó
- Các vấn đề có thể gặp phải
- Solution có các vấn đề

## 5. Database Design

- Từ Use case => Object cần cho nó => Database

## 6. Choice technique solution

# Low-Level Design 

`Louis design`
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

![UseCaseToService](/UseCaseToService.png)

## 4. Class UML Diagram

1. Dựa vào Service Diagram => Class diagram (Class Name only)
2. Define action & data (abstract)
3. Define method & property (more detail - optional)

## Sequence UML Diagram

- Từ UC document + Service diagram => Workflow