### Title slide


> **Good morning everyone. Before we start reviewing probability, I want to spend a few minutes talking about why probability is here in the first place.**
>
> Most of us have seen probability before. You may remember conditional probability, Bayes' rule, expectation, variance, maybe the central limit theorem.
>
> But it is very easy to learn these as a collection of formulas without having a clear picture of what role they play in empirical research.
>
> So today, rather than starting with (P(A)), I want to start one level above that.
>
> **What exactly are we doing when we use data to learn something about the world?**

---

## Slide: From Theory to Statistical Evidence

> Let's start from the way we usually think about a social science project.
>
> We normally do not begin because we want to run a regression.
>
> We begin with some substantive or theoretical question.
>
> Maybe we want to know whether education increases political participation. Maybe we want to know whether exposure to violence changes political attitudes. Maybe we want to understand support for some policy.
>
> But those questions are still too vague to answer statistically.
>
> So one of the first things we have to do is to define exactly **what quantity we want to know**.


> Lundberg, Johnson, and Stewart call attention to precisely this step.
>
> We start with a theory or general goal.
>
> We then define a **theoretical estimand**.
>
> Then we have to link that theoretical quantity to something that can actually be learned from observable data.
>
> And only after that do we choose an estimation strategy.


> **A regression coefficient is not automatically a scientific answer. We first need to know what quantity that coefficient is supposed to teach us about.**

> This is already a useful framework.
>
> But I want to step one level further back.
>
> **Where does the observed data itself come from?**

---

# Slide: The Same Logic in Our Framework

> I am going to use a very abstract notation today, because it lets us put many different research problems into the same picture.


[
Q^\star
\xrightarrow{K^\star}
P^\star
\longrightarrow
X_n.
]

> Think of (Q^\star) as the **scientific world**.
>
> It contains whatever would need to exist if we could see everything we theoretically care about.

For example：

> It might contain people's true preferences.
>
> It might contain both potential outcomes (Y(1)) and (Y(0)).
>
> It might contain latent traits, confounders, or the full population.

Then (K^\star)：

> But we never observe that world directly.
>
> The world passes through what I will call a **research channel**, (K^\star).

For example

> Who enters our sample?
>
> Who receives treatment?
>
> How do we measure the outcome?
>
> Does someone answer a survey question truthfully?
>
> Who fails to respond?
>
> What gets recorded and what does not?

Summarize：

> **Data are not the world. Data are the world after passing through a research process.**

Why?

> The result of that process is an observable distribution, (P^\star).
>
> And even (P^\star) is not what we observe directly.
>
> What we actually get is one finite realization:
>
> [
> X_n.
> ]

---

# Before Probability — The Big Picture


> Let's make this concrete.

Use the public support example：

> Suppose I want to know how much people truly support a controversial policy.
>
> In the scientific world, people have underlying attitudes. Those attitudes may also be related to education, income, ideology, party identification, local context, and many other things.
>
> But I do not get to observe that world.

Next, the channel：

> I run a survey.
>
> Now suddenly many things happen between the scientific quantity I care about and the number in my dataset:
>
> I choose a sampling frame.
>
> Some people respond and some do not.
>
> I choose particular wording.
>
> Some respondents misunderstand the question.
>
> Some may not answer truthfully.
>
> Responses may be coded with error.

Then,

> All of those mechanisms are part of (K^\star).

Finally,

> So even something as simple as a column in a survey dataset has a data-generating history behind it.

---

# Forward vs Inverse Reasoning


> Nature gets the easy direction.

> Nature moves from left to right.

[
Q^\star\to P^\star\to X_n.
]

> The world exists. A research process acts on it. Data are generated.

**However**

> **Researchers get the hard direction.**

[
X_n\to P^\star\to \tau(Q^\star).
]

> We see the end of the process and try to reason backward.

> **Nature runs the process forward.
> Researchers have to solve it backward.**

Then

> This backward problem actually contains two conceptually different problems.

We have estimation vs identification。

---

# Two Different Inverse Problems

> Suppose I gave you infinitely much data.

Ask:

> Would that solve your research problem?

Then,

> If your problem disappears with infinite data, then the problem was fundamentally about **estimation**.
>
> You did not know the observable distribution accurately enough because you only had a finite sample.

The second type:

> But suppose I give you infinite data, and you still cannot answer the scientific question.
>
> Then the problem is not sample size.
>
> It is **identification**.

Let's think of a measurement-error example：

> Suppose I can tell you with perfect precision that 60 percent of survey respondents say they support the policy.
>
> But 10 percent of people misreport their true attitudes.
>
> If I do not know how that misreporting works, does infinite survey data reveal the distribution of true attitudes?
>
> No.

Then,

> That's an identification problem.


> Similarly, suppose I know (P(Y,T)) perfectly from an observational study.
>
> Does that automatically give me (E[Y(1)-Y(0)])?
>
> No—not if treatment is confounded.

The definition:

> So the distinction is:
>
> **Estimation:** Can I learn (P^\star) from finite (X_n)?
>
> **Identification:** Even if I knew (P^\star) perfectly, would it determine the target (\tau(Q^\star))?


---

# Why we learn Probability？


