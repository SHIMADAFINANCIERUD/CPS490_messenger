# Messenger — Requirements Engineering

- Course: CPS 490 — Capstone I

- Assignment: IA 03 — Messenger: Requirements Engineering



## 1. System Context

#### 1.1 System Boundary

Messenger lets registered users communicate through private text messages and group chats. The first version includes account registration, login, logout, user lookup by username, private messaging, basic group management, and conversation access control.

The system is responsible for checking who is logged in and whether that user is allowed to access a conversation.

Voice calls, video calls, screen sharing, file attachments, message editing, message deletion, and emoji reactions are outside the first-version scope.

Message history across login sessions and message search are optional features. They are not required for the first version.

#### 1.2 Main Actors

- Visitor: A person who is not logged in. A visitor can register for an account or log in to an existing account.

- Registered User: A person with an account. After logging in, the user can find other users, exchange private messages, create groups, participate in groups they belong to, leave groups, and log out.

- Group Creator: A registered user who creates a group and can add registered users to that group. This is a role within a group, not a separate account type.

#### 1.3 External Systems and Environment

Messenger will run locally on one computer. A server program on that computer will handle accounts, conversations, and messages. Users will interact with it through a browser at a localhost address.

The local server is part of Messenger. It does not require a separate server computer or a paid hosting service.

Testing will use at least three independent browser sessions with different user accounts. Separate browsers or isolated browser profiles will be used so that the accounts can remain logged in at the same time.

Once the required software is installed, the application will work locally without an internet connection. The local server must be running for messaging to work.

The first version will not require access from other computers or connections to external messaging services.

GitHub will be used to store and submit project files. Internet access is needed to push files to GitHub, but GitHub is not needed for local messaging.

The setup guide will identify the supported operating system, browser, required software, and steps for starting the application.

#### 1.4 Relationship to the Statement of Work

These requirements describe the same first version defined in the [Statement of Work](statement-of-work.md).

If a requirement changes the agreed project scope, the statement of work will also be updated. Changes will be recorded through Git history.



## 2. Functional Requirements

#### 2.1 Account Access

- FR-01: The system shall allow a visitor to create an account using a username and password.

- FR-02: The system shall reject registration if the username is already used by another account.

- FR-03: The system shall allow a registered user to log in with the correct username and password.

- FR-04: The system shall reject a login attempt when the username or password is incorrect.

- FR-05: The system shall allow a logged-in user to log out and end the current session.

- FR-06: The system shall deny access to conversations when the user is not logged in.

#### 2.2 User Lookup and Private Messaging

- FR-07: The system shall allow a logged-in user to find another registered user by entering that user's exact username.

- FR-08: The system shall allow a logged-in user to start a private conversation with another registered user found through user lookup.

- FR-09: The system shall allow either participant in a private conversation to send text messages to the other participant.

- FR-10: The system shall display messages exchanged during an active private conversation to both participants.

- FR-11: The system shall prevent users other than the two participants from reading or sending messages in that private conversation.

#### 2.3 Group Chat

- FR-12: The system shall allow a logged-in user to create a named group, with the creator included as its first member.

- FR-13: The system shall allow the group creator to add registered users to the group.

- FR-14: The system shall allow current group members to send text messages to the group.

- FR-15: The system shall display new group messages to current members who have the group conversation open.

- FR-16: The system shall allow a current member to leave a group and remove that user from the group's membership.

- FR-17: The system shall deny requests to read or send group messages from users who are not current members, including users who have left the group.

#### 2.4 Conversation Interface

- FR-18: The system shall show a logged-in user a list of their private conversations and the groups they currently belong to.

- FR-19: The system shall allow a logged-in user to select a conversation from that list and open it to read and send messages.

These requirements cover the required first-version features. Retrieving messages from previous login sessions and searching message content are not required.



## 3. Non-functional Requirements

#### 3.1 Performance

- NFR-01: With three independent user sessions on the same computer, at least 95 out of 100 valid test messages shall appear in all intended recipients' open conversations within 2 seconds after the sender selects Send.

#### 3.2 Password Protection

- NFR-02: The system shall store passwords as salted password hashes, not as readable text. Passwords shall not appear in application logs or error messages.

#### 3.3 Access Protection

- NFR-03: The system shall check the user's login status and conversation membership for every request to read or send messages. Unauthorized requests shall be rejected even when they are made directly instead of through the interface.

#### 3.4 Message Reliability

- NFR-04: During a test of 100 valid messages while the local server is running and intended recipient sessions are active with their conversations open, every message shall appear exactly once in each intended recipient's conversation,
with the correct sender and unchanged text. The test shall include both private and group messages.

#### 3.5 Usability

- NFR-05: Using only the setup and user guide after the application is running, a first-time user shall be able to create an account, log in, send a private message, and create a group within 10 minutes without help from the developer.
A second test account shall be available for the private message.

#### 3.6 Verification Conditions

