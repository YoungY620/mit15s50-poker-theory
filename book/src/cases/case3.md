# Case 3: Satellites, Blind Defense, and ICM

> MIT 15.S50 Poker Theory and Analytics (IAP 2015, Kevin Desmond)
> Issued: Friday, January 23, 2015; Due: Friday, January 30, 2015

## Problems

**Notes**: This case contains twelve (12) questions, labeled (1.1) through (2.5). Please answer all questions concisely and show all work. State any assumptions you are making. This case is graded pass/fail, where a passing grade is 7/12 points. Partial credit will be awarded for incorrect answers with appropriate work shown. Using approximations is acceptable. These questions rely on PokerTracker's ICM Calculator, or an equivalent ICM (Independent Chip Model) calculator.

### Scenario

It is Thursday, July 3, 2014, and you are playing in a \$550 Mega Satellite to the WSOP Event #68: \$10,000 NLHE Main Event. In this tournament, 1 in 20 players wins a \$10,000 ticket to the main tournament. There were 140 entries, and the top 7 players will win tickets. 60 players remain in the tournament.

The table is 9-handed, with blinds of 1000/2000 and a 300 ante.

| Seat | Name | Chip Count |
|------|------|-----------|
| 1 | Hero | 40,000 |
| 2 | UTG | 160,000 |
| 3 | UTG+1 | 140,000 |
| 4 | MP1 | 114,000 |
| 5 | MP2 | 154,000 |
| 6 | LP | 76,000 |
| 7 | CO | 168,000 |
| 8 | BTN | 182,000 |
| 9 | SB | 160,000 |

### Question 1

Before this hand, you have developed an image of being very tight, and as a result you are facing a raise every time you are in the BB. As a short stack, losing this BB every round is painful and you are looking to defend your blind. Assume each steal attempt is a raise of 3BB and the Villains are stealing with any two cards.

**(1.1)** What is your M?

**(1.2)** If you decide to re-raise to 6BB, what odds does the Villain have to call if he is the BTN?

**(1.3)** Given that he has a range of ATC, what would your range have to be to make this a bad call for him?

**(1.4)** If the Villain re-raises all-in, what odds would you have to call?

**(1.5)** If you raise the maximum instead of 3BB, what odds does the Villain have to call?

**(1.6)** If you have QTo and re-raise all-in, do you prefer a call or a fold? Assume Villain will call with any two cards.

### Question 2

You reached the final table of the satellite and there are 8 players remaining to win seven \$10,000 tickets. Everyone values the tickets at \$10,000 (they are indifferent to playing the Main Event if they win the satellite). You view yourself as an approximately average player compared to the remainder of the table. The chip stacks are as follows:

Blinds are 8000/16000 with 2000 ante.

| Seat | Name | Chip Count |
|------|------|-----------|
| 1 | Hero | 66,000 |
| 2 | UTG | 13,000 |
| 3 | UTG+1 | 80,000 |
| 4 | MP1 | 30,000 |
| 5 | MP2 | 31,000 |
| 6 | LP | 73,000 |
| 7 | BTN | 49,000 |
| 8 | SB | 78,000 |

**(2.1)** Per PokerTracker, what is our \$EV in this tournament? If a chop (prize split) is offered and each player will get \$9,000, should you take it?

**(2.2)** You have A♥ A♣ and SB open pushes all-in with ATC. What is your chip EV from calling?

**(2.3)** What is your \$EV from calling? Should you call?

**(2.4)** What is the \$EV loss from doing the wrong action?

**(2.5)** The following hand, it is folded to you in the SB and the BB (seat 2) is forced all-in. What range should you call? Assume you folded the previous hand.

**(2.5)** What is the \$EV of calling optimally?

## Solutions

### Question 1

**(1.1)** M is the ratio of your stack to one round of forced bets (blinds plus antes):

$$M = \frac{40{,}000}{1{,}000 + 2{,}000 + 300 \times 9} = 7.1$$