> Now we can finally answer why we are spending time on probability.
>
> Probability gives us the language for describing the **forward process**.

Then

> What outcomes are possible?
>
> Which events are more or less likely?
>
> How does conditioning on new information change what is likely?
>
> What does independence mean?
>
> What distribution does a random variable have?
>
> What happens to an average if we repeat an experiment many times?

At the end,

> Once we understand the forward stochastic process, statistics gives us tools to reason in the opposite direction.

[
P^\star\to X_n
]

vs.

[
X_n\to P^\star.
]


> **Probability asks: if this were the world, what data might I see?**
>
> **Statistical inference asks: given the data I saw, what can I learn about the world?**

Then,

> With that big picture in mind, let's now build the probability language from the ground up.

---

# Sets


> We have already seen sets. I'm bringing them back for one reason:
>
> **probability assigns numbers to sets.**

Then

* (\Omega): everything that could happen.
* (A\subseteq\Omega): a question about what happened.

For example

\[
A={2,4,6}
\]


> “Did an even number occur?”

---

# Probability axioms

> Probability is a function.
>
> Its input is an admissible event.
>
> Its output is a number.

Then we write：

\[
P:\mathcal F\to[0,1].
\]


> I said *admissible event* deliberately. We will come back to what that means.


> Probabilities cannot be negative.
>
> Something in the sample space must happen.
>
> And if two events cannot happen together, we can add their probabilities.
---

# Admissible events / sigma algebra

> Suppose I roll a die and I can observe the exact face.
>
> What events can I talk about?

The answer:

> Any subset.

Then a coarse case：

> Now imagine my measurement device is terrible.
>
> It only tells me whether the outcome was in
>
> [
> {1,2},{3,4},{5,6}.
> ]
>
> Can I ask whether the outcome was exactly 1?

> Can I ask whether it was in ({1,2,5,6})?

yes。

Then,

> This collection of questions that my information allows me to distinguish is what a (\sigma)-algebra formalizes.

> **A sigma algebra is not merely mathematical decoration. It represents the granularity of information available to us.**
---

# Conditional probability


> Conditioning means that we have learned something.

For example

\[
P(A\mid B)
\]

> We used to reason over all of (\Omega).
>
> Once I learn that (B) happened, everything outside (B) is ruled out.
>
> So I restrict attention to (B) and renormalize.

Therefore,

\[
P(A\mid B) =  
\frac{P(A\cap B)}{P(B)}.
\]


> **Conditioning = restrict + renormalize.**


> Notice what Bayes' rule is doing.
>
> We start with a prior composition of the population.
>
> Then we observe new information—support for the budget.
>
> That information changes the relative plausibility of Democrat versus Republican.

---

# Independence

> We just said conditioning represents information.
>
> So independence has a very natural interpretation:
>
> **learning (B) gives me no information about (A).**

Therefore,

\[
P(A\mid B)=P(A).
\]

Then,

> This is equivalent to the familiar product condition.

> In fact, mutually exclusive positive-probability events are almost the opposite of independent.
>
> If I tell you (B) occurred, I know for sure (A) did not occur.
---

# Random variables & distributions


> Up to now, probability has lived on events in (\Omega).
>
> But in empirical research, we usually want numbers.

Therefore,

\[
X:\Omega\to\mathbb R.
\]

Then,

> A random variable is the device that turns outcomes into numerical quantities.

Next measurability：

> But remember our sigma-algebra.
>
> If our information cannot distinguish 1 from 2, a random variable cannot magically reveal whether we saw 1 or 2.
>
> That is why we require measurability.

The distribution：

> Now there is one apparent mismatch.
>
> Probability (P) lives on events in (\Omega).
>
> But (X) lives on the real line.
>
> So what does it mean to say (P(X\leq3))?

Then,

> We pull the event back through (X).

\[
P_X(A) =  P(X^{-1}(A)).
\]

> **The random variable changes the representation; the probability distribution tells us how probability is transported to that representation.**

---

# Expectation


> Once we have a distribution, we usually don't want to carry the entire distribution everywhere.
>
> We summarize aspects of it.

Then,

> Expectation tells us where the distribution is centered in a probability-weighted sense.

> Expectation is an operator.
>
> It integrates over whatever remains random.

Now the OLS,

> This is why conditioning matters so much in statistics.
>
> When we write (E[\hat\beta\mid X]), (X) is no longer something we're averaging over.


---

# Finally Data / Asymptotics


> We started the lecture with
>
> [
> P^\star\to X_n.
> ]
>
> Up to now, we have mostly talked about (P^\star): random variables, distributions, expectations, variances.
>
> Now we finally observe one realization:
>
> [
> x_1,\ldots,x_n.
> ]

Then,

> The sample mean is our finite-data attempt to learn (E[X]).
>
> The sample variance is our finite-data attempt to learn (\Var(X)).

Finally,

> Why can we do that?
>
> This is where asymptotics enters.

WLLN：

> The Law of Large Numbers says the sample average eventually finds the right target.

CLT：

> The Central Limit Theorem tells us the scale and shape of its remaining error.

Back to the openning

> And now we have closed the loop:
>
> probability described the data-generating process;
>
> asymptotic probability gives us the machinery that allows statistics to reason backward from finite data.

---
