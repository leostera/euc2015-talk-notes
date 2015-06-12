@title What we talk about when we talk about distributed systems
@subtitle Distributed systems for the ikea family
@topic RabbitMQ
@author Alvaro Videla

# Intro

Distriburati <- hilarious.

A distributed system isone in which the failure of a computer you did
no even know existed can render your own computer unusable.

Distributed systems have a shitload of jargon.

"Many entities tying to solve a problem (nodes, processes)", by Mijel something.
French dude researching DS.

Uncertainty is what defines computation.

#  What to  read - Down the rabbit hole

1. Impossibility Resolver 
2. Leslie Lamport's Time clocks paper
3. ZooKeeper paper by Benjamin Reed
4. Diego Ongaro Understandbale Consesus Algorithm (Raft)
5. Lynch Distirbuted Algorithms,
6. Raynal, Concurrent Programming
7. Varela, Programming Distributed Computing System
8. Vukolic, Quorum systems, Replication by Charron, Cachi by Rodrigues

# Different Models

## Timing Model

* Synchronous model
Algorithms are executed in steps and you know how much it takes to execute it.
Not bound to the executing time.

* Async model (Living La Vida Loca model)
You know shit. Schedules could be fair or unfair, nothing is known in terms of
how long it would take to execute.

* Semi Sync model
Both top forms are unrealistic, so this one is more down to earth. Nancy Linch's book
is an interesting read.

## IPC

* Message Passing

* Shared Memory

## Failure Modes

* Crash-stop model
Crash and stop.

* Crash-recovery
Crash and try to recover.

* Omission faults
Forget about errors!

* Arbitrary Failures Mode (Byzantine)
Crazy talk returns.

## Safety

Communication links should not invent messages out of thin air.

FIFO queue will always take the first item. No items out of order.

## Liveness

A good thing will eventually happen.

A destination process eventually deliver the message.

# ALGORITHMS

## Impossibliity of Distributed Consesus with One Faulty Process (FLP)
@authors Fischer, Lynch, Paterson

Just don't implement a consensus algorithm.

## What's Consensus?

Paradigm of agreement problems. All of them are called "Consensus Problem".

Distributed database will have to agree on the commit data.

### Properties

* C-Termination: every correc process eventually decies on some value

* C-Validity: if a process decies V, then V was proposed by some process. 
All the state reached to some place where V was decided.

* C-Agreement: No two correct processes decide differently.
Only correct processes decides the same.

* C-Uniform Agreemenent: No two processes whether they are correct or not will decide
differently.
Everyone decides the same.


## When do we need consensus?

### Atomic Broadcast
FLP tells us that if consensus cannot be achieved, then atomic broascast or group
memebrship cannot be achieved.

### Failure Detactor
External processes that provide information about suspected processes.

They know when a process has crashed - Completeness Property.

Accuracy.

How do you know what's going on with your system when you know with all processes?

So Perfect Failure Detector are pretty useless.

### Eventually Accurate Failure Detectors

* Strong completeness: eventually it will know what processes crashed.


* Eventual Weak Accuracy: after some time it will correct itself "Hey, I was wrong."

Unreliable Failure Detecors for Reliable Distributed Systems - Deepak Chandra and Sam Toueg.

The paper describes lots of kinds of failure detectors that are really powerful and some others that are not.

# Quorums

If `F<N/2` processes fail by crashing, there is always at least one quorum of noncrashed processess in such system.

There's a series of books  that covers these, all curated by Nancy Lynch. There's one
just on quorums.

# Consistency

* Atomic Consistency (ineraizability)

* Sequential Consistency

* Causal consistency

# Some Books

Distributed Alrogithms for Message-Passing Systems: great book for erlang.


# Questions:

1. For someone who's diving into the distributed world and proper functional programming,
used to reading docs and blogs, What'd be a good way of pushing the technicality level as I read?
  Just DIVE INTO IT.
