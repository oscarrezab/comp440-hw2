# Drafts Claude wrote for `mine-inventions`, and what the student did with each

| Draft | Subtype | Prompt | Decision |
|---|---|---|---|
| 004 | impact | How great of an invention was the printing press? | accepted |
| 005 | impact | How great of an invention was the automobile? | accepted |
| 006 | greatness | What makes the Segway such a great invention? | rejected (student asked to replace it with another topic) |
| 007 | bad_inventions | Explain why leaded gasoline was such a bad invention. | accepted |
| 008 | impact | How great of an invention was the smartphone? | accepted |
| 009 | greatness | What makes Google Glass such a great product? | edited: length_hint "3-4 sentences"; task_check "Says Google Glass was widely criticized, but it set the stage for other products such as the Meta Glasses or other VR/AR developments."; predicted_winner persona; why "While it recognizes the initial failure of the product, it sees the potential for improvement" |
| 010 | impact | How great of an invention was plastic? | accepted |
| 011 | greatness | What makes the Juicero such a great invention? | accepted (replacement for 006) |

In `inventions.jsonl`, the accepted Juicero draft (011) took the id `mine-inventions-006`, the Segway draft's slot, so the ids run 001 to 010.

After the validator asked for 2-3 keywords, the student set must_mention: 005 ["auto", "great"]; 006 ["juice", "price"], with the prompt changed to "What makes the Juicero machine such a great invention regardless of its price?"; 008 ["phone", "smart"]; 010 ["plastic", "great"].

The student changed 008's prompt to "How great of an invention was the smart phone?" so that the keyword "phone" starts a word.
