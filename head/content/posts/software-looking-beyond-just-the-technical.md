---
title: "Software: Looking Beyond Just the Technical"
date: 2022-10-01T00:00:00-07:00
tags: 
- management
- organization
- teams
- software
draft: false
---
(In this article I use the term "management" loosely to refer to any layer of management, not just managers.)

As a software engineer one of the most critical skillset is being able to discern which tool is the right one for the job that needs to be done. This deserves its own blog post, but in short a software engineer must know what language, features of a language, framework, and tool is the best to solve your problem.

As a manager, this critical skillset expands even further. Not only do you have the foundations of software engineer to know what toolsets are best suited for building a solution, you must be able to discern:
1. Does this project need to be built? Is this project the right project for the problem at hand (business need)
2. Who are the right people to solve this problem?
3. What is the right structure of people to solve this problem?
4. What resources will be needed for this project to be brought to completion?
5. What different teams will need to mesh together to solve this problem?
5. What performance criteria will be used to measure success fo this project? This includes both the solution built being functional and scalable, but also to measure speed of execution, team cohesion (this again, deserves its own post), etc.
... and many more.

Regardless of how long this list looks like for you, challenges at management level must involve looking at not just the technical, but the organizational. It is easy, especially coming from a deep software/engineering background, to ignore this other half when creating plans to solve problems that seem only like technical challenges. At any management level, any challenge being solved should assume it must tackle both sides of the world, the yin and yang. Software organizations are ultimately human, and you cannot solve a challenge without recognizing both for any given problem that needs to be solved. Any technical challenge has a hidden human and organization element to it, and it is management's task to figure that out. A management that looks at a problem purely technically run the risk of creating structures for long term solutions, fail to recognize human aspect that deeply affects implementation and success of large scale projects, or simply lose the opportunity to tape into something greater (speed, employee hapiness, creativity, etc).

In this post, I've picked two scenarios that can be common to see how each can be broken down into organizational and technical problems, and how both must be addressed to create a holistic solution. 

## Scenario #1: A project is failing to meet its deadline
Challenge: A project, set of features, or product launch are failing to meet expected deadline, or has failed to meet several deadlines. 

- Technical: Either the project design is too complex, engineers on the project do not have the technical knowledge (i.e. they have to build on a brand new platform or language out of their expertise), or both (ignoring other factors such as infrastructure challenges for now). Solve this by figuring out which one it is - if design is too complex, you can directly work with the team to simplify and prioritize design decisions being made; if it's the team's lack of technical expertise, provide them with training and tools that they use to learn the skills to work the project, and/or connect to the right mentors that already have the technical skillset (that would be yourself as well, limited by time that you have).

- Organizational: First, are the people working on the project meshing well? Time critical projects absolutely require people working on it to be able to work with each other; in other words, team cohesion is not an option, it is a requirement. Identify which engineers work well with who, and how. Are the right relationship dynamics on the team? If the team members dislike working with each other your project will never meet its deadline, let alone a tight deadline. Second, is there a clear leader for this project? A leader sets the tone, quality bar, and group dynamics for a team. Especially for mission critical projects you must have a leader to coordinate effort, boost morale, and keep the team on track. Such leaders are obviously rare in any organization and in much demand - some naturally grow into the role either by desire or by natural circumstances; but more often than not leaders need active cultivating by management. If a natural leader for a team does not exist, management must be hands on in cultivating candidates via direct mentorship, and showing them how to become a leader. A project without this minimal hierarchy will fail to meet desired deadlines and/or underperform. 

#### Why you need the holistic solution
Software projects should really be thought of missions. They are missions to accomplish a task, and a task can be producing a new project via a project. A mission will probably work with any set of people; but to achieve the best, you need to remember that at the end of the day it is humans building a software, and by nature, humans need to enjoy their fellow teammates they need to work with. A cohesive architectural design not only needs to be technically sound, but also need a bonded team to debate, agree, and implement various parts of a large project *together*. Such togetherness is only improved by a team that meshes well together and can operate in harmony with deep trust.

## Scenario #2: A feature area quality (i.e. bugs, test pass rates) are falling
Challenge: a set of features, or feature area, quality is falling. This is noticed by bugs seen by customers, internal metrics such as test pass rates are falling/consistently low/unpredictable, overall dissatisfaction with product area.

- Technical: Clear sign of technical debt. For brevity, technical debt can be broken down into 3 categories: bloated architectural design over time, testing gaps and/or broken test feedback loop to developers, and unreliable quality control. There's really no good way around this other than you need a long and hard look at (1) current architectural design and see if needs an evolution/redesign to accommodate for code/feature set growth, (2) triaging and spending the time and sweat to fix broken tests, (3) removing and rewriting tests that just may not work anymore. It requires work, and it is maintenance and technical debt that must be paid and there is no shortcut to this.

- Organizational: Ownership, and team morale. Start at the first step - is there a functional team behind this feature area? Who are the people on this team and what are each of their strengths? If yes, how is it organized? Is there a model for ownership, and expectation on quality, response times, and turnaround time standard for broken features and tests? Who is monitoring it (ideally, the owning team)? Second, tackle team morale. Is the team demotivated or feeling hopeless? Any team that is deflated will simply not have the energy to care or notice about quality standards. As a manager and with team leaders (you have them right?) you must motivate the team - even start with a simple "we can do this" all the way to iterative steps with clearly defined goals on quality bars to be improved (for example, work on clearly defining what success means such as "We'll raise pass rate from 90% to 91%", and avoid vague goals such as "we need to raise our pass rates!"). You need someone to believe that the team will succeed at improving as well as having the team itself also to believe they can be successful - clear team identity and a detailed roadmap will provide such a system.

#### Why you need the holistic solution
For this scenario, the technical challenge is obvious. What isn't obvious is the organizational. What organizational solution brings is continuity of implementing the technical solution. The technical solutions are a one time, emergency fix to failing quality, and the organizational fix brings the long term guarantee of continuing to iterate the best practices that would be the result of implementing the technical.

There are many other scenarios at which this conversation can continue, but the main takeaway is that management must approach challenges with both technical and organizational lens to be truly effective. You cannot solve challenges with purely organizational solutions, or purely technical solutions. Identifying both is the next step from a software engineer to someone in management, and success and products depend on this.

Have a good day! 😊 - Ren
