<!-- escape-math: v1 -->
# L7 Game Theory

This chapter is a guest lecture by Bill Chen (Susquehanna International Group), built around the University of Alberta's Cepheus program, which "solved" heads-up limit hold'em. We cover Game Theory Optimal (GTO) strategies and Nash equilibrium, regret minimization, Counterfactual Regret (CFR) and its improved variant CFR+, and finally the extension of computer solutions to other poker variants, big bet games, and multiplayer games.

## What Cepheus Accomplished

Cepheus is a GTO solution to heads-up limit hold'em (HULHE). After 900 CPU-years of computation, its strategy has an exploitability of less than 1/1000 of a big blind, virtually indistinguishable from a perfect strategy.

What does that number mean? 1/1000 of a big blind is 1/2000 of a big bet. The standard deviation of heads-up limit hold'em is about 5 big blinds per hand. Confirming even this edge with statistical significance would take roughly 25 million hands: playing heads-up at normal speed for 50 years, you would still have some probability of being behind. In practice, a win rate of 1/100 of a big bet per hand is the usual threshold for a strategy to be practically meaningful; anything below it is merely theoretical.

This is the first real poker game ever solved, and unquestionably a milestone. *The Mathematics of Poker* had previously solved toy games such as the AKQ game on paper, but Cepheus faced the full game. That said, given the prior work of Bowling, Burch, Johanson, and Tammelin, the result was only a matter of time (and a great deal of CPU). Does this mean poker will go the way of chess, dominated by computers? We return to that question at the end of the chapter.

## Nash Equilibrium

John F. Nash won the 1994 Nobel Prize "for pioneering analysis of equilibria in the theory of non-cooperative games," extending the two-player zero-sum games first studied by John von Neumann and Oskar Morgenstern.

A **Nash equilibrium** is a set of strategies, one for each player, such that no player has an incentive to unilaterally change his strategy. In two-player zero-sum games, a Nash equilibrium is also called **Game Theory Optimal (GTO)**: it is simultaneously the minimax solution, the best you can do given that your opponent can see your strategy and respond optimally to it.

The simplest example is rock-paper-scissors: the Nash equilibrium is to play each throw with probability 1/3. The equilibrium looks unexciting because both players expect 0, but its point is that nobody can exploit you. If your opponent plays 1/2 scissors and 1/2 rock, you should play 100% rock (beating scissors, tying rock, for an expectation of +0.5). So GTO is not necessarily the *best* way to play. Even heads-up, exploiting an opponent's deviations is often more profitable. The value of GTO is the guarantee that you can never be exploited: your opponent cannot take advantage of you, although you are not fully taking advantage of his mistakes either.

## A Game Theory Poker Example

Consider a simplified poker game between Rose and Colin (named after the row player and column player of matrix games; a three-player game would introduce Larry, for "layer"):

- Each player antes \\$50 for a \\$100 pot. Rose looks at one card from a full deck: she wins at showdown if it is a spade, and loses otherwise.
- Rose may bet \\$100 or check.
- If Rose bets, Colin may call \\$100 or fold. If Colin folds, Rose wins the pot; if he calls, there is a showdown for the \\$300 pot.

What are the optimal strategies?

**Rose always bets a spade.** She has nothing to lose by betting. The interesting questions are her bluffing frequency when she does not have a spade, and Colin's calling frequency.

- If Colin calls 100% of the time, Rose never bluffs: she nets +\\$150 when she has a spade and −\\$50 when she does not, for a total net gain of zero.
- If Colin never calls, Rose bets every time and nets \\$50 per hand.
- If Colin calls half the time, Rose is indifferent to bluffing: without a spade she nets −\\$50 either way, and with a spade she nets +\\$100, for an expectation of −\\$12.50 per hand. This is the correct strategy for Colin.

