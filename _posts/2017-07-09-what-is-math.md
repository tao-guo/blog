---
layout: post
title: What Is Math?
categories: math
published: yes
author: Tao
date: 2017-07-09
---

What is math? In the Greek language, the word is "knowledge, study, learning". Aristotle defined mathematics as "**the science of quantity**", and  this definition prevailed until the 18th century. At that time, math is about quantity and measurement, and the majority of the symbols used are not much different from today. [Euclidean geometry], Cartesian's [analytic geometry], Caldano's [cubic equation]/[quad equation] solutions and Newton-Leibniz's [calculus] are a series of great mathematical achievements. By the nineteenth century, mathematics had completed the perfect abstraction of quantity/unknowns. In fact, most people's mathematical knowledge also stays at this stage. For the general public, Aristotle's definition of mathematics is still valid.

<div style = "margin: 0 auto 15px; width: 60%; text-align: center;">
  <img src = "{{site.baseurl}}/img/Euclid.jpg" alt = "Euclid in the Athens Institute" style = "display: block;">
  Euclid in the "Athens Institute"
</div>

But from the beginning of the 19th century, mathematics began to study more abstract "[group]" and "[projective geometry]", and these new mathematical objects can not be directly measured. Mathematicians and philosophers are trying new definitions to adapt these changes. Their definitions are different, such as some emphasis on deductive reasoning, some emphasis on "abstract", and some focus on specific mathematical topics. Because of the introduction of more abstract concepts, the debate on mathematical definitions has not been agreed so far: is mathematics itself "invented" or "found"? Mathematics in the end is "art" or "science"? Some people simply said, "Mathematics, that is, those things that mathematicians do."

## An overview
So what are the main problems that mathematicians are solving? They can be divided into three areas:

- Pure mathematics: theoretical mathematics, according to Wikipedia including number, structure, space, changes.
- Applied mathematics: applying mathematics to specific problems such as physics, chemistry, computer, finance, game, etc.
- Foundations and philosophy: axiomatic foundations such as set theory, category theory, and computability theory in computer science(P = NP?), etc.

The study of these problems is to find the "patterns" of the objective world, to sum up the formula, and to make a reasonable guess. When mathematical structures are good models of real phenomena, then mathematical reasoning can provide insight or predictions about nature. Some seemingly completely useless theoretical math/pure mathematics, in the future may be shine in particular application areas, such as the number theory applied in cryptography. The foundations and philosophy is to find the cornerstone of various theories, so that mathematical theory can be solidly developed.

## Methodology
How can I know which mathematical guesses are correct? Mathematics uses two major weapons: **abstract** and **logical reasoning**, in an axiomatic way to formulate a series of conjectures.

Axioms in traditional thought were "self-evident truths", but that conception is problematic. At a formal level, an axiom is just a string of symbols, which has an intrinsic meaning only in the context of all derivable formulas of an axiomatic system. It was the goal of Hilbert's program to put all of mathematics on a firm axiomatic basis, but according to [Gödel's incompleteness theorem] every (sufficiently powerful) axiomatic system has undecidable formulas; and so a final axiomatization of mathematics is impossible. Nonetheless mathematics is often imagined to be (as far as its formal content) nothing but set theory in some axiomatization, in the sense that every mathematical statement or proof could be cast into formulas within set theory.

In fact, the axiomization of elementary arithmetic - [Peano axioms] system was established until the twentieth century. Therefore, the elementary arithmetic operations such as \\(1 + 1 = 2 \\), \\(3 \times7 = 7 \times3 \\) (commutative law), can be proved in the peano axioms system. It has been discussed in Terence Tao(陶哲轩)'s book "analysis", which begins from the introducation of Peano axioms.

## As a model of the real world
With regard to mathematics as a model of the real world, the expectations of mathematicians at different stages are quite different:

Galileo (1564-1642):
  > The universe cannot be read until we have learned the language and become familiar with the characters in which it is written. It is written in mathematical language, and the letters are triangles, circles and other geometrical figures, without which means it is humanly impossible to comprehend a single word. Without these, one is wandering about in a dark labyrinth.

Gauss (1777-1855):
  > Mathematics is the Queen of the Sciences