The performance, reliability, and usability targets above are proposed engineering decisions for the first version.

The test report will record the computer, operating system, browser versions, local server setup, session conditions, test steps, and results so that the checks can be repeated.

The messaging tests apply to active conversations. They do not require message history to remain available after logout or an application restart.



## 4. Acceptance Criteria

#### 4.1 Test Setup

- Run the Messenger server locally on one computer.

- Use three independent browser sessions with test accounts named Alice, Bob, and Charlie.

- Record the test environment, steps, expected results, actual results, and pass or fail status.

- The checks below are planned acceptance tests, not completed test results.

#### 4.2 Account Access

- AC-01 (FR-01, FR-02): Register an account with an unused username and password. The account is created successfully.
Try registering another account with the same username. The system rejects the duplicate registration.

- AC-02 (FR-03, FR-04, FR-06): Log in with correct credentials. The system allows access to the user's conversations.
Try an incorrect password and an unknown username. Both attempts are rejected, and conversation access remains unavailable.

- AC-03 (FR-05, FR-06): Log out, then try to reopen a conversation and request its messages using the previous session. The system rejects access until the user logs in again.

#### 4.3 Private Messaging and Navigation

- AC-04 (FR-07, FR-08, FR-18, FR-19): Alice enters Bob's exact username and starts a private conversation with him. The conversation appears in their conversation lists, and both users can select and open it.

- AC-05 (FR-09, FR-10, FR-11): Alice and Bob exchange text messages with the conversation open. Both users can see the exchanged messages. Charlie cannot open, read, or send messages in their private conversation.

#### 4.4 Group Chat

- AC-06 (FR-12, FR-13): Alice creates a named group. Alice is included as its first member and can add Bob and Charlie using their registered accounts.

- AC-07 (FR-14, FR-15, FR-18, FR-19): The group appears in each member's conversation list. All three users open it and send messages. Each member can see the messages exchanged in the group.

- AC-08 (FR-16, FR-17, FR-18): Charlie leaves the group. The group disappears from Charlie's current group list. Requests from Charlie to read or send group messages are rejected, including requests made from a previously opened group page.

#### 4.5 Access and Password Protection

- AC-09 (NFR-02): Inspect stored account data and logs generated during registration, login, and failed login tests. Passwords are stored as salted hashes rather than readable text, and the tested passwords do not appear in logs or error messages.

- AC-10 (NFR-03): Make direct requests to read and send messages without using the normal interface. Test a logged-out session, Charlie accessing Alice and Bob's private conversation, and Charlie accessing the group after leaving.
Every unauthorized request is rejected, and no protected message content is returned.

#### 4.6 Performance and Reliability

- AC-11 (NFR-01, NFR-04): Keep three independent user sessions logged in on the same computer. With the intended recipients' conversations open, send 50 private messages and 50 group messages. Record how long each message takes to appear for all intended recipients.
At least 95 of the 100 messages appear for all intended recipients within 2 seconds. All 100 messages appear exactly once for each intended recipient, with the correct sender and unchanged text.

#### 4.7 Usability

- AC-12 (NFR-05): With the application already running and a second test account available, ask a first-time user to follow the guide to register, log in, send a private message, and create a group. The user completes all four tasks within 10 minutes without help from the developer.

#### 4.8 Acceptance Decision

- All required acceptance checks must pass before the first version is considered complete.

- Failed checks must be recorded, corrected, and repeated. The final report must show the updated results.

- Message history across login sessions and message search are not required to pass acceptance.



## 5. Assumptions and Unresolved Questions

#### 5.1 Assumptions

- A-01: The development computer can run the local server and at least three independent browser sessions at the same time. This will be checked during setup.

- A-02: The required software can be installed before testing. Internet access may be needed for installation and GitHub submission, but not for local messaging after setup.

- A-03: A person who has not used Messenger before will be available for the usability test.

These assumptions have not been confirmed by the client in the assignment scenario. If an assumption is incorrect, its effect on the requirements and schedule will be reviewed.

#### 5.2 Documented Engineering Decisions

- ED-01: The first version will be a local web application running on one computer. Public hosting and access from other computers are outside the first-version scope.

- ED-02: Accounts will use unique usernames and passwords. User lookup will use an exact username rather than partial-name search.

- ED-03: A group creator will automatically become a member and can add registered users directly. Invitations and approval by the added user are not included in the first version.

- ED-04: Access checks will be enforced by the server, not only by hiding interface controls. Passwords will be stored as salted hashes.

- ED-05: The performance target is based on three local user sessions and 100 test messages. The usability target is completion of the listed basic tasks within 10 minutes.

- ED-06: Message history across login sessions and message search remain optional. Current conversation messages must still be visible as described in the functional requirements.

These are proposed engineering decisions for a manageable first version. They are not claims that the client explicitly requested or approved these details.

#### 5.3 Unresolved Questions

- Q-01: If a group creator leaves the group, who can add new members afterward? Leaving the group must remain possible, but ownership transfer has not been defined.

