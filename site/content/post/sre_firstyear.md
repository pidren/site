+++
title = "5 Lessons after Surviving my First Year as an SRE"
date = "2021-01-31"
tags = ["sre", "handbook"]
categories = [ "SRE Handbook" ]
author = "Ren Lee"
+++
I recently completed my first year as an SRE on Cloudvision as a Service team with Arista Networks, which is our core customer facing cloud service product. Working with infrastructure, building automation, doing ops, and the rest of the rodeo is nothing new to me, but doing so as an SRE to a customer facing product was a completely new ball game with entirely different set of risks, costs, mindset, and business impact to think of.

So here are 5 musings about being an SRE from a fledgling that survived their first year - 

#### 1. Being comfortable with being uncomfortable
Now, more than ever before, I needed to keep cool under pressure especially if there were customer facing problems during an on-call period. “Keep calm” while thinking of SLAs and business impact while also trying to debug at lightning speed is name of the game.

Unfortunately, I don’t think there’s any shortcut to developing the thick skin to withstand pressure as well as gaining familiarity with the systems you’re managing, but it is also a skill that only grows with time.

#### 2. Macro debugging and Micro debugging at the same time
I think a core fundamental skill that SREs should have is the ability to “switch” between “macro” debugging vs. “micro” debugging.

Macro debugging involves understanding how different layers of the system interact - for example, a misconfiguration in a low level layer such as Zookeeper or Kafka would cause problems on all other dependent layers (eventually), but understanding such dependencies requires being able to digest the bigger picture.

Micro debugging would involve looking at what I’d call “down and dirty” details such as goroutine/heap dumps and looking at code directly to fix a problem, essentially a skill any software engineer would be comfortable with.

As an SRE being able to fluidly switch between macro vs. micro debugging is not only a skill that must be practiced and honed but also a privilege, since very few other teams have such access to the big picture.

#### 3. There’s no greater frustration than missing metrics
Primary tool of SREs is metrics.

Metrics are “eyes and ears” of the operation and without them, you become blind to whatever is happening in the system, and thus, cannot make informed judgments. Details into alerts/monitoring/metrics deserves their own post - to simplify, not having good coverage of metrics and proper monitoring systems to digest such metrics into graphs/alerts is the equivalent to driving a car with maybe half of the signals working, or missing a brake and maybe only some of the headlights turned on - essentially, you’re riding on luck, and nobody wants the risks involved with relying on something as unreliable as luck.

#### 4. Embracing Chaos
There is no such thing as 100% reliable systems.

No such thing as safe deployments.

Instead of trying to achieve perfection, which is sort of like a fool’s dream, it’s better to adopt superspeed-fast-hamster-on-coffee iterations and CI/CD, and operate with the mindset that things will fail first and foremost.

There’s no such thing as code/systems that will never fail, but graceful failures and quick recovery from degraded operation are real goals you can actually achieve.

#### 5. Is this customer visible or not?
Literally, the most important question you should ask to assess/predict risks with whatever change you are about to roll out.

