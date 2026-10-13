# L3 Basic Strategy

This is the first lecture that deals with poker strategy proper. It begins with the terminology of position, then develops the three core decision tools in turn: pot odds, implied odds, and fold equity with semi-bluffing. All of them answer the same question: how to turn every decision into a computable expected-value threshold.

## Position Terminology

Seats at the table fall into four groups: the blinds, early position, middle position, and late position. Position matters because players who act later get to see what earlier actors did before making their own decision; they hold more information. When describing a hand we refer to players by position rather than by name.

![Position terminology: the blinds, early position (the UTG seats), middle position (MP1–MP3), and late position (CO, BTN)](assets/ch03-1.png)

Starting from the left of the big blind (BB), early position consists of under the gun (UTG), UTG+1, and UTG+2; middle position is MP1, MP2, MP3; late position is described relative to the button: the button itself (BTN, the small D disk in the diagram) and the cutoff (CO, the seat that "cuts off" the button). Some people call the seat to the right of the CO the hijack; this course does not. The small blind (SB) and big blind make up the blinds group. In a 6-handed game we drop the least interesting seats (UTG+2, MP1, MP2, MP3) and keep the ones with real names: UTG, UTG+1, CO, BTN, SB, BB.

The basic conclusions about position:

- In general, later position is better: you act with more information and can profitably play a wider range of starting hands. Money flows toward late position: the button should be your most profitable seat, and if you are losing money on the button you should seriously re-evaluate how you play it.
- The blinds get a discount to see the flop because they were forced to put chips in; but on every post-flop round they act first, at the worst informational disadvantage. The discount buys entry into a hand you will almost certainly play at an informational disadvantage.
- In short-stack (low-M) situations, however, early position has the edge: the first actor can go all-in before anyone else and keep the fold equity that comes from aggression. This resembles the game of chicken: two cars drive at each other and the first to swerve loses; the optimal strategy is to throw your steering wheel out the window so the opponent knows you have no choice. In a tournament, when neither player wants to flip for their tournament life at showdown, the early-position player can shove first and scare the opponent off.

## Pot Odds

### Why Odds Come into Play

The most common situation is a weak made hand versus a drawing hand: on the flop one player holds a pair or two pair while the other holds only a straight or flush draw; pre-flop it is a pocket pair against anything else. The drawer must weigh the chance of hitting the draw against what each additional card costs; the made hand wants to bet enough that the drawer's call is not +EV, or equivalently, to bet an amount that bad players will mistake for a good price. The two are equally good; the second is arguably better.

### Expected Value

Expected value (EV) is the probability-weighted average of all possible results:

$$EV = \text{Win\%} \times \text{WinAmt} - \text{Lose\%} \times \text{LoseAmt}$$

For example, with a 25% chance of winning and facing a \$60 bet into a \$100 pot: $EV = 25\% \times (100+60) - 75\% \times 30 = 17.5$. Every decision rule in this course is built on expected value.

