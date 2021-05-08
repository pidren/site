+++
title = "3 Tips for fast debugging a distributed system that you've never seen before"
date = "2021-01-31"
tags = ["sre", "handbook", "distributed systems", "fast debugging"]
categories = [ "SRE Handbook" ]
author = "Ren Lee"
+++
_Imagine things are on fire and you only have a few minutes to figure out a distributed system. To make things more difficult, you’ve never seen this system before. You feel yourself tensing up - sweaty palms, cloudy mind - and you think, gosh I just wish I knew where to start!_

Here are 3 features commonly found in most distributed systems you can use to speed debug so that you don’t have to feel lost trying to understand all the details. The goal here is speed not depth especially during an emergency. Of course not all distributed systems follow these features but they tend to implement some variant or another.

#### 1) Separation of Roles: “coordinators” and “data managers”
I guarantee you’ll find this kind of an architecture very common, where a distributed system has separated roles between coordinator(s)/master(s) and components that are solely dedicated for doing something with data (transformation, processing, storage, etc). The job of the coordinators usually is to keep track of metadata with cluster state information (i.e. how many of the data managing components there are, and which one of them are alive).

A great example of this is in Kubernetes, where you have the cluster apiserver that acts as the “coordinator” that is aware of all the nodes (container hosts) and metadata for all of the workload running on the cluster.

Now, what does this tell you?

Say if the “coordinator” components are failing. Most of the time this disables you from effectively making changes on the distributed system (i.e. scaling up and down components, making configuration changes, etc). This is usually a far greater problem than a couple componentns dedicated for data management failing - a great analogy is if you have an airport, and the air traffic control is non-functional, it’s pretty difficult, if not impossible, for planes to land or depart. You can use knowledge of separation of roles to prioritize what to do first when multiple components are failing.

#### 2) Some kind of HA mechanism, usually via replicas
Now, how a system implements HA has wild amount of variations not to mention HA can mean very different things in different context/system you are looking at.

However, many distributed systems that directly deal with data processing and management, such as Elasticsearch, have a concept of sharding or replicas where the core idea is to have more than one copy of data within the system at any point in time.

This does not guarantee all copies of data is ready for access at all times, nor does it guarantee all copies of data will get updated at the same time - what’s important is that they’re eventually consistent. What’s most important is that eventually we have multiple copies of the data spread around the system that even if one copy fails, we have others to recover from or seemlessly continue operations on.

For example, for Elasticsearch the concept of “replicas” is best represented in primary and replica shards which house essentially the same subset of data for an index. Now, ignore the jargon - what’s most important here is that despite primary and replica shards housing essentially the same data, the primary is responsible for validating operations (i.e. write op) first, processing that data and writing it out first, then passing the message to replicas - so as you can see, there are minute points in time where primaries are updating replicas and may have different data. However, such updates are fast enough and eventually primaries and replicas have all of the same data. If a primary shard(s) fails, one (or more) of the replica shards are promoted as primary shard(s) and the world continues on in HA bliss. You can find such mechanism in most distributed systems, with some variation or another.

#### 3) Fast access data is in memory, long term is on disk
Now this last point isn’t strictly in relation to distributed sytems - in fact, keeping fast access data in memory and long term access on disk is found in monoliths, and existed even before microservices were a thing.

However, this is still important in that, say you took the ideas from Point 1 above and now know what kinds of components exist in your system. Knowing what kind of data each component stores in memory vs. on a persistent store or disk will tell you what kind of data is lost when the component fails - whatever in memory is gone, and whatever it managed to write to disk still exists (this is of course, assuming you didn’t lose whatever you’re using as persistent store).

This is very useful in cases of debugging lost data or lost operations - most of the time it’s because the data in memory didn’t get to flush to disk and got lost when the component failed. Of course, the discussion of “why would you keep so much state in memory” is another discussion but really, have you seen systems like Hbase?!

--

_May you speed debug with agility and style. :)_
