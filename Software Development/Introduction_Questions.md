# Introduce Yourself

**Q:** Can you introduce yourself and your work experience

- Vietnamese outline
    - Question:
        - Giới thiệu bản thân
        - Nêu rõ kỹ năng & kinh nghiệm nổi bật
        - Định hướng phát triển
    - Answer:
        - Vị trí: Front-end Developer, hơn 5 năm kinh nghiệm
        - Công nghệ chính: ReactJS, VueJS, Scrum
        - 1 chút kinh nghiệm Back-end: NodeJS, LaravelPHP, mySQL, mongoDB
        - Lĩnh vực chuyên sâu: Ecommerce, CRM, Chatbot hỗ trợ khách hàng
        - Kinh nghiệm nổi bật: dẫn dắt team nhỏ, tham gia presale với khách hàng, mentoring
        - Định hướng: phát triển song song kỹ năng quản lý kỹ thuật và kỹ năng presale, hướng tới vai trò lãnh đạo dự án và tư vấn giải pháp
- English sample answer:
    - I’m a Front-end Developer with over five years of experience, mostly in outsourcing projects.
    -  My core technologies are ReactJS, VueJS, TypeScript, RESTful APIs, and Tailwind CSS.
    - I’ve also had hands-on experience with back-end tools like NodeJS, Laravel PHP, MySQL, and MongoDB.
    - Working in outsourcing has taught me how to adapt quickly to different business domains and development styles. 
    - I used to get stuck when specs were vague or designs unclear. But over time, I learned to ask better questions, clarify goals early, and manage uncertainty more confidently. That shift helped reduce misunderstandings and made my contributions more valuable during daily standups and sprint planning.
    - I have had the opportunity to lead small front-end teams, mentor junior developers, and participate directly in presale activities, working closely with clients to understand their business needs and propose technical solutions.
    - Moving forward, I’m excited to grow into a solution-oriented role that blends project leadership with technical consulting, where I can guide both people and product direction.

# Bespin - Recent Project Overview

### Questions

**Q:** Can you describe your recent project?

- Vietnamese outline
    - Question: Dự án gần đây nhất của bạn
    - Answer:
        - Dự án web chatbot hỗ trợ quản lý server và cloud
        - Front-end: Vue 3, Socket
        - Back-end: Python, khách hàng tự phát triển AI server
        - Team tôi phụ trách chủ yếu phần Front-end, UI/UX, Admin system
        - Chúng tôi đồng hành với dự án từ lúc bắt đầu, thiết kế giao diện đầu tiên
        - Sau 2 năm phát triển, dự án đang phát triển web terminal
        - Trách nhiệm mà tôi đã đảm nhiệm: thiết kế high/low-level, phân task, kiểm thử, bàn giao
        - Dự án thành công trong việc gọi vốn nhiều lần
        - Học được nhiều về thích nghi yêu cầu thay đổi nhanh, giao tiếp khách hàng, quản lý nhóm nội bộ
- English sample answer:
    - My last project was building a cloud-native platform designed to assist users working with server and cloud service
    - Integrates an LLM AI model that understands and translate natural words into right commands for cloud service
    - Allows visual tracking of step-by-step execution results with AI-powered feedback.
    - Enables real-time communication through WebSocket for responsive AI command execution.
    - The chatbot initially answers user prompts using AI, with expert review and enhancement afterward.
    - I worked on the front-end using Vue 3 and Socket for real-time interactions.
    - We collaborated from the project's beginning, we setted up Front-end side for this product, designed and developed all the interfaces
    - One challenge I faced was during the early phase, when the client had a rough idea but no detailed SRS. 
    - So I had to organize the information, listing unclear points, and working with the team lead to drive conversations with the client. That helped us align quickly and avoid late misunderstandings and make high-level design for new features
    - From there, I handled the front-end structure, implemented key interactive features, supported testing, and ensured each delivery matched our milestone.
    - I'm proud that this project successfully secured multiple rounds of investment, largely based on the demos we developed
    - Looking back, this was the first time I worked on an AI-integrated developer tool from scratch.
    - I became more confident in client communication, more structured in handling vague specs, and more comfortable leading in a fast-paced team, even when things felt unclear.
## Project Introduction

### Project Overview

- Project `Bespin` is a **web‑based chatbot platform** that lets **cloud‑focused engineers** manage **servers and AWS resources** through **natural‑language conversations**.
- Users can **query multiple AI models (ChatGPT, KKANA3, Claude)** or **escalate to in‑house experts**, then **execute the resulting commands** in a secure, **real‑time AI/CLI assistant**.
- **Over four phases** the product has expanded from **basic Q&A** to **full remote control**, attracting investor interest and demonstrating the **power of combining AI guidance with human expertise**.
- Web chatbot for **server and cloud management**.
- Dual‑layer answers: **AI first, human experts refine**.

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

- `Front‑end:` Vue 3, Pinia, TailwindCSS, Socket (real‑time)
- `Back‑end:` Python, Client‑owned AI server & REST/WS APIs
- `Security:` JWT auth, RBAC, command sandboxing (future)

## User Roles

