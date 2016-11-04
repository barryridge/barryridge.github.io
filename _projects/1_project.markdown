---
layout: post
title: SSLVQ 
description: Self-Supervised Learning Vector Quantization
img: /assets/img/sslvq.png
---

# [SSLVQ](https://github.com/barryridge/SSLVQ): A self-supervised online multi-view learning vector quantization framework for object affordance learning.

***

SSLVQ is a Matlab library distributed to accompany the publication of my [Ph.D. thesis](http://eprints.fri.uni-lj.si/2888/) and [2015 IJARS journal article](http://arx.sagepub.com/content/12/3/24.full) and was developed in order to enable developmental learning of object affordance categories for autonomous robots.

<center>
<img src="{{ site.baseurl }}/assets/img/object_affordance_learning_scenario.png" width="80%" alt="" title="Our object affordance learning scenario."/>
</center>
<div class="col three caption">
	Our object affordance learning scenario.
</div>

*Multi-view learning*, sometimes also referred to using the terms 'cross-modal learning', 'multi-modal learning' or 'co-clustering' is a type of machine learning where, rather than being isolated to a single feature space, learning is instead performed over multiple separate feature spaces, otherwise known as ‘data views’ or ‘modalities’, in which data co-occur. Given this common theme, the learning goal may otherwise differ depending on the particular context. In our object affordance learning scenario, object properties such as shape features define the feature space in one data view, the input space $$ X \subseteq \mathbb{R}^m $$, whereas object effects observed from interaction, such as motion features and changes in shape features, define the feature space in another data view, the output space $$ Y \subseteq \mathbb{R}^n $$. We assume that matching data co-occur in each of them.

<center>
<img src="{{ site.baseurl }}/assets/img/sslvq_small.png" alt="" title="SSLVQ cross-view Hebbian projection visualisation."/>
</center>
<div class="col three caption">
	Visualisation of SSLVQ cross-view Hebbian projection.
</div>

Our learning goal is to find significant clusters in $$ Y $$ (upper part of above figure) that may be projected back to $$ X $$ (lower part of above figure) and used as class labels to train a classifier, thus forming a mapping $$ f : \mathbb{R}^m \rightarrow \mathbb{N} $$ from input space feature vectors to class labels representing affordances grounded in output space feature clusters. We consider this as a multi-view learning problem given that there is a natural separation between the two feature spaces under consideration, which model potential causes and potential effects respectively, and also as a *self-supervised learning* problem given that the class clusters must be discovered in output space $$ Y $$ in an unsupervised manner before being exploited
for supervised discriminative learning in input space $$ X $$, a process that must occur online, dynamically and autonomously.

Our solution to this problem involves representing each of the data views
via *vector quantization* using codebooks of prototype vectors
$$ W = \{ {\mathbf w}_j \in \mathbb{R}^{m} \,\left|\, j = 1,\ldots,M \right. \} $$
for the input space and
$$ V = \{ {\mathbf v}_k \in \mathbb{R}^{n} \,\left|\, k = 1,\ldots,N \right. \} $$ for the output space, respectively,
approximating the data distributions in each view.
We train the codebooks in each view using combinations of the *self-organizing map (SOM)* algorithm and extended forms of the *learning vector quantization (LVQ)* algorithm, while also training the cross-view weights that connect them using *Hebbian learning*.
The interested reader is referred to [the IJARS paper](http://arx.sagepub.com/content/12/3/24.full) for further details.
The project code is not well optimized, organised, or maintained, but I am preserving it on Github for posterity and potential future inspiration.
