# The ten moves

Each move has a check you can answer from the draft, and one or more published pieces that show the move done well.

The notes on each piece were checked against the piece's own text on 2026-11-16. They are paraphrases, so read the piece for the exact wording. Numbers are the piece's own.

## 1. Lead with the decision or question, and name the default view before showing where it breaks

**Check.** Do the first three sentences state the decision or question in the reader's words? Is the default view stated in a form its holders would accept, before any evidence against it?

**See**

- [Decision Making at Netflix](https://netflixtechblog.com/decision-making-at-netflix-33065fa06481) (Tingley and others, 2021). Opens with the product questions the team had to settle, such as video against static images. It says the hard part is deciding correctly. It then lists four other ways to decide (leadership, experts, debate, copying competitors) and names the weakness they share: few viewpoints, and no systematic way to settle a disagreement. A/B testing arrives only after that.
- [Why Momentum Really Works](https://distill.pub/2017/momentum/) (Goh, Distill, 2017). It opens with the popular downhill story of momentum, grants that the story is not wrong, and then says what it fails to explain.

## 2. State the scope, and give limitations their own planned section

**Check.** Does the introduction say what is left out? Is there a limitations section that the introduction announces?

**See**

- [Tidy Data](https://vita.had.co.nz/papers/tidy-data.pdf) (Wickham, 2014). The abstract narrows the paper to one small part of data cleaning. The introduction announces that Section 6 will discuss what the framework misses. Section 6 does that, and says much work remains.
- [Good enough practices in scientific computing](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510) (Wilson and others, 2017). The title sets the bar. A section named "What we left out" lists good practices the authors use daily and did not recommend, with the reason: they pay off only on top of the core practices, or they need a larger investment first.

## 3. Use a small worked model with a known true answer, and compare the naive answer against it

**Check.** When the document argues about a method, is there a case where the truth is known by construction? Is the naive answer computed on that same case, as a number?

**See**

- [Experimentation in a Ridesharing Marketplace, Part 1](https://eng.lyft.com/experimentation-in-a-ridesharing-marketplace-b39db027a66e) (Chamandy, Lyft, 2016). The whole network is shrunk to two passengers and one driver, with a three-line probability model. The true effect of the subsidy is a one-third increase in rides, from 0.75 to 1. The usual passenger-level A/B estimate, worked through on the same toy, comes out six times too large.
- [Why Most Published Research Findings Are False](https://journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.0020124) (Ioannidis, 2005). A short formula gives the chance that a finding is true from the pre-study odds, the power and the bias. Six numbered corollaries follow from it. Box 1 works one example down to a probability of 1.5 × 10⁻⁴.
- [How to Use t-SNE Effectively](https://distill.pub/2016/misread-tsne/) (Wattenberg, Viégas and Johnson, Distill, 2016). The first example is two widely separated clusters, where the reader knows what the plot should show. The same data is then plotted at five perplexity values.

## 4. Keep a compact methods block

**Check.** Can a reader find the n, the dates, the sampling frame, the weighting and the exact measure definitions in one place, without reading the narrative? Is every measure defined before the first result that uses it?

**See**

- [Online opt-in polls can produce misleading results](https://www.pewresearch.org/short-reads/2024/03/05/online-opt-in-polls-can-produce-misleading-results-especially-for-young-people-and-hispanic-adults/) (Mercer, Kennedy and Keeter, Pew Research Center, 2024). A "How we did this" section gives the sample (5,140 U.S. adults), the field dates (Jan. 16 to 21, 2024), the panel and how it was recruited (random sampling of residential addresses), and the weighting variables. The narrative stays free of them.
- [An Evaluation of 2016 Election Polls in the United States](https://aapor.org/wp-content/uploads/2022/11/AAPOR-2016-Election-Polling-Report.pdf) (AAPOR, 2017). In its introduction, ahead of the results sections, the report defines its two error measures, absolute error and signed error on the vote margin. Each gets a one-line numeric example and a sentence on what it does and does not show.
- [Switchback Tests and Randomized Experimentation Under Network Effects](https://careersatdoordash.com/blog/switchback-tests-and-randomized-experimentation-under-network-effects-at-doordash/) (Kastelman and Ramesh, DoorDash, 2018). The analysis code sits at the end of the post as an R snippet, out of the way of the argument.

## 5. Design the comparison to rule out the obvious objection, then say that you did

**Check.** Is the first objection a skeptic would raise written down? Does the document name the comparison that answers it, and say that this is why the comparison was made?

**See**

- Pew, opt-in polls (linked under move 4). An opt-in poll had reported that 20% of adults under 30 agreed the Holocaust is a myth. Pew repeated five questions from that poll on its own panel, with the same wording and format, and says it did so to make sure wording could not explain a difference. Pew found 3%.
- [What is an A/B Test?](https://netflixtechblog.com/what-is-an-a-b-test-b08cc1b57962) (Tingley and others, Netflix, 2021). Figure 3 is a before-and-after chart where engagement jumps on the day of a rollout. The text then adds that a hit title launched the same day. Figure 4 shows the same month as an A/B test: both groups rise with the hit title, and the treatment group sits lower.
- Lyft, interference (linked under move 3). Right after the toy result, the post raises the reader's objection that two users is a tiny sample. It answers by treating the real network as many independent copies of the toy, where the same arithmetic holds.

## 6. Tie the statistics to a decision rule

**Check.** Does every reported metric have a role: primary, guardrail or secondary? Is the rule for acting on them stated, and does the document say whether each condition was met?

**See**

- Netflix, "What is an A/B Test?" (linked under move 5). A hypothesis has a fixed form: change X will improve the experience in a way that moves metric Y. There is one primary decision metric. Secondary metrics are chosen along the causal chain from the change to the primary metric. Guardrail metrics, such as customer service contacts, limit the downside.
- [Risk-aware product decisions in A/B tests with multiple metrics](https://engineering.atspotify.com/2024/03/risk-aware-product-decisions-in-a-b-tests-with-multiple-metrics) (Schultzberg, Ankargren and Frånberg, Spotify, 2024). Metrics are typed as success, guardrail, deterioration and quality. The summary at the top states the main result plainly: false positive rates need no adjustment for guardrail metrics, and false negative rates must be corrected for the number of guardrails.

## 7. State confidence and caveats before the findings

**Check.** Does a confidence label appear before the first finding? Do the caveats that change how a number reads come before that number?

**See**

- [Understanding how 2020 election polls performed](https://www.pewresearch.org/short-reads/2020/11/13/understanding-how-2020s-election-polls-performed-and-what-it-might-mean-for-other-kinds-of-survey-work/) (Keeter, Kennedy and Deane, Pew Research Center, 2020). Early on, the authors call the piece a preliminary attempt and say solid conclusions are many months away. The next paragraph gives two caveats before any diagnosis: mail votes counted late will likely shrink the measured error, and the polls in several important states were sound. The authors also say they are asking the same question of their own work.

## 8. Give a calibrated verdict, and show negative results

**Check.** Does the verdict say what held up as well as what failed? Does it say where the criticized method still works? Is there at least one null or negative result, reported at full weight?

**See**

- AAPOR, 2016 polls (linked under move 4). The report splits one blanket story into two findings. National polls were among the most accurate since 1936, with an average absolute error of 2.2 points. State polls were much worse, at 5.1 points.
- Pew, opt-in polls (linked under move 4). While criticizing opt-in samples, the piece says that for some purposes, election polling among them, they can do about as well as traditional methods.
- [Assessing the Representativeness of Public Opinion Surveys](https://www.pewresearch.org/politics/2012/05/15/assessing-the-representativeness-of-public-opinion-surveys/) (Pew Research Center, 2012). A general reassurance sits beside a named exception. Weighted phone surveys still give accurate data on most measures despite falling response rates. People who take surveys tend to be more civically engaged, and the report says this has serious implications for measuring volunteering and civic activity.
- [Experiments at Airbnb](https://medium.com/airbnb-engineering/experiments-at-airbnb-e2db3abf39e7) (Overgoor, 2014). The worked example is a test that raised the price filter's maximum from $300 to $1000 and came back neutral. The post reports the neutral result, then says the change was launched anyway and why. It also shows dummy experiments that exposed a bias in the team's own system.
- [150 Successful Machine Learning Models: 6 Lessons Learned at Booking.com](https://blog.kevinhu.me/2021/04/25/25-Paper-Reading-Booking.com-Experiences/bernardi2019.pdf) (Bernardi, Mavridis and Estevez, KDD 2019; third-party mirror). Figure 4 plots each model's offline gain against its gain in a randomized trial. The finding cuts against the authors' own practice: a better offline score does not necessarily mean more business value.
- [The garden of forking paths](https://sites.stat.columbia.edu/gelman/research/unpublished/p_hacking.pdf) (Gelman and Loken, 2013). The paper separates the statistical mechanism from blame. It says the authors have no reason to think researchers fish for results. The problem it names is that a reasonable analysis would have been a different reasonable analysis had the data come out differently.

## 9. Carry the piece on one running example, and write section titles as the lessons

**Check.** Does one example run from the first section to the last? Read only the section titles: do they give the argument?

**See**

- t-SNE (linked under move 3). The six numbered section titles are the six lessons. The first says the hyperparameters matter, and the second says cluster sizes in the plot mean nothing.
- Netflix, "What is an A/B Test?" (linked under move 5). One made-up product change, box art flipped upside down, carries every figure. It is flagged as hypothetical twice, so no reader stops to argue about whether the feature is a good idea.
- [A Visual Introduction to Machine Learning](https://r2d3.us/visual-intro-to-machine-learning-part-1/) (Yee and Chu, R2D3). One task carries the piece: tell homes in New York from homes in San Francisco. A section named "First, some intuition" comes before any mechanism.
- Lyft, interference (linked under move 3). Plain pictures stand in for jargon. Potential outcomes are two slips of paper in a person's back pockets. Treatment and control are parallel universes.

## 10. End with the recommendation and the risk that remains, and invite correction

**Check.** Does the close name an action? Does it name what could still be wrong? Does it tell the reader where to send a correction?

**See**

- DoorDash, switchback tests (linked under move 4). The post credits Lyft's earlier series, says what it adds, admits the team is only getting started, and asks readers to report anything it got wrong.
- Airbnb, experiments (linked under move 8). The close turns the pitfalls into a rule for action: run experiments to make good decisions, not to push one metric, and investigate any result that looks too good to be true.
- [Why You Only Need to Test with 5 Users](https://www.nngroup.com/articles/why-you-only-need-to-test-with-5-users/) (Nielsen, 2000). The verdict is in a summary line at the top, and a section named "When To Test More Users" bounds the rule. Use it as a model of structure only. The five-user claim itself is disputed.
