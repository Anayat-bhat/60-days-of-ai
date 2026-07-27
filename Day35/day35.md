# Day 35 – Prompt Puzzle
## 🧩 Master AI Prompting Through Play

## Overview

Day 35 of the #60DayClaudeChallenge focused on learning Prompt Engineering through an interactive puzzle game. Instead of reading theory, I completed practical challenges that demonstrated how prompt structure affects AI-generated responses.

---

# What is Prompt Engineering?

Prompt engineering is the process of designing clear, structured, and specific instructions so that AI systems generate accurate, relevant, and useful responses.

A well-designed prompt typically includes:
- Role
- Context
- Constraints
- Expected output format

---

# Why Prompt Engineering Matters

Effective prompting helps AI:
- Understand the user's objective clearly.
- Produce more accurate and relevant responses.
- Reduce ambiguity.
- Improve consistency.
- Minimize unnecessary or incorrect outputs.

---

# Selected Domain

**Software Development & Coding**

---

# Selected Difficulty

**Beginner**

---

# Challenge 1 – Build the Prompt

### Scenario

**Explain an Error Message**

### Desired Output

A plain-English explanation of an error message plus a suggested fix.

### Prompt Blocks Used

The screenshot shows the available blocks, but it does not show which blocks were actually placed into the prompt. Add the blocks you selected after reviewing your completed playthrough.

### Distractor Blocks Removed

Not visible in the screenshots. Add the distractor blocks you excluded during your playthrough.

### Final Optimized Prompt

Not visible from the screenshots. Paste the final prompt you assembled during the activity.

---

# Challenge 2 – Clean the Prompt

### Scenario

**Explain an Error Message**

### Original Prompt

The activity contained both useful and irrelevant prompt components.

### Redundant Components Removed

Based on the challenge, the irrelevant components included:

- Give a generic definition of "error" from a dictionary.
- Ignore the specific error and talk about errors in general.

(Add any additional distractors you removed if applicable.)

### Improved Prompt

The final cleaned prompt should contain only the relevant prompt blocks from your completed activity.

---

# Challenge 3 – Choose the Best Prompt

### Scenario

Generate a REST API Endpoint

### Weak Prompt

```
make an api
```

### Optimized Prompt

```
Act as a backend engineer using Node.js and Express.
Create a POST endpoint '/users' that adds a new user to an array.
Include input validation, error handling, and comments explaining each part.
Return the response in JSON format.
```

### Over-Engineered Prompt

The version requesting an enterprise-scale distributed architecture, CQRS, event sourcing, CI/CD pipeline, and extensive documentation.

### Why the Optimized Prompt Was Best

The optimized prompt clearly defined:

- Role
- Technology stack
- Exact task
- Required features
- Output format

It provided enough context to generate a useful solution without unnecessary complexity.

---

# Weak AI Output vs Optimized AI Output

### Weak Output

```
app.post('/users', (req,res)=>{
    users.push(req.body);
    res.send('ok');
});
```

Problems:

- No validation
- No error handling
- Poor response format

### Optimized Output

Generated a properly structured Express endpoint including:

- Input validation
- Error handling
- JSON response
- Clear code comments

---

# Prompt Engineering Principle Learned

Specific, structured prompts consistently produce higher-quality AI responses.

Adding excessive instructions or unnecessary context reduces efficiency without improving output quality.

---

# Prompt Performance Report

## Prompt Score

**155 pts**

## Rating

**Developing (40%)**

## Rank

**🥉 Prompt Apprentice**

---

## Performance Statistics

| Metric | Result |
|---------|---------|
| Total Time | **202 seconds** |
| Total Moves | **15** |
| Wrong Placements | **10** |
| Hints Used | **1** |
| Correct Placements | **5** |

---

# Prompt DNA

- Specificity: **60%**
- Clarity: **30%**
- Structure: **100%**
- Efficiency: **90%**
- Judgment: **80%**

---

# Personalized Feedback

> You placed several incorrect blocks. Focus on reading the Desired Output carefully before selecting prompt components.

> Great instinct for spotting the optimized prompt over weak or bloated ones.

---

# Next Milestone

Score **50%+** by minimizing wrong placements and using fewer hints.

---

# Example Final Optimized Prompt

```
Act as an experienced JavaScript developer.
Here is the buggy code: [paste code].
Identify the bug, explain the root cause,
provide the corrected code in a code block,
and explain the fix in 2–3 simple sentences.
```

---

# Replay Comparison

Replay results are not shown in the uploaded screenshots.

Complete this section after replaying the simulator with a different randomized scenario.

---

# My Experience

The Prompt Puzzle made prompt engineering much easier to understand because every challenge demonstrated how small improvements in wording, context, and structure produced noticeably better AI responses.

The comparison between weak, optimized, and over-engineered prompts clearly illustrated that the best prompt is not necessarily the longest one—it is the one that communicates the task most effectively.

---

# Biggest Insight

Adding the correct amount of context and clearly defining the expected output is far more effective than writing long, complicated prompts.

---

# What I Learned

- Prompt engineering improves AI response quality.
- Role prompting guides AI behavior.
- Context reduces ambiguity.
- Clear constraints improve accuracy.
- Output formatting creates more useful responses.
- Removing unnecessary instructions makes prompts more efficient.
- Over-engineering prompts does not necessarily improve results.
- Structured prompts consistently outperform vague prompts.

---

# Screenshots Included

- ✅ Welcome Screen
- ✅ Build the Prompt
- ✅ Clean the Prompt
- ✅ Choose the Best Prompt
- ✅ Prompt Performance Report
- ✅ Progress Screen

---

# Conclusion

The Prompt Puzzle provided a practical introduction to prompt engineering through interactive challenges. By building prompts, removing unnecessary instructions, and comparing prompt quality, I gained a better understanding of how prompt design influences AI-generated responses. The experience reinforced the importance of clarity, structure, and relevance when communicating with AI systems.