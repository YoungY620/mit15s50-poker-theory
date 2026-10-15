<!-- escape-math: v1 -->
# Glossary

Technical concepts used in this book, grouped alphabetically. Hover (desktop) or tap (mobile) a term anywhere in the text for a short definition; click to jump to its entry here.


## A

<a id="ace-king-queen-game"></a>
**Ace-King-Queen game**　
The most classic toy game of incomplete information: each player is dealt an A, K, or Q.

Both players ante and receive one card; player 1 may check or bet, and player 2 may only check/call or fold. The solution: always bet an ace, always call with an ace facing a bet, always fold a queen; betting a king is a dominated strategy; call with all the aces and one-third of the kings to bluff catch, and bluff with the worst hands, the queens. Its structure: hands fall into value hands, bluff catchers, and bluffs, and your strategy for one hand determines your strategy for the others.

*First covered in：[L8 Decision Making](ch08-decisions.html)*

<a id="aggression-factor-af"></a>
**aggression factor (AF)**　
The ratio of bets and raises to calls.

AF corresponds to the aggressive–passive axis of the four style quadrants, while the tight–loose axis maps to VPIP. This is exactly how online analysis turns a temperament classification into data.

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*

<a id="all-in"></a>
**all-in**　
Committing your entire remaining stack to the pot at once.

Going all-in commits every chip you have. With shallow stacks you are effectively making an all-in-or-fold decision with your entire range of starting hands. Below M = 10 push-or-fold is essentially the whole game, because raising leaves room to be re-raised and costs you fold equity; shoving directly maximizes it.

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*

<a id="ante"></a>
**ante**　
A small forced bet every player posts before the deal, part of one round of forced bets.

The ante enters the denominator of the M ratio as part of the "sum of the blinds and antes." Counting stacks in big blinds ignores antes entirely: with blinds of 50/100 plus a 25 ante, the real pressure on your stack nearly doubles while the "number of big blinds" does not change at all.

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*


## B

<a id="bankroll-management"></a>
**bankroll management**　
Rules that size your poker bankroll in buy-ins at a 2% risk of ruin.

A bankroll is the amount of money whose loss you would deem irrecoverable and that would force you to stop playing — a concept that only matters for winning players. Rules of thumb at a 2% risk of ruin: 20 maximum buy-ins for no-limit cash, 300 big bets for limit, 30 buy-ins for STTs, 50–100 for MTTs — and you should move stakes up and down with results, since moving down after losses drives the risk of ruin asymptotically to zero. Staking and selling shares spread the risk of high-variance events.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*

<a id="bb-100"></a>
**BB/100**　
Big blinds won per 100 hands online — one quantitative yardstick of a winning player.

A "winner" in poker must be defined by quantitative metrics: online cash games use big blinds won per 100 hands, with 5 BB/100 as the mark of excellence; live cash games use big blinds per hour, with 5 BB/hour as the equivalent standard.

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*

<a id="blinds"></a>
**blinds**　
The forced bets from the small and big blind; the fundamental force driving preflop decisions.

The small blind (SB) and big blind (BB) make up the blinds group. Having been forced to put chips in, the blinds get a discount to see the flop, but on every post-flop round they act first, at the worst informational disadvantage. The only reason anyone plays any hand of poker is that someone wants to win the blinds; their share of your stack directly determines how much they matter.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*

<a id="bluff"></a>
**bluff**　
A bet that is +EV because fold equity alone is positive.

A bluff is a bet that is +EV because the fold equity alone is positive; its breakeven fold rate is bet / (pot + bet). Bet the way you would with a real hand — neither too small nor over the pot; do not fear getting caught or showing a bad hand, since your cards are irrelevant to the bluff; and never bluff a calling station, the only way to lose to one.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*

<a id="bubble"></a>
**bubble**　
The phase about 10% of the field away from the money, where amateurs make their biggest mistakes.

The bubble begins roughly when the field is about 10% of the remaining players away from the money. The average amateur plays noticeably too tight, preferring to forfeit a sliver of added chance at first place rather than risk busting. Your bubble performance arguably determines how deep you finish: a good player who exploits this is much better than 50% to double up during this phase. The metagame comes in a traditionally passive form and a newer over-aggressive form.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*