Where do the frequencies come from? When Rose bluffs, she risks \\$100 to win the \\$100 in the pot (1-to-1 odds), so Colin must call with frequency 1/2 to make her bluffs unprofitable. Conversely, Rose's ratio of bluffs to value bets (the spade bets) should be 1:2, exactly the pot odds Colin faces when calling (the \\$200 pot against his \\$100 call), which makes Colin indifferent to calling. Rose should therefore bluff with half of her hearts: she can always bet the high hearts and randomize on a borderline card like the 8♥, betting it half the time.

These strategies form the Nash equilibrium and the GTO strategy of the game; the value of the game to Colin is \\$12.50 per hand.

## Formal Definition of GTO

Let the game have a value function $u(\sigma\_x, \sigma\_y)$, where $\sigma\_x \in X$ and $\sigma\_y \in Y$ are the two players' strategies; player X wins $u$ and player Y loses $u$. Strategies admit convex linear combinations: if $\sigma\_{x\_k} \in X$, with coefficients $a\_k \ge 0$ and $\sum\_k a\_k = 1$, then $\sigma\_x = \sum\_k a\_k \sigma\_{x\_k}$ is also a strategy, and $u$ is bilinear:

$$u(\sigma\_x, \sigma\_y) = \sum\_k a\_k \\, u(\sigma\_{x\_k}, \sigma\_y).$$

That is, the payoff of a mixed strategy is the weighted average of the pure-strategy payoffs. We say a pair of strategies $(\sigma\_x^\*, \sigma\_y^\*)$ is in $\epsilon$-equilibrium if

$$\max\_{\sigma\_x} u(\sigma\_x, \sigma\_y^\*) \\;-\\; \min\_{\sigma\_y} u(\sigma\_x^\*, \sigma\_y) \\;\le\\; \epsilon.$$

When $\epsilon = 0$ this is a Nash equilibrium. What Cepheus found with its 900 CPU-years was precisely a pair $(\sigma\_x^\*, \sigma\_y^\*)$ within 1/1000 of a big blind of equilibrium.

## Regret Minimization

The core idea behind the solving algorithm is borrowed from **regret minimization**. Suppose that at each time step $t$ the player chooses a linear combination of $n$ pure strategies

$$\sigma^t = \sum\_{k=1}^{n} a\_k^t \sigma\_k, \qquad \sum\_{k=1}^n a\_k^t = 1,\\; a\_k^t \ge 0.$$

After the player commits to $\sigma^t$, an all-knowing adversary reveals the values $u^t(\sigma\_k)$ of each pure strategy for this step, and the player's actual payoff is $u^t(\sigma^t) = \sum\_k a\_k^t u^t(\sigma\_k)$. The adversary may make a given strategy score well at some times and badly at others.

Define the total **regret** of strategy $k$ as the accumulated difference between always playing $k$ and actually playing $\sigma^t$:

$$R\_k^T = \sum\_{t=1}^{T} \bigl( u^t(\sigma\_k) - u^t(\sigma^t) \bigr).$$

Regret can be positive or negative: negative regret means your actual play has been better than always playing $k$. The goal is to drive the average positive regret to zero, i.e. $R\_k^T / T < \epsilon\_t$ for a sequence $\epsilon\_t$ converging to 0. This is achieved by **regret matching**: writing $R\_k^{T+} = \max(R\_k^T, 0)$, set

$$a\_k^T = \frac{R\_k^{T-1,+}}{\sum\_{j=1}^{n} R\_j^{T-1,+}},$$

i.e. weight each option in proportion to its positive regret; if all regrets are non-positive, pick a strategy at random.

**Example.** Let $n=2$, and at each step the adversary makes one strategy worth 1 and the other worth 0:

1. $t=1$: pick arbitrarily $\sigma^t = \sigma\_1$. The adversary gives $u^t(\sigma\_1)=0$, $u^t(\sigma\_2)=1$. Then $R\_1=0$, $R\_2=1$ (playing $\sigma\_1$ itself generates no regret; the regret comes from not having played $\sigma\_2$).
2. $t=2$: by the weights, pick $\sigma^t = \sigma\_2$. The adversary gives $u^t(\sigma\_1)=1$, $u^t(\sigma\_2)=0$. Now $R\_1=1$, $R\_2=1$.
3. $t=3$: pick $\sigma^t = \sigma\_1/2 + \sigma\_2/2$. The adversary gives $u^t(\sigma\_1)=0$, $u^t(\sigma\_2)=1$. Now $R\_1=0.5$, $R\_2=1.5$.
4. $t=4$: pick $\sigma^t = \sigma\_1/4 + 3\sigma\_2/4$. The adversary gives $u^t(\sigma\_1)=0$, $u^t(\sigma\_2)=1$. Now $R\_1=-0.25$, $R\_2=1.75$.
5. $t=5$: only $R\_2$ is positive, so pick $\sigma^t = \sigma\_2$. If the adversary now rewards $\sigma\_1$ instead, $R\_1$ climbs back to 0.75, and so on.

The adversary seems able to torment us indefinitely, but there is a bound: in this example

$$\bigl(R\_1^{T+}\bigr)^2 + \bigl(R\_2^{T+}\bigr)^2 \le T,$$

because when both regrets are positive, the cross terms of each step's increments cancel, so the quadratic sum grows by at most 1 per step. Hence the average regret satisfies $R\_k^T / T \le 1/\sqrt{T}$. In general,

$$\frac{R\_k^T}{T} \le \frac{(n-1)\\,\Delta}{\sqrt{T}},$$

where $\Delta$ is the maximum deviation among the options' payoffs and $n$ is the number of strategies. Average regret converges to zero at the rate $1/\sqrt{T}$.

Note that a "strategy" here means a full strategy in the poker sense: a complete description of what you do at every decision point (e.g. after being dealt A6o, ace-six offsuit), not a single payoff.

## From Regret Minimization to GTO

How does regret minimization approach GTO? Let X's pure strategies be $\\{\sigma\_{x,k}\\}\_{k=1}^m$ and Y's be $\\{\sigma\_{y,j}\\}\_{j=1}^n$. Instead of an adversary assigning arbitrary payoffs, let the two players regret-match against each other: X's payoff function at step $t$ is $u\_x^t(\cdot) = u(\cdot, \sigma\_y^t)$ and Y's is $u\_y^t(\cdot) = -u(\sigma\_x^t, \cdot)$. At each step both players update their regrets and adjust their strategies; then take the average of all historical strategies:

$$\bar{\sigma}\_x^T = \frac{1}{T}\sum\_{t=1}^T \sigma\_x^t, \qquad \bar{\sigma}\_y^T = \frac{1}{T}\sum\_{t=1}^T \sigma\_y^t.$$

Examine the exploitability of this pair of average strategies:

$$u(\sigma\_{x,k}, \bar{\sigma}\_y^T) - u(\bar{\sigma}\_x^T, \sigma\_{y,j}) = \frac{R\_{x,k}^T}{T} + \frac{R\_{y,j}^T}{T} < 2\epsilon\_t,$$

so the average strategies are within $2\epsilon\_t$ of GTO. Intuitively, the best response your opponent can find after observing your strategy is often called the "nemesis" strategy. As long as you are not at the exact equilibrium, the nemesis always scores above the game value. Each side computes the nemesis response to the other, and the difference between the two values is the exploitability, the number Cepheus pushed below 1/1000 of a big blind.

## Counterfactual Regret (CFR)

CFR is the major innovation of this work. First note that convergence does not require the true value of $u$ at every step. An unbiased sample of $u$ suffices, because by the Central Limit Theorem the sampled regrets converge to the true regrets. So there is no need to compute "what is my terabyte-sized strategy worth against your terabyte-sized strategy"; one can simply play out a hand (or a few variations of it) and use the result as one sample.

