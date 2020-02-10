---
title: Neural Symbolic Weakly Supervised Semantic Parsing
published: true
---

Written by Evelyn(Yining) Hong

Department of Computer Science

Feb.10th, 2020

Literature Survey of CS269

# [](#header-1)Paper: Neural Symbolic Machines: Learning Semantic Parsers on Freebase with Weak Supervision
ACL 2017

_Chen Liang, Jonathan Berant, Quoc Le, Kenneth D. Forbus, Ni Lao_

[Link to paper](https://arxiv.org/pdf/1611.00020.pdf)



## [](#header-2)What is Semantic Parsing?

The goal of semantic parsing is to generate compositional, executable, formal representation, e.g. code/sql/sparql.

Formal representation requires following strict constraints:

1. Syntax (e.g., correct number of parentheses)
2. Semantics (e.g., calling function with the right type of arguments)

Previously, most semantic parsing tasks make use of Seq2Seq model. It was first introduced into this area by [(Dong & Lapata, 2016)](https://arxiv.org/pdf/1805.04793.pdf). With a single neural network, it soon beat all the other rule-based human-written semantic parsing techniques. The authors also propose seq2tree because semantic sentences always have hierarchical structure. Seq2seq structures are easy to build with toolkits.

![](https://evelinehong.github.io/assets/images/seq2seq.png)


## [](#header-3)Neural Symbolic Weakly Supervised Semantic Parsing 
Recently, the neural-symbolic paradigm has been extensively explored in the tasks of semantic parsing. Concretely, for these tasks, neural networks are used to map raw signals (images/questions/instructions) to symbolic representations (scenes/programs/actions), which are then used to perform symbolic reasoning/execution to generate final outputs. Weak supervision in these tasks usually provides pairs of raw inputs and final outputs, with intermediate symbolic representations unobserved.

![](https://evelinehong.github.io/assets/images/supervision.png)

Since symbolic reasoning is non-differentiable, previous methods usually learn the neural-symbolic models by policy gradient methods like REINFORCE. The policy gradient methods generate samples and update the policy based on the generated samples that happen to hit high cumulative rewards. 

![](https://evelinehong.github.io/assets/images/reinforce.png)

## [](#header-4)Neural Symbolic Machines
Back to our paper, ["Neural Symbolic Machines: Learning Semantic Parsers on Freebase with Weak Supervision"](https://arxiv.org/pdf/1611.00020.pdf).

Seq2seq has a good performance. However it also has several disadvantages:
1. Require strong/full supervision. So it is only applied on domains with tiny schemas/vocabs and known semantic annotations.
2. Lack of integration with the executor. As we said before, intermediate symbolic programs must be executed to get the final answer. In seq2seq, only after the whole program is written can any feedback be generated from the executor. However, usually the search space is large and there's no way to search over the exponentially large hypothesis space given a large schema. So the **entire burden is on the neural network.**

The authors present a manager-programmer-computer framework, in which the generated programs are executed sequentially.

![](https://evelinehong.github.io/assets/images/MPC.png)

### [](#header-5) Dataset
They use the [WebQuestions](https://worksheets.codalab.org/worksheets/0xba659fe363cb46e7a505c5b6a774dc8a) dataset. It contains 5810 questions crawled from Google Suggest API and answered using Amazon MTurk. Specifically, they have 3778 questions for training and 2032 for testing. A question may have multiple answers using Avg.F1 as main evaluation metric.

### [](#header-6) Symbolic Computer
In fact, their computer -or symbolic part, is similar to Lisp, which is a high-level language with uniform syntax.

It's composed of some predefined functions (F A0...Ak) where F is the function name and A0...Ak are variables (v) or relations (r).

![](https://evelinehong.github.io/assets/images/function.png)