## C

<a id="cev-and-ev"></a>
**cEV and \\$EV**　
Chip EV and money EV; in tournaments they move together but are not strictly equal.

In cash games every chip has a definite monetary value and cEV = \\$EV; in tournaments cEV ≈ \\$EV, and in some spots a decision that is positive cEV can be negative \\$EV. The extreme case is the satellite: calling with KK against any two cards gains +1600 in cEV yet loses \\$800 in \\$EV, so the correct play is to fold.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*

<a id="continuation-bet"></a>
**continuation bet**　
The preflop aggressor bets again on the flop.

A continuation bet (cbet) is a bet by the player who showed strength preflop after the opponent checks to him on the flop: when two face cards flop, the preflop raiser very likely has at least top pair, and the opponent can hardly fight back. A 2/3-pot continuation bet needs only a 40% success rate to break even. Statistics must distinguish "river bet" from "river cbet" — otherwise you are reasoning on the wrong data.

*First covered in：[L2 Analytical Techniques](ch02-analysis.html)*

<a id="counterfactual-regret-cfr"></a>
**counterfactual regret (CFR)**　
Solves games by running regret matching separately at every decision node of each player's information-set tree.

CFR builds a personal tree from each player's information sets and runs regret matching at every decision node; the weighting assumes the player "played himself to that node," hence counterfactual. Convergence only requires unbiased samples of the payoffs, so actually playing out one hand completes one iteration, making huge games solvable. CFR+ further truncates regrets at zero and replaces Monte Carlo sampling with exhaustive traversal.

*First covered in：[L7 Game Theory](ch07-game-theory.html)*


## D

<a id="draw"></a>
**draw**　
A drawing hand — not yet made, needing outs to win.

The drawer must weigh the chance of hitting the draw against what each additional card costs. Do not draw to a hand that may not win even when it hits: a queen-high or smaller flush can be dominated by a bigger flush, the low end of a straight is dangerous, and on a paired board a flush or straight draw may even be drawing dead, with zero chance to win.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*


## E

<a id="effective-stack"></a>
**effective stack**　
The most chips you can possibly lose in this one hand.

Effective stack = min(your stack, the biggest stack still in play). The player with fewer chips determines when the action ends, so decisions are always based on the effective stack, not the nominal one: with your 1500 against an opponent's 300, any raise from him means a shove, and you might as well have 300 yourself.

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*

<a id="expected-value-ev"></a>
**expected value (EV)**　
The probability-weighted average of all outcomes; the basis of every decision rule in the course.

EV = Win% × WinAmt − Lose% × LoseAmt, with breakeven at EV = 0. Instead of asking "should I call," ask "how much can I call," and solve for the threshold at EV = 0. Poker advantage is precisely the accumulation of marginal decisions — even a gap of a few tenths of a percentage point between two options is worth computing.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*

<a id="exploitive-play"></a>
**exploitive play**　
Adjusting at the margins on top of a balanced base, according to the opponent's tendencies.

Exploitive play adjusts on top of a balanced foundation by moving the margins — only the hands whose expectation is near zero, never the core: expand marginal calls against opponents who bluff too much, expand marginal bluffs against those who fold too much. The credibility of the read sets the size of the move; and however confident you are in your read, you are probably overestimating it.

*First covered in：[L8 Decision Making](ch08-decisions.html)*


## F

<a id="fifty50"></a>
**Fifty50**　
A 10-player format where the top 5 cash: buy-in returned, the rest of the pool split by remaining chips.

In a Fifty50, 10 players enter and the top 5 make the money; cashing returns your buy-in (\\$10), and the other half of the prize pool is distributed in proportion to remaining chips. Analyzing its bubble decisions requires ICM: the default "average player" model says call, but refining to the opponent's tight range flips the verdict to a fold.

*First covered in：[L2 Analytical Techniques](ch02-analysis.html)*

<a id="flop"></a>
**flop**　
The first three community cards; the classic flop spot is a weak made hand versus a draw.

The flop is the first three community cards. The blinds get a discount to see it; the most common flop situation is one player holding a pair or two pair against another holding only a straight or flush draw. At medium stacks (M > 10), the preflop aggressor should follow up with a 2/3-pot continuation bet on the flop.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*