The main idea is to build a "personal tree" from each player's **information set** (the cards he was dealt, the community cards, and the sequence of actions by each player) and to run regret matching separately at every node of that tree where the player has a decision. It is called *counterfactual* regret because of the weighting, which assumes the player "plays himself to that node": nature (the deal) is weighted by its own probabilities, the opponent's actions are weighted by their probabilities under his current strategy $\sigma\_y^t$, and the player's own choices along the path to the node are given weight 1.

This means hands can be sampled intrinsically: playing out one hand, or a few variations of a hand, completes one iteration. Compared with methods such as fictitious play, there is no need to compute a hard-to-find best response; each simulation is a single pass through the tree, which makes convergence feasible.

## Improving CFR: CFR+

- **CFR+**: the final algorithm makes two key changes. First, regrets are **floored at 0** rather than allowed to become very negative (folding aces preflop, for example, quickly accumulates an enormous negative regret). The reason is that this is a process in which both strategies evolve simultaneously. A strategy evaluated as bad early on may not truly be bad, and once it is in fact the right response to the opponent's current strategy, regret can re-accumulate from 0 much faster than it can climb back from a huge negative number. Second, Monte Carlo sampling is replaced by a more **exhaustive search** along the tree.
- **Branch weighting**: branches with higher average regret can be visited more often. For example, if the branch where the A♥ comes on the turn has long since converged and carries almost no positive regret, its visit frequency can be reduced and its results rescaled by a weight of 10, concentrating computation on the still-unresolved 2♣ branch.
- **General weighting flexibility**: for instance, later iterations can be weighted more heavily; on the river, the regret of calling can be the whole pot while the regret of folding is at most one bet, and a weighting scheme can correct this asymmetry.

One interesting evolutionary phenomenon: starting from a completely random initial strategy, "bet and raise every time with every hand" quickly becomes the dominant strategy. A random opponent folds often, and even when he raises back you can re-raise hoping he folds. If he calls, the pot is bigger on the next street, and you should keep betting as long as he folds 1/3 of the time. As the opponent's strategy evolves, this style is gradually walked back. The implementation maintains two trees: one for the small blind's strategy and one for the big blind's.

## The Size of Limit Hold'em

How big is the tree? It suffices to concentrate on the river nodes, which are the most numerous (in a tree you only need to count the leaves).

- **Action sequences**: assume a 4-bet cap (the standard approximation in the literature). On each street (preflop, flop, turn) there are 9 action sequences that reach the next street: check-check counts as 1; putting in exactly $k$ bets ($k \ge 1$) can happen in exactly 2 ways (e.g. bet–raise–reraise–call, or check–bet–raise–reraise–call), so a cap of $k$ bets gives $2k+1 = 9$ sequences per street. Sequences that end in a fold and never reach the river are a small fraction of the nodes.
- **Flop symmetries**: using suit symmetry, there are 1755 distinct flops: $\binom{13}{3}=286$ one-suited, $13 \times \binom{13}{2} = 1014$ two-suited, and $\binom{15}{3} = 455$ three-suited (ranks may repeat, so we choose 3 from 15 "rank values with repetition," not $\binom{13}{3}$).
- **Turns and rivers**: $49 \times 48 = 2352$. Hence there are $1755 \times 9^3 \times 2352 \approx 3$ billion action sequences reaching the river.
- **River hand types**: $47 \times 46 = 2162$, giving about $6.5 \times 10^{12}$ "hand–river" situations in total. Each river node must be visited roughly 1000 times. This is an enormous computational problem, but still tractable, especially with 900 CPU-years available, plus many shortcuts: suit symmetries, splitting the problem into about 100 subgames solved separately, exploiting cache locality once the computation reaches the river, and optimizing the regret updates into simple additions. Storing the full strategy requires terabytes of memory.

## Solving Other Poker Games

