# Distributed Consensus Reading List 📚

Since its inception in the 1980s, [distributed consensus](https://en.wikipedia.org/wiki/Consensus_(computer_science)) has been the subject of extensive academic research. Whilst definitions vary, [distributed consensus](https://en.wikipedia.org/wiki/Consensus_(computer_science)) (or equivalently, [atomic broadcast](https://en.wikipedia.org/wiki/Atomic_broadcast)) most often refers to the problem of how to decide an ordered sequence of values between a set of distributed nodes. This can be used to implement an append-only replicated log which can be utilized either directly or indirectly, to provide services such as primary backup replication or [state machine replication](https://en.wikipedia.org/wiki/State_machine_replication). These abstractions can, in turn, form the building blocks of new abstractions, such as a distributed [key-value store](https://en.wikipedia.org/wiki/Key–value_database). Some consensus algorithms instead decide only a single value or a partially ordered sequence of values.
What unifies distributed consensus algorithms is the fact that they are always safe, regardless of delays and crashes (though they are not necessarily [Byzantine fault tolerance](https://en.wikipedia.org/wiki/Byzantine_fault)), and are guaranteed to make progress provided sufficient liveness. 

This is a long list of papers relating to distributed consensus. Many of the papers listed below fit into more than one section. However, for simplicity, each paper is listed only in the most relevant section. Where possible, open access links for each paper have been provided. Contributions via pull requests are welcome. 

⭐️ Influential papers - If you are looking for a starting point, a subset of the most influential papers on distributed consensus are highlighted using a yellow star. ⭐️

💎 Hidden gems - Papers which I personally love but are not as highly cited as the influential papers 💎

Key: acmdl = [ACM Digital Library](https://dl.acm.org)

The sections are as follows:
* [Distributed consensus](#distributed-consensus)
  * [Theoretical results](#theoretical-results)
  * [Surveys](#surveys)
  * [Algorithms for consensus](#algorithms-for-consensus)
  * [Consensus for specialist hardware](#consensus-for-specialist-hardware)
  * [Consensus for geo-distributed systems](#consensus-for-geo-distributed-systems)
  * [Consensus in production](#consensus-in-production)
  * [Implementations of consensus](#implementations-of-consensus)
  * [Evaluations of consensus](#evaluations-of-consensus)
  * [State machine replication](#state-machine-replication)
  * [Reconfiguration](#reconfiguration)
* [Related Topics](#related-topics)
  * [Weaker consistency models](#weaker-consistency-models)
  * [Failures](#failures)
  * [Clocks](#clocks)
  * [Correctness of consensus algorithms](#correctness-of-consensus-algorithms)
  * [Quorum systems](#quorum-systems)
  * [Byzantine fault tolerance](#byzantine-fault-tolerance)
  * [Alternative fault models in distributed consensus](#alternative-fault-models-in-distributed-consensus)
  * [Misc](#misc)
* [Future reading list](#future-reading-list)
  * [Blogroll](#blogroll)
  * [Reading lists](#reading-lists)
  * [Academic conferences & symposiums](#academic-conferences--symposiums)
  * [Academic workshops](#academic-workshops)
  * [Academic journals & magazines](#academic-journals--magazines)

## Distributed Consensus

### Theoretical results
This section lists theoretical results relating to distributed consensus.
* ⭐️ Time, Clocks, and the Ordering of Events in a Distributed System, CACM 1978 [[acmdl](https://dl.acm.org/citation.cfm?id=359563),[pdf](https://lamport.azurewebsites.net/pubs/time-clocks.pdf)]
  * Easily one of the most influential papers in distributed computing. Introduces the "happens-before" relation and [Lamport clocks](https://en.wikipedia.org/wiki/Lamport_timestamp).
* The implementation of reliable distributed multiprocess systems, Computer Networks 1978 [[pdf](https://www.microsoft.com/en-us/research/publication/implementation-reliable-distributed-multiprocess-systems/)]
  * Precursor to Paxos, notes on achieving fault-tolerance with some degree of clock synchronization.
* ⭐️ Impossibility of Distributed Consensus with One Faulty Process, JACM 1985 [[acmdl](https://dl.acm.org/citation.cfm?id=214121),[pdf](https://groups.csail.mit.edu/tds/papers/Lynch/jacm85.pdf)]
  * The famous FLP result, proving that distributed consensus algorithms need synchrony to guarantee progress.
* On the Minimal Synchronism Needed for Distributed Consensus, JACM 1987 [[acmdl](https://dl.acm.org/citation.cfm?id=7533),[pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.456.4362&rep=rep1&type=pdf)]
  * Follow up to the FLP result with some extra considerations
* Unreliable Failure Detectors for Reliable Distributed Systems, JACM 1996 [[acmdl](https://dl.acm.org/citation.cfm?id=226647),[pdf](https://www.cs.utexas.edu/~lorenzo/corsi/cs380d/papers/p225-chandra.pdf)]
* The Weakest Failure Detector for Solving Consensus, JACM 1996 [[acmdl](https://dl.acm.org/citation.cfm?id=234549),[pdf](http://www.cs.utexas.edu/~lorenzo/corsi/cs380d/papers/weakestfd.pdf)]
* Omega Meets Paxos: Leader Election and Stability without Eventual Timely Links, DISC 2005 [[acmdl](https://dl.acm.org/citation.cfm?id=2162336),[pdf](https://www.microsoft.com/en-us/research/wp-content/uploads/2005/09/paxos-leader.pdf)]
* Lower Bounds for Asynchronous Consensus, Distributed Computing 2006 [[acmdl](https://dl.acm.org/citation.cfm?id=3271328),[pdf](https://lamport.azurewebsites.net/pubs/lower-bound.pdf)]
* The Heard-Of Model: Computing in Distributed Systems with Benign Failures, Distributed Computing 2009 [[acmdl](https://dl.acm.org/citation.cfm?id=3271165),[pdf](https://infoscience.epfl.ch/record/109375/files/HO-TR-2007.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2016/02/09/the-heard-of-model/)
* Virtually Synchronous Methodology for Dynamic Service Replication, MS Tech report 2010 [[pdf](https://www.microsoft.com/en-us/research/wp-content/uploads/2010/11/vs-submit.pdf)]

### Surveys
This section lists surveys, tutorials, and systemization of knowledge papers covering distributed consensus algorithms.
* A Modular Approach to Fault-Tolerant Broadcasts and Related Problems, Tech Report 1994 [[acmdl](https://dl.acm.org/citation.cfm?id=866693),[pdf](http://csis.pace.edu/~marchese/CS865/Papers/hadzilacos_ps.ps)]
* How to Build a Highly Available System Using Consensus, WDAG 1996 [[acmdl](https://dl.acm.org/citation.cfm?id=675640),[pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.72.5429&rep=rep1&type=pdf)]
* Revisiting the PAXOS algorithm, WDAG 1997 [[acmdl](https://dl.acm.org/citation.cfm?id=675657),[pdf](https://groups.csail.mit.edu/tds/papers/DePrisco/paxos-tcs.pdf)]
* The ABCD’s of Paxos, PODC 2001 [[acmdl](https://dl.acm.org/citation.cfm?id=383969),[pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.595.4829&rep=rep1&type=pdf)]
* ⭐️ Paxos Made Simple, SIGACT News 2001 [[pdf](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf)]
  * Describes single-degree Paxos as well as Multi-Paxos for SMR
  * Is much more readable than the original Paxos paper
  * Featured in [the morning paper](https://blog.acolyer.org/2015/03/04/paxos-made-simple/)
* Deconstructing paxos, SIGACT News 2003 [[pdf](http://www.cs.utexas.edu/~lorenzo/corsi/cs380d/papers/deconstr_paxos.pdf),[acmdl](https://dl.acm.org/citation.cfm?id=637447)]
* Total order broadcast and multicast algorithms: Taxonomy and survey, CSUR 2004 [[acmdl](https://dl.acm.org/citation.cfm?id=1041682),[pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.110.6701&rep=rep1&type=pdf)]
* 💎 Vive La Difference: Paxos vs. Viewstamped Replication vs. Zab, TDSC 2005 [[pdf](https://www.cs.cornell.edu/fbs/publications/vivaLaDifference.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2015/03/11/vive-la-difference-paxos-vs-viewstamped-replication-vs-zab/)
* The Alpha of Indulgent Consensus, Comp Journal 2007 [[acmdl](https://dl.acm.org/citation.cfm?id=1188295),[pdf](https://infoscience.epfl.ch/record/89695/files/bxl046.pdf)]
* The Paxos Register, SRDS 2007 [[acmdl](https://dl.acm.org/citation.cfm?id=1308227),[pdf](http://www.cs.cornell.edu/lorenzo/papers/li07Paxos.pdf)]
* Classic Paxos vs. Fast Paxos: Caveat Emptor, HotDep 2007 [[acmdl](https://dl.acm.org/citation.cfm?id=1323158),[pdf](http://www.sysnet.ucsd.edu/sysnet/miscpapers/hotdep07.pdf)]
* Tutorial Summary: Paxos Explained from Scratch, OPODIS 2013 [[acmdl](https://dl.acm.org/citation.cfm?id=2696603),[pdf](http://www.ux.uis.no/~meling/papers/2013-paxostutorial-opodis.pdf)]
* 💎 Paxos Made Moderately Complex, CSUR 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2673577),[pdf](http://www.cs.cornell.edu/courses/cs7412/2011sp/paxos.pdf)]
* On the Parallels between Paxos and Raft, and how to Port Optimizations, PODC 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3331595),[pdf](http://mpaxos.com/pub/raft-paxos.pdf)]
* Paxos vs Raft: Have we reached consensus on distributed consensus?, PaPoC 2020 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3380787.3393681),[arxiv](https://arxiv.org/abs/2004.05074)]
* 60 Years of Mastering Concurrent Computing through Sequential Thinking, SIGACT News 2020 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3406678.3406690)]
* What's Live? Understanding Distributed Consensus, PODC 2021 [[acmdl](https://dl.acm.org/doi/10.1145/3465084.3467947),[arxiv](https://arxiv.org/abs/2001.04787)]
* SoK: A Generalized Multi-Leader State Machine Replication Tutorial, JSys 2021 [[pdf](https://mwhittaker.github.io/publications/bipartisan_paxos.pdf)]

### Algorithms for consensus
This section lists papers describing algorithms for distributed consensus. These papers tend to be theory papers (venues such as PODC, DISC, OPODIS) whereas the [Implementations of consensus](#implementations-of-consensus) section focuses on systems papers.
*  Another Advantage of Free Choice: Completely Asynchronous Agreement Protocols, PODC 1983 [[acmdl](https://dl.acm.org/doi/10.1145/800221.806707)]
    * As known as the Ben-Or algorithm
* Reliable communication in the presence of failures, TOCS 1987 [[acmdl](https://dl.acm.org/citation.cfm?id=7478),[pdf](https://pdos.csail.mit.edu/archive/6.824-2006/papers/isis87.pdf)]
* ⭐️ Consensus in the Presence of Partial Synchrony, JACM 1988 [[acmdl](https://dl.acm.org/citation.cfm?id=42283),[pdf](https://groups.csail.mit.edu/tds/papers/Lynch/jacm88.pdf)]
* Viewstamped Replication: A New Primary Copy Method to Support Highly-Available Distributed Systems, PODC 1988 [[acmdl](https://dl.acm.org/citation.cfm?id=62549),[pdf](http://pmg.csail.mit.edu/papers/vr.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2015/03/02/viewstamped-replication-a-new-primary-copy-method-to-support-highly-available-distributed-systems/)
* Efficient Message Ordering in Dynamic Networks, PODC 1996 [[acmdl](https://dl.acm.org/citation.cfm?id=248062),[pdf](http://citeseerx.ist.psu.edu/viewdoc/download;jsessionid=A396429A7FB80EE184CC3AFC78347A86?doi=10.1.1.27.6092&rep=rep1&type=pdf)]
* ⭐️ The Part-Time Parliament, TOCS 1998 [[acmdl](https://dl.acm.org/citation.cfm?id=279229),[pdf](https://lamport.azurewebsites.net/pubs/lamport-paxos.pdf)]
  * The original paper introducing Paxos
  * Featured in [the morning paper](https://blog.acolyer.org/2015/03/03/the-part-time-parliament/)
* Disk Paxos, DISC 2000 [[acmdl](https://dl.acm.org/citation.cfm?id=675967),[pdf](https://lamport.azurewebsites.net/pubs/disk-paxos.pdf)]
  * This paper describes how to replace acceptors in Paxos with disks
  * Each disk is divided into blocks, one for each proposer. Each proposer may only write to its own block and read from other blocks, which they do in each of the two usual Paxos phases
  * Each block contains the rough equivalent to last promised ballot number and last accepted proposal for the assigned proposer
* Specifying and Using a Partitionable Group Communication Service, TOCS 2001 [[acmdl](https://dl.acm.org/citation.cfm?id=377776&dl=ACM&coll=DL),[pdf](https://groups.csail.mit.edu/tds/papers/Lynch/TOCS.pdf)]
* Active Disk Paxos with infinitely many processes, PODC 2002 [[acmdl](https://dl.acm.org/citation.cfm?id=1146169),[pdf](https://groups.csail.mit.edu/tds/papers/Chockler/podc-02.pdf)]
  * This paper makes Disk Paxos more “Paxos like” by assuming the disks support more operations e.g. conditional write
  * ADP claims that Disk Paxos requires a fixed set of proposers and that ADP fixes this.
* Cheap Paxos, DSN 2004 [[acmdl](https://dl.acm.org/citation.cfm?id=1009745),[pdf](https://lamport.azurewebsites.net/pubs/web-dsn-submission.pdf)]
* Generalized Consensus and Paxos, Tech Report 2005 [[pdf](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-2005-33.pdf)]
  * Introduces the idea of deciding a partial ordering of values instead of a total ordering
* Fast Paxos, Distributed Computing 2006 [[pdf](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-2005-112.pdf)]
  * Variant of Paxos where proposers can bypass the leader by allowing multiple values to be proposed in the same ballot. This requires stronger quorums intersection, e.g. fast paxos needs 3/4 of acceptors (instead of a simple majority) to provide the same liveness guarantees as classic Paxos.
* Consensus on Transaction Commit, TODS 2006 [[acmdl](https://dl.acm.org/citation.cfm?id=1132867),[pdf](https://lamport.azurewebsites.net/video/consensus-on-transaction-commit.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2016/01/13/consensus-on-transaction-commit/)
* Multicoordinated Paxos, PODC 2007 [[acmdl](https://dl.acm.org/citation.cfm?id=1281150),[pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.94.8831&rep=rep1&type=pdf)]
  * Variant of Paxos which replaces the one leader with a group of leaders. Clients send operations to all leaders and they all propose values to the acceptors. Acceptors only accept a value if they have received proposals from a quorum of leaders. Similar to the non-equivocation phase in BFT. Liveness now does not depend on the leader.
* Stoppable Paxos, Tech Report 2008 [[pdf](https://www.microsoft.com/en-us/research/wp-content/uploads/2008/04/stoppableV9.pdf)]
* Yet Another Visit to Paxos, Tech report 2009 [[pdf](https://dominoweb.draco.res.ibm.com/reports/rz3754.pdf)]
* Dynamic atomic storage without consensus, JACM 2011 [[acmdl](https://dl.acm.org/citation.cfm?id=1944348),[pdf](https://dahliamalkhi.files.wordpress.com/2015/12/dynastore-podc2009.pdf)]
* Fast Genuine Generalized Consensus, SRDS 2011 [[acmdl](https://dl.acm.org/citation.cfm?id=2085374),[pdf](https://pages.lip6.fr/Marc.Shapiro/papers/FGGC-SRDS-2011.pdf)]
* 💎 Viewstamped Replication Revisited, Tech Report 2012 [[pdf](http://pmg.csail.mit.edu/papers/vr-revisited.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2015/03/06/viewstamped-replication-revisited/)
* On Collision-fast Atomic Broadcast, AINA 2014 [[pdf](https://infoscience.epfl.ch/record/100857/files/CFAbcastTR.pdf)]
* Paxos Quorum Leases: Fast Reads Without Sacrificing Writes, SOCC 2014 [[acmdl](https://dl.acm.org/citation.cfm?id=2671001),[pdf](https://www.cs.cmu.edu/~dga/papers/leases-socc2014.pdf)]
  * Extends the idea of master read leases to allow the master to promise to use a specified subset of acceptors in every majority quorum. Acceptors in this quorum can then serve reads locally.
  * Similar to master read leases, it relies on clock synchrony.
* Consus: Taming the Paxi, Unpublished 2016 [[arxiv](https://arxiv.org/abs/1612.03457)]
* Flexible Paxos: Quorum Intersection Revisited, OPODIS 2016 [[pdf](http://drops.dagstuhl.de/opus/volltexte/2017/7094/pdf/LIPIcs-OPODIS-2016-25.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2016/09/27/flexible-paxos-quorum-intersection-revisited/)
* 💎 CASPaxos: Replicated State Machines without logs, Unpublished 2018 [[arxiv](https://arxiv.org/pdf/1802.07000.pdf)]
* Fast Flexible Paxos: Relaxing Quorum Intersection for Fast Paxos, ICDCN 2021 [[arxiv](https://arxiv.org/abs/2008.02671)]
* Spire: A Cooperative, Phase-Symmetric Solution to Distributed Consensus, IEEE Access 2021 [[pdf](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9481103)]
  * Consensus algorithm which permits multiple proposals in the same round (similar to Fast Paxos) but uses two phases instead of larger quorums.
* Paxos Made Practical, Unpublished [[pdf](http://www.scs.stanford.edu/~dm/home/papers/paxos.pdf)]

### Consensus for specialist hardware
This section lists papers describing consensus algorithms using specialist hardware such as [SDN](https://en.wikipedia.org/wiki/Software-defined_networking), [IP-multicast](https://en.wikipedia.org/wiki/IP_multicast), or [RDMA](https://en.wikipedia.org/wiki/Remote_direct_memory_access).
* Ring Paxos: A high-throughput atomic broadcast protocol, DSN 2010 [[pdf](https://ieeexplore.ieee.org/document/5544272),[code](http://libpaxos.sourceforge.net/paxos_projects.php#ringpaxos)]
* Multi-Ring Paxos, DSN 2012 [[acmdl](https://dl.acm.org/citation.cfm?id=2354410.2355144),[pdf](https://ieeexplore.ieee.org/document/6263916)]
* NetPaxos: consensus at network speed, SOSR 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2774999),[pdf](https://mcanini.github.io/papers/netpaxos.sosr15.pdf)]
* Taming uncertainty in distributed systems with help from the network, Eurosys 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2741976),[pdf](http://www.cs.utexas.edu/falcon/papers/albatross-eurosys2015.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2015/05/05/taming-uncertainty-in-distributed-systems-with-help-from-the-network/)
* DARE: High-Performance State Machine Replication on RDMA Networks, HPDC 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2749267),[pdf](https://spcl.inf.ethz.ch/Research/Parallel_Programming/DARE/dare-TR.pdf)]
* Paxos Made Switch-y, CCR 2016 [[acmdl](https://dl.acm.org/citation.cfm?id=2935638),[pdf](https://www.sigcomm.org/sites/default/files/ccr/papers/2016/April/0000000-0000002.pdf)]
* Consensus in a Box: Inexpensive Coordination in Hardware, NSDI 2016 [[acmdl](https://dl.acm.org/citation.cfm?id=2930639),[pdf](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-istvan.pdf)]
* Distributed Consensus and Implications of NVM on Database Management Systems, ACM Queue 2016 [[acmdl](https://dl.acm.org/citation.cfm?id=2967618),[html](https://queue.acm.org/detail.cfm?id=2967618)]
  * Featured in [the morning paper](https://blog.acolyer.org/2016/09/28/distributed-consensus-and-the-implications-of-nvm-on-database-management-systems/)
* AllConcur: Leaderless Concurrent Atomic Broadcast, HPDC 2017 [[acmdl](https://dl.acm.org/citation.cfm?id=3078598),[pdf](https://spcl.inf.ethz.ch/Publications/.pdf/poke2017allconcur.pdf)]
* APUS: Fast and Scalable Paxos on RDMA, SoCC 2017 [[acmdl](https://dl.acm.org/citation.cfm?id=3128609),[pdf](https://i.cs.hku.hk/~heming/papers/socc17-apus.pdf)]
* When Raft Meets SDN: How to Elect a Leader and Reach Consensus in an Unruly Network, APNet 2017 [[acmdl](https://dl.acm.org/citation.cfm?doid=3106989.3106999),[pdf](https://conferences.sigcomm.org/events/apnet2017/papers/raft-zhang.pdf)]
* P4xos: Consensus as a Network Service, Tech Report 2018 [[pdf](http://web.inf.usi.ch/file/pub/105/p4xos.pdf)]
  * P4xos is also evaluated in The Case For In-Network Computing On Demand [[acmdl](https://dl.acm.org/citation.cfm?id=3303979),[pdf](https://www.inf.usi.ch/faculty/soule/pubs/eurosys2019.pdf),[code](https://github.com/P4xos/P4xos)]
* Derecho: Fast State Machine Replication for Cloud Services, TOCS 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3302258),[pdf](http://www.cs.cornell.edu/ken/derecho-tocs.pdf),[code](https://derecho-project.github.io)]
  * Derecho: Group Communication at the Speed of Light, Unpublished [[pdf](https://www.cs.cornell.edu/projects/Quicksilver/public_pdfs/Derecho-Protocols.pdf)]
  * Groups, Subgroups and Auto-Sharding in Derecho: A Customizable RDMA Framework for Highly Available Cloud Services, Unpublished [[pdf](https://pdfs.semanticscholar.org/5dc4/ac5ac578fae726adcc5776d2a277f09dd9b5.pdf?_ga=2.198677487.1756250239.1559555537-1469340531.1559555537)]
* NetChain: Scale-Free Sub-RTT Coordination, NSDI 2018 [[acmdl](https://dl.acm.org/citation.cfm?id=3307445),[pdf](https://www.usenix.org/system/files/conference/nsdi18/nsdi18-jin.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2018/04/30/netchain-scale-free-sub-rtt-coordination/)
* Kernel Paxos, SRDS 2018 [[pdf](https://www.inf.usi.ch/faculty/pedone/Paper/2018/2018SRDSa.pdf)]
* Partitioned Paxos via the Network Data Plane, Tech Report 2019 [[pdf](https://www.inf.usi.ch/faculty/soule/pubs/usi-tr-2019-01.pdf)]
* The Impact of RDMA on Agreement, PODC 2019 [[pdf](https://arxiv.org/abs/1905.12143)]
* HovercRaft: Achieving Scalability and Fault-tolerance for microsecond-scale Datacenter Services, Eurosys 2020 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3342195.3387545)]
* FLAIR: Accelerating Reads with Consistency-Aware Network Routing, NSDI 2020 [[acmdl](https://dl.acm.org/doi/10.5555/3388242.3388295),[pdf](https://www.usenix.org/conference/nsdi20/presentation/takruri)]
* Microsecond Consensus for Microsecond Applications, OSDI 2020 [[arxiv](https://arxiv.org/abs/2010.06288)]
* Odyssey: The Impact of Modern Hardware on Strongly-Consistent Replication Protocols, Eurosys 2021 [[acmdl](https://dl.acm.org/doi/10.1145/3447786.3456240), [pdf](https://homepages.inf.ed.ac.uk/vnagaraj/papers/eurosys21.pdf),[techreport](https://arxiv.org/abs/2103.14701),[thesis](https://vasigavr1.github.io/files/thesis.pdf)]

### Consensus for geo-distributed systems
This section covers papers describing consensus algorithms for WANs and/or geo-replicated systems. Many of these algorithms (such as [EPaxos](https://www.cs.cmu.edu/~dga/papers/epaxos-sosp2013.pdf)) are leaderless and decide a partial-ordering over values instead of the more traditional total-ordering approach.
* Mencius: Building Efficient Replicated State Machines for WANs, OSDI 2008 [[acmdl](https://dl.acm.org/citation.cfm?id=1855767),[pdf](https://www.usenix.org/legacy/event/osdi08/tech/full_papers/mao/mao.pdf)]
* Scalable Consistency in Scatter, SOSP 2011 [[acmdl](https://dl.acm.org/citation.cfm?id=2043559),[pdf](https://homes.cs.washington.edu/~tom/pubs/scatter.pdf)]
* MDCC: Multi-Data Center Consistency, Eurosys 2013 [[acmdl](https://dl.acm.org/citation.cfm?id=2465363),[pdf](http://mdcc.cs.berkeley.edu/mdcc.pdf)]
* There Is More Consensus in Egalitarian Parliaments, SOSP 2013 [[acmdl](https://dl.acm.org/citation.cfm?id=2517350),[pdf](https://www.cs.cmu.edu/~dga/papers/epaxos-sosp2013.pdf)]
  * This paper describes EPaxos, which realizes [Generalized Paxos](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-2005-33.pdf) and makes some further improvements (e.g. reducing the size of fast quorums by 1).
* Geo-replicated storage with scalable deferred update replication, DSN 2013 [[acmdl](https://dl.acm.org/citation.cfm?id=2515164),[pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.724.1706&rep=rep1&type=pdf)]
* Low-Latency Multi-Datacenter Databases using Replicated Commit, VLDB 2013 [[acmdl](https://dl.acm.org/citation.cfm?id=2536366),[pdf](http://www.vldb.org/pvldb/vol6/p661-mahmoud.pdf)]
* Be General and Don’t Give Up Consistency in Geo-Replicated Transactional Systems, OPODIS 2014 [[pdf](https://www.ssrg.ece.vt.edu/papers/opodis14-alvin.pdf)]
* CalvinFS: Consistent WAN Replication and Scalable Metadata Management for Distributed File Systems, FAST 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2750482.2750483),[pdf](https://www.usenix.org/system/files/conference/fast15/fast15-paper-thomson.pdf)]
* GlobalFS: A Strongly Consistent Multi-Site File System, SRDS 2016 [[pdf](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7794339)]
* Canopus: A Scalable and Massively Parallel Consensus Protocol, CoNEXT 2017 [[acmdl](https://dl.acm.org/citation.cfm?id=3143394),[pdf](https://cs.uwaterloo.ca/~bernard/Canopus.pdf)]
* Multileader WAN Paxos: Ruling the Archipelago with Fast Consensus, Tech report 2017 [[pdf](https://cse.buffalo.edu/tech-reports/2017-01.pdf)]
* WPaxos: Wide Area Network Flexible Consensus, Unpublished 2017 [[pdf](https://arxiv.org/abs/1703.08905)]
  * Related blog post, [Modelling Paxos performance in wide area](http://charap.co/modeling-paxos-performance-in-wide-area-part-3/)
* Speeding up Consensus by Chasing Fast Decisions, DSN 2017 [[pdf](https://arxiv.org/pdf/1704.03319.pdf)]  
  * Implements an optimization to EPaxos
* Leader Set Selection for Low-Latency Geo-Replicated State Machine, IEEE TPDS 2017 [[pdf](https://ieeexplore.ieee.org/document/7774985)]
* DPaxos: Managing Data Closer to Users for Low-Latency and Mobile Applications, SIGMOD 2018 [[acmdl](https://dl.acm.org/citation.cfm?id=3196928),[pdf](https://nawab.me/Uploads/Nawab_DPaxos_SIGMOD2018.pdf)]
* SDPaxos: Building Efficient Semi-Decentralized Geo-replicated State Machines, SoCC 2018 [[acmdl](https://dl.acm.org/citation.cfm?id=3267837),[pdf](https://www.microsoft.com/en-us/research/publication/sdpaxos-building-efficient-semi-decentralized-geo-replicated-state-machines/)]
* FleetDB: Follow-the-workload Data Migration for Globe-Spanning Databases, Tech report 2018 [[pdf](https://cse.buffalo.edu/tech-reports/2018-02.pdf)]
* Geographic State Machine Replication, SRDS 2018 [[pdf](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8613971)]
* Session Guarantees with Raft and Hybrid Logical Clocks, ICDCN 2019 [[acmdl](https://dl.acm.org/doi/pdf/10.1145/3288599.3288619)]
* Near-Optimal Latency Versus Cost Tradeoffs in Geo-Distributed Storage, NSDI 2020 [[pdf](https://www.usenix.org/system/files/nsdi20-paper-uluyol.pdf)]
* State-Machine Replication for Planet-Scale Systems, Eurosys 2020 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3342195.3387543),[arxiv](https://arxiv.org/abs/2003.11789)]
* Low-Latency Geo-Replicated State Machines with Guaranteed Writes, PaPoC 2020 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3380787.3393686)]
* EPaxos Revisited, NSDI 2021 [[pdf](https://www.usenix.org/system/files/nsdi21-tollman.pdf)]
* Efficient Replication via Timestamp Stability, Eurosys 2021 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3447786.3456236),[arxiv](https://arxiv.org/abs/2104.01142)]
  * Describes Tempo, a leaderless partial ordering protocol that uses timestamp ordering.
* Reducing the Latency of Dependent Operations in Large-Scale Geo-Distributed Systems, PhD Thesis 2021 [[pdf](https://uwspace.uwaterloo.ca/bitstream/handle/10012/17639/Yan_Xinan.pdf?sequence=1&isAllowed=y)]
* LEGOStore: A Linearizable Geo-Distributed Store Combining Replication and Erasure Coding, Preprint 2021 [[arxiv](https://arxiv.org/abs/2111.12009)]

### Consensus in production
This section lists papers describing experiences of deploying distributed consensus in production.
* ⭐️ The Chubby lock service for loosely-coupled distributed systems, OSDI 2006 [[acmdl](https://dl.acm.org/citation.cfm?id=1298487),[pdf](https://static.googleusercontent.com/media/research.google.com/en//archive/chubby-osdi06.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2015/02/13/the-chubby-lock-service-for-loosely-coupled-distributed-systems/)
* ⭐️ Paxos Made Live - An Engineering Perspective, PODC 2007 [[acmdl](https://dl.acm.org/citation.cfm?id=1281103),[pdf](https://www.cs.utexas.edu/users/lorenzo/corsi/cs380d/papers/paper2-1.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2015/03/05/paxos-made-live/)
* ⭐️ ZooKeeper: Wait-free coordination for Internet-scale systems, ATC 2010 [[acmdl](https://dl.acm.org/citation.cfm?id=1855840.1855851),[pdf](https://www.usenix.org/legacy/event/atc10/tech/full_papers/Hunt.pdf)]
    * Featured in [the morning paper](https://blog.acolyer.org/2015/01/27/zookeeper-wait-free-coordination-for-internet-scale-systems/)
* Windows Azure Storage: a highly available cloud storage service with strong consistency, SOSP 2011 [[acmdl](https://dl.acm.org/citation.cfm?id=2043571),[pdf](https://webcourse.cs.technion.ac.il/236802/Spring2018/ho/WCFiles/Azure_Cloud_Storage.pdf)]
* Megastore: Providing Scalable, Highly Available Storage for Interactive Services, CIDR 2011 [[pdf](http://cidrdb.org/cidr2011/Papers/CIDR11_Paper32.pdf)]
  * Megastore uses SMR with witnesses, replicas that participate in log replication but do not run a state machine and read-only replicas that only run a state machine. This paper seems to use an unusual definition of Multi-Paxos where each instance is district but the 1a/1b messages for slot i is piggybacked onto 2a2/b for slot i-1.  
* Zab: High-performance broadcast for primary-backup systems, DSN 2011 [[acmdl](https://dl.acm.org/citation.cfm?id=2056409),[pdf](https://knowably-attachments.s3.amazonaws.com/u/55b69a1ce4b00ab397d67250/7c8734d3cf02154499a9b3161ef9f575/Zab_2011.pdf)]
  * Widely utilized Apache licensed open source project written in Java [project website](https://zookeeper.apache.org)
  * [Apache Kafka](https://kafka.apache.org) uses Zookeeper, as well as its own replication protocol, by described [here](https://www.confluent.io/blog/distributed-consensus-reloaded-apache-zookeeper-and-replication-in-kafka/). This is no longer true.
  * Architecture is similar to Google's Chubby but unlike Chubby is described in detail and is open source
  * Writes are linearizable, reads may be stale
  * Note: calling sync before a write doesn't make it linearizable
  * Clients may have multiple outstanding requests, they will be handled FIFO
  * Uses primary-backup replication instead of state machine replication
  * Featured in [the morning paper](https://blog.acolyer.org/2015/03/09/zab-high-performance-broadcast-for-primary-backup-systems/)
* Large-scale cluster management at Google with Borg, Eurosys 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2741964),[pdf](https://pdos.csail.mit.edu/6.824/papers/borg.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2015/05/07/large-scale-cluster-management-at-google-with-borg/)
* PaxosStore: High-availability Storage Made Practical in WeChat, VLDB 2017 [[acmdl](https://dl.acm.org/citation.cfm?id=3137778),[pdf](http://www.vldb.org/pvldb/vol10/p1730-lin.pdf)]
* Bizur: A Key-value Consensus Algorithm for Scalable File-systems, Unpublished 2017 [[pdf](https://arxiv.org/pdf/1702.04242.pdf)]
* SLOG: Serializable, Low-latency, Geo-replicated Transactions, VLDB 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3360377),[pdf](http://www.vldb.org/pvldb/vol12/p1747-ren.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2019/09/04/slog/)
* CockroachDB: The Resilient Geo-Distributed SQL Database, ICMD 2020 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3318464.3386134)]
* Millions of Tiny Databases, NSDI 2020 [[pdf](https://www.usenix.org/system/files/nsdi20-paper-brooker.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2020/03/04/millions-of-tiny-databases/)
* Virtual Consensus in Delos, OSDI 2020 [[pdf](https://www.usenix.org/system/files/osdi20-balakrishnan.pdf)]
* Log-structured Protocols in Delos, SOSP 2021 [[pdf](https://maheshba.bitbucket.io/papers/delos-sosp2021.pdf)]

### Implementations of consensus
This section lists papers describing implementations of distributed consensus algorithms.
* Replication and fault-tolerance in the ISIS system, Tech Report 1985 [[acmdl](https://dl.acm.org/citation.cfm?id=866067),[pdf](https://ecommons.cornell.edu/handle/1813/6508)]
* The ISIS project: real experience with a fault tolerant programming system, OSR 1991 [[acmdl](https://dl.acm.org/citation.cfm?id=122133),[pdf](http://web.eecs.utk.edu/~mbeck/classes/Fall04-distrsys/p103-birman.pdf)]
* Replication in the Harp File System, SOSP 1991 [[acmdl](https://dl.acm.org/citation.cfm?id=121169),[pdf](http://www.pmg.csail.mit.edu/papers/harp.pdf)]
* Boxwood: Abstractions as the Foundation for Storage Infrastructure, OSDI 2004 [[acmdl](https://dl.acm.org/citation.cfm?id=1251262),[pdf](https://www.usenix.org/legacy/event/osdi04/tech/full_papers/maccormick/maccormick.pdf)]
* The Farsite Project: A Retrospective, OSR 2007 [[acmdl](https://dl.acm.org/citation.cfm?id=1243422),[pdf](https://www.microsoft.com/en-us/research/wp-content/uploads/2007/04/OSR2007-4aa.pdf)]
* Paxos for System Builders: An Overview, LADIS 2008 [[acmdl](https://dl.acm.org/citation.cfm?id=1529979),[pdf](http://www.cnds.jhu.edu/pub/papers/psb_ladis_08.pdf)]
* Using Paxos to Build a Scalable, Consistent, and Highly Available Datastore, VLDB 2011 [[acmdl](https://dl.acm.org/citation.cfm?id=1938549),[pdf](https://arxiv.org/pdf/1103.2408.pdf)]
* Paxos replicated state machines as the basis of a high-performance data store, NSDI 2011 [[acmdl](https://dl.acm.org/citation.cfm?id=1972472),[pdf](https://www.usenix.org/legacy/events/nsdi11/tech/full_papers/Bolosky.pdf)]
* Granola: Low-Overhead Distributed Transaction Coordination, ATC 2012 [[acmdl](https://dl.acm.org/citation.cfm?id=2342821.2342842),[pdf](https://www.usenix.org/system/files/conference/atc12/atc12-final118.pdf)]
* S-Paxos: Offloading the Leader for High Throughput State Machine Replication, SRDS 2012 [[acmdl](https://dl.acm.org/citation.cfm?id=2477529),[pdf](https://infoscience.epfl.ch/record/179912/files/2012_SPaxos-CameraReady.pdf)]
* Calvin: Fast Distributed Transactions for Partitioned Database Systems, SIGMOD 2012 [[acmdl](https://dl.acm.org/citation.cfm?id=2213838),[pdf](http://cs.yale.edu/homes/thomson/publications/calvin-sigmod12.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2019/03/29/calvin-fast-distributed-transactions-for-partitioned-database-systems/)
* Commodifying Replicated State Machines with OpenReplica, Tech report 2012 [[pdf](https://ecommons.cornell.edu/handle/1813/29009)]
* Optimizing Paxos with batching and pipelining, Theoretical Computer Science 2013 [[acmdl](https://dl.acm.org/citation.cfm?id=2514451),[pdf](https://infoscience.epfl.ch/record/189440/files/TCS.pdf)]
* Tango: Distributed data structures over a shared log, SOSP 2013 [[acmdl](https://dl.acm.org/citation.cfm?id=2522732),[pdf](http://www.cs.cornell.edu/~taozou/sosp13/tangososp.pdf)]
* CORFU: A Distributed Shared Log, TOCS 2013 [[acmdl](https://dl.acm.org/citation.cfm?id=2535930),[pdf](http://www.cs.yale.edu/homes/mahesh/papers/corfumain-final.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2017/05/02/corfu-a-distributed-shared-log/)
* Scalable State-Machine Replication, DSN 2014 [[acmdl](https://dl.acm.org/citation.cfm?id=2672426),[pdf](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6903591)]
* When Paxos Meets Erasure Code: Reduce Network and Storage Cost in State Machine Replication, HPDC 2014 [[acmdl](https://dl.acm.org/doi/10.1145/2600212.2600218)]
* ⭐️ In Search of an Understandable Consensus Algorithm (Extended Version), ATC 2014 [[acmdl](https://dl.acm.org/citation.cfm?id=2643666),[pdf](https://raft.github.io/raft.pdf)]
  * AKA the RAFT consensus paper
  * Implemented in [etcd](https://etcd.io), open sourced and widely utilized including by [kubernetes](https://kubernetes.io)
  * Implemented in [CockroachDB](https://www.cockroachlabs.com/docs/stable/), [Consul](https://www.consul.io) from [HashiCorp](https://www.hashicorp.com), [Atomix](https://atomix.io) and many other systems.
  * Featured in [the morning paper](https://blog.acolyer.org/2015/03/12/in-search-of-an-understandable-consensus-algorithm/)
* Consensus: Bridging Theory and Practice, PhD Thesis 2014 [[pdf](https://github.com/ongardie/dissertation)]
  * PhD thesis describing RAFT consensus in more detail
* Paxos made transparent, SOSP 2015 [[acmdl](https://dl.acm.org/citation.cfm?doid=2815400.2815427),[pdf](https://i.cs.hku.hk/~heming/papers/crane-sosp15.pdf)]
* Designing Distributed Systems Using Approximate Synchrony in Data Center Networks, NSDI 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2789774),[pdf](https://syslab.cs.washington.edu/papers/specpaxos-nsdi15.pdf)]
* No compromises: distributed transactions with consistency, availability, and performance, SOSP 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2815425),[pdf](https://pdos.csail.mit.edu/6.824/papers/farm-2015.pdf)]
* Building Consistent Transactions with Inconsistent Replication, SOSP 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2815404),[pdf](https://irenezhang.net/papers/tapir-sosp15.pdf)]
  * Weakly consistent key-val store with support for linearizability as requested
  * Geo-distributed performance is evaluated
  * Useful related blog post [Lessons learned from TAPIR(s)](https://irenezhang.net/blog/2015/04/02/tapir.html)
  * Featured in [the morning paper](https://blog.acolyer.org/2015/10/21/building-consistent-transactions-with-inconsistent-replication/)
* MetaSync: File Synchronization Across Multiple Untrusted Storage Services, ATC 2015 [[pdf](https://www.usenix.org/system/files/conference/atc15/atc15-paper-han.pdf),[acmdl](https://dl.acm.org/doi/10.5555/2813767.2813774)]
* Making Fast Consensus Generally Faster, DSN 2016 [[pdf](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7579738)]
* Azure Data Lake Store: A Hyperscale Distributed File Service for Big Data Analytics, SIGMOD 2017 [[acmdl](https://dl.acm.org/citation.cfm?id=3056100),[pdf](http://www.cs.ucf.edu/~kienhua/classes/COP5711/Papers/MSazure2017.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2017/07/04/azure-data-lake-store-a-hyperscale-distributed-file-service-for-big-data-analytics/)
* Leader or Majority: Why have one when you can have both? Improving Read Scalability in Raft-like consensus protocols, HotCloud 2017 [[pdf](https://www.usenix.org/system/files/conference/hotcloud17/hotcloud17-paper-arora.pdf),[acmdl](https://dl.acm.org/citation.cfm?id=3154594),[slides](https://www.usenix.org/sites/default/files/conference/protected-files/hotcloud17_slides_arora.pdf)]
* Bolt-On Global Consistency for the Cloud, SoCC 2018 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3267809.3267835),[pdf](https://web.eecs.umich.edu/~harshavm/papers/socc18.pdf)]
* Stable and Consistent Membership at Scale with Rapid, ATC 2018 [[pdf](https://www.usenix.org/system/files/conference/atc18/atc18-suresh.pdf)]
  * Uses Fast Paxos to decide on membership changes. Conflicts are rare as the proposed value is the output of a membership algorithm so proposers usually propose the same proposal.
  * Fast Paxos implementation is [here](https://github.com/lalithsuresh/rapid/blob/master/rapid/src/main/java/com/vrg/rapid/FastPaxos.java) and [here](https://github.com/lalithsuresh/rapid/blob/master/rapid/src/main/java/com/vrg/rapid/Paxos.java)
* The FuzzyLog: A Partially Ordered Shared Log, OSDI 2018 [[pdf](https://www.usenix.org/system/files/osdi18-lockerman.pdf)]
* Aegean: Replication beyond the client-server model, SOSP 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3359663)]
  * Also supports BFT
* Exploiting Commutativity For Practical Fast Replication, NSDI 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3323240),[pdf](https://www.usenix.org/system/files/nsdi19-park.pdf)]  
  * More details in [author's thesis](https://web.stanford.edu/~ouster/cgi-bin/papers/ParkPhD.pdf)
  * Featured in [the morning paper](https://blog.acolyer.org/2019/03/15/exploiting-commutativity-for-practical-fast-replication/)
* Unifying Consensus and Atomic Commitment for Effective Cloud Data Management, VLDB 2019 [[acmdl](https://dl.acm.org/doi/10.14778/3303753.3303765),[pdf](http://www.vldb.org/pvldb/vol12/p611-maiyya.pdf)]
* Linearizable Quorum Reads in Paxos, HotStorage 2019 [[pdf](https://www.usenix.org/system/files/hotstorage19-paper-charapko.pdf),[slides](https://www.usenix.org/sites/default/files/conference/protected-files/hotstorage19_slides_charapko.pdf)]
  * A two phase quorum read algorithm which does not require the leader and does not rely on bounded clock drift like read leases.
* RMWPaxos: Fault-Tolerant In-Place Consensus Sequences, Unpublished 2020 [[arxiv](https://arxiv.org/abs/2001.03362)]
* Bipartisan Paxos: A Modular State Machine Replication Protocol, Unpublished [[pdf](https://mwhittaker.github.io/publications/compartmentalized_bipartisan_paxos.pdf)]
* Scalog: Seamless Reconfiguration and Total Order in a Scalable Shared Log, NSDI 2020 [[pdf](https://www.usenix.org/system/files/nsdi20-paper-ding.pdf)]
* Hermes: A Fast, Fault-Tolerant and Linearizable Replication Protocol, ASPLOS 2020 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3373376.3378496),[arxiv](https://arxiv.org/abs/2001.09804)]
* PigPaxos: Devouring the communication bottlenecks in distributed consensus, ICMD 2020 [[arxiv](https://arxiv.org/abs/2003.07760),[acmdl](https://dl.acm.org/doi/10.1145/3448016.3452834)]
* CRaft: An Erasure-coding-supported Version of Raft for Reducing Storage Cost and Network Cost, FAST 2020 [[pdf](https://www.usenix.org/conference/fast20/presentation/wang-zizhong)]
* Scaling Replicated State Machines with Compartmentalization, VLDB 2021 [[pdf](https://mwhittaker.github.io/publications/compartmentalized_consensus.pdf)]
* Rabia: Simplifying State-Machine Replication Through Randomization, SOSP 2021 [[arxiv](https://arxiv.org/pdf/2109.12616.pdf)]
* Boki: Stateful Serverless Computing with Shared Logs, SOSP 2021 [[pdf](https://www.cs.utexas.edu/~zjia/boki-sosp21.pdf)]
  * Latest edition in the line of papers on shared totally-ordered logs: Tango, Corfu, vCorfu, Scalog, Delos
* Gossip Consensus, Middleware 2021 [[pdf](https://www.inf.usi.ch/faculty/pedone/Paper/2021/middleware2021b.pdf)]
  * Looks at using gossip to reduce communication overhead of Multi-Paxos. An unstructured version of PigPaxos/Canopus. 

### Evaluations of consensus
This section lists papers describing standalone evaluations of consensus algorithms.
* The Performance of Paxos in the Cloud, SRDS 2014 [[acmdl](https://dl.acm.org/citation.cfm?id=2707675.2707801),[pdf](https://www.cs.cornell.edu/projects/Quicksilver/public_pdfs/SRDS14.pdf)]
* Consensus in the Cloud: Paxos Systems Demystified, Tech report 2016 [[pdf](https://cse.buffalo.edu/tech-reports/2016-02.pdf)]
* Spectrum: A Framework for Adapting Consensus Protocols, Unpublished 2019 [[pdf](https://arxiv.org/abs/1902.05873)]
* Dissecting the Performance of Strongly-Consistent Replication Protocols, SIGMOD 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3319893),[pdf](https://dl.acm.org/ft_gateway.cfm?id=3319893&type=pdf)]
  * [Author's blog post](http://muratbuffalo.blogspot.com/2019/07/dissecting-performance-bottlenecks-of.html)
* Blockchains and Distributed Databases: a Twin Study [[arxiv](https://arxiv.org/abs/1910.01310)]
  * Performance anaylsis of 5 consensus systems, 3 non-byzantine algorithms (including etcd) and 2 byzantine consensus algorithms
* Scalable but Wasteful: Current State of Replication in the Cloud, HotStorage 2021 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3465332.3470882)]
  * Study of the efficiency (CPU utilization) of Multi-Paxos vs EPaxos, finding that EPaxos provides better throughput than Multi-Paxos at the cost of much worse efficiency.

### State machine replication
This section lists papers about the application of consensus to State Machine Replication (SMR/RSMs) and Linearizability.
* ⭐️ Implementing Fault-Tolerant Services Using the State Machine Approach: A Tutorial, CSUR 1990 [[acmdl](https://dl.acm.org/citation.cfm?id=98167),[pdf](https://www.cs.cornell.edu/fbs/publications/SMSurvey.pdf)]
* ⭐️ Linearizability: A Correctness Condition for Concurrent Objects, TOPLAS 1990 [[acmdl](https://dl.acm.org/citation.cfm?id=78972),[pdf](https://cs.brown.edu/~mph/HerlihyW90/p463-herlihy.pdf)]
* Implementing Linearizability at Large Scale and Low Latency, SOSP 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2815416),[pdf](https://web.stanford.edu/~ouster/cgi-bin/papers/rifl.pdf)]
* Cheap and Available State Machine Replication, ATC 2016 [[acmdl](https://dl.acm.org/citation.cfm?id=3026984),[pdf](https://www.usenix.org/system/files/conference/atc16/atc16_paper-shi.pdf)]
* Fine-Grained Replicated State Machines for a Cluster Storage System, NSDI 2020 [[pdf](https://www.usenix.org/system/files/nsdi20spring_liu-ming_prepub_0.pdf)]

### Reconfiguration
This section lists papers on reconfiguration & leader election.
* The SMART Way to Migrate Replicated Stateful Services, EuroSys 2006 [[acmdl](https://dl.acm.org/citation.cfm?id=1217946),[pdf](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/eurosys2006.pdf)]
* 💎 Vertical Paxos and Primary-Backup Replication, PODC 2009 [[acmdl](https://dl.acm.org/citation.cfm?id=1582783),[pdf](https://www.microsoft.com/en-us/research/wp-content/uploads/2009/05/podc09v6.pdf)]
* Reconfiguring a State Machine, SIGACT News 2010 [[acmdl](https://dl.acm.org/citation.cfm?id=1753191),[pdf](https://lamport.azurewebsites.net/pubs/reconfiguration-tutorial.pdf)]
* Dynamic Reconfiguration of Primary/Backup Clusters, ATC 2012 [[acmdl](https://dl.acm.org/doi/10.5555/2342821.2342860),[pdf](https://www.usenix.org/system/files/conference/atc12/atc12-final74.pdf)]
  * Describes [Zookeeper's approach to reconfiguration](https://zookeeper.apache.org/doc/r3.5.3-beta/zookeeperReconfig.html).
* Take me to your leader! Online Optimization of Distributed Storage Configurations, VLDB 2015 [[pdf](https://research.google/pubs/pub43999/)]
* Unbounded Pipelining in Dynamically Reconfigurable Paxos Clusters, Unpublished 2016 [[pdf](http://tessanddave.com/paxos-reconf-902f8b7.pdf)]
  * Related blog post, [UPaxos and primary-backup replication](https://davecturner.github.io/2017/09/18/upaxos-primary-backup.html)
* Matchmaker Paxos: A Reconfigurable Consensus Protocol, JSys 2021 [[pdf](https://mwhittaker.github.io/publications/matchmaker_paxos.pdf),[arxiv](https://arxiv.org/abs/2007.09468)]

## Related Topics

### Weaker consistency models
This section lists papers that discuss alternative consistency models to [linearizability](https://en.wikipedia.org/wiki/Linearizability) or systems that depend upon clocks for correctness.
* Leases: An Efficient Fault-Tolerant Mechanism for Distributed File Cache Consistency, SOSP 1989 [[acmdl](https://dl.acm.org/citation.cfm?id=74870),[pdf](https://web.stanford.edu/class/cs240/readings/89-leases.pdf)]
  * This paper introduced the idea of leases for distributed caches. This idea is used in master leases and read quorum leases.
* ⭐️ Towards Robust Distributed Systems, PODC 2000 [[acmdl](https://dl.acm.org/citation.cfm?id=343502),[pdf](https://people.eecs.berkeley.edu/~brewer/cs262b-2004/PODC-keynote.pdf)]
  * PODC keynote in which [Eric Brewer](https://en.wikipedia.org/wiki/Eric_Brewer_(scientist)) proposed the now infamous [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem).
* Chain replication for supporting high throughput and availability, OSDI 2004 [[acmdl](https://dl.acm.org/citation.cfm?id=1251261),[pdf](https://www.cs.cornell.edu/home/rvr/papers/OSDI04.pdf)]
* Dynamo: Amazon’s Highly Available Key-value Store, SOSP 2007 [[acmdl](https://dl.acm.org/citation.cfm?id=1294281),[pdf](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)]
* Bigtable: A Distributed Storage System for Structured Data, TOCS 2008 [[acmdl](https://dl.acm.org/citation.cfm?id=1365816),[pdf](https://static.googleusercontent.com/media/research.google.com/en//archive/bigtable-osdi06.pdf)]
* What consistency does your key-value store actually provide?, HotDep 2010 [[acmdl](https://dl.acm.org/citation.cfm?id=1924919),[pdf](https://www.usenix.net/legacy/events/hotdep10/tech/full_papers/Anderson.pdf)]
  * Offline consistency checking of key-value traces
* Cassandra - A Decentralized Structured Storage System, OSR 2010 [[acmdl](https://dl.acm.org/citation.cfm?id=1773922),[pdf](https://www.cs.cornell.edu/projects/ladis2009/papers/lakshman-ladis2009.pdf)]
  * Not discussed in the paper but Cassandra now uses Paxos for [lightweight transactions](https://docs.datastax.com/en/archived/cassandra/3.0/cassandra/dml/dmlLtwtTransactions.html).
* Benchmarking Cloud Serving Systems with YCSB, SoCC 2010 [[acmdl](https://dl.acm.org/citation.cfm?id=1807152),[pdf](https://www2.cs.duke.edu/courses/fall13/compsci590.4/838-CloudPapers/ycsb.pdf)]
  * Popular benchmarking tool for key-values stores
  * Actively maintained [open source project](https://github.com/brianfrankcooper/YCSB/wiki) with support for various data stores
* Spanner: Google’s Globally-Distributed Database, OSDI 2012 [[acmdl](https://dl.acm.org/citation.cfm?id=2387880.2387905),[pdf](https://static.googleusercontent.com/media/research.google.com/en//archive/spanner-osdi2012.pdf)]
  * Provides linearizability but it assumes a bounded clock drift
  * Google implements this using Truetime, GPS, and atomic clocks in their data centers instead of [NTP](https://en.wikipedia.org/wiki/Network_Time_Protocol).
  * Closed source but now available as a cloud service called [Cloud Spanner](https://cloud.google.com/spanner/).
* TAO: Facebook’s Distributed Data Store for the Social Graph, ATC 2013 [[acmdl](https://dl.acm.org/citation.cfm?id=2535468),[pdf](https://www.usenix.org/system/files/conference/atc13/atc13-bronson.pdf)]
* Eventual Consistency Today: Limitations, Extensions, and Beyond, ACM Queue 2013 [[acmdl](https://dl.acm.org/citation.cfm?id=2462076),[pdf](https://queue.acm.org/detail.cfm?id=2462076)]
* Quantifying eventual consistency with PBS, CACM 2014 [[acmdl](https://dl.acm.org/citation.cfm?id=2632792),[pdf](http://www.bailis.org/papers/pbs-vldbj2014.pdf)]
* Existential Consistency: Measuring and Understanding Consistency at Facebook, SOSP 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2815426),[pdf](http://sigops.org/s/conferences/sosp/2015/current/2015-Monterey/printable/240-lu.pdf)]
* Minimizing coordination in replicated systems, PaPoC 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2745955),[pdf](http://staff.ustc.edu.cn/~chengli7/papers/a8-Li.pdf)]
* Consistency in Non-Transactional Distributed Storage Systems, CSUR 2016 [[acmdl](https://dl.acm.org/citation.cfm?id=2926965),[pdf](http://www.vukolic.com/consistency-survey.pdf)]
* Just say NO to Paxos Overhead: Replacing Consensus with Network Ordering, OSDI 2016 [[acmdl](https://dl.acm.org/citation.cfm?id=3026914),[pdf](https://www.usenix.org/system/files/conference/osdi16/osdi16-li.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2016/12/08/just-say-no-to-paxos-overhead-replacing-consensus-with-network-ordering/)
* The many faces of consistency, DE 2016 [[pdf](http://sites.computer.org/debull/A16mar/p3.pdf)]
* Spanner, TrueTime & The CAP Theorem, Tech Report 2017 [[pdf](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45855.pdf)]
* Amazon Aurora: Design Considerations for High Throughput Cloud-Native Relational Databases, SIGMOD 2017 [[acmdl](https://dl.acm.org/citation.cfm?id=3056101)]
  * Related blog on [all things distributed](https://www.allthingsdistributed.com/2019/03/Amazon-Aurora-design-cloud-native-relational-database.html)
  * Featured in [the morning paper](https://blog.acolyer.org/2019/03/25/amazon-aurora-design-considerations-for-high-throughput-cloud-native-relational-databases/)
* Fine-grained consistency for geo-replicated systems, ATC 2018 [[pdf](https://www.usenix.org/system/files/conference/atc18/atc18-li_cheng.pdf)]
* Amazon Aurora: On Avoiding Distributed Consensus for I/Os, Commits, and Membership Changes, SIGMOD 2018 [[acmdl](https://dl.acm.org/citation.cfm?id=3183713.3196937)]
  * Featured in [the morning paper](https://blog.acolyer.org/2019/03/27/amazon-aurora-on-avoiding-distributed-consensus-for-i-os-commits-and-membership-changes/)
* Sharding the Shards: Managing Datastore Locality at Scale with Akkio, OSDI 2018 [[acmdl](https://dl.acm.org/citation.cfm?id=3291201),[pdf](https://www.usenix.org/system/files/osdi18-annamalai.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2018/11/05/sharding-the-shards-managing-datastore-locality-at-scale-with-akkio/)
* On mixing eventual and strong consistency: Bayou revisited, PODC 2019 [[arxiv](https://arxiv.org/abs/1905.11762),[pdf](https://dl.acm.org/citation.cfm?id=3331583)]
* Harmonia: Near-Linear Scalability for Replicated Storage with In-Network Conflict Detection, VLDB 2020 [[pdf](https://drkp.net/papers/harmonia-vldb20.pdf)]
  * Implemented on programmable switches
  * Comes with TLA+ spec in [tech report](https://arxiv.org/pdf/1904.08964.pdf)
* Strong and Efficient Consistency with Consistency-Aware Durability, FAST 2020 [[pdf](http://pages.cs.wisc.edu/~ag/cad.pdf)]
  * [talk/slides](https://www.usenix.org/conference/fast20/presentation/ganesan)
* Regular Sequential Serializability and Regular Sequential Consistency, SOSP 2021 [[pdf](https://arxiv.org/pdf/2109.08930.pdf)]
  * New consistency models which are invariant equivalent to linearizability.

### Failures
This section lists papers that analyze and/or handle real-world failures of distributed systems.
* Understanding Network Failures in Data Centers: Measurement, Analysis, and Implications, SIGCOMM 2011 [[acmdl](https://dl.acm.org/citation.cfm?id=2018477),[pdf](http://conferences.sigcomm.org/sigcomm/2011/papers/sigcomm/p350.pdf)]
* The Network is Reliable: An informal survey of real-world communications failures, ACM Queue 2014 [[acmdl](https://dl.acm.org/citation.cfm?id=2655736),[pdf](https://queue.acm.org/detail.cfm?id=2655736)]
* What Bugs Live in the Cloud? A Study of 3000+ Issues in Cloud Systems, SOCC 2014 [[acmdl](https://dl.acm.org/citation.cfm?id=2670986),[pdf](https://ucare.cs.uchicago.edu/pdf/socc14-cbs.pdf)]
* All File Systems Are Not Created Equal: On the Complexity of Crafting Crash-Consistent Applications, OSDI 2014 [[acmdl](https://dl.acm.org/citation.cfm?id=2685082),[pdf](https://www.usenix.org/system/files/conference/osdi14/osdi14-paper-pillai.pdf)]
* Gray Failure: The Achilles’ Heel of Cloud-Scale Systems, HotOS 2017 [[acmdl](https://dl.acm.org/doi/10.1145/3102980.3103005)]
    * [Interested related talk by Jon Currey](https://www.hashicorp.com/resources/failure-detection-in-the-era-of-gray-failures)
* Redundancy Does Not Imply Fault Tolerance: Analysis of Distributed Storage Reactions to Single Errors and Corruptions, FAST 2017 [[acmdl](https://dl.acm.org/citation.cfm?id=3129648),[pdf](https://www.usenix.org/system/files/conference/fast17/fast17-ganesan.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2017/03/08/redundancy-does-not-imply-fault-tolerance-analysis-of-distributed-storage-reactions-to-single-errors-and-corruptions/)
* An Analysis of Network-Partitioning Failures in Cloud Systems, OSDI 2018 [[acmdl](https://dl.acm.org/doi/10.5555/3291168.3291173),[pdf](https://cs.uwaterloo.ca/~amsalqur/neat/NEAT-OSDI18.pdf)]
* CrashTuner: Detecting Crash-Recovery Bugs in Cloud Systems via Meta-Info Analysis, SOSP 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3359645)]
* The Inflection Point Hypothesis: A Principled Debugging Approach for Locating the Root Cause of a Failure, SOSP 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3359650)]
* Toward a Generic Fault Tolerance Technique for Partial Network Partitioning, OSDI 2020 [[pdf](https://www.usenix.org/system/files/osdi20-alfatafta.pdf)]
* Tolerating Slowdowns in Replicated State Machines using Copilots, OSDI 2020 [[pdf](https://www.usenix.org/system/files/osdi20-ngo.pdf)]
* Metastable Failures in Distributed Systems, HotOS 2021 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3458336.3465286)]
* Immunizing Systems from Distant Failures by Limiting Lamport Exposure, HotNets 2021 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3484266.3487387)]

### Clocks
The liveness of distributed consensus depends on some degree of clock synchronization. The following section lists papers on the topic of clock synchronization.
* IEEE Standard for a Precision Clock Synchronization Protocol for Networked Measurement and Control Systems, Standard 1588-2008 [[ieee](https://ieeexplore.ieee.org/document/4579760)]
* Globally Synchronized Time via Datacenter Networks, SIGCOMM 2016 [[acmdl](https://dl.acm.org/doi/10.1145/2934872.2934885),[pdf](http://fireless.cs.cornell.edu/publications/dtp_sigcomm16.pdf)]
* Exploiting a Natural Network Effect for Scalable, Fine-grained Clock Synchronization, NSDI 2018 [[acmdl](https://dl.acm.org/doi/10.5555/3307441.3307449),[pdf](https://www.usenix.org/conference/nsdi18/presentation/geng)]
* Sundial: Fault-tolerant Clock Synchronization for Datacenters, OSDI 2020 [[pdf](https://www.usenix.org/system/files/osdi20-li_yuliang.pdf)]
  * [Useful write up by Aleksey Charapko](http://charap.co/reading-group-sundial-fault-tolerant-clock-synchronization-for-datacenters/)

### Correctness of consensus algorithms
This section lists papers on proving or testing the correctness of consensus algorithms.
* Specifying Systems: The TLA+ Language and Tools for Hardware and Software Engineers, Book 2002 [[acmdl](https://dl.acm.org/citation.cfm?id=579617),[pdf](https://lamport.azurewebsites.net/tla/book-02-08-08.pdf),[website](https://lamport.azurewebsites.net/tla/book.html),[amazon](https://www.amazon.com/Specifying-Systems-Language-Hardware-Engineers/dp/032114306X)]
  * Directory of TLA+ specs, including many for consensus algorithms [TLA+ Examples](https://github.com/tlaplus/Examples)
* I Do Declare: Consensus in a Logic Language, NetDB 2009 [[pdf](https://dsf.berkeley.edu/papers/netdb09-idodeclare.pdf)]
  * Paxos implementation in a datalog like [logic language](https://en.wikipedia.org/wiki/Logic_programming).
* A Proof of Correctness for Egalitarian Paxos, Tech report 2013 [[pdf](http://www.cs.cmu.edu/~imoraru/epaxos/tr.pdf)]
* Verdi: A framework for implementing and formally verifying distributed systems, PLDI 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2737958),[pdf](https://homes.cs.washington.edu/~ztatlock/pubs/verdi-wilcox-pldi15.pdf)]
* IronFleet: Proving Practical Distributed Systems Correct, SOSP 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2815428),[pdf](http://sigops.org/s/conferences/sosp/2015/current/2015-Monterey/printable/250-hawblitzel.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2015/10/15/ironfleet-proving-practical-distributed-systems-correc/)
* Lineage-driven Fault Injection, SIGMOD 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2723711),[pdf](https://people.ucsc.edu/~palvaro/molly.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2015/03/26/lineage-driven-fault-injection/)
* How Amazon web services uses formal methods, CACM 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2699417),[html](https://cacm.acm.org/magazines/2015/4/184701-how-amazon-web-services-uses-formal-methods/fulltext)]
* PSYNC: A partially synchronous language for fault-tolerant distributed algorithms, POPL 2016 [[acmdl](https://dl.acm.org/citation.cfm?id=2837650),[pdf](https://www.di.ens.fr/~cezarad/popl16.pdf)]
  * Featured in [the morning paper](https://blog.acolyer.org/2016/02/01/psync/)
* Ivy: safety verification by interactive generalization, PLDI 2016 [[acmdl](https://dl.acm.org/citation.cfm?id=2908080.2908118),[pdf](http://www.cs.tau.ac.il/~odedp/pldi16-paper228.pdf),[code](http://apanda.github.io/ivy/)]
* Brief Announcement: A Family of Leaderless Generalized-Consensus Algorithms, PODC 2016 [[acmdl](https://dl.acm.org/citation.cfm?id=2933072),[pdf](https://www.losa.fr/2016_podc.pdf)]
  * TLA+ specs are [online](https://www.losa.fr/research/leaderless/)
* Paxos Made EPR: Decidable Reasoning about Distributed Protocols, OOPSLA 2017 [[acmdl](https://dl.acm.org/citation.cfm?doid=3152284.3140568),[pdf](https://www.cs.tau.ac.il/~odedp/paxos-made-epr-oopsla17.pdf)]
* Growing a protocol, HotCloud 2017 [[acmdl](https://dl.acm.org/citation.cfm?id=3154593),[pdf](https://www.usenix.org/conference/hotcloud17/program/presentation/ramasubramanian)]
  * Featured in [the morning paper](https://blog.acolyer.org/2017/08/23/growing-a-protocol/)
* Teaching Rigorous Distributed Systems With Efficient Model Checking, EuroSys 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3303947),[pdf](https://homes.cs.washington.edu/~mernst/pubs/dslabs-eurosys2019.pdf)]
  * Describes DSLabs, an alternative to TLA+, for model checking distributed protocols.
  * Featured in [the morning paper](https://blog.acolyer.org/2019/04/17/teaching-rigorous-distributed-systems-with-efficient-model-checking/)
* FlyMC: Highly Scalable Testing of Complex Interleavings in Distributed Systems, Eurosys 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3303986),[pdf](https://ucare.cs.uchicago.edu/pdf/eurosys19-flyMC.pdf)]  
* Proving the Correctness of Disk Paxos in Isabelle/HOL, Unpublished 2019 [[pdf](https://www.isa-afp.org/browser_info/current/AFP/DiskPaxos/outline.pdf)]
* I4: Incremental Inference of Inductive Invariants for Verification of Distributed Protocols, SOSP 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3359651)]
  * [Source code online](https://github.com/GLaDOS-Michigan/I4)
* Scaling symbolic evaluation for automated verification of systems code with Serval, SOSP 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3359641)]
* WormSpace: A Modular Foundation for Simple, Verifiable Distributed Systems, SoCC 2019 [[acmdl](https://dl.acm.org/doi/10.1145/3357223.3362739)]
* Towards an Automatic Proof of Lamport’s Paxos, FMCAD 2021 [[arxiv](https://arxiv.org/abs/2108.08796)]
  * Automatic inference of Paxos's inductive invariants
* DistAI: Data-Driven Automated Invariant Learning for Distributed Protocols, OSDI 2021 [[pdf](https://www.usenix.org/system/files/osdi21-yao.pdf)]
  * Next step in the inference of inductive invariants for distributed protocols, following on from Ivy and I4. Still does not support Paxos.
* Much ADO about Failures: A Fault-Aware Model for Compositional Verification of Strongly Consistent Distributed Systems, OOPSLA 2021 [[pdf](https://flint.cs.yale.edu/flint/publications/ado-tr.pdf)]
  * Formal proofs of distributed protocols in Coq including Multi-Paxos, produces verified C executables.

### Quorum systems
This section lists papers on quorum systems.
* ⭐️ A Majority Consensus Approach to Concurrency Control for Multiple Copy Databases, TODS 1979 [[acmdl](https://dl.acm.org/citation.cfm?id=320076),[pdf](http://csis.pace.edu/~marchese/CS865/Papers/p180-thomas.pdf)]
* ⭐️ Weighted Voting for Replicated Data, SOSP 1979 [[acmdl](https://dl.acm.org/citation.cfm?id=806583),[pdf](http://pages.cs.wisc.edu/~remzi/Classes/739/Fall2015/Papers/gifford79.pdf)]
* How to Assign Votes in a Distributed System, JACM 1985 [[acmdl](https://dl.acm.org/citation.cfm?id=4223),[pdf](https://www.cs.purdue.edu/homes/bb/cs542-17Spr/How%20to%20assign%20Votes-JACM-garcia-molina.pdf)]
* A √N algorithm for mutual exclusion in decentralized systems, TOCS 1985 [[acmdl](https://dl.acm.org/citation.cfm?id=214445),[pdf](https://cseweb.ucsd.edu/classes/wi09/cse223a/p145-maekawa.pdf)]
* A Quorum-Consensus Replication Method for Abstract Data Types, TOCS 1984 [[acmdl](https://dl.acm.org/doi/10.1145/6306.6308)]
* The Reliability of Voting Mechanisms, TC 1987 [[acmdl](https://dl.acm.org/citation.cfm?id=32406),[pdf](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=1676860)]
* The Tree Quorum Protocol: An Efficient Approach for Managing Replicated Data, VLDB 1990 [[pdf](http://www.vldb.org/conf/1990/P243.PDF)]
* An Efficient and Fault-tolerant Solution for Distributed Mutual Exclusion, TOCS 1991 [[acmdl](https://dl.acm.org/citation.cfm?doid=103727.103728),[pdf](https://users.soe.ucsc.edu/~scott/courses/Fall11/221/Papers/Sync/agrawal-tocs91.pdf)]
* Hierarchical Quorum Consensus: A New Algorithm for Managing Replicated Data, TC 1991 [[acmdl](https://dl.acm.org/citation.cfm?id=126154),[pdf](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=83661)]
* The Generalized Tree Quorum Protocol: An Efficient Approach for Managing Replicated Data, TODS 1992 [[acmdl](https://dl.acm.org/citation.cfm?id=146935),[pdf](https://www.cs.rice.edu/~alc/old/comp520/papers/generalized-tree.pdf)]
* The Grid Protocol: A High Performance Scheme for Maintaining Replicated Data, TKDE 1992 [[acmdl](https://dl.acm.org/citation.cfm?id=627546),[pdf](https://ieeexplore.ieee.org/abstract/document/180609)]
* Enhancing concurrency and availability for database systems, Thesis [[acmdl](https://dl.acm.org/doi/10.5555/143912)]
* The Availability of Quorum Systems, Tech report 1993 [[acmdl](https://dl.acm.org/citation.cfm?id=903705),[pdf](https://pdfs.semanticscholar.org/ab7d/30f7a808173bc305d679262f9838869cb681.pdf)]
* Crumbling Walls: A Class of Practical and Efficient Quorum Systems, PODC 1995 [[acmdl](https://dl.acm.org/citation.cfm?id=224978),[pdf](https://link.springer.com/article/10.1007/s004460050027)]
* Evaluating quorum systems over the Internet, PODC 1996 [[acmdl](https://dl.acm.org/doi/10.1145/248052.248125)]
* An Adaptive Data Replication Algorithm, TODC 1997 [[acmdl](https://dl.acm.org/doi/10.1145/249978.249982)]
* 💎 The Load, Capacity, and Availability of Quorum Systems, SIAM 1998 [[acmdl](https://dl.acm.org/citation.cfm?id=279082.279096),[pdf](https://epubs.siam.org/doi/pdf/10.1137/S0097539795281232)]
  * Featured in [the morning paper](https://blog.acolyer.org/2016/10/03/the-load-capacity-and-availability-of-quorum-systems/)
* Optimal availability quorum systems: Theory and practice, IPL 1998 [[pdf](https://www.eng.tau.ac.il/~yash/ipl98.pdf)]
* Are Quorums an Alternative for Data Replication?, TODS 2003 [[acmdl](https://dl.acm.org/doi/10.1145/937598.937601)]
* Coterie Availability in Sites, DISC 2005 [[acmdl](https://dl.acm.org/citation.cfm?id=2162323),[pdf](https://link.springer.com/chapter/10.1007/11561927_3)]
* The virtue of dependent failures in multi-site systems, HotDep 2005 [[acmdl](https://dl.acm.org/citation.cfm?id=1973401),[pdf](https://pdfs.semanticscholar.org/720c/1b5222bc91e8238b1ced2991232b9742dedc.pdf)]
* Read-Write Quorum Systems Made Practical, PaPoC 2021 [[pdf](https://arxiv.org/abs/2104.04102)]


### Byzantine fault tolerance
This section lists papers on [Byzantine Fault Tolerance](https://en.wikipedia.org/wiki/Byzantine_fault) (BFT), often used as the basis of permissioned blockchains.
* ⭐️ Reaching Agreement in the Presence of Faults, JACM 1980 [[pdf](https://lamport.azurewebsites.net/pubs/reaching.pdf)]
  * Considered to be the first proof that Byzantine agreement requires at least 3f+1 nodes to tolerate f faults.
* ⭐️ The Byzantine Generals Problem, TPLS 1982 [[acmdl](https://dl.acm.org/doi/10.1145/357172.357176),[pdf](https://www.microsoft.com/en-us/research/uploads/prod/2016/12/The-Byzantine-Generals-Problem.pdf)]
  * Famous Lamport paper which popularized the Byzantine agreement problem
* Asynchronous consensus and broadcast protocols, JACM 1985 [[acmdl](https://dl.acm.org/citation.cfm?id=214134),[pdf](https://zoo.cs.yale.edu/classes/cs426/2013/bib/bracha85asynchronous.pdf)]
  * Another proof that crash fault tolerance requires 2f+1 nodes and BFT requires 3f+1 nodes.
* Byzantine quorum systems, STOC 1997 [[acmdl](https://dl.acm.org/citation.cfm?id=258650),[pdf](https://dahliamalkhi.files.wordpress.com/2015/12/byzquorums-distcomputing1998.pdf)]
  * Similar to the [Naor and Wool paper on the load, capacity, and availability of quorum systems](https://epubs.siam.org/doi/pdf/10.1137/S0097539795281232) but with Byzantine faults.
* The load and availability of Byzantine quorum systems, PODC 1997 [[acmdl](https://dl.acm.org/doi/abs/10.1145/259380.259450)]
  * Follow up to Byzantine quorum systems paper.
* ⭐️ Practical Byzantine Fault Tolerance, OSDI 1999 [[acmdl](https://dl.acm.org/citation.cfm?id=296824),[pdf](http://pmg.csail.mit.edu/papers/osdi99.pdf)]
  * Considered to be the first practical BFT-SMR protocol.
* Separating agreement from execution for byzantine fault tolerant services, SOSP 2003 [[acmdl](https://dl.acm.org/citation.cfm?id=945470),[pdf](http://www.cs.cornell.edu/lorenzo/papers/sosp03.pdf)]
  * Proposes decoupling consensus from state machine execution, similar to the distinction in Paxos between proposers/acceptors and learners.
* Byzantine disk paxos: optimal resilience with byzantine shared memory, PODC 2004 [[acmdl](https://dl.acm.org/citation.cfm?id=1011801),[pdf](https://dahliamalkhi.files.wordpress.com/2015/12/byzdp-dc2006.pdf)]
  * Byzantized variant of Disk Paxos.
* Fault-Scalable Byzantine Fault-Tolerant Services, SOSP 2005 [[acmdl](https://dl.acm.org/citation.cfm?id=1095817)]
  * Describes the Q/U protocol, leaderless but requires 5f+1 nodes instead of 3f+1 nodes
* Fast Byzantine Consensus, IEEE TDSC 2006 [[acmdl](https://dl.acm.org/citation.cfm?id=1159374),[pdf](http://www.cs.cornell.edu/lorenzo/papers/Martin06Fast.pdf)]
  * Describes FaB, similar in nature to Q/U.
* HQ Replication: A Hybrid Quorum Protocol for Byzantine Fault Tolerance, OSDI 2006 [[acmdl](https://dl.acm.org/citation.cfm?id=1298473),[pdf](http://pmg.csail.mit.edu/papers/hq/hq-osdi06.pdf)]
* Zyzzyva: speculative byzantine fault tolerance, SOSP 2007 [[acmdl](https://dl.acm.org/citation.cfm?id=1294267),[pdf](http://www.cs.cornell.edu/lorenzo/papers/kotla07Zyzzyva.pdf)]
* Attested Append-Only Memory: Making Adversaries Stick to their Word, SOSP 2007 [[acmdl](https://dl.acm.org/doi/10.1145/1294261.1294280),[pdf](http://www.sosp2007.org/papers/sosp134-chun.pdf)]
* Tolerating Byzantine Faults in Transaction Processing Systems using Commit Barrier Scheduling, OSR 2007 [[pdf](http://db.csail.mit.edu/pubs/hrdb.pdf),[acmdl](https://dl.acm.org/doi/10.1145/1323293.1294268)]
* Bosco: One-Step Byzantine Asynchronous Consensus, DISC 2008 [[acmdl](https://dl.acm.org/citation.cfm?id=1432322),[pdf](https://www.cs.cornell.edu/projects/Quicksilver/public_pdfs/52180438.pdf)]
  * Byzantine consensus in 1 round trip (instead of the usual three) using quorums of 4f+1 from 5f+1 nodes.
* Matrix Signatures: From MACs to Digital Signatures in Distributed Systems, DISC 2008 [[pdf](http://www.cs.cornell.edu/lorenzo/papers/Aiyer08Matrix.pdf)]
* Upright cluster services, SOSP 2009 [[acmdl](https://dl.acm.org/citation.cfm?id=1629602),[pdf](http://www.cs.albany.edu/~jhh/courses/readings/clement.sosp09.upright.pdf)]
  * Develops a BFT fork of Zookeeper and HDFS, source code is [available](https://github.com/amiller/upright) but does not seem to be used/maintained
* Making Byzantine Fault Tolerant Systems Tolerate Byzantine Faults, NSDI 2009 [[acmdl](https://dl.acm.org/citation.cfm?id=1558988),[pdf](http://static.usenix.org/events/nsdi09/tech/full_papers/clement/clement.pdf)]
* TrInc: Small Trusted Hardware for Large Distributed Systems, NSDI 2009 [[pdf](https://www.usenix.org/legacy/events/nsdi09/tech/full_papers/levin/levin.pdf),[acmdl](https://dl.acm.org/doi/10.5555/1558977.1558978)]
* Zzyzx: Scalable Fault Tolerance through Byzantine Locking, DSN 2010 [[pdf](https://www.cs.unc.edu/~reiter/papers/2010/DSN.pdf)]
* Leaderless Byzantine Paxos, DISC 2011 [[pdf](https://www.microsoft.com/en-us/research/uploads/prod/2016/12/Leaderless-Byzantine-Paxos.pdf)]
* Byzantizing Paxos by Refinement, DISC 2011 [[acmdl](https://dl.acm.org/citation.cfm?id=2075058),[pdf](https://lamport.azurewebsites.net/tla/byzsimple.pdf)]
  * Also see: [Mechanically Checked Safety Proof of a Byzantine Paxos Algorithm](https://lamport.azurewebsites.net/tla/byzpaxos.html)
* Byzantine Chain Replication, OPODIS 2012 [[pdf](http://www.cs.cornell.edu/home/rvr/newpapers/opodis2012.pdf)]
* Automatic Reconfiguration for Large-Scale Reliable Storage Systems, TDSC 2012 [[pdf](http://www.pmg.csail.mit.edu/papers/tdsc12.pdf)]
  * Describes an approach to reconfigure BFT systems
* The Next 700 BFT Protocols, TOCS 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2658994),[pdf](http://www.vukolic.com/700-Eurosys.pdf)]
* Algorand: Scaling Byzantine Agreements for Cryptocurrencies, SOSP 2017 [[acmdl](https://dl.acm.org/doi/10.1145/3132747.3132757),[pdf](https://people.csail.mit.edu/nickolai/papers/gilad-algorand-eprint.pdf)]
* Hardening Cassandra Against Byzantine Failures, OPODIS 2017 [[pdf](http://drops.dagstuhl.de/opus/volltexte/2018/8642/pdf/LIPIcs-OPODIS-2017-27.pdf)]
* Revisiting Fast Practical Byzantine Fault Tolerance, Unpublished 2017 [[arxiv](https://arxiv.org/abs/1712.01367)]
  * Describes bugs in Zyzzyva and FaB
* Casper the Friendly Finality Gadget, Tech report 2017 [[arxiv](https://arxiv.org/abs/1710.09437)]
  * Casper FFG, the proposed PoS alternative for [Ethereum](https://ethereum.org/en/) (aka [Eth2](https://ethereum.org/en/eth2/))
* SoK: Consensus in the Age of Blockchains, AFT 2019 [[acmdl](https://dl.acm.org/doi/abs/10.1145/3318041.3355458),[arxiv](https://arxiv.org/abs/1711.03936)]
  * Featured in [the morning paper](https://blog.acolyer.org/2018/02/12/sok-consensus-in-the-age-of-blockchains/)
* Algorand: A secure and efficient distributed ledger, TCS 2019 [[pdf](https://www.algorand.com/Algorand_%20A%20secure%20and%20efficient%20distributed%20ledger.pdf)]
  * 2nd of the two Algorand papers
* HotStuff: BFT Consensus with Linearity and Responsiveness, PODC 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3331591),[arxiv](https://arxiv.org/abs/1803.05069)]
* The latest gossip on BFT consensus, Unpublished 2018 [[arxiv](https://arxiv.org/abs/1807.04938)]
  * Describes [Tendermint](https://tendermint.com)
* SBFT: a Scalable and Decentralized Trust Infrastructure, Unpublished 2019 [[arxiv](https://arxiv.org/abs/1804.01626)]
  * Now open source, [Concord](https://github.com/vmware/concord-bft)
* Stellar Consensus by Instantiation, DISC 2019 [[pdf](http://drops.dagstuhl.de/opus/volltexte/2019/11334/pdf/LIPIcs-DISC-2019-27.pdf)]
  * Includes Isabelle/HOL proof in [AFP](https://www.isa-afp.org/entries/Stellar_Quorums.html)
* Fast and secure global payments with Stellar, SOSP 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3359636)]
  * Formal verification in Ivy and Isabelle/HOL
* Flexible Byzantine Fault Tolerance, CCS 2019 [[acmdl](https://dl.acm.org/citation.cfm?id=3319535.3354225),[pdf](https://dahliamalkhi.files.wordpress.com/2019/09/flex-bft-ccs19.pdf)]
* Making Reads in BFT State Machine Replication Fast, Linearizable, and Live, SRDS 2021 [[arxiv](https://arxiv.org/abs/2107.11144)]
  * Identifies and fixes a liveness issue in [PBFT](http://pmg.csail.mit.edu/papers/osdi99.pdf)'s fast path for non-linearizable read-only operations
* Be Aware of Your Leaders, Unpublished 2021 [[pdf](https://sonnino.com/papers/leader-reputation.pdf)]
  * Reputation-based leader rotation algorithm as an alternative to simple round robin.
* Basil: Breaking up BFT with ACID (transactions), SOSP 2021 [[arxiv](https://arxiv.org/pdf/2109.12443.pdf)]
* BigBFT: A Multileader Byzantine Fault Tolerance Protocol for High Throughput, 2021 [[arxiv](https://arxiv.org/abs/2109.12664)]
* Scaling Membership of Byzantine Consensus, TOCS 2021 [[acmdl](https://dl.acm.org/doi/full/10.1145/3473138)]

### Alternative fault models in distributed consensus
Most of these papers handle crash faults or byzantine faults. This section considers the fault models between crash and byzantine.
* Practical Hardening of Crash-Tolerant Systems, ATC 2012 [[acmdl](https://www.usenix.org/system/files/conference/fast18/fast18-alagappan.pdf),[pdf](https://www.usenix.org/system/files/conference/atc12/atc12-final190.pdf)]
* Visigoth Fault Tolerance, EuroSys 2015 [[acmdl](https://dl.acm.org/citation.cfm?id=2741979),[pdf](http://staff.ustc.edu.cn/~chengli7/papers/a8-porto.pdf)]
* XFT: Practical Fault Tolerance beyond Crashes, OSDI 2016 [[acmdl](https://dl.acm.org/citation.cfm?id=3026877.3026915),[pdf](https://www.usenix.org/system/files/conference/osdi16/osdi16-liu.pdf)]
* 💎 Protocol-Aware Recovery for Consensus-Based Storage, FAST 2018 [[acmdl](https://dl.acm.org/citation.cfm?id=3241062),[pdf](https://www.usenix.org/system/files/conference/fast18/fast18-alagappan.pdf)]
  * Enabling nodes who lose persistent storage (e.g. due to corruption) to rejoin consensus systems without reconfiguration.
  * Implemented & evaluated in LogCabin and Zookeeper, but no source code is available
  * Best paper award at FAST 2018
  * Authors' claim to have model checked with TLA+ but no spec is available
  * Featured in [the morning paper](https://blog.acolyer.org/2018/02/27/protocol-aware-recovery-for-consensus-based-storage/)

### Misc
Blog posts, books, talks, dissertations, etc...
* Readings in Database Systems (5th Edition), Book 2015 [[pdf](http://www.redbook.io/pdf/redbook-5th-edition.pdf)]
* Introduction to Reliable and Secure Distributed Programming, Book 2011 [[acmdl](https://dl.acm.org/citation.cfm?id=1972495),[website](https://www.distributedprogramming.net)]
* Designing Data-Intensive Applications: The Big Ideas Behind Reliable, Scalable, and Maintainable Systems, Book 2017 [[website](https://dataintensive.net),[amazon](https://www.amazon.com/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321)]
* CAP Twelve Years Later: How the "Rules" Have Changed, Computer Magazine 2012 [[html](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed/)]
* [FaunaDB: An Architectural Overview](https://fauna-assets.s3.amazonaws.com/public/FaunaDB-Technical-Whitepaper.pdf)
* [Distributed Coordination Engine (DConE)](https://www.wandisco.com/assets/blt1d792cb4d9252692/WANdisco_DConE_White_Paper.pdf)
* [Communication Costs in Real-world Networks](http://www.bailis.org/blog/communication-costs-in-real-world-networks/)
* [Modeling Paxos and Flexible Paxos in Pluscal and TLA+](http://muratbuffalo.blogspot.com/2016/11/modeling-paxos-and-flexible-paxos-in.html)
* [Waltz: A Distributed Write-Ahead Log](https://wecode.wepay.com/posts/waltz-a-distributed-write-ahead-log)
* [Open-sourcing LogDevice, a distributed data store for sequential data](https://logdevice.io/blog/)

## Future reading list
The following lists contain places to watch for new writings in the field of distributed consensus.

### Blogroll
* [Jepsen](https://jepsen.io) by Kyle Kingsbury
* [Aphyr](https://aphyr.com/posts) by Kyle Kingsbury
* [The Paper Trail](https://www.the-paper-trail.org)
* [Brave new geek](https://bravenewgeek.com/archive/) by Tyler Treat
* [Highly Available, Seldom Consistent](http://www.bailis.org/blog/) by [Peter Bailis](https://twitter.com/pbailis)
* [Christopher Meiklejohn](http://christophermeiklejohn.com)
* [Denis Rystsov](http://rystsov.info)
* [Metadata](http://muratbuffalo.blogspot.com) by [Murat Demirbas](https://twitter.com/muratdemirbas)
* [Slash dev slash null](https://simbo1905.blog)
* [David Turner](https://davecturner.github.io)
* [Aleksey Charapko](http://charap.co)
* [Marc Brooker](http://brooker.co.za/blog/)
* [The Morning Paper](https://blog.acolyer.org/about/) by [Adrian Colyer](https://twitter.com/adriancolyer)
* [Hacking, Distributed](http://hackingdistributed.com) by Emin Gün Sirer
* [All Things Distributed](https://www.allthingsdistributed.com) by [Werner Vogels](https://twitter.com/Werner)
* [Decentralized Thoughts](https://ittaiab.github.io/) by various authors including [Ittai Abraham](https://twitter.com/ittaia?lang=en)

### Reading lists
* [Awesome Consensus](https://github.com/dgryski/awesome-consensus) by [Damian Gryski](https://twitter.com/dgryski)
* [Testing Distributed Systems](https://asatarin.github.io/testing-distributed-systems/) by [Andrey Satarin](https://twitter.com/asatarin)
* [An introduction to distributed systems](https://github.com/aphyr/distsys-class) by Kyle Kingsbury
* [Distributed systems theory for the distributed systems engineer](https://www.the-paper-trail.org/post/2014-08-09-distributed-systems-theory-for-the-distributed-systems-engineer/) by [Henry Robinson](https://twitter.com/henryr)
* [Collective works of Leslie Lamport](http://lamport.azurewebsites.net/pubs/pubs.html)
* [Paxosmon: Gotta Consensus Them All](https://vadosware.io/post/paxosmon-gotta-concensus-them-all/)
* [Foundational distributed systems papers](http://muratbuffalo.blogspot.com/2021/02/foundational-distributed-systems-papers.html)
* [Errors found in distributed protocols](https://github.com/dranov/protocol-bugs-list)
* [Practical Byzantine Fault Tolerance](https://pmg.csail.mit.edu/bft/)

### Academic conferences & symposiums
* USENIX Symposium on Networked Systems Design and Implementation (NSDI) [[2019](https://www.usenix.org/conference/nsdi19),[2020](https://www.usenix.org/conference/nsdi20)]
* USENIX Conference on File and Storage Technologies (FAST) [[2019](https://www.usenix.org/conference/fast19),[2020](https://www.usenix.org/conference/fast20)]
* European Conference on Computer Systems (EuroSys) [[2019](https://2019.eurosys.org),[2020](https://www.eurosys2020.org)]
* IEEE/IFIP International Conference on Dependable Systems and Networks (DSN) [[2019](http://2019.dsn.org),[2020](https://dsn2020.webs.upv.es)]
* ACM Symposium on Parallelism in Algorithms and Architectures (SPAA) [[website](https://spaa.acm.org),[2019](https://spaa.acm.org/2019/)]
* ACM SIGMOD/PODS Conference [[2019](https://sigmod2019.org),[2020](https://sigmod2020.org)]
* ACM SIGMETRICS / IFIP Performance [[2019](https://www.sigmetrics.org/sigmetrics2019/),[2020](http://www.sigmetrics.org/sigmetrics2020/)]
* ACM SIGPLAN Conference on Programming Language Design and Implementation (PLDI) [[2019](https://pldi19.sigplan.org),[2020](https://conf.researchr.org/home/pldi-2020)]
* ACM Symposium on Theory of Computing (STOC) [[2019](http://acm-stoc.org/stoc2019/),[2020](http://acm-stoc.org/stoc2020/)]
* ACM Symposium on Principles of Distributed Computing (PODC) [[website](http://www.podc.org)]
* IEEE International Conference on Distributed Computing Systems (ICDCS) [[2019](https://theory.utdallas.edu/ICDCS2019/),[2020](https://icdcs2020.sg)]
* USENIX Annual Technical Conference (ATC) [[2019](https://www.usenix.org/conference/atc19),[2020](https://www.usenix.org/conference/atc20)]
* ACM Annual Conference of the Special Interest Group on Data Communication (SIGCOMM) [[website](http://sigcomm.org/events/sigcomm-conference),[2019](http://conferences.sigcomm.org/sigcomm/2019/),[2020](https://conferences.sigcomm.org/sigcomm/2020/)]
* International Conference on Very Large Data Bases (VLDB) [[2019](http://vldb.org/2019/),[2020](https://vldb2020.org)]
* USENIX Symposium on Operating Systems Design and Implementation (OSDI) [[website](https://www.usenix.org/conferences/byname/179),[2018](https://www.usenix.org/conference/osdi18),[2020](https://www.usenix.org/conference/osdi20)]
  * Biennial evens only
* International Symposium on Reliable Distributed Systems (SRDS) [[website](https://srds-conference.org),[2019](https://srds2019.projet.liris.cnrs.fr)]
* International Symposium on Distributed Computing (DISC) [[website](http://www.disc-conference.org/wp/),[2019](http://www.disc-conference.org/wp/disc2019/)]
* International Conference on Principles of Distributed Systems (OPODIS) [[2019](https://opodis2019.unine.ch)]
* ACM Symposium on Operating Systems Principles (SOSP) [[2019](https://sosp19.rcs.uwaterloo.ca)]
  * Biennial odds only
* ACM Symposium on Cloud Computing (SoCC) [[2019](https://acmsocc.github.io/2019/)]
* Conference on Innovative Data Systems Research (CIDR) [[2021](http://cidrdb.org/cidr2021/cfp.html)]

[Dan Tsafrir](http://www.cs.technion.ac.il/~dan/index.html) maintains a useful list of [systems conferences by deadline](http://www.cs.technion.ac.il/~dan/index_sysvenues_deadline.html).

### Academic workshops
* Workshop on Principles and Practice of Consistency for Distributed Data (PaPoC) [[2019](https://novasys.di.fct.unl.pt/conferences/papoc19/)]
* ACM SIGOPS Workshop on Large-Scale Distributed Systems and Middleware (LADIS) [[website](http://ladisworkshop.org)]
* USENIX Workshop on Hot Topics in Storage and File Systems (HotStorage) [[2019](https://www.usenix.org/conference/hotstorage19)]
* Workshop on Hot Topics in Operating Systems (HotOS) [[2019](https://www.sigops.org/2018/hotos2019/)]
* ACM Workshop on Hot Topics in Networks (HotNets) [[2019](https://conferences.sigcomm.org/hotnets/2019/)]
* USENIX Workshop on Hot Topics in Cloud Computing (HotCloud) [[2019](https://www.usenix.org/conference/hotcloud19)]
* USENIX Workshop on Hot Topics in Edge Computing (HotEdge) [[2019](https://www.usenix.org/conference/hotedge19)]
* International Workshop on Distributed Cloud Computing (DCC) [[2019](http://www.disc-conference.org/wp/dcc2019/)]

### Academic journals & magazines
* ACM
  * [Transactions on Computer Systems (TOCS)](https://tocs.acm.org)
  * [Journal of the ACM (JACM)](https://jacm.acm.org)
  * [Communications of the ACM (CACM)](https://cacm.acm.org)
  * [SIGOPS Operating Systems Review (OSR)](https://www.sigops.org/osr.html)
  * [Computing Surveys (CSUR)](https://csur.acm.org)
  * [Transactions on Database Systems (TODS)](https://tods.acm.org)
  * [ACM Queue](https://queue.acm.org)
  * [SIGACT News](https://dl.acm.org/citation.cfm?id=J697)
* IEEE
  * [Transactions on Dependable and Secure Computing (TDSC)](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=8858)
  * [Transactions on Parallel and Distributed Systems (TPDS)](https://www.computer.org/csdl/journal/td)
  * [Transactions on Computers (TC)](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=12)
  * [Transactions on Software Engineering](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=32)
* [Journal of Systems Research (JSys)](http://jsys.org/)