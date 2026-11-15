# Lab 05 — Conclusion

<!--
Read this before you write.

This file is graded by your instructor, by hand, and it is worth 6 of the 15 points.

- Type it yourself. Do not use a chatbot, an AI assistant, an AI autocomplete or a "rewrite my
  text" tool for any part of it, not even for grammar. English that is plain and a little
  clumsy but yours is better than polished text that is not.
- Use your own numbers. Every number you quote must be one your own notebook printed. Copy
  the number exactly as it appeared. A number your notebook did not print is marked as wrong.
- Answer in your own words, about 80-200 words per question. A short answer that uses your
  numbers beats a long answer that could have been written by anyone.
- Delete these comment lines if you like. Keep the three headings and the last line.
-->

## 1. Which layer changed your results the most?

Give the numbers before -> after for that layer (correct / wrong / no answer, out of 20) and say
whether it changed what the agent *can do* or only what it *admits*. If no layer changed the
number of correct answers, say so and explain what the layers did change instead.

Layer 1 changed the results the most. Out of 24 questions, correct went from 16 to 18, wrong went from 4 to 6, and no answer went from 4 to 0. Layer 1 changed what the agent can do: q23 and q24 went from no answer to correct. Layer 3 changed only what the agent admits. It turned two wrong answers into no answer, and correct stayed at 18.

## 2. One failure the full harness did not fix

Pick one question that the full harness (layer 3) still gets wrong or refuses. Give its id
(q01 ... q20). Open its trace in the notebook: at which step did it go wrong, and what did
the model do instead? Name one thing you would add to the harness, and what it would cost
(extra model calls, tokens, time, or a new way to fail).

q17 is still wrong with all three layers. The agent answered 8.89.
The tool gave 4.5 and 4.1. The question asks for percentage points, but the model used the percent change formula in the calculate step. The number 8.89 came from a tool, so the harness thought it was grounded.
I would add a second model call to check the formula. It costs more model calls and more tokens. The checker can also make mistakes, so it is a new way to fail.

## 3. Workflow or agent for the monthly ranking?

Dala Insight wants to publish, every month, "which region is highest and which is lowest on one
indicator in one year". Would you ship the fixed workflow or the agent? Use the accuracy, the
number of model calls, the tokens and the time you measured in Part 1. Then say in one sentence
what kind of question would make you choose the other one.

I would ship the fixed workflow. On the 15 fixed questions, the workflow got 13 correct and the agent got 9. The workflow used 15 model calls, 3852 tokens and 15.7 seconds. The agent used 26 model calls, 19835 tokens and 48.0 seconds.
I would choose the agent for an open question, for example a percent change, because the workflow cannot answer those.

---

I wrote this file myself, without any AI tool.
