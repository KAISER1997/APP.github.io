---
layout: post
title: Decision Making Under Uncertainty-Part 1
date: 2022-06-04
description: motivating the need for imprecise probabilities
---
The goal of decision making is to take an optimal decision according to some optimality criterion. In high-stake scenarios, making an optimal decision is crucial to avoid catastrophic consequences. Imagine a doctor making a diagnosis for some patient, a wrong decision (in this case, diagnosis) can be life threatening. The goal of this post is to formalize decision making using probability theory, and argue why this is not enough. We will use the diagnosis of skin lesions as a running example to underscore the importance of optimal decision making.

**Setting:** We assume a finite set of all the decisions available to the decision maker. Denote this set by $$\mathcal{D}$$, and the decision maker aims to take some decision $$d$$ from $$\mathcal{D}$$. In the skin lesion diagnosis setting, a doctor has to decide whether the lesion is benign $$(d_{1})$$ or cancerous $$(d_{2})$$. A doctor may also choose to refer to a senior doctor $$(d_{3})$$, or refer to a psychiatrist $$(d_{4})$$. Thus, $$\mathcal{D} = \{d_{1}, d_{2}, d_{3}, d_{4}\}$$. 

Of course, there are consequences of taking some decision $$d$$. We model consequence by attaching costs to each decision. A lesion could be cancerous, and the doctor may decide to label it as benign. This decision comes with a high cost. To model consequences of decision, we associate with each decision a random variable $$J_{d_{i}}: \mathcal{X} \rightarrow \mathbb{R}$$. $$\mathcal{X}$$ is our possibility space, and the outcome $$x \in \mathcal{X}$$ is uncertain. For example, $$\mathcal{X} = \{\text{benign}, \text{cancerous}\}$$ for our running example. And $$J_{d_{1}}(x)$$ is very high when $$x = \text{cancerous}$$. So, how do we take an optimal decision $$d_{\text{opt}}$$ with uncertainties on $$x \in \mathcal{X}$$?

**Minimum Expected Cost Framework:** A classical approach from probability theory for the above question is taking the decision with minimum expected cost. One consider a probability measure space $$(\mathcal{X}, \mathcal{F}, \mu)$$ to model beliefs about an uncertain outcome $$x \in \mathcal{X}$$. $$\mu$$ is a probability measure on the $$\sigma-\text{algebra}$$  $$\mathcal{F}$$ on $$\mathcal{X}$$. We consider $$\mathcal{F}$$ large enough that each $$J_{d_{i}}$$ is a measurable function w.r.t. $$\mathcal{F}$$. One can now take an expectation to each $$J_{d_{i}}$$ w.r.t. to the measure $$\mu$$ as defined below:

$$
	\mathbb{E}[J_{d_{i}}] = \int J_{d_{i}} d\mu
$$ 

The minimum expected cost model for decision making then says to take the decision with that minimise $$\mathbb{E}[J_{d_{i}}]$$, i.e.

$$
	d_{\text{opt}} \in \arg \min_{d \in \mathcal{D}}\mathbb{E}[J_{d}]
$$

Note: A minimum expected cost framework for decision making says to take the decision with the minimum expected cost. It is presented in a slightly complicated way here just to elucidate the complexity of this framework.  

**Limitations of the Minimum Expected Cost Framework:** The goal of this post is to highlight the limitations of the above approach. To say in simple terms, the minimum expected cost framework is asking for too much. It asks for a well-defined probability measure $$\mu$$ on a well-defined measurable space. In many practical situations, it is unreasonable to come up with those to a precise degree. In our medical setting, assigning a well-defined measure $$\mu$$ to the outcome of the diagnosis is non-trivial. This results simply because we might not have full information, or very well can have vague or imprecise information. Thus, we cannot precisely assign $$\mu(F)$$ to every $$F \in \mathcal{F}$$. If we use minimum expected cost framework to arrive at an optimal decision, we get very unreliable decision as the following example shows.

**Example:** In our example of skin lesion diagnosis, assume the following costs are associated to each decision based on the outcome $$x \in \mathcal{X}$$.

$$J_{d_{1}}(\text{benign}) = 0, J_{d_{1}}(\text{cancerous}) = 1$$
$$J_{d_{2}}(\text{benign}) = 0.7, J_{d_{2}}(\text{cancerous}) = 0$$
$$J_{d_{3}}(\text{benign}) = 0.5, J_{d_{3}}(\text{cancerous}) = 0.2$$
$$J_{d_{4}}(\text{benign}) = 0.1, J_{d_{4}}(\text{cancerous}) = 0.8$$

And we assume to have only incomplete information about the underlying $$\mu$$. Consider that we know the probability of the skin lesion being cancerous is between $$0.2$$ and $$0.5$$, i.e. $$0.2 \leq \mu(\text{cancerous}) \leq 0.5$$. 

{% include figure.html path="assets/img/uncertainty.png" class="img-fluid rounded z-depth-1" %}
