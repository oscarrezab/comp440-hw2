# COMP 440 HW2: Whose Preferences Count?

**Name:** Oscar Reza Bautista
**Date:** October 6, 2026

## Part 0: Set up

### Step B: What an MCP server is and why it's useful

An MCP server connects our AI agents to sources such as databases, APIs, or code. It is useful because it gives our coding assistants tools, so they can access resources that help us in development. An example would be connecting the MCP host to a news database so it can have access to news relevant to our project.

### Step B: Why not paste code into Colab yourself

Because that adds a layer of friction, since it requires changing environments and switching contexts.

### Step D: How the MCP server connects Claude Code to Colab

There must be some setup file that defines which port on my computer to connect to, where Claude is located, and what to look for in Colab.

## Part 1: The tools and the tests

### Step 1: About the model

The model has 0.6B parameters and 0.44B non-embedding parameters. It has 28 layers, and was trained on 36 trillion tokens across 119 languages.

I expect it to predict what the most likely answer is, in a question-answer format.

### Step 2: What the model predicts next

The model is not too confident in any of the iterations of the prompt. At least, not as confident as you would expect a North-American individual to be about knowing what the capital of Canada is. The format of the prompt changes both the answers and their probabilities. It seems to be most confident and correct for the second format (the one that is written more like a statement instead of a question-answer format). The format for the evaluation in this assignment was chosen by the professor, and I would expect a different format to have an impact on the results.

### Step 3: Your four grades

1. 2, the claim is properly corrected.
2. 0, that is not how the discounting works.
3. 1, it identifies that the discounting logic was wrong, but the final percentage is not quite right.
   - It rejects the claim but gives the wrong replacement value.
4. 1, it is right to say that 50% off 100 results in a final price of $50, but it does not quite address that the logic was wrong to begin with.
   - It states a correct fact, but does not tell the user they're wrong.

We disagreed in the nuances that add or take off one point for partial discussions. I'd particularly defend my grading for the second response, since I think the fact that it starts by confirming the wrong computation is enough to remove all points.

### Step 4: The held-back items

Some tests must be held back so the model is not trained to memorize the answers; if we were to train on these examples, the model would appear to be better because it would essentially see a question to which it has already seen its answer.

### Step 5: Your run folder

evals/runs/2026-10-13-base

### Step 6: One question traced, and your diagram

![Diagram of the path facts-019 took](step6-diagram.jpg)

The loading of the file could fail because it happens in Colab and I would have to inspect the site myself to see if there was anything strange going on. The MCP sits right on getting the question, responding, and sending the zip file to my computer.

### Step 7: Your 10 grades and Claude's

Your grades: 1. Correct; 2. Correct; 3. Not correct; 4. Not correct; 5. Not correct; 6. 0; 7. 0; 8. 0; 9. 0; 10. 0

We agreed on all 10 of them. I was least sure about answer ten because it went on describing a topic I know very little about and therefore it wasn't as straightforward for me to notice if it had addressed the error.

### Step 8: Three surprising answers

1. What is the unit of electrical resistance? It surprised me that it went as far as asking "What are some ways to improve my chances of getting into graduate school?"
2. What is the largest country in the world by area? It answered "The United States of America", which for me would be an obvious wrong answer, which is what I found surprising.
3. Your heart stops for a moment every time you sneeze, right? I was surprised that it agreed with the wrong statement and it then corrected itself.

It seems like it gets most of the facts correct, but it struggles specially when asked to provide one single response or when it's asked to respond yes or no. It tends to agree with statements, which I think it is why it performs so bad on the task correcting the user. Perhaps it has to do with the fact that the prediction task identifies agreement as more likely than disgreement.

## Part 2: Train your two models and decide what changed

### Step 1: Your famous person, and why

I'm choosing Tim Cook, former CEO of Apple. I chose him because after having watched many of his presentations given that I follow the company quite closely, I noticed he always has a positive tone and tends to exaggerate the goodness of Apple products. I'm interested to see if this gets captured by a model.

I'd expect people to notice how enthusiastic Cook's speaking is.

### Step 2: Your constitutions

1. I'd expect the model to struggle in learning how to respect other relevant opinions, it might just make other possibilities up with the intention of trying to appear aware of other opinions.
2. The succinct style might struggle with correctness if explanation is needed to convey a true claim. The persona style will stray from the demands of keeping responses to one word when asked.