Hilbert (1862-1943):
  > We are not speaking here of arbitrariness in any sense. Mathematics is not like a game whose tasks are determined by arbitrarily stipulated rules. Rather, it is a conceptual system possessing internal necessity that can only be so and by no means otherwise.

Einstein (1879-1955):
  > As far as the laws of mathematics refer to reality, they are not certain; and as far as they are certain, they do not refer to reality.

<div style = "margin: 0 auto 15px; width: 60%; text-align: center;">
  <img src = "https://upload.wikimedia.org/wikipedia/commons/5/5b/Lorenz_attractor_yb.svg" alt = "Lorentz transformation in chaos theory" style = "display: block;">
   Lorenz attractor in Chaos theory
</div>

It can be seen that, to the last Einstein's argument, mathematics as a real-world model has become increasingly uncertain. Beginning in the 1960s, the [chaos theory], developed from meteorological forecasts, also demonstrated this. In fact, quantum physics which is closely related to mathematics, also appeared in a similar situation. Quantum physics itself is deeply influenced by mathematics, and Eugene Wigner has published "[The unreasonable effectiveness of mathematics]", pointing out how mathematics can unbelievably lead the discovery of the natural sciences. The most surprising and most mysterious is that in the mathematical layers of the concept of non-material abstraction, contains the deepest and most secret of the material world. Such as π may appear in the demographic model, and imaginary numbers exist in quantum mechanics etc.

## The history

Mathematics is from "counting" and "measurement of land" two production activities, which formed the algebra and geometry as the two pillars. Western mathematics focuses on the development of geometry, and the use of Euclid's axiomatic and logical derivation, not only promoted the development of mathematics, but also profoundly affected the other natural sciences.

For many abstract mathematical concepts, the geometric sense of understanding is more intuitive, such as the commutative real multiplication can be understood as geometric rectangular area unchanged. In some systems, element operations are not necessarily commutative, such as in "groups". Algebra and geometry correspond to two abstract concepts: time and space, which belong to different regions of the brain. Many great mathematicians use geometry to help themselves quickly grasp the core concepts of mathematics, such as VI Arnold (1937-2010), who proved that Hilbert's thirteenth question at 19: [On teaching mathematics(1997)](https://www.uni-muenster.de/Physik.TP/~munsteg/arnold.html).

