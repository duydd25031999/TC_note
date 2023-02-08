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