# Case 1: Pot Odds, Draws, and the Semi-Bluff

> MIT 15.S50 Poker Theory and Analytics (IAP 2015, Kevin Desmond)
> Issued: Friday, January 9, 2015; Due: Friday, January 16, 2015

## Problems

**Notes**: This case contains seventeen (17) questions, labeled (1.1) through (4.5). Please answer all questions concisely and show all work. State any assumptions you are making. This case is graded pass/fail, where a passing grade is 10/17 points. Partial credit will be awarded for incorrect answers with appropriate work shown. Using approximations is acceptable.

### Scenario

It is Friday, May 30, 2014, and you are returning for the second day of the World Series of Poker (WSOP) Event #3 \$1000 No-Limit Hold'em. There are 186 of 2,224 players remaining, and you have 63,500 chips, making you 26th of 186 overall at the start of Day 2. You are entering a new table and have no reads. Already in the money, you can treat the payoff differences as immaterial until the final table, so act to maximize expected chips for that hand.

The table is 8-handed as follows. Blinds are 600/1200 with 200 antes. You are on the button and will be in that position for all questions, although chip amounts will vary slightly as the day progresses.

| Seat | Name | Chip Count |
|------|------|-----------|
| 1 | SB | 22,800 |
| 2 | [Empty] | N/A |
| 3 | BB | 17,900 |
| 4 | UTG | 32,400 |
| 5 | UTG+1 | 25,800 |
| 6 | MP1 | 10,000 |
| 7 | MP2 | 29,100 |
| 8 | CO | 77,100 |
| 9 | Hero | 63,500 |

### Hand 1

- UTG+1: 25,800, M = 7.59
- MP1: 10,000, M = 2.94
- Hero (BTN): 63,500, M = 18.68

**Pre Flop**: (3,400) Hero is BTN with A♣ 9♥
1 fold, UTG+1 raises to 3,600, 1 fold, MP2 calls 3,600, 1 fold, Hero calls 3,600, 2 folds

**Flop**: (14,200) 2♣ T♣ K♣ (3 players)
UTG+1 bets 3,000, MP2 folds, Hero…

### Question 1

**Assumptions**: UTG+1 will bet again on the turn, except if it is a club, in which case he will check/fold to any bet.

**(1.1)** What hand is the Hero drawing to?

**(1.2)** How likely is he to hit his draw on the next card, or the next two cards?

**(1.3)** What percentage of the pot is the Hero contributing to see another card?

**(1.4)** Should the Hero make this call? Approximately what is the EV of this call?

**(1.5)** What is the largest bet that the Hero can profitably call?

### Hand 1 (continued)

- UTG+1: 25,800, M = 7.59
- MP1: 10,000, M = 2.94
- Hero (BTN): 63,500, M = 18.68

**Pre Flop**: (3,400) Hero is BTN with A♣ 9♥
1 fold, UTG+1 raises to 3,600, 1 fold, MP2 calls 3,600, 1 fold, Hero calls 3,600, 2 folds

**Flop**: (14,200) 2♣ T♣ K♣ (3 players)
UTG+1 bets 3,000, MP2 folds, Hero calls 3,000

**Turn**: (20,200) 5♦ (2 players)
UTG+1 bets 9,000, Hero…

### Question 2

**Assumptions**: UTG+1 will bet/call any size bet on the river, regardless of the board.

**(2.1)** How likely is the Hero to hit his draw on the river?

**(2.2)** What percentage of the pot is the Hero contributing to see another card?

**(2.3)** How much does the Hero have to make on the river to make this a profitable call? Is this realistic?

### Scenario Update

Later in the day, MP1 has been eliminated and replaced by a short stack. Your reads are that UTG+1 and BB are aggressive and loose callers. You have identified SB as weak/tight. Chip stacks are as follows.

| Seat | Name | Chip Count |
|------|------|-----------|
| 1 | SB | 19,500 |
| 2 | MP1 | 4,200 |
| 3 | BB | 5,500 |
| 4 | UTG | 38,600 |
| 5 | UTG+1 | 13,200 |
| 6 | [Empty] | N/A |
| 7 | MP2 | 33,100 |
| 8 | CO | 90,500 |
| 9 | Hero | 78,200 |

### Hand 2

- Hero (BTN): 78,200, M = 23.00
- SB: 19,500, M = 5.74

**Pre Flop**: (3,400) Hero is BTN with 5♥ 6♦
4 folds, Hero raises to 3,600, SB calls 3,000, 1 fold

**Flop**: (10,000) 4♣ 7♠ K♥ (3 players)
SB checks, Hero bets 6,000, SB…

### Question 3

**Assumptions**: SB will call with a two pair or better. If he calls, he will check the turn on any card.

**(3.1)** What is the Hero's fold equity if the SB folds 70% of the time?

**(3.2)** What is the Hero's EV-if-called after this bet?

