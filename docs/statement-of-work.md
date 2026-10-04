# Messenger — Statement of Work

- Course: CPS 490 — Capstone I

- Assignment: IA 02 — Messenger: Statement of Work



## 1. Project Purpose and Objectives

#### 1.1 Purpose

Messenger is an application that lets registered users send private messages to each other and chat in groups 

For the first version, I plan to implement basic features such as account registration and login, private messaging, and group chat.

Consider advanced features such as viewing message history and message search.

#### 1.2 Objectives

- Allow users to create an account and log in.

- Allow registered users to send and receive private text messages.

- Allow users to exchange text messages in a group.

- Allow users to view earlier messages in their conversations.

- Keep conversations accessible only to the users who are part of them.



## 2. Stakeholders

#### 2.1 Client in the Assignment Scenario

The client wants a messaging application that supports private messages and group chat. The client's stated needs guide the project scope. Any unclear requirements will be listed as questions or assumptions.

#### 2.2 Intended Users

The intended users are people who register for Messenger to communicate with others. They need to send and receive messages easily and access only the conversations they are part of.

#### 2.3 Student Developer

I am responsible for planning, building, testing, and documenting the application. I need to keep the project manageable and prepare the agreed work for delivery by the deadline.

#### 2.4 Course Instructor

The course instructor provides the assignment requirements and evaluates the submitted work. The instructor checks whether the statement of work is clear, realistic, and consistent with the assignment.



## 3. Scope

#### 3.1 In Scope

The first version of Messenger will include the following features:

- Account registration, login, and logout.

- Private text messaging between two registered users. Users can find another user by their username and start a conversation.

- Basic group chat. Users can create a named group, add registered users, and leave a group. Group members can send and receive text messages within the group.

- Conversation access control. Only the two participants can access a private conversation. Only current group members can access a group conversation.

- A basic interface for opening conversations, reading incoming messages, and sending new messages.

#### 3.2 Out of Scope

If time permits, include these additional features. These features are not part of the committed deliverables for the first version, nor are they mandatory acceptance criteria.

- Voice calls, video calls, and screen sharing.

- Sending images, videos, or other file attachments.

- Message editing, message deletion, and emoji reactions.



## 4. Deliverables

#### 4.1 Working Application and Source Code

A working version of Messenger with the required features listed in Section 3.1. The source code and files needed to run the application will be stored in the course GitHub repository.

#### 4.2 Test Report

A test report showing how the required features were checked. It will include the test steps, expected results, actual results, and whether each test passed or failed. Any known problems will also be listed.

#### 4.3 Setup and User Guide

A short guide explaining how to set up and run Messenger. It will also explain how to create an account, log in and out, start a private conversation, and create, use, and leave a group.



## 5. Assumptions, Constraints, and Dependencies

#### 5.1 Assumptions

The following assumptions are used for planning and still need confirmation:

- The first version will be used by a small group for testing and demonstration.

- Users will have a supported device and a network connection.

- The person creating a group can add registered users directly. The first version will not require an invitation and approval process.

If an assumption is incorrect, I will review its effect on the scope and schedule and update the plan.

#### 5.2 Constraints

- The completed Messenger application must be ready for final delivery no later than November 2, 2026.

- The schedule must leave time for integration, testing, fixes, and final review before delivery.

- The IA02 document and supporting files must be committed and pushed to the individual course GitHub repository by October 12, 2026.

- The application must allow registered users to exchange private messages and participate in group chats.

- Optional features must not delay the required features or the planned delivery.

#### 5.3 Dependencies

- The project needs access to the course GitHub repository to store and submit the work.

- Development and testing need the required software tools and libraries to be available. These will be listed in the setup guide.

- Testing needs multiple test accounts and an environment where users can connect at the same time.

- Questions about unclear course requirements need clarification from the instructor. Until they are answered, any related assumptions will be documented.



## 6. Milestones and Schedule

#### 6.1 Planning Assumptions

- This schedule assumes that I can work on the project regularly throughout the week.

- The dates are planned targets, not a record of completed work.

- Required features will be developed first. Optional features are not included in this schedule.

- Setup and usage instructions will be written during development and finished before the final review.

- The planned delivery date is October 30, 2026. October 31 through November 2 is reserved for unexpected problems.

#### 6.2 Major Milestones

