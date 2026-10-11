# Messenger — Ethics Reflection

Course: CPS 490 — Capstone I

Assignment: IA 05 — Messenger: Ethics Reflection



## 1. Project Context

This reflection looks at the possible effects of the first version of Messenger described in the [Statement of Work](statement-of-work.md) and [Requirements](requirements.md).
The application will run on one computer with separate browser sessions.
It will support accounts, private text messages, and group text messages. Public hosting is not part of this version.

Because this is a local project, its immediate impact will be small.
Some risks could become more important if Messenger is later made available to the public.
I will separate those future possibilities from what the first version actually does.



## 2. Design Impact Analysis

#### 2.1 Cultural Impact

- Positive impact: Messenger allows users to create groups where they can communicate in their own language and share cultural interests. For example, users could discuss their traditions, festivals, or experiences
  without having to use a language they are less comfortable with. The local prototype can demonstrate this use, although it does not yet connect people on different computers.

- Negative impact: Messenger has no content moderation or reporting feature. A group member could send racist comments or insult another person's religion or cultural background.
  Other members may feel unwelcome or stop participating. Login and membership checks cannot prevent this behavior because the person sending the harmful message may be an authorized group member.

- Mitigation: During local testing, participants should agree not to send 
  discriminatory or abusive messages.
  If this happens, the test organizer should stop the session and address
  the behavior before testing continues.
  Users can also leave a group under FR-16, but this does not prevent
  further abuse by the sender.
  Before a public release, reporting and blocking features would need
  to be considered, together with a clear process for reviewing reports.
  These are proposed improvements, not features promised for the first version.

#### 2.2 Economic Impact

- Positive impact: Keeping the first version small helps control development time and cost. By focusing on private and group text messages, I can spend more time
  making the required features work instead of building voice calls, video calls, or file sharing. There are also fewer features to test and maintain.

- Negative impact: The current design does not guarantee that messages remain available after the server restarts.
  If users rely on a chat to keep task assignments or important decisions, losing those messages could force them to repeat discussions or redo work.
  This could waste time and become costly if Messenger were later used for real work.

- Mitigation: The setup and user guide should clearly explain that the first version is not intended to keep permanent records. During testing, important task details should also be saved in a separate
  document instead of being kept only in the chat. Before Messenger is used for real work, Q-04 should be resolved by deciding which data must survive a restart.
  If message retention becomes required, the requirements and acceptance tests should include saving messages and checking them after a restart.

#### 2.3 Environmental Impact

- Positive impact: The local version can run on the development computer, so this project does not need a separate server machine.
  Reusing available equipment avoids buying extra hardware just for development and classroom demonstrations.

- Negative impact: The local server and browser sessions still use electricity. Leaving the computer running after testing just to keep Messenger available
  would use energy even when nobody is using the application. The impact is limited for this small prototype, but unnecessary running time can still be avoided.

- Mitigation: The setup guide should explain how to stop the local server after a test or demonstration. Messenger does not need to run all day for this assignment.
  Test sessions should be closed when they are no longer needed, and the computer can sleep or shut down when it is not being used for other work.

#### 2.4 Global Impact

- Positive impact: Once the required software is installed, Messenger can be demonstrated locally without an internet connection.
  This makes classroom demonstrations possible even when internet access is unavailable or unreliable. This benefit is limited to local use; it does not provide communication between people in different locations.

- Negative impact: The first version runs on one computer, so people using other computers cannot join its conversations. For example, a student at home could not join a group demonstration
  running on a classroom computer. This limits who can participate and means the current version does not support international or remote communication.

- Mitigation: The setup guide should clearly state that Messenger is a single-computer prototype. For the current demonstration, participants can take turns using the separate browser sessions on that computer.
  This supports local participation but does not solve remote access. If remote participation becomes a project goal, the scope and ED-01 would need to be revised before planning hosting, connection security, and tests involving different computers.

#### 2.5 Public Health Impact

The current version has no clear, significant direct impact on public health. It is a small messaging prototype used for local testing and demonstration.
It does not provide health advice, collect health measurements, or support medical decisions.

This does not mean that messaging software can never affect health. If Messenger is later used by real communities or for health-related discussions, this assessment should be reviewed.

For the current tests, participants should use fictional information instead of sharing personal health details.

#### 2.6 Public Safety Impact

- Positive impact: Ending a session after logout helps prevent someone else from using that session to send messages on a shared computer.
  For example, after one user logs out, the next person using the browser should not be able to send messages under the previous user's account.
  FR-05 and FR-06 require logout and restricted access, and AC-03 checks that the previous session can no longer access conversations.

- Negative impact: Messenger depends on the local server and computer remaining available.
  If the server program closes or the computer loses power, messaging stops. Someone relying on Messenger for an urgent message could lose contact with the intended recipient.
  This limits its suitability for safety-critical communication.