<a id="fold-equity"></a>
**fold equity**　
The value a bettor gains from the chance that the opponent folds.

Fold equity is the value of the opponent's possible fold assuming you lose when called: for a pure bluff, FE = Pot × Fold% − Bet × (1 − Fold%). When you bet you own all the equity that comes from fold equity; when you call you have none. In the dead zone (M < 2) you have almost no fold equity — the big blind has the odds to call any shove.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*


## G

<a id="game-theory-optimal-gto"></a>
**game theory optimal (GTO)**　
In two-player zero-sum games, the Nash equilibrium — the guarantee that you can never be exploited.

In two-player zero-sum games a Nash equilibrium is also called game theory optimal; it is simultaneously the minimax solution, the best you can do given that your opponent can see your strategy and respond optimally. GTO is not necessarily the best way to play — exploiting an opponent's deviations is often more profitable — but its value is the guarantee that your opponent cannot take advantage of you.

*First covered in：[L7 Game Theory](ch07-game-theory.html)*

<a id="gap-theory"></a>
**gap theory**　
Calling an all-in takes a much stronger hand than shoving does.

Sklansky's gap theory: when you bet you own all the equity that comes from fold equity, and when you call you have none — so in many spots you can shove with any two cards but can only call with a real hand.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*


## I

<a id="implied-odds"></a>
**implied odds**　
How many more chips you must win after hitting your draw for the call in front of you to be good.

The method: find the pot size at which the current call would be exactly x% of the pot (x% being your win rate), then subtract the pot that will actually exist after the call; the difference is the dead money that must be won later. Whether that dead money is realistic is a judgment about how disguised your hand is: sets are nearly impossible to read and carry huge implied odds, flushes are glaringly obvious and carry very small ones.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*

<a id="independent-chip-model-icm"></a>
**Independent Chip Model (ICM)**　
Converts tournament chips into real-money equity in the prize pool.

The Independent Chip Model converts tournament chips into real-money equity in the prize pool: your last chip is worth far more than your first, because once you are out you win nothing. On the bubble the value of survival can override pot odds — even KK can be a clear fold against all-ins.

*First covered in：[L2 Analytical Techniques](ch02-analysis.html)*


## K

<a id="kelly-criterion"></a>
**Kelly criterion**　
With logarithmic utility, bet in proportion to your edge to maximize long-run growth.

If your utility function is logarithmic, maximizing the long-run growth rate of utility requires betting in proportion to your edge: on an even-money bet with a 60% chance to win, the optimal fraction is f* = 0.6 − 0.4 = 0.2, or 20% of the bankroll. It is the theoretical basis for bet sizing in blackjack card counting and for the bankroll rules of thumb above.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*


## L

<a id="levels-of-thinking"></a>
**levels of thinking**　
The ladder from 'what do I have' to 'what does he think I am representing.'

L0 is not reading hands at all; L1 is "what do I have"; L2 is "what does he have"; L3 is "what does he think I have"; and so on. Your goal is to be exactly one level above your opponent, not as high as possible — thinking at L3 about "representation" against someone who is not reading you at all is a mismatched level. Reasonable defaults: new players are at L1, average tournament players at L2, cash-game players at L3.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*

<a id="loose-aggressive-lag"></a>
**loose-aggressive (LAG)**　
Bets good hands but also sees many flops and calls a lot, reluctant to give up a hand.

A loose-aggressive player bets his good hands but is willing to see many flops and call a lot. Whether the style wins depends on the game type, the opponents, and skill at picking spots — some big winners are indeed LAGs.

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*


## M

<a id="m-ratio"></a>
**M ratio**　
Effective stack divided by the cost of one round of blinds and antes.

M = effective stack ÷ (sum of the blinds and antes), invented by Paul Magriel and popularized by Harrington. Two equivalent readings: how many rounds you survive if you fold every hand before being blinded out, and the size of your stack relative to the value of stealing the blinds. M also normalizes decisions across blind levels: multiply stacks and blinds by ten and the decision is essentially the same.

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*

<a id="made-hand"></a>
**made hand**　
A hand that is already complete, such as a pair or two pair.