**Omaha 8 (Omaha high-low)**: identical structure to limit hold'em, except the hand types go from $\binom{47}{2}$ to $\binom{47}{4}$, making the tree about 82.5 times larger. If limit hold'em takes 900 CPU-years, this would take roughly 75,000 CPU-years, still tractable. **Bucketing** offers further compression: group hand types into buckets and play every hand in a bucket the same way. In effect this restricts play to subspaces $X' \subset X$ and $Y' \subset Y$ of the strategy spaces, solves the subgame $u(X', Y')$, and then evaluates how good that solution is in the full game. With well-designed buckets (usually more necessary on the river) the result is quite close; putting AA and 75s in the same bucket will obviously not give a good answer. The Alberta group originally used exactly these methods to build strong limit hold'em programs.

**Razz (seven-card stud low)**: unquestionably the simplest stud variant. It has only 13 card types, and suits are irrelevant (flushes do not count). The difficulty is that the four upcards can come in $13^8$ ways, there are $9^4$ action sequences (one extra street), and there are still $\binom{15}{3} = 455$ river hand types. In total this gives about $2.44 \times 10^{15}$ river situations, a factor of 374 over hold'em. Much simplification is possible, however: there are really only 78 distinct "subgames" (the A-versus-2 game, and so on); some streets are nearly trivial (when you show a queen and your opponent completes a deuce, third street will not become a raising war); and bucketing is more natural in Razz (e.g. K-8-6-2 is very close to K-8-6-A, so starting hands can be merged by rank order).

## Big Bet Games

The difficulty with No Limit and Pot Limit games is that bet sizes form a **continuum**: each bet size has a continuum of responses, with further streets behind. Any solution requires some kind of interpolation between bet sizes. Even if some sizes are themselves non-optimal, a complete strategy must include responses to those bets. The commercial program Snowie assumes only three sizes (half pot, full pot, all-in), which is likely too coarse: what if the opponent bets 1/4 pot or 1.1× pot? And responding to a 1.1× pot bet, should you raise to 1.1× pot, or to 0.9× pot so as to return to the original stack depth? These are hard questions.

The alternative is brute-force densification of sizes (0.01× pot, 0.02× pot, ...), but that produces a large number of options with extremely close expectations. Regret minimization takes a long time to distinguish them, all while balancing value bets against bluffs. Promising directions include studying a "rigid" pot limit game where only full-pot bets are allowed, which may reveal interesting structure, and small stack games, where much of the action terminates quickly (all-in), making them more amenable to solution.

## Multiplayer Games (3+ Players)

The paper *Using Counterfactual Regret Minimization to Create Competitive Multiplayer Poker Agents* by Risk and Szafron (2011) addresses this problem; its programs finished first and second in an annual three-player limit hold'em event. Two core obstacles:

1. **No $\epsilon$-convergence guarantee**: CFR no longer guarantees convergence to within an $\epsilon$ neighborhood of a Nash equilibrium.
2. **Multiple equilibria**: multiplayer games can have many Nash equilibria, especially in tournaments and satellites with proportional payouts for places other than first, where nonlinear effects are significant. You do not know which (possibly collusive) equilibrium your opponents are playing. The "Rock-Maniac" game in *The Mathematics of Poker* shows that other players can use a simple strategy to ensure you lose. A non-poker version is three-player odds-and-evens with "odd man out wins": if two players collude, one always playing 1 and the other always playing 2, the third player can never win. Analogous situations arise in poker. Still, outside of tournaments and absent collusion, playing a Nash equilibrium usually turns out fine. This is a rich area of study.

## Further Discussion

**Cepheus's impact on real play.** Does this mean poker will be dominated by computers the way chess is? At least for other games, not yet. Even for heads-up limit hold'em itself, the solution's impact is limited: approximately optimal strategies of this kind had existed for years before the solution was published, top online players were already playing near-optimally, and the game was effectively "dead" before it was solved. And even with the full GTO strategy in hand, you still have to learn it.

