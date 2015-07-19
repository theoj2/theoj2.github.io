---
author: tjones
comments: false
date: 2014-02-11 21:47:04+00:00
layout: post
slug: time-publishes-flawed-article-d-wave-quantum-computer-2
title: Time Publishes Flawed Article on D-Wave "Quantum Computer"
wordpress_id: 1099
categories:
- old
tags:
- Bzzt Quantum
- Edward Snowden
- Matthias Troyer
- NSA
- Old
---

Time's [most recent cover article](http://content.time.com/time/subscriber/article/0,33009,2164806-1,00.html) was about a quantum computer produced by startup D-Wave. However, this article is deeply flawed and represents severe problems that pervade science journalism  





 
    
  1. Time's writer has no expertise in the relevant subject matters. Quantum computing involves very complex issues in computer science and physics. Time assigned the story to their book critic who has a degree in literature.

    
  2. Time's story gives equal weight to the claims made in D-Wave's advertising, and to the relevant published research done by independent computer scientists and physicists. The academic research gives strong reasons to doubt the plausibility of many of D-Wave's claims.

    
  3. The story has a multitude of outright errors and misleading statements.

 



D-Wave has developed a special purpose quantum computer. The computer you are reading this on is a general purpose computer -- it can do any mathematical calculation that you want. On the other hand D-Wave's computer is optimized to solve only one problem, discrete combinatorial optimization, which has applications in engineering. D-Wave's computer can do one thing that your computer cannot, use quantum mechanical effects to aid the solving of this problem. There is however one problem that did not get enough play in Time's story, independent researchers have not been able to verify that D-Wave's quantum computer is any better at solving this problem than a classical computer, or even that quantum computers in general are better at this problem.



<!-- more -->



The issues with the Time article start with the first paragraph.  





<blockquote>For years astronomers have believed that the coldest place in the universe is a massive gas cloud 5,000 light-years from Earth called the Boomerang Nebula. ...

But as it turns out, the scientists have been off by about 5,000 light-years. The coldest place in the universe is actually in a small city directly east of Vancouver called Burnaby.</blockquote>

 



Two issues here  





 
    
  1. The Boomerang is the the coldest known _natural_ object, artificial experiments have long gone below this level

    
  2. The internals of the D-Wave computer are _NOT_ the coldest man-made object

 



Now lets look at the last paragraph of the article preview  





<blockquote>The reason D-Wave has so few customers is that it makes a new type of computer called a quantum computer that's so radical and strange, people are still trying to figure out what it's for and how to use it. .... it has the potential to solve problems that would take conventional computers centuries, with revolutionary consequences for fields ranging from cryptography to nanotechnology, pharmaceuticals to artificial intelligence.</blockquote>

 



I'm tempted to tone down the flameage on this one because the issues in this paragraph are corrected later in the article. However, this is the last paragraph that is below the fold. So, this will be as far as many readers read. And this paragraph is incorrect when taken by itself. As I noted above, the D-Wave is a special purpose computer. Its not useful at running Shor's algorithm, or Grover's algorithm -- the two quantum algorithms with relevance to cryptography. It can just solve the discrete combinatorial optimization problem, which has much more limited use.  





<blockquote>.... But D-Wave's customers buy them anyway, for around $10 million a pop, because if they're the real deal they could be the biggest leap forward since the invention of the microprocessor.</blockquote>

 



Same issue here. Classical computers do a lot more than just solve one math problem.





The discussion of the history of quantum mechanics is pretty good. There is one sentence that I would take exception to  





<blockquote>Einstein ultimately found quantum mechanics so monstrously counterintuitive that he rejected it as either wrong or profoundly incomplete. As he famously put it, "I cannot believe that God plays dice with the world."</blockquote>

 



Einstein didn't reject quantum mechanics, he argued for the [ensemble interpretation](http://en.wikipedia.org/wiki/Ensemble_Interpretation) which attempts to explain quantum effects in terms of statistical aggregates of particles.  





<blockquote>The supercooled niobium chip at the heart of the D-Wave Two has 512 qubits and therefore could in theory perform 2512 operations simultaneously.</blockquote>

 



Bzzt!! Quantum computers don't do 2512 operations simultaneously. The quantum computer does an operation that pretty much amounts to randomly guessing at the right answer. The qubits then undergo what is known as entanglement.  At this point you can imagine  2512 parallel universes with their own parallel qubits. These "virtual" qubits interact, and eventually they decohenere into a state where only one set of qubits is observed. At first glance it looks like you just have quantum [bogosort](http://en.wikipedia.org/wiki/Bogosort) -- most of the possible guesses are incorrect. But in fact, during the period of time when the "virtual" qubits are entangled and interacting, and when the problem being solved follows certain patterns it is possible to "stack the deck" and increase the probability that the correct answer will be the one observed.  