**(3.3)** Is the Hero's bet +EV?

**(3.4)** What percentage of the time does SB have to fold to make this bet +EV?

### Hand 2 (continued)

- Hero (BTN): 78,200, M = 23.00
- SB: 19,500, M = 5.74

**Pre Flop**: (3,400) Hero is BTN with 5♥ 6♦
4 folds, Hero raises to 3,600, SB calls 3,000, 1 fold

**Flop**: (10,000) 4♣ 7♠ K♥ (3 players)
SB checks, Hero bets 6,000, SB raises to 15,700 all in, Hero…

### Question 4

**(4.1)** What hand is the Hero drawing to?

**(4.2)** How likely is he to hit his draw on the next two cards?

**(4.3)** What percentage of the pot is the Hero contributing to see another two cards?

**(4.4)** Should the Hero make this call? Approximately what is the EV of this call?

**(4.5)** What is the largest raise that the Hero can profitably call?

## Solutions

### Question 1

**(1.1)** Flush.

**(1.2)** Hero has 9 outs (the remaining clubs).

- Quick rule: $9 \times 2\% = 18\%$ for one card, or $9 \times 4\% = 36\%$ for two cards.
- Exact: $9/47 \approx 19\%$ for one card, or

$$1 - \frac{38}{47}\times\frac{37}{46} \approx 35\% \quad \text{for two cards}$$

**(1.3)** Hero must call 3,000 into a pot that will be 20,200 after the call:

$$\frac{3{,}000}{20{,}200} \approx 15\%$$

**(1.4)** Yes, call.

- If one card: $EV \approx 19\% \times 17{,}200 - 81\% \times 3{,}000 = 838$
- If two cards: $EV \approx 35\% \times 17{,}200 - 65\% \times 3{,}000 = 4{,}070$

**(1.5)** Let $x$ be the largest callable bet, and set its share of the pot equal to the probability of hitting:

- One card: $\dfrac{x}{14{,}200 + 2x} = 19\%$, which gives $x = 4{,}350$
- Two cards: $\dfrac{x}{14{,}200 + 2x} = 35\%$, which gives $x = 16{,}550$

### Question 2

**(2.1)** The flush draw still has 9 outs, with 46 unknown cards remaining:

$$\frac{9}{46} = 19.6\% \quad(\text{18\% by the quick rule})$$

**(2.2)** Hero must call 9,000 into a pot that will be 38,200 after the call:

$$\frac{9{,}000}{38{,}200} \approx 23.6\%$$

**(2.3)** If only the flush is good, the pot needs to be

$$9{,}000 / 19.6\% \approx 45{,}900$$

or 7,700 more than it currently offers (implied odds). With the quick rule: $9{,}000 / 18\% \approx 50{,}000 - 38{,}200 = 11{,}800$ more.

The Villain has 10,000 left after this bet, so the 11,800 more required by the quick rule is not realistic, while the 7,700 more from the exact solution probably is.

### Question 3

**(3.1)** Fold equity:

$$70\% \times 10{,}000 - 30\% \times 6{,}000 = 5{,}200$$

**(3.2)** Hero's equity against SB's calling range (74 / K7 / K4 / 44 / 77 / KK) is 29% (quick rule: $8 \times 4\% = 32\%$).

$$EV = 16{,}000 \times 29\% - 6{,}000 \times 71\% = 380$$

(i.e., we prefer a call)

**(3.3)** Yes:

$$EV = 70\% \times 10{,}000 + 30\% \times \left[16{,}000 \times 29\% - 6{,}000 \times 71\%\right] = 7{,}114$$

**(3.4)** Let $F$ be SB's folding frequency, and set $EV = 0$:

$$0 = F \times 10{,}000 + (1-F) \times \left[16{,}000 \times 29\% - 6{,}000 \times 71\%\right]$$

which solves at $F < 0\%$. We have the pot odds to see two more cards, so it is profitable even if he calls 100% of the time.

### Question 4

**(4.1)** Straight.

**(4.2)** Hero has 8 outs (a 3 or an 8, an open-ended straight draw):

$$1 - \frac{39}{47}\times\frac{38}{46} \approx 31\% \quad(\text{quick rule: } 8 \times 4\% = 32\%)$$

**(4.3)** Hero must call $15{,}700 - 6{,}000 = 9{,}700$ into a pot that will be 41,400 after the call:

$$\frac{9{,}700}{41{,}400} \approx 23\%$$

**(4.4)** Yes:

$$EV = 31{,}700 \times 31\% - 9{,}700 \times 69\% = 3{,}134$$

**(4.5)** Let $x$ be the largest callable raise:

$$\frac{x}{22{,}000 + 2x} = 31\% \;\Rightarrow\; x \approx 17{,}947$$

---

*Source: MIT OpenCourseWare, 15.S50 Poker Theory and Analytics, January IAP 2015. <http://ocw.mit.edu>*