The classic flop spot is a weak made hand versus a drawing hand. The made hand wants to bet enough that the drawer's call is not +EV, or equivalently to bet an amount that bad players will mistake for a good price. Any made hand worse than top pair with a good kicker should be treated as a draw.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*


## N

<a id="nash-equilibrium"></a>
**Nash equilibrium**　
A set of strategies where no player can gain by unilaterally changing his own.

A Nash equilibrium is a set of strategies, one per player, such that no player has an incentive to unilaterally change his strategy. In rock-paper-scissors the equilibrium is to play each throw with probability 1/3 — the point of the equilibrium is not its expectation but that nobody can exploit you.

*First covered in：[L7 Game Theory](ch07-game-theory.html)*


## O

<a id="outs"></a>
**outs**　
The remaining cards that will win you the hand if they come.

Outs are the cards that make you a winner; your win rate follows from the count — the exact chance of making a flush with 9 remaining hearts is about 34%. Outs can also be discounted into "partial outs" by the probability of winning after you hit: if the call is right even on a conservative estimate, it is even more right in reality.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*


## P

<a id="pfr"></a>
**PFR**　
Preflop raise frequency; read together with VPIP to sketch an opponent's type.

On a HUD, VPIP 65 with PFR 45 marks a loose-aggressive opponent; a 73-hand sample with VPIP 11 and PFR 1 means the player had raised exactly once before — an ultra-tight profile, so the baseline for inferring his short-stack shoving range should start very tight.

*First covered in：[L2 Analytical Techniques](ch02-analysis.html)*

<a id="position"></a>
**position**　
Your seat group at the table, which sets the order of action and how much you know.

Seats fall into four groups: the blinds, early position, middle position, and late position. Acting later means seeing what earlier actors did first, so later position supports a wider profitable range of starting hands, and money flows toward late position. In short-stack (low-M) spots early position has the edge instead: the first actor can go all-in before anyone else and keep the fold equity that comes from aggression.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*

<a id="pot"></a>
**pot**　
The total of all bets accumulated over the rounds of a hand.

The pot is the reference for decisions: pot odds relate the call to the size of the pot after the call; a pot-size bluff needs a 50% success rate to break even, scaling down roughly linearly for smaller bets. Bets with a made hand should run from half to two-thirds of the pot to punish draws.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*

<a id="pot-odds"></a>
**pot odds**　
The relation between the call and the pot after the call; decides whether calling is +EV.

Calling is +EV when Win% > CallAmt / (Pot + BetAmt + CallAmt): the percentage of the new pot your call contributes must not exceed your win rate. At the table you do not solve equations — knowing your chance to hit, you may contribute up to that percentage of the new pot. A pot-odds answer is "can I call" or "what is the most I can call."

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*


## Q

<a id="q-ratio"></a>
**Q ratio**　
Your stack divided by the average stack, measuring your relative standing in a tournament.

Q = your stack ÷ the average stack in the field. At Q = 5 there is no need for aggression; at Q = 0.2 you are far from the money with a great deal of catching up to do. Harrington proposed it, but it never caught on.

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*


## R

<a id="range"></a>
**range**　
A set of hands — the basic language for analyzing opponents and planning your own play.

A range is a set of hands; suitedness is marked with o (offsuit) or s (suited), and notation names the bottom of a run of hands, as in QQ+. Ranges serve two purposes: analyzing opponents (estimate the distribution of hands he holds, then compute your equity) and deciding your own play (e.g. "shove AT+, 88+, fold the rest"). If a range is optimal, every single hand in it is individually +EV.

*First covered in：[L4 Preflop Analysis](ch04-preflop.html)*

<a id="reading-your-own-hand-ryoh"></a>
**reading your own hand (RYOH)**　
Knowing where you are in your own distribution and shaping it to be balanced — the most important skill in poker.

RYOH means updating your distribution twice on every street: card removal (new board cards change combination counts) and accounting for your action (delete the hands that would not take that action), then checking whether your value-to-bluff ratio is balanced. Rule of thumb: if you would have value bet a hand, you should shape your distribution so that you do not have to fold it.

*First covered in：[L8 Decision Making](ch08-decisions.html)*

