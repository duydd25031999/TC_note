# High-level Design

### Questions 

[3. {Interrogate} Why is creating a system diagram important during high-level design?](./Presale_Requirement_Question.md/#high-level-design-3)

[5. {Interrogate} Why is database design crucial for system performance and scalability?](./Presale_Requirement_Question.md/#high-level-design-5)

## Concept

[7. {Scan} What is purpose of high-level Design?](./Presale_Requirement_Question.md/#high-level-design-7)

- Focus: System architecture overview
- Audience: Architects, senior developers, stakeholders
- View: "Big picture" - systems, modules, how they connect
- Purpose: Plan system structure, presale process

-----

- Example: Live Streaming System Design

## 1. Analyzing the Business

[1. {Scan} Why is analyzing the idea important before starting system design?](./Presale_Requirement_Question.md/#high-level-design-1)

- Analyzing the ideas => understand the `problem domain`.
- Ask: `What` is the system supposed to achieve?
- Identify: high-level goals, user types, and business needs.
- Avoid thinking about technical solutions too early.

### Example

- Goal: Allow users to broadcast live video and others to view the live feed with minimal delay.
- Target Users: Broadcasters and Viewers.
- Business Need: High availability and minimal latency.

## 2. Summarizing core requirements

[2. {Scan} What is the purpose of identifying core requirements early?](./Presale_Requirement_Question.md/#high-level-design-2)

- Translate main ideas into core functional requirements.
- Differentiate between Must-have and Nice-to-have features.
- Think in terms of what the system must deliver.

### Example

- Must-have:
		- Streamer can broadcast live video.
		- Viewer can watch live stream with minimal delay.
- Nice-to-have:
		- Support for chat during live stream.
		- Multiple video quality options.

## 3. Diagramming the approaches

[8. {Scan} How do you image how system operates?](./Presale_Requirement_Question.md/#high-level-design-8)

- Visualize the core system components and their relationships.
- Focus on data flow, user interactions, and services.
- High-level diagram first, then refine progressively.

### Example

- Diagram basic flow: Broadcaster → Uploads Stream → Streaming Server → Viewer → Receives Stream
- Additional components:
		- Authentication service
		- Chat service (optional)

## 4. Designing main workflow (Use Case/APIs)

[4. {Scan} What are key factors to consider when designing a system’s use cases?](./Presale_Requirement_Question.md/#high-level-design-4)

- Define how users interact with the system.
- Each interaction = a Use Case/APIs.
- Focus on input, processing, and output for each API.

------

- Các việc cần làm của hệ thống
- Các bước của nó
- Các vấn đề có thể gặp phải
- Solution có các vấn đề

### Example
- Use Case 1: Start Live Stream
		- Actor: Broadcaster
		- Description: Broadcaster starts a live video session.
		- API: POST /startStream
		- Input: Broadcaster ID, Stream metadata (title, description)
		- Output: Stream URL, Stream ID
- Use Case 2: Watch Live Stream
		- Actor: Viewer
		- Description: Viewer joins and watches a live video stream.
		- API: GET /watchStream
		- Input: Stream ID
		- Output: Video feed stream
- Use Case 3: Send Chat Message
		- Actor: Viewer
		- Description: Viewer sends a chat message during a live stream.
		- API: POST /sendMessage
		- Input: Stream ID, Viewer ID, Message content
		- Output: Success or failure confirmation
- Use Case 4: End Live Stream
		- Actor: Broadcaster
		- Description: Broadcaster ends the live video session.
		- API: POST /endStream
		- Input: Stream ID
		- Output: Stream status updated to "ended"

## 5. Designing database overview

[9. {Scan} Is main workflow enough to define non-functional requirement and choice technique solution?](./Presale_Requirement_Question.md/#high-level-design-9)

- Map out core entities based on the requirements.
- Identify main relationships (one-to-many, many-to-many).
- Normalize to reduce duplication, but denormalize carefully for performance.

------

- Từ Use case => Object cần cho nó => Database

### Example: Database table

- Users: { user_id, name, role }
- Streams: { stream_id, user_id, start_time, end_time, status }
- Messages: { message_id, stream_id, user_id, content, timestamp }

## 6. Define Non-functional requirement

[6. {Scan} How do you select the right technical solution for a system?](./Presale_Requirement_Question.md/#high-level-design-6)

- Define Non-functional requirement then choice technique solution
- Pick technologies matching system requirements (not trendy tech).
- Consider factors: performance, cost, team expertise, scalability.
- Design for future evolution if possible (extensibility).

### Example

- Video Streaming: Use WebRTC or HLS protocol.
- Backend: Use Node.js with scalable microservices.
- Storage: Use AWS S3 for video storage.

# Presale Process

### Questions

[1. {Interrogate} Describe a challenging presale scenario where conflicting client expectations threatened to derail the engagement. How did you resolve the issues and secure client trust?](./Presale_Requirement_Question.md/#client-presale-1)

## 1. Analyse the idea

[3. {Scan} What is the first step of presale processing?](./Presale_Requirement_Question.md/#client-presale-3)

- Analyze the client’s business needs and ideas in detail to generate effective, well-thought-out proposals.
- Produce a high‑level design.
- Identify any unresolved issues within the initial client concept, confirm uncertainties with the client, and offer additional solution recommendations.

## 2. Break that design into tasks

[4. {Scan} How can you break that design into tasks?](./Presale_Requirement_Question.md/#client-presale-4)

- Leverage standardized project data and shared resources that can be applied across multiple projects to define tasks accurately.

- Balance the client’s requirements with my organization’s capabilities, ensuring that proposals are realistic and mutually beneficial.

## 3. Estimate each task to build the WBS

[5. {Scan} How to make real value for customer while processing presale?](./Presale_Requirement_Question.md/#client-presale-5)


- Encourage team members to document their communications and comments with the client, ensuring a transparent trail of information and decisions.

- Document all assumptions, decisions, and Q&A in dedicated pages for each development phase or version, enabling easy reference and clear evidence for future discussions.

## 4. Compile the plan and contract

- Present plan to the customer for approval

## 5. Implement product

- After customer approves, we start write SRS
- Process [Low-Level-Design](./System_design.md/#low-level-design) and [Functional Requirement](./System_design.md/#Functional-Requirement)

# Presale Quality

## Solution Vision & High-Level Design

[1. {Scan} While processing high-level design, how can you suggest solution for customer?](./Presale_Requirement_Question.md/#presale-quality-1)

- When get the customer’s idea, their vision is the first thing to understand.
	- Focus vision more than understand the solution customer proposes
- Look for ways to improve or adjust solution to match customer's vision, their needs, and their constraints.
- We always study the requirements first, and only after that do we design the solution.

## Task Decomposition & Effort Estimation

[2. {Scan} How can you decide effort for a task on wbs?](./Presale_Requirement_Question.md/#presale-quality-2)

- Break the design into independent, very small tasks so each one can stand alone.
- Watch for repeated / reusable work and cut the effort of those tasks to reflect that reuse.
- Create tasks from both functional and non-functional needs to keep quality visible.
- Base every task on real evidence: the client’s idea, their real constraints, and the high-level design we agreed on.
- Compare with similar projects and use the team’s past experience when defining new tasks. Presale
- If a task relies on an assumption, write that assumption clearly next to the task.
- After Front-end, Back-end, and other roles finish own estimates, the whole team meets to review the numbers before we send them to the customer.

## Risk, Assumption & Non-Functional Requirement Management

[3. {Scan} What are risks you have in presale process?](./Presale_Requirement_Question.md/#presale-quality-3)

[4. {Scan} How can you define non-functional requirements for product?](./Presale_Requirement_Question.md/#presale-quality-4)

- Scope creep: unclear requirements let the project grow beyond plan.
- Wrong estimates: under-estimating effort leads to a shortage of people or budget.
- Technical unknowns: missing details or heavy dependence on third-party services.
- Poor communication: misunderstandings with stakeholders slow decisions.
- Collect NFRs from business goals and the agreed high-level design.
- Link NFRs to the Definition of Done and to performance / security test plans.
- Record every assumption beside the task or design note, then review it with the client to keep risks clear.

## Proposal Documentation & Stakeholder Communication

### Document

[5. {Scan} Which document types are needs in presale process?](./Presale_Requirement_Question.md/#presale-quality-5)

- Business brief: captures the client’s idea and goals.
- High-level design: document to visualise the solution.
- WBS: estimates so cost and timeline are transparent.
- Formal proposal: explains scope and price.
- Q&A / Assumption log: every decision is traceable

### Communication

[6. {Scan} What is common problem do you usually meet in communication with stakeholder while processing presale?](./Presale_Requirement_Question.md/#presale-quality-6)

- Common problem:
	- Mismatched expectations because roles are not clearly defined (Most)
	- Promise unrealitic value / features
	- Missing decision records can cause misunderstandings between our team and the client.
	- Clarify responsibilities - what the customer owns and what our team handles.
	- Note our assumptions clearly and share them early to avoid confusion.
	- Regular check-ins to update each other and make sure everyone stays aligned.
