---
title: "The Single Most Important Vocabulary in SRE"
date: 2022-10-16T00:00:00-07:00
tags: 
- sre
- reliability
- risk 
draft: false
---
Ever since I've started my career in software engineering, I've always been obsessed with one question in mind --- _what can go wrong?_

💭 What can go wrong with the code I just wrote?  
💭 What can go wrong with this framework I am using?  
💭 What happens when something "goes wrong"? Do I have a fallback mechanism? Kill switch?  

Sometimes I would even obsess over a single line of code written, thinking of all the ways that one line could break, trying to make it as bulletproof as possible. Of course, experience has taught me that any code written in itself is a liability and that there is no such thing as bulletproof code, but that doesn't mean we can't create safe software, or even better, safe systems that allow for safe software to operate in.

There are many people that have tried and still is defining what it means to be a Site Reliability Engineer, or what an SRE organization should do. If you really want the source of SRE, read the Google's [Site Reliability Engineering](https://sre.google/sre-book/table-of-contents/) book, or go listen to countless talks presented at SRECon over the years to hear many impassioned talks on this matter. SRE is that one field where we are not bound in particular by a single feature we ship, or that one new product that was just launched, etc. The identity can be blurry, and purpose, even blurrier. To be pedantic, you can literally define SRE as "ensuring reliability of a site" and move on.

But what does that even mean? How _do_ you define reliability?

Reliability is, to me at least, an incredibly vague term. Reliability can mean everything from ensuring your CI/CD processes are smooth and delivering software "reliably" (again, this differs per organization and how you want to define it), to sitewide disaster recovery processes, or more objective measurements such as SLIs, SLOs, SLAs and numerical targets to hit, and so much more --

-- and that's exactly the problem with the terminology, the fact that it's incredibly vague. It's just as vague as trying to define all kinds of programming paradigms and calling them generically "software engineering". 

To me the "R" in SRE always stood for one thing and one thing only.

***Risk.***

SREs, with risk oriented mindset, should be dedicated to the following:
- *Assessing risk of changes made to system*,  
be it configuration change to a cluster, a new deployment, bugs found, failure to scale up to meet demand in time, changes in security systems such as RBAC, new features being shipped that impacts existing parts of the system, so on and so forth,

- *Calculating the cost/benefit of that risk*,  
to answer the question "Is this change worth it?",

- *Predict outcomes of that risk*,  
by gaining best understanding of the consequences of assuming the risk to plan for probabilities of failure, rollback mechanisms, failover and other disaster recovery,

- *Protect rest of the system from the assumed risk*,  
by building reasonable guardrails as part of the system design from day 1 rather than safety being an afterthought, 

- *Maintain velocity of changes made to the system by always taking calculated risks*,  
by quantifying risks so you can calculate how much risk you can assume continuously to prevent a stagnating system, and understanding that you cannot have a 100% reliable system, but you can strive to be as near to that as much as possible.

Now, I think some folks definitely have a reaction when they hear the word "risk" - it is scary, it spells danger, it's unpleasant, and for most people, incredibly stress inducing. 

I'd like to argue that we should see risk in an opposite way.

Risk is the best vocabulary we've got to really, concretely define what it means to have a reliable system. Risk allows us to define reliability. Risk is the tool with which we can design reliability into a system. Risk is the paradigm with which we can reason about bounds of guaranteed reliability of a system. It is the most important tangibility we can apply to the concept of reliability.

And that's why risk should be the single most important vocabulary for any SRE.

Have a good day! 😊 - Ren