Consider the following scenario (the hand format used throughout this chapter: relevant stacks and blinds on top, the pot before the current round's action in parentheses; Hero is the player we care about, Villain is the opponent):

```
John_VH925 (UTG+1): $500        Blinds 20/40 + 10 ante
Hero (MP1): $500

Pre Flop: ($140) Hero is MP1 with A♥T♥
1 fold, John_VH925 raises to $120, Hero calls $120, 5 folds

Flop: ($380) 8♥ 3♥ K♣ (2 players)
John_VH925 bets $370 all in, Hero…?
```

Rather than asking "should we call," ask the more resilient question: **what is the maximum bet Hero can call?** If Villain bets $x$, then

$$EV = \text{W\%} \times (380 + x) - \text{L\%} \times x$$

and the calling threshold sits at $EV = 0$.

### Pot Odds

Pot odds describe the relationship between the **call amount and the size of the pot after the call**. The general rule: a call is +EV whenever

$$\text{Win\%} > \frac{\text{CallAmt}}{\text{Pot} + \text{BetAmt} + \text{CallAmt}}$$

For instance, if Villain bet \$100 into the \$380 pot, the pot odds would be $100/\$580$ (where 580 = pot + bet + call): Hero's call contributes about 17% of the new pot, so any win rate above 17% is profitable. (Some players use "4-to-1"-style notation instead; this course consistently uses "your percentage of the pot," which is more intuitive.)

Win% is determined by **outs**, the cards that win you the hand. Here the 9 remaining hearts all make the flush, and the exact win rate is the probability of hitting at least one of them on the turn or river:

$$\text{Win\%} = 1 - \frac{40}{49} \times \frac{39}{48} \approx 34\%$$

Since 34% far exceeds 17%, this is a very good call: $EV = 34\% \times \$480 - 66\% \times \$100 = \$97.2$.

![The pie-chart intuition for pot odds: in a \$580 pot, your 34% share is \$197, of which \$100 is the cost of the call and the remaining \$97 is EV](assets/ch03-2.png)

The figure gives the intuition: the whole pie is the \$580 pot after your call, and your 34% win rate corresponds to a \$197 slice. That slice consists of the cost of the call (\$100) plus the expected profit (\$97). The cheaper the call, the bigger the EV slice; an oversized call turns the EV slice negative.

### Gordon's Rule of 2 and 4

The quick tool for estimating win rate is Phil Gordon's rule of 2 and 4, from *Phil Gordon's Little Green Book*. Gordon finished fourth in the 2001 WSOP Main Event, won a WPT title and two North American Bridge Championships, and served as head referee of the World Series of Rock Paper Scissors. The rule:

- Each out is worth about **2%** of equity per additional card you get to see (2% comes roughly from 1/50, a coarse approximation over the 47–49 remaining cards);
- If you get to see both the turn and the river (for example, because the opponent is all-in), count each out at **4%**.

Examples: holding a low pair on the flop and drawing to three-of-a-kind, you have 2 outs, about 4% per card; a flush draw has 9 outs, $9/47 \approx 18\% = 9 \times 2\%$; an inside straight draw has 4 outs, $4/47 \approx 8\% = 4 \times 2\%$. The exact calculation is very close to simply multiplying by 2.

### Solving the Threshold and the Real-Time Method

Back to Scenario A: Villain shoves $x$ into the \$380 pot. Because he is all-in, we are guaranteed both cards, so the win rate is about $9 \times 4\% = 36\%$ (exact value 34%). Setting $EV = 0$:

$$34\% \times (380 + x) - 66\% \times x = 0 \implies x = \$404$$

Check: $404 / (404 \times 2 + 380) \approx 0.34$. This yields a solution set: **call any bet up to \$404, fold to anything larger.**

![Solution set: bets up to \$404 are calls, anything larger is a fold](assets/ch03-3.png)

At the table you do not solve equations. Hero knows he makes the flush about 36% of the time, so he can profitably contribute up to 36% of the new pot. Facing the \$370 shove, the new pot would be $380 + 370 + 370 = 1120$ and his contribution is $370/1120 = 33\% < 36\%$, so he calls. That is how the decision is made in real time.

### More Examples

**Example 1 (open-ended straight draw).** Villain (MP): \$250, Hero (BTN): \$1000, blinds 20/40+10. Hero holds 6♦7♦; Villain raises to \$90 pre-flop, Hero calls. Flop (\$320) 8♠5♥K♣, Villain shoves \$150.

1. Drawing to? An open-ended straight.
2. Outs? Any 9, any 4: 8 cards total.
3. Chance of hitting? $8 \times 4\% = 32\%$ (Villain is all-in, so we see both cards).
4. Correct play? Call: $150/620 = 24\% < 32\%$.
5. EV? $32\% \times 470 - 68\% \times 150 = 48.4$.

**Example 2 (set drawing to a full house, against an undersized bet).** Villain (MP): \$3000, Hero (BTN): \$3000, blinds 100/200. Hero holds 5♦5♥; Villain raises to \$400, two players call, Hero calls. Flop (\$1900) 5♣A♣6♣, Villain bets \$200. With three clubs on board, Hero's set is very likely behind a flush.

1. Drawing to? A full house or four-of-a-kind.
2. Outs? Three A's, three 6's, one 5: 7 cards total.
3. Chance of hitting? Only one card can be counted on (Villain is deep and will very likely bet again on the turn): $7 \times 2\% = 14\%$.
4. Correct play? Call: $200/2300 \approx 9\% < 14\%$.
5. EV? $14\% \times 2100 - 86\% \times 200 = 122$.

Note Villain's mistake: he bet only about a tenth of the pot. If he has the flush, he failed to protect his hand; if he doesn't, he is giving money away. Newer players make this error constantly. They bet small because they are afraid of scaring the opponent off, when a fold would actually be preferable. The right bet size leaves the opponent with two options: fold, or call and make a mistake.

**Example 3 (small blind versus big blind, "blind vs blind").** Villain (BB): \$200, Hero (SB): \$1000, blinds 100/200. Hero holds 5♣7♥ in the small blind, and the big blind's entire \$200 is already in the pot; calling is equivalent to facing his all-in.

1. Drawing to? Anything: Villain holds any two cards (ATC).
2. Win rate? 57o versus a random hand is about 40% (even the worst hand, 32o, is about 32% against a random hand).
3. Correct play? Call: $100/400 = 25\%$, and 40% (even 32%) is far above 25%.
4. EV? $40\% \times 300 - 60\% \times 100 = 60$. Folding here throws away about \$60.

## Implied Odds

### Hand Rules

The solution to a pot-odds question is "can I call" or "what is the most I can call"; the solution to an implied odds question is different: **how many more chips must I win after hitting my draw for the call in front of me to be good.** The method: find the pot size at which the current call would be exactly x% of the pot (x% being your win rate), then subtract the pot that will actually exist after the call. The difference is the "dead money" that must be added later.

Example: a flush draw, 18% to hit on one card, facing a \$180 bet into a \$300 pot. After the call the pot is \$660, and the call represents $180/660 = 27\%$ of it, too expensive by pot odds, a fold. But if the pot were $180/18\% = \$1000$, the same call would break even. The difference, $\$1000 - \$660 = \$340$, is the dead money that must be won after the flush comes in: that \$340 turns our \$180 call into 18% of a \$1000 pot. The remaining question, a matter of judgment, is whether that \$340 is realistic.

![Implied odds: a \$180 call is 27% of the \$660 pot, but adding \$340 of dead money makes it 18% of a \$1000 pot](assets/ch03-4.png)

### Examples

**Example 1 (middle pair drawing to two pair or trips).** Villain (MP): \$3000, Hero (BTN): \$3000, blinds 25/50. Hero holds K♦T♥; Villain raises to \$150, Hero calls. Flop (\$375) T♣A♥6♦, Villain bets \$100.

1. Drawing to? Two pair or three-of-a-kind.
2. Outs? Three K's, two T's: 5 cards total.
3. Chance of hitting? One card only: $5 \times 2\% = 10\%$.
4. Pot odds? $100/575 \approx 17\%$, too expensive.
5. Additional bets needed after the draw to break even? $100/10\% = \$1000$, and $\$1000 - \$575 = \$425$.

That \$425 is realistic: Villain has already put \$100 into what was a \$400 pot; he will very likely bet another \$200–\$300 on the turn, and our draw is extremely well disguised: if we hit and raise, he can hardly get away.

**Example 2 (flush + straight combination draw).** Villain (MP): \$3000, Hero (BTN): \$3000, blinds 25/50. Hero holds K♣Q♣; Villain raises to \$100, Hero calls. Flop (\$275) T♣J♣3♥, Villain bets \$600.

1. Drawing to? A straight or a flush (a K-high flush should be good; one pair does not count).
2. Outs? 9 flush outs + 8 straight outs − 2 overlapping = 15 cards (any A, any 9, and the 7 other clubs).
3. Chance of hitting? One card only: $15 \times 2\% = 30\%$.
4. Pot odds? $600/1475 \approx 41\%$, too expensive.
5. Additional bets needed after the draw to break even? $600/30\% = \$2000$, and $\$2000 - \$1475 = \$525$.

The \$525 is likewise realistic: Villain already bet \$600, so even when the club comes he will most likely be committed to at least another \$500 bet or call.

### Drawing Formulas

- **EV (marginal value of any decision)**: $x = \text{Win\%} \times \text{WinAmt} - \text{Lose\%} \times \text{LoseAmt}$
- **Rule of 2 and 4 (chance of hitting a draw)**: $x = 2\% \times \#\text{Outs} \times \#\text{FreeCards}$
- **Pot odds (decision rule for calling a bet)**: $\text{Win\%} > \dfrac{\text{CallAmt}}{\text{Pot} + \text{BetAmt} + \text{CallAmt}}$
- **Implied odds (chips needed after the draw hits to justify the call)**: $x = \dfrac{\text{BetAmt}}{\text{Win\%}} - (\text{Pot} + \text{BetAmt} + \text{CallAmt})$

Applied to the earlier examples: calling \$150 into a \$320 pot with a 32% chance to win, $EV = 32\% \times 470 - 68\% \times 150 = \$48.4$; a flush draw with 9 outs seeing only the turn, $18\% = 2\% \times 9 \times 1$; facing a \$370 all-in for a \$380 pot with a flush draw, $36\% > 370/1120$ holds, so call; facing a \$100 bet into a \$375 pot with a 10% draw, the implied-odds requirement is $(100/10\%) - 575 = \$425$.

### Live Example: 2014 WSOP Main Event Final-Table Bubble

The 2014 WSOP Main Event is down to 10 players, the final-table bubble; one more elimination sends the "November Nine" into a three-month break. Blinds 150k/300k with a 50k ante:

```
Hero/Jacobson (UTG): 22,450k   Tonking (SB): 6,775k

Pre Flop: (950k) Hero is UTG with A♣J♣
Hero calls 300k, 7 folds, Tonking calls 150k, Sindelar (BB) checks

Flop: (1,400k) 7♣ 8♥ T♣ (3 players)
Tonking checks, Sindelar bets 500k, Hero raises to 1,750k,
Tonking raises 4,525k to 6,275k all in, Sindelar folds, Hero…?
```

Analysis (the ESPN broadcast revealed both opponents' hole cards: Tonking actually held J♥9♣ for a made straight; Sindelar held J♠8♠ for middle pair plus a gutshot, which explains his 500k lead on the flop and his fold to the raises. Hero knew none of this. The three-way flop equities were Tonking 56%, Jacobson 34%, Sindelar 2%):

- Drawing to? A flush, and possibly a straight.
- Outs? All 9 remaining clubs win outright; the 3 non-club 9's win only sometimes (a split if Villain has a J, a loss against QJ), so we discount them at 50% into 1.5 outs, for **10.5 outs** total. Outs can be prorated into "partial outs" by the probability that hitting them wins; if the conservative estimate still says call, the real answer is an even clearer call.
- Chance of hitting? Villain is all-in, so we see both cards: $10.5 \times 4\% = 42\%$.
- Correct play? The pot will be $1400\text{k} + 500\text{k} + 2 \times 6275\text{k} = 14{,}450\text{k}$ (Sindelar's folded 500k is dead money), and the call of 4,525k is about 31% < 42%, so call.
- EV? $42\% \times 9925\text{k} - 58\% \times 4525\text{k} = 1544\text{k}$; even under the conservative estimate, this call is worth about 1.5 million chips.

Jacobson called. The turn came 5♦ and the river 7♦; the third club never arrived, and Tonking's straight took the pot. Notably, the broadcast showed Jacobson down to 8 live outs (about 18%) on the turn: the 9♣ was in Tonking's hand, and the other three non-club 9's would only produce a split, so they no longer counted as winning outs, a real-game confirmation of the partial-out discount. Jacobson lost the hand but went on to win the 2014 WSOP Main Event.

### Drawing — Be Careful About

- **Don't draw to a hand that may not win even when you hit it**: a Q-high or lower flush can be dominated by a bigger flush; the low end of a straight is extremely dangerous: players routinely hit it, discover they made the second-best hand, and go broke; on a paired board (a pair on the board, making full houses and quads possible) a flush or straight draw may be drawing dead (0% to win).
- **Don't assume one bet buys you both the turn and the river**: unless the aggressor is all-in, this very rarely happens. Many players call the flop planning to see two cards cheaply; the assumption fails, and they bleed EV.
- **Don't overestimate how easy it is to extract chips after you hit**: a flush completing on the turn or river is glaringly obvious, a straight is better disguised, and a set is nearly impossible to read, so sets carry huge implied odds while flush draws carry very small ones.
- **Don't bet so little that you give opponents a +EV call**: most flop and turn bets should be around half to two-thirds of the pot, to punish chasing.

## Fold Equity and Semi-Bluffing

### The Concept

Fold equity is the value the bettor gains from the possibility that the opponent folds, under the assumption that being called means losing. Write Fold% for the opponent's fold rate and showdown-win% (SD-Win%) for the probability of winning at showdown:

$$\text{Fold Equity} = \text{Pot} \times \text{Fold\%} - \text{Bet} \times (1 - \text{Fold\%}) \quad (\text{SD-Win\%} = 0)$$

$$\text{Fold Equity} = \text{Pot} \times \text{Fold\%} + (1 - \text{Fold\%}) \times EV_{\text{if called}} \quad (\text{SD-Win\%} > 0)$$

where the showdown value is $\text{SD Value} = (1 - \text{Fold\%}) \times EV_{\text{if called}}$.

A **bluff** is a bet that is +EV because the fold equity alone is positive; a **semi-bluff** is a bet whose fold equity is negative but which is still +EV once a sufficiently high showdown-win% is added. A semi-bluff has two ways to win, stealing the pot outright or drawing out, and is used constantly in tournaments: you won't always have a made hand, but you will always have something that can become one.

### Breakeven Fold Rate for a Pure Bluff

```
Turkito694 (UTG): $2098        Blinds $5/$10
Hero (CO): $990

River: ($350) A♦ 5♥ 8♦ Q♠ 2♦ (2 players)
Turkito694 checks, Hero holds 6♠7♠ and bets $150…
How often does this bluff have to work to be profitable?
```

Hero's draws never came in, but his passive calls on the first three streets "represent a flush" in the opponent's eyes; the river check is exactly the fear of that flush. Hero's showdown-win% is 0:

$$EV = 350 \times \text{Fold\%} - 150 \times (1 - \text{Fold\%}) > 0 \iff \text{Fold\%} > \frac{150}{350 + 150} = 30\%$$

Check: $30\% \times 350 - 70\% \times 150 = 0$. Note the denominator is "pot + your own bet" (if Villain folds, he never adds chips to the pot), one bet fewer than in the pot-odds formula. As long as Villain folds more than 30% of the time the bluff is +EV, and since Hero represents a flush, that seems well within reach.

### Semi-Bluffing: The Impact of Win%

Same \$150 bet into the \$350 pot, but now Hero is raising and holds an open-ended straight draw (one card to come, 8 outs, 16% to win at showdown). Solving $EV = 0$ for the breakeven fold rate:

$$\text{Fold\%} = \frac{13\,\text{Win\%} - 3}{13\,\text{Win\%} - 10}$$

At 16% Win%, the breakeven fold rate is only about 12%, far below the 30% of the pure bluff. That difference is the value of semi-bluffing. Plotting the function reveals more structure:

![Breakeven Fold% as a function of Win%: endpoints (0%, 30%) and (23%, 0%), with secant slope ≈ 1.5](assets/ch03-5.png)

Three points on the curve are worth noting (coordinates are (Win%, Fold%)):

- **(0%, 30%)**: with zero showdown value this is the pure-bluff breakeven, $150/(150+350) = 30\%$.
- **(16%, 12%)**: the open-ended straight draw seeing one card; Villain only needs to fold more than 12% of the time for the bet to be +EV.
- **(23%, 0%)**: if Villain never folds, our bet is equivalent to facing a \$150 bet and calling it; the point degenerates to the pot-odds breakeven, $150/(350+150+150) \approx 23\%$.

The secant line connecting the two endpoints gives a fast approximation: **each additional 1% of showdown-win% lowers the breakeven fold rate by about 1.5%** (a slight underestimate, but accurate enough in practice). Taking the partial derivative with respect to bet size pins down the bounds of that sensitivity:

$$\lim_{\text{Bet} \to \infty} \frac{\partial \text{F\%}}{\partial \text{W\%}} = 2, \qquad \lim_{\text{Bet} \to \text{Pot}} \frac{\partial \text{F\%}}{\partial \text{W\%}} = 1.5, \qquad \lim_{\text{Bet} \to 0} \frac{\partial \text{F\%}}{\partial \text{W\%}} = 1$$

A pot-sized bet corresponds to the coefficient 1.5, and no matter how large or small the bet, the coefficient always falls in the interval (1, 2).

### Real-Time Rules of Thumb

- With zero showdown value: breakeven Fold% = bet / (pot + bet). A pot-sized bet needs to work 50% of the time; scale approximately linearly downward: a half-pot bet needs about 25% (the exact value is $0.5/1.5 = 33\%$, and the approximation error is acceptable).
- With positive showdown value there is no clean general rule, but: value is much higher with a real draw; you can assume "showdown-win% × 1.5 discounted off the breakeven fold rate"; and pre-flop bets are essentially always semi-bluffs (there is always a flop to come). Pure bluffs are rare precisely because showdown-win% improves value so materially.

### Examples

**Example 1 (pure bluff).** Villain (MP): \$3000, Hero (BTN): \$3000, blinds 25/50. Hero holds T♦5♠ and calls Villain's \$150 raise. River (\$375) 4♣8♥9♦6♥6♦, Villain checks, Hero bets \$250. Hero has ten-high and always loses at showdown.

1. Bluff or semi-bluff? Pure bluff.
2. Showdown-win%? 0.
3. Breakeven Fold%? $250/625 = 40\%$.
4. If Villain calls only 25% of the time, is it a good bet? Yes: fold rate 75% > 40%.
5. Fold equity? $375 \times 75\% - 250 \times 25\% = 218.75$.

**Example 2 (semi-bluff).** Villain (MP): \$800, Hero (BTN): \$1500, blinds 25/50. Hero holds 9♥T♥ and calls a \$150 raise. Turn (\$775) 4♣8♠7♦2♥, Villain checks, Hero bets \$450. Hero has a gutshot (any 6, 4 outs, one card to come).

1. Bluff or semi-bluff? Semi-bluff, showdown-win% 16%.
2. If Villain calls 80%, showdown value? $80\% \times (16\% \times 1225 - 84\% \times 450) = -\$145.6$.
3. Breakeven Fold%? $450/1225 = 37\%$, minus $16\% \times 1.5 = 24\%$, giving about 13%.
4. Is it a good bet if Villain calls 80% (folds 20%)? Yes: 20% > 13%.
5. Fold equity? $775 \times 20\% + 80\% \times (16\% \times 1225 - 84\% \times 450) = 9.4$.

### Live Example: The Continuation Bet

Same 2014 WSOP Main Event (blinds 150k/300k+50k): Jacobson (MP2) 22,000k, Hero/Pappas (CO) 18,000k. Hero holds A♣Q♥; Jacobson raises to 650k, Hero re-raises to 1,425k, Newhouse accidentally exposes the A♥ while folding, Jacobson calls 775k. Flop (3,800k) K♦J♥3♣, Jacobson checks, Hero bets 1,800k. Is this a good bet?

- If showdown-win% were 0: breakeven Fold% $= 1800/(3800+1800) = 33\%$.
- If only the gutshot is good (any T, 4 outs, one card): win rate 8%, and the breakeven Fold% drops to roughly $33\% - 1.5 \times 8\% \approx 21\%$.
- Full solution: any T (4 cards) plus any A, which wins sometimes (2 cards discounted at 50%), gives about $5 \times 2\% = 10\%$:

$$EV = 3800 \times \text{F\%} - 90\% \times 1800 \times (1-\text{F\%}) + 10\% \times (1-\text{F\%}) \times 5600 = 0 \implies \text{F\%} = 21.8\%$$

The bet is profitable as long as Villain folds more than about 22% of the time. In fact Jacobson folded (he held 7♠7♥, and the broadcast showed him at roughly 60% equity on this flop). This pattern, showing strength pre-flop, then betting again when the opponent checks the flop, is called a continuation bet: with two face cards on the flop, the pre-flop raiser very plausibly has at least top pair, and the opponent can hardly push back.

### Bluffing Formulas

- **Breakeven Fold% (SD-Win% = 0)**: $x = \dfrac{\text{BetAmt}}{\text{Pot} + \text{BetAmt}}$ — e.g. a \$150 bluff into a \$350 pot: $150/500 = 30\%$
- **Fold equity (EV of a pure bluff)**: $x = \text{Fold\%} \times \text{Pot} - (1-\text{Fold\%}) \times \text{BetAmt}$ — e.g. a \$250 bluff into a \$375 pot against a 25% call rate: $75\% \times 375 - 25\% \times 250 = \$218.75$
- **Showdown value (EV contribution of being called)**: $x = (1-\text{Fold\%}) \times (\text{Win\%} \times \text{WinAmt} - \text{Lose\%} \times \text{LoseAmt})$ — e.g. a \$450 bluff into a \$775 pot with a 16% win rate against an 80% call rate: $80\% \times (16\% \times 1225 - 84\% \times 450) = -\$145.6$
- **Fold equity (EV of a semi-bluff)**: $x = \text{Fold\%} \times \text{Pot} + (1-\text{Fold\%}) \times (\text{Win\%} \times \text{WinAmt} - \text{Lose\%} \times \text{LoseAmt})$ — e.g. the same hand: $20\% \times 775 + 80\% \times (16\% \times 1225 - 84\% \times 450) = \$9.4$
- **Semi-bluff breakeven Fold% (quick rule)**: $x = \dfrac{\text{BetAmt}}{\text{Pot} + \text{BetAmt}} - 1.5 \times \text{Win\%}$ — e.g. $450/1225 - 1.5 \times 16\% = 37\% - 24\% = 13\%$

### Bluffing — Be Careful About

- **Don't bluff too small**: with a real hand you wouldn't (or at least shouldn't) bet a third of the pot, so a small bet announces that you have nothing to do with the board. Bet as you would with a real hand, enough to deny a draw the right price.
- **Don't bluff too big**: overbets larger than the pot are basically never a good idea (unless a normal-sized bet already has you pot-committed), and the overbet itself is a bluff tell: it says the bettor never did the math and just wants you out. When short-stacked, don't bluff an amount that would force you to call a raise on pot odds; in that spot just shove all-in.
- **Don't fear getting caught bluffing or showing down a bad hand**: this fear is especially common live. A mark of a good player is calmly showing the bad hand after a caught bluff. What you actually hold while bluffing is completely immaterial: a hopeless hand is no different from a marginal one.
- **Don't semi-bluff when a free card is available**: in position, after the opponent checks weakness, taking the free card with your open-ended straight draw may simply be better; compare the EV of checking against the EV of bluffing.
- **Don't bluff calling stations**: your value against them comes from value bets; bluffing is the only way to lose money to them.

## Key Takeaways

- Later position means more information, a wider playable range, and higher profit; the blinds enter at a discount but act first on every post-flop round; with a short stack, early position's first shove preserves the equity of aggression (the game of chicken).
- Every decision reduces to EV: $EV = \text{Win\%} \times \text{WinAmt} - \text{Lose\%} \times \text{LoseAmt}$, with breakeven at $EV = 0$.
- Pot odds: call when $\text{Win\%} > \text{CallAmt}/(\text{Pot} + \text{Bet} + \text{Call})$; estimate Win% with the rule of 2 and 4 (about 2% per out per card, 4% per out when you see both cards).
- Implied odds answer "how much more must I win after hitting": $\text{BetAmt}/\text{Win\%} - (\text{Pot} + \text{Bet} + \text{Call})$; whether the dead-money requirement is realistic depends on how well disguised the draw is (sets are the most hidden, flushes the most visible).
- Fold equity: the pure-bluff breakeven fold rate is $\text{Bet}/(\text{Pot} + \text{Bet})$; for a semi-bluff use the quick rule "showdown-win% × 1.5 discounted off the fold rate," and the coefficient always lies in (1, 2).
- Never draw dead and never assume one bet buys two free cards; with a made hand bet 1/2–2/3 of the pot so chasing is unprofitable; bluff as you would bet a real hand, don't fear getting caught, and never bluff a calling station.