**(1.2)** The Villain is facing a call of 6,000 (3BB, having already put in a 3BB raise). The pot is

$$1{,}000 + 2{,}000 + 300 \times 9 + 6{,}000 \times 3 - 2{,}000 = 21{,}700$$

so he would need his equity to be

$$\frac{6{,}000}{27{,}700} \approx 22\% \quad \text{to call}$$

**(1.3)**

- Exact: the threshold is the top 2% (QQ+, AKs+); that range vs. ATC is an 80%/20% split.
- Model: set the threshold at 22%:

$$22\% = 50\% + 0.085 \times \ln(C\%) - 0.085 \times \ln(1)$$

which solves at $C\% \approx 3.7\%$, i.e., your range has to be about the top 3.7%.

**(1.4)** Effective stacks are 40,000. After this raise, your stack would be $40{,}000 - 12{,}300 = 27{,}700$. Before the raise, the pot would be $15{,}700 + 12{,}000 = 27{,}700$. So you would be facing a bet of 27,700 to win a pot of $3 \times 27{,}700$, for 33% equity.

**(1.5)** The effective stack is $40{,}000 - 6{,}300 = 33{,}700$. We would raise this amount into a pot of 21,700, giving the Villain

$$\frac{33{,}700}{21{,}700 + 33{,}700 \times 2} \approx 38\% \quad \text{to call}$$

**(1.6)** QTo is 57% vs. ATC. If the Villain folds, our EV is

$$100\% \times 15{,}700 = 15{,}700$$

If the Villain calls, our EV is

$$57\% \times (15{,}700 + 33{,}700) - 43\% \times 33{,}700 = 13{,}667$$

so we prefer a fold.

### Question 2

**(2.1)** Our ICM equity is \$9,668. We should not take a deal for \$9,000 unless we are very risk averse.

**(2.2)** AA vs. ATC is 85%. So our chip EV is

$$cEV = (48{,}000 + 8{,}000 \times 2 + 16{,}000 + 2{,}000 \times 8) \times 0.85 - 48{,}000 \times 0.15 = 74{,}400$$

**(2.3)** If we call and lose, our \$EV is 0. If we call and win, the stacks are as follows:

| Seat | Name | Chip Count |
|------|------|-----------|
| 1 | Hero | 144,000 |
| 2 | UTG | 11,000 |
| 3 | UTG+1 | 78,000 |
| 4 | MP1 | 28,000 |
| 5 | MP2 | 29,000 |
| 6 | LP | 71,000 |
| 7 | BTN | 47,000 |
| 8 | SB | 12,000 |

giving us a \$EV of \$9,990. Our \$EV from the call is then

$$0.85 \times \$9{,}990 + 0.15 \times 0 = \$8{,}492$$

If we fold, our stack is 48,000, giving us a \$EV of \$9,445, which is higher than \$8,492. So fold.

**(2.4)** The difference between the calling \$EV and the folding \$EV is

$$\$9{,}445 - \$8{,}492 = \$953$$

so taking the wrong action (calling) loses \$953.

**(2.5)** BB's range is ATC. If we fold, we have 38,000 chips, giving us a \$EV of \$8,452. If we call and lose, our stack is 37,000, giving us a \$EV of \$8,384. If we call and win, our \$EV is \$10,000. So we can profitably call if our chance to win is $x$, where $x$ solves

$$\$10{,}000 \times x + \$8{,}384 \times (1-x) > \$8{,}452$$

or $x > 4\%$. So call with ATC.

**(2.5)** We should call any time our equity is more than 4% (i.e., always). This gives us an equity of 50% vs. ATC, meaning our \$EV from calling is

$$50\% \times \$10{,}000 + 50\% \times \$8{,}384 = \$9{,}192$$

---

*Source: MIT OpenCourseWare, 15.S50 Poker Theory and Analytics, January IAP 2015. <http://ocw.mit.edu>*