- Q-02: Should usernames be case-sensitive? For example, should Alice and alice identify the same account? Registration, login, and user lookup must use a consistent rule.

- Q-03: What should happen to a message when its recipient is disconnected or does not have the conversation open? Offline delivery and later retrieval are not currently promised.

- Q-04: Which data must remain available after the server restarts? Message history is optional, but restart behavior for accounts, groups, and memberships still needs to be defined.

- Q-05: Which operating system, browser versions, and computer specifications will be used for acceptance testing? These must be recorded before performance and usability results are evaluated.

#### 5.4 Handling Open Questions

- Questions about course expectations will be raised with the instructor when clarification is needed.

- When a scenario detail has no available stakeholder answer, I will record a reasonable engineering decision and its reason rather than claim that the client approved it.

- Decisions that change required behavior will be reflected in the functional requirements and acceptance criteria.

- Any change to the project scope will also be reflected in the statement of work.

- Existing requirement identifiers will be kept stable so that later documents can refer to them.



## 6. Traceability

#### 6.1 Sources

The tables below connect each requirement to its source and acceptance checks.

- SOW refers to the [Statement of Work](statement-of-work.md).
- ED refers to the engineering decisions in Section 5.2 of this document.
- AC refers to the acceptance criteria in Section 4 of this document.

A requirement may come from the project scope or a documented engineering decision. It does not have to be a direct statement from the client.

#### 6.2 Functional Requirement Traceability

| Requirement | Source and Reason | Acceptance Checks |
| --- | --- | --- |
| FR-01 | SOW 3.1 requires account registration. ED-02 defines username and password accounts. | AC-01 |
| FR-02 | ED-02 requires unique usernames so that accounts can be identified correctly. | AC-01 |
| FR-03 | SOW 3.1 requires login. ED-02 defines the login credentials. | AC-02 |
| FR-04 | SOW 3.1 requires controlled account access. Incorrect credentials must not grant access. | AC-02 |
| FR-05 | SOW 3.1 includes logout. | AC-03 |
| FR-06 | SOW 3.1 requires conversation access control. Users must be logged in to access conversations. | AC-02, AC-03, AC-10 |
| FR-07 | SOW 3.1 includes user lookup by username. ED-02 specifies exact username lookup. | AC-04 |
| FR-08 | SOW 3.1 requires private conversations between registered users. | AC-04 |
| FR-09 | SOW 1.2 and 3.1 require sending private text messages. | AC-05 |
| FR-10 | SOW 1.2 and 3.1 require receiving and reading private text messages. | AC-05 |
| FR-11 | SOW 3.1 limits private conversation access to its two participants. | AC-05, AC-10 |
| FR-12 | SOW 3.1 includes named groups. ED-03 makes the creator the first member. | AC-06 |
| FR-13 | SOW 3.1 and ED-03 allow the group creator to add registered users. | AC-06 |
| FR-14 | SOW 1.2 and 3.1 require group text messaging. | AC-07 |
| FR-15 | SOW 3.1 requires group members to receive and read group messages. | AC-07 |
| FR-16 | SOW 3.1 allows members to leave a group. | AC-08 |
| FR-17 | SOW 3.1 limits group conversation access to current members. | AC-08, AC-10 |
| FR-18 | SOW 3.1 requires an interface for accessing conversations. A conversation list supports this task. | AC-04, AC-07, AC-08 |
| FR-19 | SOW 3.1 requires users to open conversations, read messages, and send messages. | AC-04, AC-07 |

#### 6.3 Non-functional Requirement Traceability

| Requirement | Source and Reason | Acceptance Checks |
| --- | --- | --- |
| NFR-01 | SOW 3.4 defines local operation. ED-05 sets a measurable response-time target for local messaging. | AC-11 |
| NFR-02 | SOW 3.1 includes account access. ED-04 defines password protection to reduce exposure of user credentials. | AC-09 |
| NFR-03 | SOW 3.1 requires conversation access control. ED-04 requires checks that cannot be bypassed through direct requests. | AC-10 |
| NFR-04 | SOW 1.2 requires users to exchange messages. This quality requirement checks that messages arrive without loss, duplication, or changes during the defined test. | AC-11 |
| NFR-05 | SOW 3.1 requires a usable conversation interface, and SOW 4.3 provides a user guide. ED-05 sets a measurable task-completion target. | AC-12 |

#### 6.4 Consistency and Updates

- All listed requirements apply to the required local first version.

- Message history across login sessions and message search remain optional and are not required for acceptance.

- The open questions in Section 5.3 may lead to revisions. Related requirements, acceptance checks, and traceability entries will be updated together.

- Changes to the project boundary will also be reflected in the statement of work.

- Requirement identifiers will remain stable. If a requirement is removed, its identifier will not be reused for an unrelated requirement.

- These tables show planned coverage. Actual pass or fail results will be recorded in the test report.