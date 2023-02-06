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