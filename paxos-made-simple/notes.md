Reading Notes of Paxos Made Simple
====

## Preset

The problem is about __reaching consensus between different processes__. And each process act as an "agent" which can communicate with other "agents" by sending messages.

The communication model is customary async, non-Byzantine model:

- Agent may fail, stuck, hang, restart randomly
- Messages can take arbitarily long to be recieved, can be duplicated, can be dropped, but message is not corrupted.

### Terms:

- Proposal: A message contains a value (and maybe a sequence number as well), sent by the proposers
- Proposer: A process that can send the proposal.
- Acceptor: A process that can accept the proposal. In P2, acceptor can accept multiple proposals.
- Learner: (Not same as raft learner). A process that can learn if a proposal is accepted or not.
- Chosen: When the majority set of acceptors accept a value in a proposal, we say the proposal is **chosen**.

## The Algorithm

We skip the complex description of the problem. The algorithm want to solve one problem. In a non-Byzantine network, how should we propose a value and make it accepted by all the processes(nodes)?

The algorithm is described as two-phase:

### Phase 1, Prepare

1. Before a proposer issue a proposal, it first generate a global monotonically increment number *N* (You can think this as a sequence number) and send the number to all acceptors.
2. All the acceptors will response to the message with two information
  a. A promise that it won't accept any proposal with number less than *N* (to avoid old ongoing proposals accepted)
  b. The highest proposal value less than N it has accepted.

This conclude the prepare phase. 


### Phase 2, Accept

1. If a majority of acceptor respond to the prepare request. It will send the accept request.
2. The accept request contains a sequence number same to the prepare request, which is *N*. And a value to propose.
3. The value in the request is either "the value of the highest numbered proposal among the responses" or "any value" if no one respond a value.
4. The proposer send the proposal to the set of responded acceptors.

After the accept request is sent out. The acceptor will accept the request if it doesn't recv any prepare request with sequence number larger than *N*.
If the acceptor accepts a proposal, it will notify the accept to (a set of)**learner**.

**Note: In order to guarantee the system makes progress, only ONE selected proposer can propose values at any time**

## Persistent State

In order to keep the algorithm maintain the invariant even in system failure such as machine restart, machine failure. The following information need to be stored in the persisted storage:

* Acceptor
  - Highest accepted proposal index (and value)
* Proposer
  - A disjoint set of numbers (different from each proposer).
  - The maximum sequence number *N* of the proposed proposal.
* Learner
  - Nothing

## My Questions.

1. 为什么我们需要 prepare 阶段? 不能让 acceptor 自己决定，当收到的 proposal Sequence Number <= 这个 acceptor 目前记录的最大值的时候, 直接丢弃这个 proposal 呢.
2. 为什么需要让 acceptor 回复自己记录的 value 给 proposer? proposer 明显可以通过 acceptor 在 accept 的阶段是否 response 了知道这个值有没有被 acceptor 选中 (chosen). 只要 proposer 自己记录一下哪个发出去的值被 majority acceptor 接受了就行?
3. Paxos 和 Raft 的本质区别是什么, 具体地来说， Raft Leader 和 Selected Proposer 的区别是什么?