<blockquote>One of the documents leaked by Edward Snowden, published last month, revealed that the NSA has an $80 million quantum-computing project suggestively code-named Penetrating Hard Targets. Here's why: much of the encryption used online is based on the fact that it can take conventional computers years to find the factors of a number that is the product of two large primes. A quantum computer could do it so fast that it would render a lot of encryption obsolete overnight. You can see why the NSA would take an interest.</blockquote>

 



Correct but confusing. Contrary to the impression that you would get so far in the article, the D-Wave computer cannot solve these cryptographic problems.





The article then goes into a two-page speel about how great the inventors of the D-Wave computer how, and how great the technique they invented is. -- All without any mention of the objection from the academic community.  





<blockquote>For example, you can't as yet perform the kind of cryptographic wizardry the NSA was interested in, because an adiabatic quantum computer won't run the right algorithm. It's a special-purpose tool. "You take your general-purpose chip," Rose says, "and you do a bunch of inefficient stuff that generates megawatts of heat and takes forever, and you can get the answer out of it. But this thing, with a picowatt and a microsecond, does the same thing. So it's just doing something very specific, very fast, very efficiently."</blockquote>

 



Finally on page five out of eight.  





<blockquote>This is great if you have a really hard discrete combinatorial optimization problem to solve. Not everybody does. But once you start looking for optimization problems, or at least problems that can be twisted around to look like optimization problems, you find them all over the place: in software design, tumor treatments, logistical planning, the stock market, airline schedules, the search for Earth-like planets in other solar systems, and in particular in machine learning.</blockquote>

 



No mention of how no one has been able to prove that quantum computers can actually solve the discrete combinatorial optimization problem in a way thats appreciably more effective than classical computers.





The article then continues on about how great the D-wave people are, and how big name companies have bought their stuff for another page.





On the last page of the article Time gets to D-Wave's critics, but portrays them as a bunch of ivory tower eggheads that are a bit too removed from real life -- instead of a sizeable portion of those who are capable of evaluating D-Wave's claims.  





<blockquote>Another challenge rose and company face is that there is a small but nonzero number of academic physicists and computer scientists who think that they are partly or completely full of sh-t. Ever since D-Wave's first demo in 2007, snide humor, polite skepticism, impolite skepticism and outright debunkings have been lobbed at the company from any number of ivory towers. "There are many who in Round 1 of this started trash-talking D-Wave before they'd ever met the company," Jurvetson says.</blockquote>

 



Extraordinary claims require extraordinary evidence.  





<blockquote>Any blog post or news story about D-Wave instantly grows a shaggy beard of vehement comments, both pro- and anti-.</blockquote>

 



Yup.  





<blockquote> The critics argue that D-Wave is insufficiently transparent,</blockquote>

 



Then D-Wave should release more information about how their computer works. Reproducibility of your results is an important part of science.  





<blockquote>that its adiabatic approach is unpromising, that its machines are no faster than classical computers</blockquote>

 



Then they should release evidence that quantum computers can solve the discrete combinatorial optimization problem faster than a classical computer.   

Lets check what actual physicists say about this dispute then.  





<blockquote>Last month a team including Matthias Troyer, an internationally respected professor of computational physics at ETH Zurich, attempted to clarify things with a report based on an extensive series of tests pitting Google's D-Wave Two against classical computers solving randomly chosen problems. Verdict? To quote from the study: "We find no evidence of quantum speedup when the entire data set is considered and obtain inconclusive results when comparing subsets of instances on an instance-by-instance basis." This has, not surprisingly, generally been interpreted as a conspicuous failure for D-Wave.</blockquote>

 



But this analysis would not be complete without looking at more of D-Wave's advertising, would it?  





<blockquote>But where quantum computing is concerned, there always seems to be room for disagreement.</blockquote>

 



No. Where journalists are involved there always seems to be room for disagreement.  





<blockquote>The attitude in D-Wave's C-suite toward all this back-and-forth is, unsurprisingly, dismissive. "The people that really understand what we're doing aren't skeptical," says Brownell. Rose is equally calm about it; all that wrestling must have left him with a thick skin. "Unfortunately," he says, "like all discourse on the Internet, it tends to be driven by a small number of people that are both vocal and not necessarily the most informed."</blockquote>

 



Thats some real peer reviewed research Time has there. A D-Wave employee saying that "The people that really understand what we're doing aren't skeptical" really proves that their computer works.
