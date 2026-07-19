# Day 27 – Prior Authorization Story Simulator

## Objective

The objective of Day 27 was to explore how interactive storytelling and conversational user interfaces can make complex topics easier to understand.

For this challenge, I created a **Prior Authorization Story Simulator** that follows a patient named Rahul through a healthcare journey involving diagnosis, treatment, Prior Authorization, insurance review, denial, appeal, and final approval.

Instead of explaining the entire process through a long document, the application presents the information as an interactive conversation between Rahul and Priya, a healthcare operations specialist.

---

## What is Interactive Storytelling?

Interactive storytelling is a way of presenting information through a story in which the user actively participates.

Instead of simply reading information from beginning to end, the user can make choices and interact with characters as the story progresses.

In my Prior Authorization Story Simulator, I followed Rahul's healthcare journey through eight different scenes. After each scene, I was given two dialogue choices that allowed me to decide what Rahul should ask next.

This made the experience feel more like participating in Rahul's journey rather than simply reading about Prior Authorization.

---

## Why Storytelling is Useful for Education

Storytelling can make difficult concepts easier to understand by placing them in a realistic and relatable situation.

Healthcare processes such as Prior Authorization can be complicated because they involve multiple people, organizations, documents, decisions, and administrative steps.

Instead of explaining these concepts only through definitions, the simulator shows them through Rahul's experience.

By following Rahul from his doctor's appointment to the final insurance approval, I could understand why each stage of the process exists and how one stage connects to the next.

The story-based approach made the topic more engaging and easier to remember.

---

## What is a Conversational UI?

A Conversational UI is a user interface that presents information through conversations or chat-style interactions.

In my application, the conversation is displayed using different visual styles for each character:

- 👦 **Rahul – Patient:** Appears on the left side.
- 👧 **Priya – Healthcare Operations Specialist:** Appears on the right side.
- 🩺 **Dr. Patel:** Appears as centered italic text.
- **Narrator:** Appears as centered italic text.

New messages are continuously added to the conversation without removing previous messages. This creates an append-only chat experience where I can scroll back and review the complete journey.

This design makes it easy to identify who is speaking and follow the story naturally.

---

## What is Prior Authorization?

Prior Authorization, commonly called PA, is a healthcare process where an insurance payer reviews certain requested treatments, medications, procedures, or services before agreeing to cover them.

In Rahul's story, Dr. Patel prescribed Humira for Rheumatoid Arthritis. Before the treatment could proceed with insurance coverage, Dr. Patel's office had to submit a Prior Authorization request to the illustrative payer, StarCare Health.

The application demonstrated that the PA process can involve reviewing clinical information, diagnosis details, treatment history, and other supporting documentation.

---

# Introduction to Rahul and Priya

The story has two main characters.

## 👦 Rahul – Patient

Rahul is the patient whose healthcare journey I followed throughout the simulation.

He experiences stiffness and swelling in his hands and visits City Medical Center for medical evaluation.

Through Rahul's questions, the application introduces important Prior Authorization concepts in beginner-friendly language.

## 👧 Priya – Healthcare Operations Specialist

Priya helps Rahul understand and navigate the Prior Authorization process.

She explains:

- What Prior Authorization means
- How the insurance review works
- Why documentation is important
- What step therapy means
- Why Rahul's request was denied
- How the appeal process works
- What happens after approval

Priya acts as the educational guide throughout the story.

---

# Rahul's Healthcare Scenario

Rahul visits City Medical Center after experiencing stiffness and swelling in his hands for several weeks.

Dr. Patel reviews his symptoms and bloodwork and diagnoses him with:

**Rheumatoid Arthritis (RA)**

Dr. Patel recommends:

**Humira (adalimumab)**

However, before the treatment can proceed with insurance coverage, Dr. Patel's office needs to complete the Prior Authorization process with StarCare Health, a fictional payer used for educational purposes in the simulation.

This begins Rahul's Prior Authorization journey.

---

# Scene 1 – Doctor Visit

The first scene takes place at City Medical Center.

Rahul tells Dr. Patel that his hands have been stiff and swollen for weeks and that the symptoms are affecting normal activities.

After reviewing Rahul's symptoms and bloodwork, Dr. Patel diagnoses Rheumatoid Arthritis and recommends Humira.