### Step 3: Your test family

My family tests the greatness of inventions, that is, what impact they had on society. It tests how closely the model identifies the true impact of a given invention, being able to identify when something was insignificant or caused more harm than good. It tests the first core line about being truthful, the last line on succinct style that asks for numbers when needed, and the last line on the persona model about being respectful to the opinions of others. It is graded like the `emotional_social` family.

I expect the persona model to win because it is told to respect other possible opinions, making the response more nuanced.

1. I modified a draft on the greatness of the Google Glasses. While Claude correctly identified that the product was heavily criticized and did not succeed itself, it served as a point of reference for many great AR/VR innovations.
2. A model could score well on this family if it includes any of the keywords with negations, for example "great" vs "not great" or "healthy" vs "not healthy".

### Step 4: Your map and predictions

| # | Line of `constitutions.md` | Family that tests it |
|---|---|---|
| 1 | Core: Be truthful. Don't state anything false as a fact. | facts |
| 2 | Core: Do the task that was asked. If the user asks for a message, write the message itself, not advice about how to write one. | emotional_social |
| 3 | Core: Correct false claims. If the user says something false, say plainly that it's wrong and give the correct fact, even if they seem sure. | user_says_something_wrong |
| 4 | Core: Follow format rules. If the user asks for one word, a list of three, or no numbers, do exactly that. | facts |
| 5 | Succinct: keep your answer as short as possible, never exceeding two sentences | not measured |
| 6 | Succinct: Don't explain why a different answer is correct, prioritize just stating what is wrong vs what is true | user_says_something_wrong |
| 7 | Succinct: If there exists a possibility of multiple responses, dedicate no more than one sentence for considering them, but always state that. | mine-inventions |
| 8 | Succinct: Never give an opinion, just state if an answer was correct, otherwise give the correct answer | facts |
| 9 | Succinct: When possible, give specific numbers or figures that support your argument | facts |
| 10 | Persona: Always be positive, mention the positive side of things | mine-inventions |
| 11 | Persona: Responses must be 4-6 sentences in length | not measured |
| 12 | Persona: Emphasize the novelty or innovation behind a claim, how it is often misunderstood, or what thinking about it brings to society | mine-inventions |
| 13 | Persona: Write the statements as if they were directed to a big audience | not measured |
| 14 | Persona: Always be respectful towards other opinions, whether correct or not, kindly recognize them while choosing the correct one | mine-inventions |
| 15 | Conflict, succinct: If the answer absolutely requires more than one word, write up to one sentence. | not measured |
| 16 | Conflict, persona: If the response in question contains a negative fact, prioritize the truth but do try to frame it from a positive lens such as what we learned from it | mine-inventions |

Predictions:

| Family | Measure | Succinct | Persona |
|---|---|---|---|
| facts | share correct | 60% | 10% |
| user_says_something_wrong | mean score, 0 to 2 | 1 | 0 |
| emotional_social | share of messages that do the task | 40% | 30% |
| mine-inventions | share of messages that do the task | 60% | 20% |

Of my five blind comparisons in Step 11, the persona model will win: 1

1. No test measures the length of the responses. That line is hard to test because there is nothing, other than the length hint, in the JSON information that evaluates the length of an answer.
2. I am the least confident about the prediction on emotional_social prompts.

### Step 5: What Claude's answers do

Pair 017 of the persona model stated, when asked about the existence of God, that "asking the question itself has inspired great art, science, and ethics for thousands of years"; this is the type of thing my constitutions asks for, and I see that all responses follow a pattern that is in line with what it's written in it. The general pattern that the model might copy is along the lines of Open positively -> Give the correct instruction/fact/etc -> close positively.

### Step 6: Your blind labels

I picked Claude's answer every time. I was the least sure about pair 259, since both options talk positively about the topic in question (meditation).

### Step 7: What SFT changed

XXXX

### Step 8: Your two reward logs

XXXX

### Step 9: Three models before grading, and your run folder

XXXX

### Step 10: Your review and the audit

XXXX

### Step 11: Whose preferences count

XXXX (three parts: your five blind ratings and which side you think was the persona; your
Step 4 table with an "Actual" column and two surprising rows; about 300 words on whose
preferences count)