- `User` - **Devs, DevOps, cloud admins, CTOs**: ask questions & overact with **cloud servise with simple interface**.
- `Engineer` - **In‑house experts**: support users and also operate as users.
- `Admin` - **Configure menus, permissions, languages** via separate Admin panel.

## Non‑Functional Requirements

- **Clean & developer-oriented User interface**: Interface should be **minimalist, intuitive, and optimized for developers’ workflows**.
- **Always-on real-time connectivity**: The system must maintain always-on, low-latency, real-time connections across all user-facing components.
    - End-to-end 128-bit SSL encryption on both FE & BE
    - **WebSocket integration + Session Expiry** for expert/admin layers
- Protection against XSS, Cookie Poisoning, Session Fixation, Hijacking
    - Trusted Browser Assumption + Same-Origin Policy Consideration
- API-level Authorization with 64-character randomized API keys per environment
- Infrastructure & Attack Surface Protection: DDOS protection, dependency vulnerability scanning, and compliance with browser security standards (Same-Origin Policy, Trusted Browsers) must be enforced.

## Challenge and Achievements

- Multiple funding rounds secured through live demos
- **Adaptability to rapid change**
- **Client communication & stakeholder alignment**
- Internal leadership under dynamic conditions

## My responsibilities

### Pre-sale

- Trigger: Customer submits a **new phase idea**.
1. **Analyze the idea** and produce a **high‑level design**.
2. Break that **design into tasks**.
3. **Estimate each task** to build the WBS.
4. Compile the plan and contract, then present it to the customer for approval.
5. After customer approves, we **start write SRS, implement new phase**


### Team Lead

- Feature‑development management
- **Low‑level design** and technical specification
- Task assignment & workload balancing
- **Team coordination and daily support**

### Senior Front‑End Developer

- Implementation of **critical Front-end features**
- **Testing** (unit, integration, manual UAT) and bug‑fixing

# Bespin - Function requirements

## Chat with AI

### Introduction

- Users **chat with an AI** Chatbot to get **support and manage a cloud service**.
- The **interface is similar** to typical AI Chatbots **like ChatGPT**.
- Users can select the instance ID and region to focus the conversation on a specific cloud service, making it easier to manage.
- The response of AI chatbot also has **many type: text, code, graph, workplan form, etc;** based on user's question

### Agent

- `Agent` refers to a **component in an AI system or cloud management assistant**
- The `Agent` can be a background service or AI worker responsible for:
    - **Receiving user prompts**
    - Analyzing the intent, **calling the corresponding API** (e.g., AWS CLI, Copilot CLI)
    - Executing tasks such as **creating services, deploying applications, or monitoring**
    - Sending results back to the chatbot or user interface

### AI Model

- Select the type of AI model to perform question answering
    - ChatGPT 30
    - KKANA3 70B
    - Claude 3.5 Sonnet#

## Freshdesk

- Engineer user can manage **Freshdesk to support customer**
    - Categorize, track, respond to, and resolve tickets
    - Provide a self-service portal for customers
- Engineer user view the details of the ticket and add notes to the ticket.

## AWS Copilot

- **AWS Copilot** is an official **CLI tool** provided by AWS to help developers easily **deploy and manage containerized applications** on services like:
    - Amazon ECS (Elastic Container Service)
    - AWS Fargate
    - App Runner
- With Bespin, interaction with AWS is more easier with Chatbox interface

### AWS Conductor agent

- AWS Conductor is a custom AI-powered agent developed as part of the Bespin platform.
- It acts as a layer that allows users to **control AWS Copilot via natural language or structured forms**. 

### Workplan

- A Workplan is a **structured, deployment plan** that defines what cloud infrastructure to create **configure it, and execute it using AWS Copilot**, all coordinated by AWS Conductor.
    - Users must select `aws_conductor` agent for room chat
- User manages AWS Workplans
    - Access pre-defined **AWS Workplan templates**
    - Generate custom Workplans using natural language prompts
    - System suggests the most relevant template based on intent
- **Execute the Workplan** and view its detailed execution steps
    - AI analyzes execution results and provides actionable suggestions
    - View real-time status of each execution step
- **Save personalized Workplan templates** for future use
- Workplans are editable and support variable-based form generation

## EKS Copilot

- EKS Copilot is a **chat-based AI assistant** that helps developers **interact with Amazon EKS** (Elastic Kubernetes Service) using natural language or form-based inputs - **suggest `kubectl` commands or `Helm` charts**.
-  Users **manage their EKS clusters**, so that they can efficiently deploy, monitor, and troubleshoot applications in Kubernetes without diving deep into command-line tools or extensive documentation.

## Mermaid

- **Generate diagram from nature language prompt** directly without going over code
- When AI chat generate the code representing diagram, the system would use Mermaind library to apply the diagram overriding the code

## Web terminal

### Introduction

- **Elastic Compute Cloud** (EC2): a **renting virtual computers (instances) service**, launch virtual servers 
- **AWS Systems Manager** (SSM): a comprehensive management service **manages and configures AWS resources** (EC2 instances, on-premises servers, and virtual machines)
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

