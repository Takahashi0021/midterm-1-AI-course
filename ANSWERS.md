# Midterm 1: answers

GitHub username:takahashi0021
Session code:maple-66
Fingerprint:1f43b5c7

> Fill in the three lines above from `my_data/DATA.md`. Do not rename headings or table columns: a script reads the numbers.
> Write only in the empty cells and lines. Percentages as 0.78 or 78 %, money as plain numbers.

## AI-use declaration

I used Claude Code for this task. I used to understand methods
## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

| config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|---|---|---|---|
| A |0.350|0.467|0.550|0.414|
| B |0.333|0.533|0.833|0.490|

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---|---|---|
| A, k=3 |0.467 |0.346 |0.591 |
| A, k=5 |0.550 |0.425 |0.669 |
| B, k=3 |0.533 |0.409 |0.654 |
| B, k=5 |0.833 |0.720 |0.907 |

### 1c. Annual model cost in USD

| candidate | annual cost |
|---|---|
| A, k=3 |23240 |yes
| A, k=5 |30512 |no
| B, k=3 |15423 |yes
| B, k=5 |17484 |no

### 1d. Decision (at most 150 words)

(A, 5) costs $30,512, above the $26,900 budget, so it is out. The other three fit. (B, 5) has recall 0.833 [0.720, 0.907]; the upper limits of (A, 3) [0.346, 0.591] and (B, 3) [0.409, 0.654] lie below its lower limit, so (B, 5) is better than both. It is also the second cheapest ($17,484). Recall of (B, 5) per language (20 questions each): EN 0.90 (18/20), RU 0.80 (16/20), KK 0.80 (16/20). RU and KK users are served worst. With 20 questions per language the intervals are wide (about 0.58 to 0.92 for RU and KK), so the gap to EN is not shown. Still, about one in five RU or KK questions gets no correct chunk in the top 5, so those answers need monitoring.

### 1e. Next measurement (at most 60 words)

## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---|---|---|---|---|---|
| H |0.894 |KK,degraded |0.767 |0.591 |0.882 |14782,5 |
| L |0.850 |KK,degraded |0.733 |0.556 |0.858 |14400 |

Personal-data pages per year sent abroad under H:
273750
### 2b. Memo (at most 300 words)

## Part 3: Explain your own numbers

### Q1

Number:
Why (at most 40 words):

### Q2

Number:
Why (at most 40 words):

### Q3

Number:
Why (at most 40 words):

### Q4

Number:
Why (at most 40 words):

### Q5

Number:
Why (at most 40 words):
