---
title: "Air France Flight 447 - an Operational failure"
date: 2022-11-06T00:00:00-07:00
tags:
- sre
- operations
- risk
- alert fatigue
- air france flight 447
draft: false
---

I came across an amazing piece of article over this weekend, one that provided an in-depth analysis of the tragedy of Air France Flight 447, ["The Long Way Down: The crash of Air France flight 447"](https://admiralcloudberg.medium.com/the-long-way-down-the-crash-of-air-france-flight-447-8a7678c37982). 

(Disclaimer: I am in no shape or form affiliated with this author or Medium - I simply think this was an astoundingly well done article and I encourage anyone that is interested in systems safety or aviations to have a read.)

There's no one word that can summarize how I felt as I was learning about this tragedy. Sadness? Yes. Shock? Absolutely. But more than anything, I could _relate_.

I could _relate_ beause this is the kind of scenario that Site Reliability Engineers can deeply relate to -- because what I saw was human, machine, and the glue between them, _operations_, _and_ how this combined components of a larger system devolved in a _systemic failure_.

This tragedy was a systemic failure where no one component was at fault to blame; a systemic failure where vicious feedback loop snowballed; a systemic failure that, at its core, the glue that was supposed to combine the two worlds - _operations_ - had failed both. And this failed operational excellence resulted in a fatal systemic failure that created one of the worst tragedies in aviation history.

## Operations is hard
In our software engineering industry, I often see operations treated as second class, or at least with some contempt because it deviates from pure coding - which seems regularly misguided. 

More than ever, as more and more software is provided as a managed service and more and more software is being applied to mission critical environments (i.e. health care, space flight, vehicular control plane), experts that understand how a given software works so deeply to the point of being able to not only manage risks involved with running the software, but be able to mitigate and rescue when that software fails are more in need and critical than ever. This does not diminish those whose main focus is to develop - this simply highlights the importance of the merged world between software that is written and expert operators of such software. One cannot exist without the other and one cannot succeed without the other.

All software - no matter how well unit, end to end, QA tested - have bugs. Even if one software doesn't have bugs, the sheer scale of permutations of different software with varying levels of quality with changing inputs/outputs will create scenarios that have never been tested before and cannot be tested in advance. This is prevalent in the microservices world and ubiquitous in our world where any given service is powered by global groups of services operating at unfathomable scales. Guaranteeing reliability in this chaotic web of software is the cornerstone of operational challenges - and what Site Reliability Engineering is constantly solving. 

Operations must achieve ***deterministic outcome*** where the given problem is ***non-deterministic by nature, mutates with time, and in an unbounded environment***. I'm not talking about NP-complete/NP-hard kinds of software challenges. I'm talking about the fact that operations is really, really, _really_ hard to get right. Why?

Bugs in software might be deterministic by itself, but non-deterministic when you put a lot of buggy software together. Interventions by human or even automated machines can be unpredictable. Over time, you have a non-deterministic system created by non-deterministic inputs where now the operator must find a very deterministic recovery outcome. It's about restoring order in chaos, and chaos that is dynamically changing with every passing second. And that's _hard_. 

To put into context, that deterministic outcome could be as simple as "available service" where non-deterministic environment is "we just found a bunch of security vulnerabilities in the system". Even harder, that deterministic outcome could be "keep the plane flying" where non-deterministic environment is "a plane's unknown airspeed in a tropical storm with faulty monitoring equipment". In both examples, the deterministic outcome is "restore back to working order".

So, _operations is really hard_.  
Achieving ***operational excellence*** is even harder.  

Now, going back to Air France Flight 447, I believe the biggest failure with Air France Flight 447 happened at operations. It wasn't the pilots, nor the faulty Pitot tubes, nor policy failure to ban aircrafts not yet retrofitted with Goodrich sensors to fly on hazardous routes, ... It was _operations_. It was dynamic failure to solve operational problems that was happening real time. The "bugs" in humans (pilots), the "bugs" in Pitot tubes (machine), the "bugs" in uncontrolled fallout from Normal Law to Alternate Law (machine), etc, all didn't matter nearly as much as the failure in operational excellence.

Now let's unpack that.

## Challenges to Operational Excellence 

### Alert Fatigue
As you're reading the article, you might've noticed all the lines from the transcript that illustrated how the alerting systems were constantly bombarding the pilots. The screaming "STALL! STALL!" alerts, that was preceeded by the constant "C-chord" tone. The overwhelming sensory exposure, and rising panic as the pilots were trying to respond to these alarms all the while working with faulty airspeed readings and other automated monitoring that were confusing at best.

Alert fatigue is a classic and well known problem in any operational setting. Ask any SRE or engineer that's ever been on oncall and they'll tell you how their blood pressure "spikes" when they receive a pager; awful if it's a critical level pager, and made even worse when you are bombarded by hundreds of pagers that constantly ram you with the no new information. 

Alert fatigue is perhaps one of the most dangerous situations in operations - receiving a constant stream of critical pagers completely disables the operator's critical thinking as the emotional response to overwhelming situations is to shut down and panic. You are trigger a human's natural fight or flight response. One can only learn to be able to control the panic through experience and cannot be taught. Even receiving a constant stream of non-critical pagers is dangerous in the fact that it makes the operator apathetic to the alert, which disables the operator from being able to respond quickly when there is a real present risk. All types of alert fatigue hinder the operators' ability to find the root cause and address it.

No human being, no matter how seasoned they are, can think clearly when experiencing alert fatigue. You can painfully see this play out between Pilot Robert and Pilot Bonin's increasingly dulled reactions to these alarms. Their minds shut down, entirely overwhelmed by sensory input. You'll more quickly reach an overwhelming level of panic the less experienced you are which makes the effects of alert fatigue far more dangerous and this is something you constantly see in new SREs or any operations folks. This leads to my next point --

### Emotional Control
In operations, especially during incidents, controlling emotional response is a critical skill. Notice how I mentioned control, not regulate. Control, because you must find effective methods of preventing panic overwhelming yourself and your team. Regulating is not enough.

What Captain Dubois could've done in the scenario as the most seasoned and senior member would be to prevent panic himself, and take control so that the other pilots would not further escalate into panic. On your operations teams, be it SRE or not, if you are one of the more senior members of the team, that is your job - to regulate panic when that big outage hits. It is your job to objectively assess data present, sort what you know and don't know, quickly make decisions, and regain control. Your job isn't to panic alongside everyone else. This is incredibly hard, of course. I personally also know this is very hard, but it must be done. If the most senior members panic you can be assured everyone else also will, with certainty.

Now, why was Captain Dubois, who was seasoned, senior, and perfectly capable of controlling the panic in this situation unable to do this? ---

### The Human Factor
--- because he had 1 hour of sleep. 

People in operations are ultimately still (as of today) humans with biological needs. 

This is why it's terrible practice to promote oncall shifts that span 24 hours, or shifts that stretch more than 1 week max a time. This is not because your team is incapable of waking up at the middle of the night (not to mention significant drop in quality of life) or because they're incompenent - it is because when it comes to operations, _stress is a limiting capacity_. All individual team members and team as a whole has max capacity for how much stress they can absorb, handle, and expel. Take away someone's restorative night of sleep, you reduce that capacity. Put someone on 24h shifts, you reduce that capacity. If you want your operations team to operate at max available capacity for stress, you must attend to their basic needs. And yes that includes sleep and something Captain Dubois sorely needed. 
### Training vs. Reality 
One of the biggest challenges in operations is that it is not possible to train for all scenarios. The article touches on this and how the pilots' simulations shallowly covers training in aircraft stalling scenarios because it is difficult to illustrate. 

Every SRE team and operations team must constantly train with disaster recovery scenarios, drills, and simulation exercises. But it is simply not possible to prepare for everything that can happen. The best you can do is help the team build the skills they'll need when faces with that new unknown, the "non-deterministic" failure. Nothing teaches better than experience.

In addition to the drills, I would say the best way to bridge the gap between training and reality is by ensuring oncall has a fallback mechanism, That is built through multiple layers of primary, secondary, and other layers of responses with a clear escalation policy. This helps engaging more experienced members to get involved at the right time and act as mentor to newer folks that are gaining experience.

### Over-reliance on Automation
Perhaps one of the most poignant point made in the article is how at the end of the day, all three pilots failed to revert to their basic flying skills to take control of the aircraft and fly the plane without automation assistance. When the plane fell out from Normal Law, to Alternate Law, then ultimately Direct Law, the pilots were not able to switch to traditional flying to regain control. 

I think we are an incredibly challenging place where the scale at which operators must manage necessitates the need for automation; but automation has itself has become complex and operators to become too reliant on automation so that there is significant risk in failing to recover from failure modes in automation in response to an underlying root failure in the system. We've added even more layers to failure complexity, and sometimes automation can be a curse rather than a tool. 

There will always be a need for operators to be able to run systems without automation assistance, with deep understanding of exactly what automation is replacing. Unfortunately, there's no easy way to approach this problem; training can only get you so far but it is something that experience and proper mentorship can teach over time when combined with continued training. This is also why, in the SRE world, it is imperative for all SREs to continue being great software engineers to best understand software as they evolve.

## Closing Thoughts
Reading about Air France Flight 447 was possibly one of the most distressing events I've ever learned - mostly because I would relate to so much of what had failed as an SRE. What we can learn from this tragedy is about who to blame but rather, how we can learn from it so that we can prevent such tragedies in the future. Especially as SREs, we can learn much from other industries that run critical systems - so that we also do not repeat it in the software world.

---
Have a good day! 😊 - Ren
