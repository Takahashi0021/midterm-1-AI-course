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
Who is served worst. Under both pipelines it is Kazakh scans in poor condition. H gets 23/30 right (0.767, interval 0.591 to 0.882); L gets 22/30 (0.733, 0.556 to 0.858). The overall figures (H 0.894, L 0.850) hide this: about one in four degraded Kazakh invoices fails. With only 30 scans per cell we are not sure: the intervals overlap, so H is not shown to be better than L in that cell.

Personal data. 15 % of pages carry a name and ИИН, which Law No. 94-V covers. Under H that is 273,750 pages a year. The three questions for H: where does the scan go (a data centre abroad: known); who stores it (the vendor: unknown); for how long (unknown). We would have to find out the vendor's retention and the legal basis for transfer; a vendor's statement is not a compliance review. For L: the scan goes to our own server in Kazakhstan (known), we store it (known), and we must set the retention period ourselves.

Safeguards anyone can verify: (1) network logs show no outbound traffic from the L server; (2) a written retention period with an automatic deletion job and a monthly deletion report; (3) an access list for the server, reviewed quarterly; (4) every Kazakh degraded scan, and any page with low confidence, goes to a human check; (5) a quarterly retest with at least 100 scans per cell.

Choice. L is $382 a year cheaper, keeps personal data in the country, and its accuracy gap to H is not shown by our data. Remaining risk: about one in four degraded Kazakh invoices may be wrong, and we now own server security and retention. The human check covers the first; the safeguards cover the second.
## Part 3: Explain your own numbers

### Q1

Number: 2.24
Why (at most 40 words): Output tokens cost five times more than input tokens. English has a larger output share of its bill than Kazakh, so Kazakh's cost grows slower (2.24) than its token count (2.62).

### Q2

Number: 35.1
Why (at most 40 words): Only English is cut: 768 cl100k tokens become about 789 e5 tokens, above 512. RU (384) and KK (228) fit. The tail is silently truncated, so the embedding never represents it.

### Q3

Number: 75.0
Why (at most 40 words): Top-p keeps the smallest set of tokens reaching 0.95 (Monday, Friday, Sunday) and drops the rest, then renormalises. Lower temperature instead reshapes all probabilities and drops nothing.
### Q4

Number: 25
Why (at most 40 words): The public leaderboard prefers X (72 against 67), because "I don't know" scores zero. That teaches models to guess rather than abstain. With the penalty, Y wins (41 against 16).

### Q5

Number:
Why (at most 40 words):
