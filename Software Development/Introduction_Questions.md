# Introduce Yourself

**Q:** Can you introduce yourself and your work experience

- Vietnamese outline
    - Question:
        - Giới thiệu bản thân
        - Nêu rõ kỹ năng & kinh nghiệm nổi bật
        - Định hướng phát triển
    - Answer:
        - Tên: Duy
        - Vị trí: Senior Front-end Developer, hơn 5 năm kinh nghiệm
        - Công nghệ chính: ReactJS, VueJS, Scrum
        - 1 chút kinh nghiệm Back-end: NodeJS, LaravelPHP, mySQL, mongoDB
        - Lĩnh vực chuyên sâu: Ecommerce, CRM, Chatbot hỗ trợ khách hàng
        - Kinh nghiệm nổi bật: dẫn dắt team nhỏ, tham gia presale với khách hàng, mentoring
        - Định hướng: phát triển song song kỹ năng quản lý kỹ thuật và kỹ năng presale, hướng tới vai trò lãnh đạo dự án và tư vấn giải pháp
- English sample answer:
    - My name is Duy.
    - I am a Senior Front-end Developer with more than five years of experience, mainly focusing on ReactJS, VueJS, and working within Scrum environments.
    - Besides front-end development, I also have some hands-on experience in back-end technologies like NodeJS, Laravel PHP, MySQL, and MongoDB, which helps me understand the full-stack flow and collaborate better across teams.
    - Throughout my career, I have specialized in projects related to Ecommerce platforms, CRM systems, and chatbot solutions, always aiming to deliver user-friendly and high-performance applications.
    - I have had the opportunity to lead small front-end teams, mentor junior developers, and participate directly in presale activities, working closely with clients to understand their business needs and propose technical solutions.
    - Moving forward, I aim to strengthen both my technical leadership and presale consulting skills, with a clear goal of growing into project leadership and solution consulting roles.
    - I’m excited to bring my technical expertise, leadership experience, and client-oriented mindset to contribute to new challenges and opportunities.

# Bespin - Recent Project Overview

### Questions

**Q:** Can you describe your recent project?

- Vietnamese outline
    - Question: Dự án gần đây nhất của bạn
    - Answer:
        - Dự án web chatbot hỗ trợ quản lý server và cloud
        - Front-end: Vue 3, Socket; 
        - Back-end: khách hàng tự phát triển AI server
        - Team tôi phụ trách chủ yếu phần Front-end, UI/UX, Admin system
        - Chúng tôi đồng hành với dự án từ lúc bắt đầu, thiết kế giao diện đầu tiên
        - Sau 2 năm phát triển, dự án đang phát triển web terminal
        - Trách nhiệm mà tôi đã đảm nhiệm: presale, thiết kế high/low-level, phân task, kiểm thử, bàn giao
        - Dự án thành công trong việc gọi vốn nhiều lần
        - Học được nhiều về thích nghi yêu cầu thay đổi nhanh, giao tiếp khách hàng, quản lý nhóm nội bộ
- English sample answer:
    - Project Overview:
        - Worked on a web-based chatbot platform that supports server and cloud management tasks.
        - The chatbot initially answers user prompts using AI, with expert review and enhancement afterward.
    - Technical Stack:
        - Front-end developed with Vue 3 and Socket for real-time interactions.
        - Back-end, including AI server integration, was fully developed by the client.
    - Team Role:
        - Our team mainly handled Front-end development, UI/UX design, and Admin system development.
        - We collaborated from the project's beginning, designing and developing from the very first interface.
    - Project Evolution: After two years of development, the project is currently expanding to build a Web Terminal where users can execute server commands directly from the browser.
    - My Responsibilities:
        - Participated in presale activities for new phases.
        - Designed high-level and low-level solutions for new features.
        - Created work breakdown structures (WBS) for better task management.
        - Assigned tasks and supported internal team collaboration.
        - Implemented, tested, and delivered each phase to the client.
    - Achievements: The project successfully secured multiple rounds of investment, largely based on the demos we developed.
    - Lessons Learned:
        - Improved adaptability to rapid client-driven changes.
        - Enhanced communication skills with clients and stakeholders.
        - Strengthened internal leadership and team management skills under dynamic conditions.

## Project Introduction

### Project Overview