**Other tricks for bucketing and approximation.** One shortcut is to cut out the river street entirely, substituting an estimated equity on the river for the full expansion. Note that this is not showdown equity, since you may still face a bet, so some kind of implied value must be used. Another is game-specific natural bucketing, such as grouping only the two cards that actually play on an Omaha river and ignoring the rest. But such approaches lose **card removal** effects: in GTO solutions at milli-big-blind precision, card removal is a significant component. The underlying principle: with a pot of $p$ facing a bet of 1, the bettor risks 1 to win $p$, so to make him indifferent to bluffing you must call with frequency about $p/(p+1)$. If you ignore card removal entirely, the opponent can pick exactly the spots where you are more likely to hold a mediocre hand and bluff there. The canonical example is PLO (pot-limit Omaha) with three of a suit on board: holding the ace of that suit (e.g. A♠ on a spade-flush board) is an excellent bluff, since you simultaneously block the opponent's nuts and many of his strong hands.

**Utility theory.** Players routinely apply utility analysis to "which tournaments to enter and which games to play," but optimizing personal utility *within* a game has rarely been studied. Limit hold'em requires a bankroll of hundreds of bets, so the assumption "once in the game, just try to win the most money" is correct for most situations. In tournaments, however, chip value is nonlinear (as ICM already computes): at a main event final table, the step from \\$2 million to \\$3.5 million is worth far less in personal utility than the step from \\$0 to \\$2 million. The treatment of marginal hands may therefore genuinely require a utility correction, a direction worth studying.

**Detecting and exploiting opponents' deviations.** Deviating from GTO to exploit an opponent also exposes you to exploitation, a dynamic problem: when does the opponent go on tilt, for how long, and with what evidence? The CMU group studied a "zero-loss exploitation" idea: estimate how much equity the opponent has already given up by playing sub-optimally, and take only a fraction of it (say half), so that your own exposure to being exploited stays bounded.

**Poker and trading.** Trading firms prize poker because it concentrates the essentials of trading in a single game: many participants, incomplete information, the need to read a counterparty's intent (is his bid motivated by unloading risk or something else), and the ability to adjust your bid/offer around a known "value of \\$10" based on counterparty characteristics. The analysis of poker strategies is also methodologically very similar to the analysis of quantitative trading strategies.

## References

1. Bowling, M., Burch, N., Johanson, M., Tammelin, O. (2014). *Heads-up Limit Hold'em Poker is Solved*.
2. Risk, N., Szafron, D. (2011). *Using Counterfactual Regret Minimization to Create Competitive Multiplayer Poker Agents*.
3. Zinkevich, M., Johanson, M., Bowling, M., Piccione, C. (2008). *Regret Minimization in Games with Incomplete Information*.

## Key Takeaways

- Cepheus solved heads-up limit hold'em to an exploitability below 1/1000 of a big blind using 900 CPU-years, the first real poker game ever solved; the residual gap (detectable only after roughly 25 million hands) is equivalent to perfection in practice.
- A Nash equilibrium is a set of strategies where no player can gain by unilaterally changing strategy; in two-player zero-sum games it is the GTO (minimax) solution. GTO guarantees you cannot be exploited, but does not fully capitalize on opponents' mistakes.
- The Rose–Colin example shows the typical structure of GTO: value bets are always made, the bluff frequency (1:2) makes the opponent indifferent to calling, and the calling frequency (1/2) makes bluffs indifferent.
- Regret matching weights each pure strategy in proportion to its positive regret, with average regret converging at the rate $R\_k^T/T \le (n-1)\Delta/\sqrt{T}$; two players regret-matching against each other and averaging their historical strategies approaches GTO within $2\epsilon\_t$.
- CFR performs regret matching separately at every decision node of each player's information-set tree, weighted counterfactually, and replaces exact computation with unbiased sampling, making huge games solvable; CFR+ further accelerates convergence by flooring regrets at zero and using exhaustive traversal.
- Limit hold'em has about $6.5 \times 10^{12}$ river situations, solvable only with shortcuts such as suit symmetries, bucketing, and subgame decomposition; Omaha 8 (82.5×) and Razz (374×) are tractable in principle, big bet games are complicated by continuous bet sizes, and multiplayer games lack convergence guarantees and admit multiple equilibria.
