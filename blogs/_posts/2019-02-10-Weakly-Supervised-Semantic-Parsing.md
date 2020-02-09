---
title: Weakly Supervised Semantic Parsing
published: true
---

Written by Evelyn(Yining) Hong

Feb.10th, 2020



# [](#header-1)Neural Symbolic Machines: Learning Semantic Parsers on Freebase with Weak Supervision
ACL 2017

_Chen Liang, Jonathan Berant, Quoc Le, Kenneth D. Forbus, Ni Lao_

[Link to paper](https://arxiv.org/pdf/1611.00020.pdf)



## [](#header-2)What is Semantic Parsing?

The goal of semantic parsing is to generate compositional, executable, formal representation, e.g. code/sql/sparql.

Formal representation requires following strict constraints:

1. Syntax (e.g., correct number of parentheses)
2. Semantics (e.g., calling function with the right type of arguments)

Previously, most semantic parsing tasks make use of Seq2Seq model. It was first introduced into this area by [(Dong & Lapata, 2016)](https://arxiv.org/pdf/1805.04793.pdf). With a single neural network, it soon beat all the other rule-based semantic parsing techniques. The authors also propose seq2tree because semantic sentences always have hierarchical structure.

### Small image

![](https://evelinehong.github.io/assets/images/seq2seq.png)


### [](#header-3)Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### [](#header-4)Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### [](#header-5)Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### [](#header-6)Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)

### Large image

![](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