In recent years, with the development of computers, geometric graphics can be more easily displayed. Stanford Math graduate [3blue1brown] (http://www.3blue1brown.com/about/) just used graphical intuitive to explain the "[Essence of calculus](https://www.youtube.com/playlist?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr)" and "[Essence of linear algebra](http://space.bilibili.com/88461692/#!/channel/detail?cid=94502)" and a serie of courses, which is a great learning material. And even as highly abstract group theory/modern algebra, Professor Macauley just explained in a graphical way on youtube: [Visual Group Theory](http://www.math.clemson.edu/~macaule/classes/m17_math4120/index.html).

In history algebra and geometric developed seperately and they usually have different theories, but Klein unified all geometries into algebra group theory in 20th centry, in the higher level of a unified abstraction. The book "the history of algebra" also covers the development of geometric trends. The author summarizes the three stages of algebra in the book:

  - the first abstraction: the value
    - the transition from an instance to a value
  - the second abstraction: the word symbol system, that is, with the letter symbol to represent any number (the unknown \\( x \\))
    - Newton called "pan arithmetic"
    - the core for solving equations
    - and the symbols in the geometric concept are slowly differentiated
  - third abstraction: new math objects - group, matrix, manifold ...
    - new abstraction level
    - research logic, abstract algebra (modern algebra), group theory and so on

Shiing-Shen Chern(陈省身) also had a wonderful lecture ["what is geometry(1987)"] ({{site.baseurl}}/math/1987/04/21/what-is-geometry.html), summed up the geometric development process. The lecture is still profoundly inspiring.

## Math fields
- [Fundamentals and Philosophy](https://en.wikipedia.org/wiki/Mathematics#Foundations_and_philosophy)
  - Mathematical logic, set theory, category theory
- [Pure mathematics](https://en.wikipedia.org/wiki/Mathematics#Pure_mathematics)
    - quantity: natural number, integer, rational number, real number, complex number and so on
    - structure: number theory, group theory, graph theory, order theory
    - space: geometry, trigonometry, differential geometry, topology, fractal, measure theory
    - change: calculus, vector analysis, differential equations, dynamical systems, chaos theory, complex analysis
- [Applied Mathematics](https://en.wikipedia.org/wiki/Mathematics#Applied_mathematics)
  - physical mathematics, mathematical fluid mechanics, numerical analysis, optimization, probability theory, statistics, measurement finance, game theory, mathematical economics, bio-mathematics, homework research, cybernetics

![The Map of Mathematics]({{site.baseurl}}/img/map-of-mathmatics.png)

See Wikipedia's "mathematics" item and the video [The Map of Mathematics](https://www.youtube.com/watch?v=OmJ-4B-mS-Y).

## Chinese mathematicians
- Fields Award
  - 1982 Shing-Tung Yau(丘成桐)
  - 2006 Terence Tao(陶哲轩)
- Abel Award
  - No (2016 winner for the Fermat theorem Proved by Wiles)
- Wolf Prize
  - 1983 Shiing-Shen Chern(陈省身)
  - 2010 Shing-Tung Yau(丘成桐)
- Cole algebra award and number award
  - 2014 Yitang Zhang(张益唐)

The two most influential Chinese mathematicians: Hua Luogeng(华罗庚 1910-1985) and Shiing-Shen Chern(陈省身 1911-2004), both were in the Tsinghua University Department of Mathematics, and in the Southwest United Datong dormitory.

Chen-Ning Yang(杨振宁) had this comparison between Hua and Chern:
  > Hua Luogeng and Shiing-Shen Chern are the important mathematicians of our country, that is our wisdom and wisdom of the Chinese nation on behalf of. If there were a teacher, asked them a question, Hua Luogeng could solve it immediately, but Chern would need a month to solve it. However, Chern would developed a subject based on that question.
  >
  > Isaiah Berlin (1900-1997) popularizes the Greek concept of two different types of philosophers: "the fox has many skills, and the hedgehog is proficient in a stunt." I think this is an excellent The way to describe Hua Luogeng is different from that of Chern: He has a wide range of interests and has made an important contribution to several different branches of mathematics; while Chern is focused on a branch of differential geometry, but he innovates this branch, and this innovation later on the 20th century Geometric, algebra, analysis, topology of the major branches have far-reaching impact, and even in-depth impact on the past 40 years the development of theoretical physics.

Similar to the metaphor of "[Birds and Frogs(2009)](http://www.ams.org/notices/200902/rtx090200212p.pdf)" by Freeman Dyson (1923-), and twenty-century great "bird" mathematician Hilbert, Chern paid more attention to the overall view, founded MSRI, and also expanded the scope of differential geometry.

## Key mathematicians
The core concept of modern math is "group", but it is devloped from **Galois** who died at only twenty years old in a legendary way. "The Equation that Couldn't Be Solved" made a profound description for the tragic heroes.  As the language of symmetry--"group", it penetrates into the physical, geometric, biological and other areas.

[Hilbert's 23 questions], are still the climax of mathematicians dreaming of climbing. **Gödel**'s incompleteness theorem, is descripted in the book "Gödel's proof" in an easy way. Nowadays artificial intelligence and creativity are hot topics, and the discussion in that book is still profoundly insightful.

[Euclidean geometry]: https://en.wikipedia.org/wiki/Euclidean_geometry
[Analytic geometry]: https://en.wikipedia.org/wiki/Analytic_geometry
[Cubic equation]: https://en.wikipedia.org/wiki/Cubic_function
[Quad equation]: https://en.wikipedia.org/wiki/Quadratic_equation
[Calculus]: https://en.wikipedia.org/wiki/Calculus
[Group]: https://en.wikipedia.org/wiki/Group_(mathematics)
[Projective Geometry]: https://en.wikipedia.org/wiki/Projective_geometry
[Gödel's incompleteness theorem]: https://en.wikipedia.org/wiki/G%C3%B6del%27s_incompleteness_theorems
[Chaos theory]: https://en.wikipedia.org/wiki/Chaos_theory
[The unreasonable effectiveness of mathematics]: https://en.wikipedia.org/wiki/The_Unreasonable_Effectiveness_of_Mathematics_in_the_Natural_Sciences
[Hilbert's 23 questions]: https://en.wikipedia.org/wiki/Hilbert%27s_problems
[Peano axioms]: https://en.wikipedia.org/wiki/Peano_axioms