The system records:

- Diagnosis: Rheumatoid Arthritis
- Prescribed Treatment: Humira
- Next Step: Prior Authorization request

At the end of the scene, I could choose between asking what happens next or asking why a strong medication was needed.

This was the first example of branching dialogue in the application.

---

# Scene 2 – Insurance Roadblock

In the second scene, Priya introduces herself and explains that Dr. Patel's office has submitted Rahul's Prior Authorization request directly to StarCare Health.

The workflow shown in the application is:

**Provider → PA Request → Payer**

The story explains that no pharmacy is involved at this particular stage of the simulated process.

Rahul asks questions about how the process works and how long approval might take.

This scene helped establish the roles of the healthcare provider and payer in the Prior Authorization workflow.

---

# Scene 3 – What Rahul Learned About Prior Authorization

Priya explains Prior Authorization to Rahul in simple language.

She describes it as the insurance company reviewing and agreeing to cover a treatment before it is provided.

The scene also introduces **step therapy**.

Step therapy may require a patient to try certain treatments before another treatment is approved.

The story highlights an important point: delays in treatment can matter for conditions such as Rheumatoid Arthritis, where timely treatment may be important.

The application also presents an evidence note referencing the AMA 2023 PA Survey and treatment delays.

This scene helped me understand why Prior Authorization is not only an administrative workflow but can also affect the patient's treatment journey.

---

# Scene 4 – Insurance Review Process

Priya explains four major areas that StarCare Health checks during the simulated Prior Authorization review.

### 1. Eligibility

The payer checks whether Rahul is actively enrolled and covered under the insurance plan.

### 2. Clinical Documentation

The payer reviews the doctor's notes and laboratory information supporting Rahul's diagnosis.

### 3. ICD-10 Diagnosis Match

The diagnosis information needs to match the condition for which the requested treatment is being reviewed.

### 4. Step Therapy History

The payer reviews whether Rahul has previously tried the treatments required under the simulated step therapy criteria.

This scene showed me how important accurate and complete information can be during an insurance review.

---

# Scene 5 – Reason for Denial

Rahul's initial Prior Authorization request is denied.

The reason shown in the simulator is:

**Missing step therapy documentation – no record of a prior trial with a first-line Rheumatoid Arthritis medication.**

Rahul initially thinks that the denial means he cannot receive the treatment.

Priya explains that a denial does not necessarily mean the process is permanently over. In this story, the problem is a documentation gap that can be addressed.

The application also explains that resolving PA denials can create additional administrative work for healthcare organizations.

This was one of the most important parts of the story because it demonstrated how missing documentation can affect the entire workflow.

---

# Scene 6 – Appeal Process

After the denial, Priya explains the plan for appealing the decision.

The appeal package in the simulation includes:

- Past medication history
- Proof of previous step therapy attempts, if available
- Letter of Medical Necessity from Dr. Patel
- Formal appeal submission referencing the original PA request

Rahul mainly needs to confirm that his treatment history is accurate and provide a signature where required.

The healthcare team then handles the remaining appeal process.

This scene showed how healthcare providers can respond when a Prior Authorization request is initially denied.

---

# Scene 7 – Final Approval

After the appeal is submitted, Rahul receives good news.

The simulated Prior Authorization is:

**APPROVED**

The application displays the reference number:

**SC-PA-88213-RA**

Within the story, the approval is recorded on file, and Rahul can proceed with the treatment according to the simulated scenario.

Rahul expresses relief after receiving the approval, and Priya explains what happens after the successful resolution.

This scene completes the main Prior Authorization journey from the initial doctor's visit to the final approval.

---

# Scene 8 – Final Takeaways

The final scene summarizes the journey from two perspectives.

## Patient Perspective

Rahul learned that:

- A denial is not always the end of the process.
- Documentation gaps can sometimes be addressed.
- Understanding what the payer reviews can make the process easier to understand.
- Having someone guide the patient through a complicated administrative process can reduce confusion.

## Healthcare System Perspective

The simulator explains that healthcare organizations may track metrics such as:

- **Denial Rate:** The percentage of PA requests denied initially.
- **Appeal Rate:** The number of denied requests that are appealed.
- **Resolution Time:** The total time from the initial request to the final outcome.