- October 11: Complete the statement of work and Gantt chart for review.

- October 12: Commit and push the IA02 document and supporting files.

- October 13: Complete the basic application design.

- October 24: Have all required features ready for integration and testing.

- October 29: Complete testing, required fixes, the test report, and the setup and user guide.

- October 30: Complete the final review and deliver the application, source code, and documents.

- November 2: Latest allowed final delivery date.

#### 6.3 Gantt Chart

The chart below shows the planned work and its order. Task durations use calendar days, including weekends. Milestones mark when the preceding work should be ready.

```mermaid
%%{init: {"gantt": {"useMaxWidth": false, "useWidth": 1200, "leftPadding": 140, "rightPadding": 180, "barHeight": 22, "barGap": 12, "fontSize": 14, "sectionFontSize": 14}}}%%
gantt
    title Messenger Project Schedule
    dateFormat YYYY-MM-DD
    axisFormat %m/%d
    tickInterval 3day
    todayMarker off

    section Planning
    SOW and schedule    :sow, 2026-10-04, 7d
    SOW ready           :milestone, sow_ready, 2026-10-11, 0d
    Submit IA02         :milestone, ia02, 2026-10-12, 0d
    Basic design        :design, after sow, 2d

    section Development
    Accounts            :accounts, after design, 3d
    Private messages    :private_chat, after accounts, 3d
    Group chat          :groups, after private_chat, 3d
    Access and interface :access, after groups, 2d
    Features ready      :milestone, features_ready, after access, 0d

    section Testing
    Integration tests   :testing, after access, 3d
    Fixes and report    :fixes, after testing, 2d

    section Documents
    Setup and user guide :guide, 2026-10-13, 16d

    section Delivery
    Final review        :review, after fixes guide, 1d
    Planned delivery    :milestone, delivery, after review, 0d
    Final deadline      :milestone, deadline, 2026-11-02, 0d
```

#### 6.4 Dependencies and Readiness

- Account access must work before private messaging can be tested with registered users.

- Group messaging builds on the basic messaging work.

- Integration and full feature testing begin after the required features are ready.

- Testing will cover account access, private messages, group membership, group messages, and attempts to access conversations without permission.

- The final review depends on completing the required fixes, test report, and setup and user guide.

- Delivery will include the working application, source code, test report, and instructions. Any remaining limitations will be documented.




## 7. Acceptance

The project will be considered complete when the required deliverables meet the checks below.

#### 7.1 Statement of Work and Schedule

- The statement of work covers the project purpose, objectives, stakeholders, scope, deliverables, assumptions, constraints, dependencies, schedule, and acceptance criteria.

- The Gantt chart is readable and shows the main tasks, dependencies, milestones, integration, testing, and planned delivery.

- The schedule allows time for fixes and final review before delivery and meets the November 2, 2026 deadline.

#### 7.2 Working Application

The required features will be checked using multiple test accounts:

- A new user can create an account, log in with the correct credentials, and log out. Incorrect credentials are rejected.

- After logging out, the user cannot access conversations without logging in again.

- A registered user can find another user by username and start a private conversation. Both users can send messages and see the messages they receive.

- A third user cannot read or send messages in a private conversation between two other users.

- A user can create a named group and add registered users. At least three group members can exchange text messages.

- A user who is not a group member cannot read or send messages in that group.

- A member can leave a group. After leaving, that user can no longer access the group conversation or send messages to it.

- Users can open their conversations, read incoming messages, and send new messages through the interface.

These checks must pass for the required application features to be accepted.

#### 7.3 Test Report

- The report includes test steps, expected results, actual results, and a pass or fail result for each required feature check.

- Failed checks are recorded. After a fix, the report includes the result of testing the feature again.

- Any remaining problems or limitations are listed clearly. Problems that prevent a required acceptance check from passing must be fixed before delivery.

#### 7.4 Setup and User Guide

- A reviewer can follow the setup instructions to install the required tools, configure the application, and start it.

- The user guide explains registration, login, logout, private messaging, group creation, adding members, and leaving a group.

- The instructions are checked against the delivered version of the application.

#### 7.5 Final Delivery Review

- The source code, required application files, test report, and setup and user guide are committed and pushed to the course GitHub repository.

- The delivered version matches the version used for the final test results.

- Message history across login sessions and message search are optional and are not required for acceptance.