<a id="return-on-investment-roi"></a>
**return on investment (ROI)**　
Total returned divided by amount invested, minus one — the core efficiency metric for tournaments.

ROI = total returned ÷ invested − 1: invest \\$100k, get back \\$150k, and ROI is 50%. Excellence is about 30% in multi-table tournaments and 15% in sit-and-go's. You should generally maximize ROI until it falls to the hourly floor you set for yourself; the standard way to supplement ROI is to move down in stakes.

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*

<a id="river"></a>
**river**　
The fifth and final community card.

The river is the last community card. Loose-passive opponents let you see draws cheaply when they have a hand, letting you reach the river before deciding whether you have anything. River statistics must match the situation: a player's overall river-bet frequency is not his river continuation-bet frequency, and inferring hand strength from the former is reasoning on the wrong data.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*

<a id="rule-of-2-and-4"></a>
**rule of 2 and 4**　
Quick win-rate estimate: about 2% per out per card, 4% per out if you see both cards.

Phil Gordon's rule of thumb: each out is worth about 2% per additional card you get to see, and 4% if you are guaranteed both the turn and the river (for example when the opponent is all-in). The approximation tracks the exact math closely: a 9-out flush draw is about 18%, a 4-out gutshot about 8%.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*


## S

<a id="satellite"></a>
**satellite**　
An event where the top finishers win seats to a bigger tournament — the format where ICM bites hardest.

Satellites make giant mistakes easy: with 10 players left for 9 seats, calling an all-in with KK against any two cards is hugely positive cEV but negative \\$EV, and even AA should be folded unless it is better than roughly a 90% favorite. If everyone were rational, every calling range would be 0%, so the action player should shove any two cards until the blinds force someone in.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*

<a id="semi-bluff"></a>
**semi-bluff**　
A bet whose fold equity is negative but which stays +EV on showdown-win%.

A semi-bluff has two ways to win — stealing the pot outright or drawing out — and is used constantly in tournaments: you will not always have a made hand, but you will always have something that can become one. Quick rule: the breakeven fold rate is roughly the pure-bluff rate minus 1.5 times your showdown-win%, a coefficient that always lies in (1, 2). Preflop bets — and preflop shoves — are almost always semi-bluffs.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*

<a id="set-mining"></a>
**set mining**　
Flatting cheap preflop with a pocket pair, hoping to flop a well-disguised set.

Above M = 30 you are in the set-mining zone: wait patiently for monsters and value bet them hard; see flops cheaply, use pot odds to evaluate draws to the nuts, and estimate implied odds conservatively; if your hand is not the absolute best possible, do not go broke for 50M.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*

<a id="shootout"></a>
**Shootout**　
An elimination format in which each table first plays down to a single winner.

A Shootout is structured like the WSOP \\$3000 event: forty 10-handed tables each play down to one winner, and the 40 survivors redraw into new tables on Day 2. Case 2 applies push/fold strategy and the Sklansky-Karlson model at the heads-up stage of exactly this format.

*First covered in：[Case 2](cases/case2.html)*

<a id="showdown"></a>
**showdown**　
After the last betting round, surviving players show their cards to decide the pot.

A showdown is where players still in the hand reveal their cards and compare strength. In a tournament, when neither player wants to flip for their tournament life at showdown, the early-position player can shove first and scare the opponent off. Only hands that reach showdown reveal an opponent's hole cards in PokerTracker.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*

<a id="sklansky-karlson-ranking"></a>
**Sklansky-Karlson ranking**　
The standard percentile ranking of starting hands by their chance of being ahead preflop heads-up.

The most used percentile ranking of starting hands, based on the likelihood of being ahead preflop in a two-player game: the top 10 are AA, KK, AKs, QQ, AKo, JJ, AQs, TT, AQo, 99. It comes from Sklansky's "open-shove" problem — the stack size x below which shoving face-up is still +EV — solved for every hand by Victor Chubukov. Percentiles map to ranges: the top 5% is TT+, AQ+; the top 30% is 22+, A2+, Broadway.

*First covered in：[L4 Preflop Analysis](ch04-preflop.html)*

<a id="steal"></a>
**steal**　
Raising to take down the blinds and antes uncontested.

