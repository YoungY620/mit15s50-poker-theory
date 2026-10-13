# Case 2: Push/Fold Strategy and the Sklansky-Karlson Model

> MIT 15.S50 Poker Theory and Analytics (IAP 2015, Kevin Desmond)
> Issued: Friday, January 19, 2015; Due: Friday, January 26, 2015

## Problems

**Notes**: This case contains sixteen (16) questions, labeled (1.1) through (3.6). Please answer all questions concisely and show all work. State any assumptions you are making. This case is graded pass/fail, where a passing grade is 10/16 points. You earn partial credit for incorrect answers when you show appropriate work. Approximations are acceptable. These questions rely on PokerTracker's Equity Calculator, or an equivalent range-vs-range equity calculator.

### Scenario

It is Saturday, June 7, 2014, and you are deep in the first round of the World Series of Poker (WSOP) Event #20 \$3000 NLHE Shootout. Each of the 40 ten-player tables plays down to 1 player, and the 40 winners from Day 1 form new tables on Day 2. Your table is down to two players from the starting ten, and you lead in chips, 78,000 to the other player's 12,000.

The table is 2-handed as follows. Blinds are 500/1000 with 200 antes.

| Seat | Name | Chip Count |
|------|------|-----------|
| 1 | Hero | 78,000 |
| 2 | BB | 12,000 |
| 3 | [Empty] | N/A |
| 4 | [Empty] | N/A |
| 5 | [Empty] | N/A |
| 6 | [Empty] | N/A |
| 7 | [Empty] | N/A |
| 8 | [Empty] | N/A |
| 9 | [Empty] | N/A |

### Question 1

With good fortune, you recognize your opponent from a Sit-n-Go tournament you played earlier in the week, where you watched this veteran roulette player give advice to the younger crowd.

> Veteran: "The trick is never put all your chips at risk with less than a pair. You see, I see all of these hot shots losing all their money with no hands. The way I see it is that unless you have a made hand, don't risk your tournament life."

After watching his play throughout that SnG tournament and throughout the Shootout, you notice that he goes all-in only with pocket pairs. You believe this mentality will hold when you play him heads up.

**(1.1)** What is the range of the Villain?

**(1.2)** As the small blind, if you open bet all-in, what percentage of the time does the Villain call?

**(1.3)** What is your optimal pushing range from the SB given his calling frequency?

**(1.4)** What is your chance of winning the hand if called, given your pushing range?

**(1.5)** What is your EV before seeing your cards, given your position and both players' ranges?

### Question 2

The following hand, you are in the BB with 79,200 chips to the Villain's 10,800. He open pushes all-in.

**(2.1)** What is the Villain's pushing range and what percentage of hands does that represent?

**(2.2)** Is calling with the top 30% of hands (Sklansky-Karlson) a +EV call?

**(2.3)** Is there a more optimal range for you to call?

**(2.4)** If so, what is the range and what percentage of the time should you call?

**(2.5)** What is the Villain's EV, given that he has pushed all-in, assuming you will call only the optimal range?

### Question 3

You advance to the next round and join a 4-handed table, playing down to two players where you are short-stacked. In the SB, you identify the Villain as a solid player who will call about 30% of your all-in pushes.

**(3.1)** Using the Sklansky-Karlson model, what hands are in the Villain's calling range?

**(3.2)** If you have a stack of 4M, what is your optimal pushing range?

**(3.3)** If you have T♦5♦ in the small blind, what is the maximum chip stack that would make this a profitable all-in bet? Assume BB = 2×SB with no antes.

**(3.4)** If you have 8♥8♦ in the small blind, what is the maximum chip stack that would make this a profitable all-in bet?

**(3.5)** If you have 5M and the Villain's calling range is top 15%, what is your optimal pushing range?

**(3.6)** If you have 5M and the Villain's calling range is Any Two Cards, what is your optimal pushing range? Assume BB = 2×SB with no antes.

## Solutions

### Question 1

**(1.1)** 22+ (all pocket pairs).

**(1.2)** 5.88%.

**(1.3)** 100% (push any two cards).

**(1.4)**

- Model: $50\% + 0.085 \times \ln(5.88\%) - 0.085 \times \ln(100\%) \approx 26\%$
- Exact: 33%

**(1.5)**

- Exact:

$$EV = 1{,}900 \times 94.12\% + 5.88\% \times \left(33\% \times 10{,}800 - 67\% \times 11{,}300\right) \approx 1{,}553$$

- Model:

$$EV = 1{,}900 \times 94.12\% + 5.88\% \times \left(26\% \times 10{,}800 - 74\% \times 11{,}300\right) \approx 1{,}462$$

### Question 2

**(2.1)** 22+, representing 5.88% of hands.

**(2.2)** No. The top 30% of hands has about 40% equity against 22+:

$$EV = 40\% \times 12{,}000 - 60\% \times 9{,}600 = -960$$

**(2.3)** Yes.

**(2.4)** Call with any hand that is 44.4% or better against 22+: 77+, AQs+, which is 4.22% of hands.

**(2.5)**

$$EV = 95.78\% \times 1{,}900 + 4.22\% \times \left(39.67\% \times 11{,}500 - 60.33\% \times 10{,}100\right) \approx 1{,}755$$

### Question 3

**(3.1)** 22+, A2s+, K4s+, Q9s+, JTs, A2o+, K8o+, QJo.

**(3.2)** Any two cards.

**(3.3)** Let $x$ be the stack size (in M), and set $EV = 0$. T♦5♦ has 35.67% equity against this range:

$$0 = 70\% \times 1 + 30\% \times \left(35.67\% \times \left(x + \tfrac{1}{3}\right) - 64.33\% \times \left(x - \tfrac{1}{3}\right)\right)$$

which solves at $x \approx 9.3\text{M}$.

**(3.4)** 88 is a favorite against this range, so any size stack makes this a profitable push.

**(3.5)** Any two cards.

**(3.6)** Let $P\%$ be the pushing frequency, and maximize

$$EV = P\% \times \left[\left(0.50 + 0.085\ln(1) - 0.085\ln(P\%)\right) \times 5.33 - \left(1 - \left(0.50 + 0.085\ln(1) - 0.085\ln(P\%)\right)\right) \times 4.67\right]$$

which peaks at $EV = 0.46$ when Push% ≈ 54%. So the optimal pushing range is roughly the top 54% of hands.

---

*Source: MIT OpenCourseWare, 15.S50 Poker Theory and Analytics, January IAP 2015. <http://ocw.mit.edu>*