- Mitigation: The setup and user guide should explain that the local server must remain running and that Messenger is not an emergency communication service.
  Test participants should have another way to contact each other if the application stops.
  A proposed acceptance check is to stop the server during a test and verify that the interface shows a connection error instead of reporting a new message as successfully sent.
  This check should be added to the requirements and acceptance criteria before being treated as a required feature.

#### 2.7 Public Welfare Impact

- Positive impact: A small set of basic features can make Messenger easier to learn.
  Users only need to understand accounts, private conversations, and groups. Keeping these actions easy to find can help first-time users complete basic tasks without needing help from the developer.

- Negative impact: A simple interface is not automatically accessible to everyone.
  For example, if sending a message requires clicking a mouse, someone who uses only a keyboard may be unable to use the application.
  Input fields without clear labels could also make the interface difficult to understand when using a screen reader.

- Mitigation: Important actions should be usable with a keyboard, and input fields and buttons should have clear labels.
  A proposed acceptance check is to log in, open a conversation, type a message, send it, and log out without using a mouse.
  NFR-05 currently checks whether a first-time user can complete basic tasks, but it does not specifically cover accessibility.
  Keyboard access and screen-reader checks should be recorded as proposed additions to the requirements and acceptance criteria.

#### 2.8 Social Impact

- Positive impact: Group chat allows members to discuss tasks together instead of passing the same information through separate private messages.
  For example, a project group could use one conversation to divide tasks and ask questions, helping members follow the same discussion. The local prototype can demonstrate this with separate user sessions.

- Negative impact: The current design allows a group creator to add registered users without asking for their agreement.
  A person could be added to a group they do not want to join. Although FR-16 allows that person to leave, the requirements do not say whether the creator can add them again after they leave.
  Repeatedly adding someone could pressure them to participate.

- Mitigation: During local testing, group creators should ask participants before adding their accounts and respect requests not to be added again.
  This is a testing rule; the application does not currently enforce it. For wider use, users should be able to accept or decline an invitation
  before becoming group members. Adopting that change would require updating FR-13, ED-03, and AC-06, which currently describe direct addition by the group creator. The design would also need a rule for repeated unwanted invitations.



## 3. Connection to Engineering Decisions

#### 3.1 Adding Users to Groups Without Consent

- Who could be affected: Registered users who are added to groups they do not want to join.

- Potential harm: Users may feel pressured to participate. Someone who leaves a group could be added again because the current requirements do not define a restriction on repeated additions.

- Mitigation: During local testing, the group creator should ask before adding another participant's account and should respect a request not to be added again.
  This should be included in the demonstration instructions as a testing policy.

- Engineering connection: FR-13 and ED-03 currently allow group creators to add registered users directly.
  FR-16 allows users to leave, but leaving does not prevent another unwanted addition.
  For wider use, an invitation-and-acceptance process is a proposed design change.
  If adopted, FR-13, ED-03, AC-06, and the statement of work would need to be updated together.

- Verification: A future invitation test should confirm that an invited user does not become a member until they accept.
  Declining an invitation must leave the user outside the group. A separate decision is needed on how users can stop repeated invitations.

#### 3.2 Communication Failure When the Server Stops

- Who could be affected: Users trying to send or receive messages when the local server stops or the computer loses power.

- Potential harm: A user could believe that an important message was sent even though it never reached the server.
  If the message concerns an urgent situation, this misunderstanding could delay another way of contacting the recipient.

- Mitigation: The setup guide should explain that Messenger depends on the local server and should not be used as an emergency communication service.
  The interface should clearly show a connection problem when it cannot confirm that a message was accepted.

- Engineering connection: ED-01 defines the single-computer design. NFR-04 and AC-11 cover message reliability while the server is running;
  they do not define what the interface should show during an outage. A proposed requirement is that a message must not be shown as successfully sent unless the server has confirmed acceptance. 
  If confirmation is missing, its status should be shown as unconfirmed.
  Server acceptance must also not be presented as proof that a recipient has read the message.

- Verification: A proposed acceptance test is to stop the server, attempt to send a message, and check that the interface displays a connection error or unconfirmed status.
  It must not display a successful-send result. This requirement and test should be added to the requirements document if the proposed behavior is adopted.



## AI-Assisted Work

- Assisted in organizing assignment documentation using ChatGPT.
- Translated and polished Chinese-to-English text using ChatGPT.
- Explained and provided guidance on Markdown and PlantUML syntax using ChatGPT.
- Identified inconsistencies and errors across multiple .md files in the current project using ChatGPT.
- 
As a non-native English speaker, I usually prefer drafting heavy textual work in my native language first, and then leveraging AI to assist with the translation process.

However, I always carefully review the AI-translated content to ensure it accurately conveys my intended meaning. For instance, in a section regarding "cultural impacts," the initial AI translation failed to fully articulate the underlying cultural risks I wanted to express.

I also used AI to cross-reference all my completed Markdown files against the assignment requirements, which successfully helped me identify missing sections and errors.

Ultimately, despite using AI to help refine the materials, I remain fully responsible for the understanding and interpretation of the submitted content. Furthermore, AI-generated test data cannot serve as proof that the application has been successfully tested.