- Project `Bespin` is a web‑based chatbot platform that lets cloud‑focused engineers manage servers and AWS resources through natural‑language conversations.
- Users can query multiple AI models (ChatGPT, Copilot, bespoke LLMs) or escalate to in‑house experts, then execute the resulting commands in a secure, real‑time web terminal.
- Over four phases the product has expanded from basic Q&A to full remote control, attracting investor interest and demonstrating the power of combining AI guidance with human expertise.
- Web chatbot for server and cloud management.
- Dual‑layer answers: AI first, human experts refine.

## Goals

1. `Multi‑Model Q&A` - Support ChatGPT, Copilot, etc., for coding, server, and AWS questions.
2. `Natural‑Language Control` - Convert user queries to shell/CLI commands and execute safely.
3. `AI‑Driven System Design` - Generate architecture diagrams and design documents.
4. `Human Expert Support` - Provide live specialists to augment AI responses.

## Evolution Phases

| Phase | Key Deliverables                                                |
| ----- | --------------------------------------------------------------- |
| 1     | Core chat with AI + expert handoff                              |
| 2     | Multiple AI models, file support, Google Drive integration      |
| 3     | Rich responses (Diagrams, Code, Commands)                       |
| 4     | Web Terminal, remote server/AWS control, OS Copilot integration |

## Technical Stack

- `Front‑end:` Vue 3, Pinia, TailwindCSS, Socket.IO (real‑time)
- `Back‑end:` Client‑owned AI server & REST/WS APIs
- `Security:` JWT auth, RBAC, command sandboxing (future)

## User Roles

- `User` - Devs, DevOps, cloud admins, CTOs: ask questions & deploy commands.
- `Engineer` - In‑house experts: support users and operate as users.
- `Admin` - Configure menus, permissions, languages via separate Admin panel.

## Non‑Functional Requirements

[ ] Tóm gọn đống này lại

- Clean, developer‑oriented UI
- Always‑on, real‑time connectivity
- High security for customer infrastructure links
-	The system will be accessed by public internet users. 
-	All request/response requests should support 128-bit SSL encryption for those pages and processes (e.g. payment) where personal data is transmitted. The requirement for SSL includes both the backend module and the front-end application accessed by users. Both admin module and front-end application sessions should expire after a defined period of inactivity (If any, this will be defined by BESPIN). Individual user IDs should be supported. There must be role-based access control (RBAC) with a hierarchy of privileges (e.g. read only access for some user roles, read/write access for other roles). The administrator should be able to disable/expire any user's ID at any time. 
4.2.	Definition of security level and countermeasures  
-	Application vulnerability 
o	XSS injections 
o	Static IP filter for accessing into production environment. 
o	Authentication: the users use Platform accounts, so security level for account management, password policy... is dependent on the Platform system. 
o	Authorization: the users' permission needs to be verified at both front-end and back-end to prevent unauthorized access. 
o	Session Management: authorization via cookie so the system needs to prevent: 
●	Cookie Poisoning 
●	Session Fixation 
●	Session Hijacking 
o	Input value injections: the system must validate the input value that is transferred between front-end and backend. It must prevent: 
●	Data injection includes SQL injections and XPath injections. 
●	File injections: file upload, file download 
-	Function bypass: parameter and response tampering. 
o	Information leakage: 
●	Development information leakage: included framework, libraries, code, api, internal documents. 
●	Redundant necessary public information. 
o	Encryption: sensitive information needs to be encrypted by a strong method and unpredictable encryption key. They include below items but not all: 
-	Browser-based Security 
o	The users can use the system by browser. From the user’s perspective, the browser acts as their Trusted Computing Base. If the user chooses a suitable browser which they can trust, then the system can be considered “secured”. However, if there is any doubt that a browser is trustable, then all the system’s interaction is impacted and may not be reliably secure. 
o	Same Origin Policy prevents pages from different origins or even iframes on the same page from exchanging information. It is important for the security of both the user and web server. 
-	Authorization and role management 
o	Non-authorized APIs are protected by the API KEY. The API Key is 64 – character length, randomized, different between environments, not stored anywhere except the environment itself. 
o	Permission matrix must be applied and prevents any unauthorized access. Users without permission must be shown the error message about unauthorized access.  
-	Data validation and sanitization 
o	Input data needs to be validated before processing. 
o	Only use known data, not all received data. 
o	String must be trimmed. 
-	Privacy consideration 
o	User’s information collection, transmission, storage, sharing must follow the law of both the user's country, the country that the system located and the company’s country.  
o	The user’s information collection must be accepted by the user. 
o	The system must have functions for user’s information extraction and deletion. They can be processed manually by the system administrator. 
-	Secure Data Storage and Transmission
o	Enforce HTTPS: Ensure data is encrypted during transit.
o	Prudent Data Storage: Avoid storing sensitive information in local storage or client-side cookies.
-	Managing Dependency Vulnerabilities
o	Dependency Audits: Use tools like npm audit or Yarn for detecting and updating vulnerable dependencies.
-	DDOS Protection