Tracking these metrics can help organizations identify where delays and problems occur in the workflow.

---

# How Branching Choices Worked

One of my favorite features of the application was the branching dialogue system.

After each scene, the application presented two choices.

For example, I could choose to:

- Ask what happens next
- Ask why a particular treatment is required
- Ask what Prior Authorization means
- Ask how long approval takes
- Ask what the payer reviews
- Ask what happens when information is missing
- Ask about the appeal process

The selected choice changed the immediate conversation and sometimes provided additional educational information before continuing to the next chapter.

Although the main Prior Authorization journey remained structured across eight scenes, the branching choices allowed me to explore different questions and explanations.

After completing the story, I could restart the journey and select different dialogue paths.

---

# Progress Bar Functionality

The application includes a visual progress tracker at the top of the page.

It displays the current scene and completion percentage.

The story progresses through:

1. Doctor Visit
2. Insurance Roadblock
3. What is PA?
4. Insurance Review
5. Denial
6. Appeal
7. Approval
8. Takeaways

The progress begins at **12%** during Scene 1 and increases as the user moves through the eight chapters.

The visual EKG-style progress indicator also updates as each scene is completed.

This feature made it easy to understand how far I had progressed through Rahul's journey.

---

# My Experience Using the Application

Using the Prior Authorization Story Simulator was a different experience from learning through a traditional document.

Instead of reading a long explanation about healthcare operations, I followed Rahul through a realistic sequence of events.

The chat-based interface made the experience feel natural, while Priya's explanations helped simplify complicated concepts.

I especially liked the branching choices because they allowed me to decide which questions Rahul should ask. This gave me some control over the learning experience while still following the main educational journey.

The combination of storytelling, conversations, choices, system cards, and progress tracking made the application engaging and easy to follow.

---

# Biggest Insight

My biggest insight was that **the same complex process can be taught in completely different ways depending on how the user experience is designed**.

On Day 26, I explored Prior Authorization through a workflow simulator. On Day 27, I explored the same general topic through Rahul's personal story and conversations with Priya.

The storytelling approach made it easier to understand the process from the patient's perspective, while the workflow approach helped visualize the operational steps.

This showed me that good educational applications should not only provide accurate information but should also present it in a way that helps users connect with and understand the subject.

---

# What I Learned

Through Day 27, I learned:

- What interactive storytelling is
- How storytelling can simplify complex concepts
- How conversational interfaces can improve educational experiences
- How branching dialogue can make applications more interactive
- How Prior Authorization works in the context of the simulated healthcare journey
- Why clinical documentation is important
- What step therapy means in the context of the story
- How missing documentation can contribute to a denial
- How an appeal can be used to request reconsideration
- How healthcare organizations can track denial rates, appeal rates, and resolution times
- How progress bars help users understand their position in a multi-step journey
- How different characters can explain information from different perspectives
- How JavaScript can dynamically create and append chat messages
- How Claude can generate a complete interactive educational web application
- How complex workflows can be transformed into engaging learning experiences

---

# Conclusion

Day 27 demonstrated how **interactive storytelling and conversational UI can transform complex information into an engaging educational experience**.

Following Rahul's journey from diagnosis to Prior Authorization, denial, appeal, and final approval helped me understand the process in a more relatable way.

The biggest lesson from this challenge was that technology can do more than display information. With thoughtful storytelling, interaction, and user experience design, it can help people understand complicated processes step by step.

---

# Screenshots Included

The following screenshots are included in my Day27 folder:

- Screenshot of the Prior Authorization Story Simulator
- Screenshot of Scene 1 – Doctor Visit
- Screenshot of Rahul and Priya's conversation
- Screenshot of the Prior Authorization explanation
- Screenshot of the Insurance Review process
- Screenshot of the Denial
- Screenshot of the Appeal process
- Screenshot of the Final Approval
- Screenshot of the Final Takeaways
- Screenshot of the completed Progress Bar

---

## Day 27 Completed ✅

**Challenge:** #60DayClaudeChallenge

**Project:** Prior Authorization Story Simulator

**Focus:** Interactive Storytelling, Healthcare Education, Conversational UI, Branching Decisions, and Web Application Development