---
layout: post
title: "Intercausal Reasoning and Bayesian Networks"
date: 2017-07-20
image: /assets/img/intercausal/Bayes-Rule-Simple.png
description: A review of the basics of bayesian networks
comments: true
---
Over the past couple of weeks, I've been doing a review of statistics to help me better grasp some of the machine learning concepts I've been studying recently. That process of course led me back to Bayesian Networks, an important idea in machine learning, and also one I happenned to sort of skip out on back in class. In an effort to truly learn Statistics, this post will be a summary of some of the key ideas I have been reviewing.

#### First, a Review of Bayesian Statistics
Bayesian statistics is basically applying our own personal perspective (or knowledge of additional variables) to a statistics problem. A simple explanation of Bayes Rule is that its a [formula that tells us how we can update probabilties when given evidence] [bayes-def].
<div class="">
    <img class="col three" src="{{ site.baseurl }}/assets/img/intercausal/Bayes-Rule-Simple.png">
</div>

#### Conditional Probability
One of the most useful applications of this rule (also called Bayes Theorem) is conditional probality. **Conditional Probability** is the probability that event A will occur given the knowledge that an event B has already occurred. The notation for this is **P(A|B)**, the probability of A given B. What's neat about Bayes Theorem is how we can use probabilities we already know to discover unknown probabilities. For example, say we know the probability of P(B|A). We can use this probability to now find P(A|B). A breakdown looks like this:
$$ P(A|B) = \frac{P(A \cap B)}{P(A)} $$
Note: $$ \cap $$ is read as and. So the above numerator is Probability of A and B occuring. 


Next, lets apply the chain rule to further breakdown the problem. The chain rule tells us that <span>$$ P(A \cap B) $$</span> can be rewritten as <span>$$ P(B|A)*P(A) $$</span>. Now let's move onto the denominator. We know that the probability of B is dependent on A, so we can rewrite <span>$$ P(B) $$</span> as <span>$$ P(B|A)*P(A) + P(B| \lnot A)*P( \lnot A) $$</span>. So now we can rewrite our entire problem as:

$$ 
P(A|B) = \frac{P(B|A)*P(A)}{P(B|A)*P(A) + P(B| \lnot A)*P( \lnot A)} 
$$

Note that 
$$ 
\lnot 
$$ is read as not. So the probability of A not occuring. 
Now lets apply these principles to solve a sample problem. Take a look at the following graph:

<div class="">
    <img class="col three" src="{{ site.baseurl }}/assets/img/intercausal/bayes-example.png">
</div>
Lets say that given this information, we want to figure out the probability that there was an accident due to a traffic jam we are stuck in. That is, we want to solve <span>$$ P(Accident = 1 | Traffic = 1) $$</span>. For simplification purposes, I'm going to assign the variables T, P, A respectivly to traffict, President, and accident. So, lets now solve <span>$$ P(A = 1 | T = 1) $$</span>.

Luckily, this problem looks very similar to the example of Bayes Theorem from above. Using what we aleady know, we can rewrite the problem as:

$$ 
P(A=1|T=1) = \frac{P(T=1|A=1)*P(A=1)}{P(T=1|A=1)*P(A=1) + P(T=1|A=0)*P(A=0)} 
$$

<br />
To make things simpler, from now own we will denote an event occuring as just it's variable, while an event not occuring as the $$ \lnot $$ not symbol with that variable. So we know have:

$$ P(A=1|T=1) = \frac{P(T|A)*P(A)}{P(T|A)*P(A) + P(T| \lnot A)*P( \lnot A)} $$

<br />
**But**, there's one problem with our current approach. Accident (A) isn't the only variable that determines if there's traffic or not; we also have to take into account wether or not the president (P) is in town. That means that our current equation needs to be expanded upon. Lets break the numerator and denominator one at a time.


First, the numerator. This part is pretty simple, we just need to include the President (P) variable for each example in which there is an accident (Accident = 1). That means expanding <span>$$ P(T=1|A=1) $$</span> to include <span>$$ P(T=1|P=1, A=1) $$</span> and <span>$$ P(T=1|P=0, A=1) $$</span> since these are the only cases that there is an accident. Taking into account that we also must include the probability that events President in town and Accident need to be included into the calculation, our numerator now looks like:

$$ 
P(T|A)*P(A) = (P(T|P,A) * P(P) * P(A)) + (P(T| \lnot P, A) * P( \lnot P) *P(A)) 
$$

Plugging in our probabilities, we get the equation:

$$ 
P(T|A)*P(A) = (0.9*0.1*0.01) + (0.5 * 0.1 * 0.99) 
$$

<br />
And that gets us <span>$$ P(T|A)*P(A) = 0.0504 $$</span>. Now let's do the denominator. This part is trickier and will require a couple more steps to fully expand. Recall that this looks like:
$$ 
P(T|A)*P(A) + P(T| \lnot A)*P( \lnot A) 
$$
And that we need include the probability of the President being in town and affecting traffic. If you looked carefully, you would have noticed that we have no work to do for the first part, 
$$
 P(T|A)*P(A) 
$$
, because it's the same as the numerator we already solved. Instead, lets jump straight into the second half of this problem. This breaks down as:

$$ 
(P(T|P, \lnot A) * P(P) * P( \lnot A)) + (P(T| \lnot P, \lnot A) * P( \lnot P) *P( \lnot A)) 
$$



Lets now combine the breakdown we got from the numerator, and put the denominator all together. We'll break it down across multiple lines to make it easier to read.

$$ 
(P(T|P, A) * P(P) * P(A))
$$


$$
+(P(T| \lnot P,A) * P( \lnot P) *P(A))
$$

$$
 +(P(T|P, \lnot A) * P(P) * P( \lnot A)) 
$$

$$
 + (P(T| \lnot P, \lnot A) * P( \lnot P) *P( \lnot A))
$$


And with the breakdown done, we can now start plugging in the correct probabilities and take one step closer to solving the problem


$$ 
(0.9* 0.1* 0.01) 
$$

$$
+ (0.5* 0.1* 0.99)
$$

$$
+ (0.6 * 0.9* 0.01)
$$

$$
+ (0.1* 0.9* 0.99) 
$$

which equals **0.1447**. Let's now put the final problem together. Remember that our initial equation after Bayes Theorem was <span>$$ \frac{P(T|A)*P(A)}{P(T|A)*P(A) + P(T| \lnot A)*P( \lnot A)} $$</span>, and that for the denominator we got 0.0504, and for our numerator we got 0.1447. We can plug this all in getting
<span>

$$ 
\frac{P(T|A)*P(A)}{P(T|A)*P(A) + P(T| \lnot A)*P( \lnot A)} = \frac{0.0504}{0.1449} 
$$


</span> which we can solve as **0.3478**, or about 35% when rounded up. And there we go, we have successfully found the probability that the traffic jam we are experiencing was caused by an accident. This is what makes Bayesian statistics so magical. The ability to better infer the likiliness of an event due to some experience or knowledge we have opens a world of opportunities. In this scenario, our experience of a traffic jam completly changes the probability of an accident having occurred. Previously, the probability of an accident occuring was 0.1, or 10%. By applying what we know about a traffic jam however, that probability jumped to 35%. Note that we can also find the probability that a traffic jam was not caused by by an accident by taking <span>$$ 1 - P(A=1|T=1) $$</span>, which turns out to be about **65%**. We can double check this answer by calculating 

<span>$$ \frac{P(T=1|A=0)*P(A=0)}{P(T=1|A=1)*P(A=1) + P(T=1|A=0)*P(A=0)} $$</span>, 

which turns out to be the exact same as the previous solved equation, except that the numerator is now <span>$$ (0.1*0.9*0.99)+(0.6*0.9*0.01) $$</span> which equals **0.0945**. Plug that back into our problem and there we go.


To conclude this post, Bayesian statistics are an awesome, albiet kinda complex, way to determine probabilities of events. Over the next couple of weeks, I may expand this post or write a new one on more topics in statistics and probability. Thanks for reading, if I made any mistakes please feel free to reach out to me!




[udacity-ai]: https://www.udacity.com/course/artificial-intelligence-nanodegree--nd889
[anaconda]: https://anaconda.org
[github-repo]: https://github.com/seb-patron/AIND-Sudoku
[bayes-def]: https://brilliant.org/wiki/bayes-theorem/