A steal is an aggressive grab at the blinds; a re-steal is re-raising a player you have identified as stealing, including when you are not in the blinds yourself. In the 2 < M < 8 steal period your only moves are push or fold, and each successful steal grows your stack by roughly 10–40%. Target players who do not defend their blinds, while cultivating the image of someone who defends his own.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*


## T

<a id="tell"></a>
**tell**　
A physical cue that leaks information — a faint signal in a sea of noise.

Tells may help against weak players, but they are not a professional's livelihood: in experiments, FBI interrogators judged lying at near-random accuracy (about 53%), only with far more confidence than laypeople — self-assessment bias makes you overrate your reads. Any moment you try to guess an opponent's strategy, she can guess yours right back.

*First covered in：[L8 Decision Making](ch08-decisions.html)*

<a id="tight-aggressive-tag"></a>
**tight-aggressive (TAG)**　
Bets with good hands, folds without them — the most profitable quadrant.

Tight-aggressive play is called solid ABC poker: it is the most profitable quadrant overall and the style this course recommends. Dan Harrington is the canonical tight-aggressive ABC player.

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*

<a id="tight-passive-and-loose-passive-tp-lp"></a>
**tight-passive and loose-passive (TP & LP)**　
The two losing quadrants: the rock-like tight-passive and the calling-machine loose-passive.

TP (tight-passive, the "rock") folds without a hand and only checks with one; such players can be run over completely and are generally considered clearly sub-optimal. LP (loose-passive, the "calling machine") calls every bet when you have a hand, yet lets you see draws cheaply when he has one; in any realistic sample this quadrant is nearly incapable of winning and is the table's biggest loser.

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*

<a id="tilt"></a>
**tilt**　
Emotional loss of control that deforms your play.

Classic signs of fear and tilt: being forced to show a bad hand, losing money, playing short sessions when winning and long sessions when losing. Players lose the most right after losing more than they planned (the threshold of misery). Stabilizing techniques include marking your bankroll to market and thinking in terms of breakeven periods rather than winning and losing streaks.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*

<a id="tournament"></a>
**tournament**　
A format where a fixed buy-in buys tournament chips and prizes follow finishing position, with rising blinds.

In a tournament only outlasting your opponents pays: one fixed buy-in, constantly rising blind levels, and selection of a player pool rather than a table — with higher variance than cash games. The most important concept is tempo: accumulate chips slowly without showdowns, avoid volunteering for coin flips, and save the unavoidable ones for when you are deeper.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*

<a id="turn"></a>
**turn**　
The fourth community card; do not assume one bet buys you both the turn and the river.

The turn is the fourth community card. Unless the aggressor is already all-in, do not assume one bet lets you see both the turn and the river — many players call the flop hoping to see two cards cheap, the assumption fails, and they bleed EV. By the turn the pot is usually already about 10M, and the decision is often reduced to push or fold.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*


## V

<a id="value-bet"></a>
**value bet**　
Betting a real hand to extract chips from worse hands.

Against calling stations your profit comes from value bets; bluffing is the only way to lose to them. In the M > 30 set-mining zone you wait patiently for monsters and value bet them hard when they arrive. In the AKQ-game structure the value and bluff regions move together: the wider you value bet, the more bluffs you must pair with them.

*First covered in：[L3 Basic Strategy](ch03-basic-strategy.html)*

<a id="vpip"></a>
**VPIP**　
The share of hands where a player voluntarily puts money in the pot preflop.

VPIP (voluntarily put money in pot) measures how involved a player gets, and it converges fast — nearly every hand is one observation; players with VPIP 40 play broadly similar styles, so it quickly classifies opponents. Read together with RFI it says even more: a player at VPIP 70, RFI 2 "only calls, never raises."

*First covered in：[L1 Introduction to Poker Theory](ch01-intro.html)*


## Z

<a id="zeebo-s-theorem"></a>
**Zeebo's theorem**　
No player is capable of folding a full house on any betting round, regardless of the size of the bet.

So when your opponent can have a full house, do not bluff with a worse hand; conversely, when you hold the full house, collect value on the assumption that you will be paid off.

*First covered in：[L5 Tournament Play](ch05-tournament.html)*