4.3.	Network communication  
-	The system must be communicated by using SSL (Secure Sockets Layer) protocol using Public CA. 


## Achievements

- Multiple funding rounds secured through live demos

## Lessons Learned

- Adaptability to rapid change
- Client communication & stakeholder alignment
- Internal leadership under dynamic conditions

## My responsibilities

### Pre-sale

- Trigger: Customer submits a new phase idea.
1. Analyze the idea and produce a high‑level design.
2. Break that design into tasks.
3. Estimate each task to build the WBS.
4. Compile the plan and contract, then present it to the customer for approval.
5. After customer approves, we start write SRS, implement new phase


### Team Lead

- Feature‑development management
- Low‑level design and technical specification
- Task assignment & workload balancing
- Team coordination and daily support

### Senior Front‑End Developer

- Implementation of critical Front-end features
- Testing (unit, integration, manual UAT) and bug‑fixing

# Bespin - Function requirements

## Chat with AI

## AI Model

- Lựa chọn loại AI model để thực hiện giải đáp câu hỏi
- ChatGPT 30
- KKANA3 70B
- Claude 3.5 Sonnet

## AWS Copilot

- (?) AWS Copilot là gì?
- User thao tác với AWS thông qua giao diện Chatbox, với sự hỗ trợ của AWS Copilot

### Workplan

- Giải đáp, quản lý liên qua AWS Workplan
- Có sẵn những AWS Workplan template để khởi tạo
- Sử dụng prompt để tạo ra riêng AWS Workplan cho riêng mình
    - Hệ thống sẽ gợi ý template phù hợp
- Execute AWS Workplan, view Execution plan
- Phân tích kết quả chạy được sau mỗi execute plan bằng AI để cho ra những gợi ý phù hợp
- View được status chạy của từng step
- Có thể save Workplan template của riêng mình
- Work plan có thể edit, tạo form (variable)

## EKS Copilot

- (?) EKS Copilot là gì?
-  As a user, I want to have A chat-based AI assistant that helps me manage my EKS clusters, so that I can efficiently deploy, monitor, and troubleshoot applications in Kubernetes without diving deep into command-line tools or extensive documentation.

## Mermaid

- As a users, I want to see the generated diagram from AI Chat’s response directly without going over code
- When AI chat generate the code representing diagram, the system would use Mermaind library to apply the diagram overriding the code

## Web terminal

### Introduction

- User control EC2 remotely with the help of OS copilot
- Effortlessly manage EC2 instances via a web terminal with intelligent OS Copilot assistance. 
- This feature simplifies remote control, offering context-aware help, suggested commands, integrated file editing

### Activity Flow

1. List EC2 on main chatbot
    1. BE attaches EC2 instance id in AI response with specific format: i-{instance_id}
    2. FE catch EC2 instance id by regex then transform them into a button to open web terminal
2. Open Terminal Popup
    - Web terminal has 2 part
    1. Left: Terminal UI: User run the command on web terminal to remote EC2
    2. Right: Copilot: GPT AI chatbot supports user to control EC2
3. Use Web terminal to remote EC2
    - Web terminal connects directly to AWS EC2 with SSM
    - Every keydown event is sent directly to AWS EC2
    - File Editor: when running a editing file command, open a specific web editor to modify file with support from OS Copilot
4. Use Copilot to suggest command to control EC2
    - System administrator attaches context so that chat OS can read the attached documents to answer questions related to the desired content
    - Suggest command for user to remote. With confirmation, it can be executed without copy into web terminal
5. Edit file with Copilot support
    1. Catch editing file command on Web terminal
    2. Open specific file editor on left side
    3. Edit file on editor
    4. Use Copilot for modification suggest, show copilot response on right side and comparative between original and insert content of left side
    5. Save file
6. Show activity logs
    - Show activity logs history
    - View activity log
    - Download log file

### Challenge

- Elastic Compute Cloud (EC2): a renting virtual computers (instances) service, launch virtual servers 
- AWS Systems Manager (SSM): a comprehensive management service manages and configures AWS resources (EC2 instances, on-premises servers, and virtual machines)
- (?) Advantage and disadvantage of using SSM instead of SSH
- (?) Connect multiple session

