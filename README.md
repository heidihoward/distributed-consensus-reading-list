This file contains a list of papers in the field of distributed consensus. Many of the papers fit into more than one section, however, for simplicity, each paper is listed only in the most relevant section.

### Papers on distributed consensus

Theoretical results relating to distributed consensus
* Impossibility of Distributed Consensus with One Faulty Process [paper](https://groups.csail.mit.edu/tds/papers/Lynch/jacm85.pdf)
  * aka the FLP result
* Unreliable Failure Detectors for Reliable Distributed Systems [paper](https://www.cs.utexas.edu/~lorenzo/corsi/cs380d/papers/p225-chandra.pdf)
* Time, Clocks, and the Ordering of Events in a Distributed System [paper](https://lamport.azurewebsites.net/pubs/time-clocks.pdf)
* The Weakest Failure Detector for Solving Consensus [paper](http://www.cs.utexas.edu/~lorenzo/corsi/cs380d/papers/weakestfd.pdf)
* Omega Meets Paxos: Leader Election and Stability without Eventual Timely Links [paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2005/09/paxos-leader.pdf)
* Lower Bounds for Asynchronous Consensus [paper](https://lamport.azurewebsites.net/pubs/lower-bound.pdf)
* On the Minimal Synchronism Needed for Distributed Consensus [paper](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.456.4362&rep=rep1&type=pdf)
* The implementation of reliable distributed multiprocess systems [paper](https://www.microsoft.com/en-us/research/publication/implementation-reliable-distributed-multiprocess-systems/)

Surveys & tutorials of consensus algorithms
* Classic Paxos vs. Fast Paxos: Caveat Emptor [paper](http://www.sysnet.ucsd.edu/sysnet/miscpapers/hotdep07.pdf)
* Vive La Difference: Paxos vs. Viewstamped Replication vs. Zab [paper](https://www.cs.cornell.edu/fbs/publications/vivaLaDifference.pdf)
* The ABCD’s of Paxos [paper](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.595.4829&rep=rep1&type=pdf)
* Paxos Made Simple [paper](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf)
  * describes single-degree Paxos as well as Multi-Paxos from SMR
* Revisiting the PAXOS algorithm [paper](https://groups.csail.mit.edu/tds/papers/DePrisco/paxos-tcs.pdf)
* Total order broadcast and multicast algorithms: Taxonomy and survey [paper](https://dl.acm.org/citation.cfm?id=1041682)
* How to Build a Highly Available System Using Consensus [paper](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.72.5429&rep=rep1&type=pdf)
* Paxos Made Moderately Complex [paper](http://www.cs.cornell.edu/courses/cs7412/2011sp/paxos.pdf)
* Tutorial Summary: Paxos Explained from Scratch [paper](http://www.ux.uis.no/~meling/papers/2013-paxostutorial-opodis.pdf)
* A Modular Approach to Fault-Tolerant Broadcasts and Related Problems [paper](http://csis.pace.edu/~marchese/CS865/Papers/hadzilacos_ps.ps)

Algorithms for distributed consensus
* Consensus in the Presence of Partial Synchrony [paper](https://dl.acm.org/citation.cfm?id=42283)
* The Part-Time Parliament [paper](https://lamport.azurewebsites.net/pubs/lamport-paxos.pdf)
* Viewstamped Replication: A New Primary Copy Method to Support Highly-Available Distributed Systems [paper](http://pmg.csail.mit.edu/papers/vr.pdf)
* Viewstamped Replication Revisited [paper](http://pmg.csail.mit.edu/papers/vr-revisited.pdf)
* Efficient Message Ordering in Dynamic Networks [paper](https://dl.acm.org/citation.cfm?id=248062)
* Stoppable Paxos [paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2008/04/stoppableV9.pdf)
* Fast Paxos [paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-2005-112.pdf)
* Consensus on Transaction Commit [paper](https://lamport.azurewebsites.net/video/consensus-on-transaction-commit.pdf)
* Generalized Consensus and Paxos [paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-2005-33.pdf)
* Vertical Paxos and Primary-Backup Replication [paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2009/05/podc09v6.pdf)
* Disk Paxos [paper](https://lamport.azurewebsites.net/pubs/disk-paxos.pdf)
* Cheap Paxos [paper](https://lamport.azurewebsites.net/pubs/web-dsn-submission.pdf)
* Paxos Made Practical [paper](http://www.scs.stanford.edu/~dm/home/papers/paxos.pdf)
* Reconfiguring a State Machine [paper](https://lamport.azurewebsites.net/pubs/reconfiguration-tutorial.pdf)
* Reliable communication in the presence of failures [paper](https://dl.acm.org/citation.cfm?id=7478)
* Efficient message ordering in dynamic networks [paper](https://dl.acm.org/citation.cfm?id=248062)
* On Collision-fast Atomic Broadcast [paper](https://infoscience.epfl.ch/record/100857/files/CFAbcastTR.pdf)
* Dynamic atomic storage without consensus [paper](https://dl.acm.org/citation.cfm?id=1944348)
* Specifying and Using a Partitionable Group Communication Service [paper](https://groups.csail.mit.edu/tds/papers/Lynch/TOCS.pdf)
* Active Disk Paxos with infinitely many processes [paper](https://groups.csail.mit.edu/tds/papers/Chockler/podc-02.pdf)
* CASPaxos: Replicated State Machines without logs [paper](https://arxiv.org/pdf/1802.07000.pdf)
* Multicoordinated Paxos [paper](https://dl.acm.org/citation.cfm?id=1281150)
* Paxos Quorum Leases: Fast Reads Without Sacrificing Writes [paper](https://www.cs.cmu.edu/~dga/papers/leases-socc2014.pdf)
  * extends the idea of master read leases to allow the master to promise to use a specified subset of acceptors in every majority quorum. Acceptors in this quorum can then serve reads locally.
  * similar to master read leases, it relies on clock synchrony.

Implementing consensus using specialist hardware, SDN, IP-multicast, RDMA etc
* Paxos Made Switch-y [paper](https://www.sigcomm.org/sites/default/files/ccr/papers/2016/April/0000000-0000002.pdf)
* NetPaxos: consensus at network speed [paper](https://dl.acm.org/citation.cfm?id=2774999)
* Consensus in a Box: Inexpensive Coordination in Hardware [paper](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-istvan.pdf)
* Ring Paxos: A high-throughput atomic broadcast protocol [paper](https://ieeexplore.ieee.org/document/5544272)
* Multi-Ring Paxos [paper](https://ieeexplore.ieee.org/document/6263916)
* Taming uncertainty in distributed systems with help from the network [paper](http://www.cs.utexas.edu/falcon/papers/albatross-eurosys2015.pdf)
* Derecho: Group Communication at the Speed of Light [paper](https://www.cs.cornell.edu/projects/Quicksilver/public_pdfs/Derecho-Protocols.pdf)
* Groups, Subgroups and Auto-Sharding in Derecho: A Customizable RDMA Framework for Highly Available Cloud Services [paper](https://pdfs.semanticscholar.org/5dc4/ac5ac578fae726adcc5776d2a277f09dd9b5.pdf?_ga=2.198677487.1756250239.1559555537-1469340531.1559555537)
* Derecho: Fast State Machine Replication for Cloud Services [paper](https://dl.acm.org/citation.cfm?id=3302258)
* Just say NO to Paxos Overhead: Replacing Consensus with Network Ordering [paper](https://www.usenix.org/system/files/conference/osdi16/osdi16-li.pdf)
* AllConcur: Leaderless Concurrent Atomic Broadcast [paper](https://spcl.inf.ethz.ch/Publications/.pdf/poke2017allconcur.pdf)
* DARE: High-Performance State Machine Replication on RDMA Networks [paper](https://spcl.inf.ethz.ch/Research/Parallel_Programming/DARE/dare-TR.pdf)

Implementing consensus for geo-distributed systems
* MDCC: Multi-Data Center Consistency [paper](http://mdcc.cs.berkeley.edu/mdcc.pdf)
* Canopus: A Scalable and Massively Parallel Consensus Protocol [paper](https://cs.uwaterloo.ca/~bernard/Canopus.pdf)
* There Is More Consensus in Egalitarian Parliaments [paper](https://www.cs.cmu.edu/~dga/papers/epaxos-sosp2013.pdf)
* DPaxos: Managing Data Closer to Users for Low-Latency and Mobile Applications [paper](https://nawab.me/Uploads/Nawab_DPaxos_SIGMOD2018.pdf)
* SDPaxos: Building Efficient Semi-Decentralized Geo-replicated State Machines [paper](https://www.microsoft.com/en-us/research/publication/sdpaxos-building-efficient-semi-decentralized-geo-replicated-state-machines/)
* FleetDB: Follow-the-workload Data Migration for Globe-Spanning Databases [paper](https://cse.buffalo.edu/tech-reports/2018-02.pdf)
* Mencius: Building Efficient Replicated State Machines for WANs [paper](https://www.usenix.org/legacy/event/osdi08/tech/full_papers/mao/mao.pdf)
* Geo-replicated storage with scalable deferred update replication [paper](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.724.1706&rep=rep1&type=pdf)
* Multileader WAN Paxos: Ruling the Archipelago with Fast Consensus [paper](https://cse.buffalo.edu/tech-reports/2017-01.pdf)
* Scalable Consistency in Scatter [paper](https://homes.cs.washington.edu/~tom/pubs/scatter.pdf)
* GlobalFS: A Strongly Consistent Multi-Site File System [paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7794339)
* CalvinFS: Consistent WAN Replication and Scalable Metadata Management for Distributed File Systems [paper](https://www.usenix.org/system/files/conference/fast15/fast15-paper-thomson.pdf)
* Modelling Paxos performance in wide area [paper](http://charap.co/modeling-paxos-performance-in-wide-area-part-3/)
* Low-Latency Multi-Datacenter Databases using Replicated Commit [paper](http://www.vldb.org/pvldb/vol6/p661-mahmoud.pdf)
* FaunaDB: An Architectural Overview [paper](https://fauna-assets.s3.amazonaws.com/public/FaunaDB-Technical-Whitepaper.pdf)

Distributed consensus in production
* Paxos Made Live - An Engineering Perspective [paper](https://www.cs.utexas.edu/users/lorenzo/corsi/cs380d/papers/paper2-1.pdf)
* The Chubby lock service for loosely-coupled distributed systems [paper](https://static.googleusercontent.com/media/research.google.com/en//archive/chubby-osdi06.pdf)
* Megastore: Providing Scalable, Highly Available Storage for Interactive Services [paper](http://cidrdb.org/cidr2011/Papers/CIDR11_Paper32.pdf)
  * seems to use an unusual definition of Multi-Paxos where each instance is district but the 1a/1b messages for slot i is piggybacked onto 2a2/b for i-1  
  * uses SMR with witnesses, replicas with participate in log replication but do not run a state machine and read-only replicas which only run a state machine.
* Zab: High-performance broadcast for primary-backup systems [paper](https://knowably-attachments.s3.amazonaws.com/u/55b69a1ce4b00ab397d67250/7c8734d3cf02154499a9b3161ef9f575/Zab_2011.pdf)
* ZooKeeper: Wait-free coordination for Internet-scale systems [paper](https://www.usenix.org/legacy/event/atc10/tech/full_papers/Hunt.pdf)
  * Widely utilized Apache licensed open source project written in Java [[project website] [paper](https://zookeeper.apache.org)
  * Architecture is similar to Google's Chubby but unlike Chubby is described in detail and open source
  * Writes are linearizable, reads may be stale unless sync is called first
  * Clients may have multiple outstanding requests, they will be handled FIFO
  * Uses primary-backup replication instead of state machine replication
* PaxosStore: High-availability Storage Made Practical in WeChat [paper](http://www.vldb.org/pvldb/vol10/p1730-lin.pdf)
* Windows Azure Storage: a highly available cloud storage service with strong consistency [paper](https://dl.acm.org/citation.cfm?id=2043571)
* Distributed Coordination Engine (DConE) [paper](https://www.wandisco.com/assets/blt1d792cb4d9252692/WANdisco_DConE_White_Paper.pdf)
* Bizur: A Key-value Consensus Algorithm for Scalable File-systems [paper](https://arxiv.org/pdf/1702.04242.pdf)

Implementations of consensus
* Replication and fault-tolerance in the ISIS system [paper](https://ecommons.cornell.edu/handle/1813/6508)
* The ISIS project: real experience with a fault tolerant programming system [paper](https://dl.acm.org/citation.cfm?id=122133)
* In Search of an Understandable Consensus Algorithm (Extended Version) [paper](https://raft.github.io/raft.pdf)
  * aka the RAFT consensus paper
  * algorithm implemented by [etcd](https://etcd.io)
    * open sourced and widely utilized including by [kubernetes](https://kubernetes.io)
    * written in golang
  * implemented by [CockroachDB](https://www.cockroachlabs.com/docs/stable/)
* Consensus: Bridging Theory and Practice [paper](https://github.com/ongardie/dissertation)
  * PhD thesis describing RAFT consensus in more detail
* S-Paxos: Offloading the Leader for High Throughput State Machine Replication [paper](https://infoscience.epfl.ch/record/179912/files/2012_SPaxos-CameraReady.pdf)
* Optimizing Paxos with batching and pipelining [paper](https://infoscience.epfl.ch/record/189440/files/TCS.pdf)
* Paxos for System Builders: An Overview [paper](http://www.cnds.jhu.edu/pub/papers/psb_ladis_08.pdf)
* Partitioned Paxos via the Network Data Plane [paper](https://arxiv.org/abs/1901.08806meni)
* The SMART Way to Migrate Replicated Stateful Services [paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/eurosys2006.pdf)
* Boxwood: Abstractions as the Foundation for Storage Infrastructure [paper](https://www.usenix.org/legacy/event/osdi04/tech/full_papers/maccormick/maccormick.pdf)
* Replication in the Harp File System [paper](http://www.pmg.csail.mit.edu/papers/harp.pdf)
* CORFU: A Distributed Shared Log [paper](https://dl.acm.org/citation.cfm?id=2535930)
* Tango: Distributed data structures over a shared log [paper](http://www.cs.cornell.edu/~taozou/sosp13/tangososp.pdf)
* The Farsite Project: A Retrospective [paper](https://www.microsoft.com/en-us/research/wp-content/uploads/2007/04/OSR2007-4aa.pdf)
* Using Paxos to Build a Scalable, Consistent, and Highly Available Datastore [paper](https://dl.acm.org/citation.cfm?id=1938549)
* Paxos replicated state machines as the basis of a high-performance data store [paper](https://dl.acm.org/citation.cfm?id=1972472)
* Granola: Low-Overhead Distributed Transaction Coordination [paper](https://www.usenix.org/system/files/conference/atc12/atc12-final118.pdf)
* Making Fast Consensus Generally Faster [paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7579738)
* Scalable State-Machine Replication [paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6903591)
* Calvin: Fast Distributed Transactions for Partitioned Database Systems [paper](http://cs.yale.edu/homes/thomson/publications/calvin-sigmod12.pdf)
* Paxos made transparent [paper](https://dl.acm.org/citation.cfm?doid=2815400.2815427)
* Designing Distributed Systems Using Approximate Synchrony in Data Center Networks [paper](https://syslab.cs.washington.edu/papers/specpaxos-nsdi15.pdf)
* No compromises: distributed transactions with consistency, availability, and performance [paper](https://pdos.csail.mit.edu/6.824/papers/farm-2015.pdf)
* Building Consistent Transactions with Inconsistent Replication [paper](https://irenezhang.net/papers/tapir-sosp15.pdf)
  * Weakly consistent key-val store with support for linearizability as requested
  * Useful related blog post [Lessons learned from TAPIR(s)](https://irenezhang.net/blog/2015/04/02/tapir.html)
  * geo-distributed performance is evaluated
* Commodifying Replicated State Machines with OpenReplica [paper](https://ecommons.cornell.edu/handle/1813/29009)

Standalone evaluations of consensus algorithms
* The Performance of Paxos in the Cloud [paper](https://www.cs.cornell.edu/projects/Quicksilver/public_pdfs/SRDS14.pdf)
* Consensus in the Cloud: Paxos Systems Demystified [paper](https://cse.buffalo.edu/tech-reports/2016-02.pdf)
* Spectrum: A Framework for Adapting Consensus Protocols [paper](https://arxiv.org/abs/1902.05873)


### Papers on related topics

Linearizability & SMR
* Implementing Fault-Tolerant Services Using the State Machine Approach: A Tutorial [paper](https://www.cs.cornell.edu/fbs/publications/SMSurvey.pdf)
* Linearizability: A Correctness Condition for Concurrent Objects [paper](https://cs.brown.edu/~mph/HerlihyW90/p463-herlihy.pdf)
* Implementing Linearizability at Large Scale and Low Latency [paper](https://dl.acm.org/citation.cfm?id=2815416)
* Cheap and Available State Machine Replication [paper](https://www.usenix.org/system/files/conference/atc16/atc16_paper-shi.pdf)

Weaker consistency models
* Existential Consistency: Measuring and Understanding Consistency at Facebook [paper](http://sigops.org/s/conferences/sosp/2015/current/2015-Monterey/printable/240-lu.pdf)
* What consistency does your key-value store actually provide? [paper](https://www.usenix.net/legacy/events/hotdep10/tech/full_papers/Anderson.pdf)
  * offline consistency checking of key-value traces
* TAO: Facebook’s Distributed Data Store for the Social Graph [paper](https://www.usenix.org/system/files/conference/atc13/atc13-bronson.pdf)
* Consistency in Non-Transactional Distributed Storage Systems [paper](http://www.vukolic.com/consistency-survey.pdf)
* Dynamo: Amazon’s Highly Available Key-value Store [paper](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)
* Bigtable: A Distributed Storage System for Structured Data [paper](https://static.googleusercontent.com/media/research.google.com/en//archive/bigtable-osdi06.pdf)
* Spanner: Google’s Globally-Distributed Database [paper](https://static.googleusercontent.com/media/research.google.com/en//archive/spanner-osdi2012.pdf)
  * Provides linearizability but it assumes a bounded clock drift
  * Google implement this using Truetime, GPS and atomic clocks in their data centers instead of NTP
  * Closed source but now available as a cloud service, [Cloud Spanner [paper](https://cloud.google.com/spanner/)
* Cassandra - A Decentralized Structured Storage System [paper](https://www.cs.cornell.edu/projects/ladis2009/papers/lakshman-ladis2009.pdf)
  * not discussion in paper but Cassandra now uses Paxos for [lightweight transactions [paper](https://docs.datastax.com/en/archived/cassandra/3.0/cassandra/dml/dmlLtwtTransactions.html).
* Spanner, TrueTime & The CAP Theorem [paper](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45855.pdf)
* Towards Robust Distributed Systems [paper](https://people.eecs.berkeley.edu/~brewer/cs262b-2004/PODC-keynote.pdf)
  * PODC keynote in which Eric Brewer proposed the now infamous CAP theorem
* Quantifying eventual consistency with PBS [paper](http://www.bailis.org/papers/pbs-vldbj2014.pdf)
* Eventual Consistency Today: Limitations, Extensions, and Beyond [paper](https://queue.acm.org/detail.cfm?id=2462076)
* Fine-grained consistency for geo-replicated systems [paper](https://www.usenix.org/system/files/conference/atc18/atc18-li_cheng.pdf)
* The many faces of consistency [paper](http://sites.computer.org/debull/A16mar/p3.pdf)
* Benchmarking Cloud Serving Systems with YCSB [paper](https://www2.cs.duke.edu/courses/fall13/compsci590.4/838-CloudPapers/ycsb.pdf)
  * Popular benchmarking tool for key-values stores
  * Actively maintained [open source project](https://github.com/brianfrankcooper/YCSB/wiki) with support for various data stores
* Leases: An Efficient Fault-Tolerant Mechanism for Distributed File Cache Consistency [paper](https://web.stanford.edu/class/cs240/readings/89-leases.pdf)
  * This paper introduced the idea of leases for distributed caches. This idea is used in master leases and read quorum leases

Failures & bugs
* The Network is Reliable: An informal survey of real-world communications failures [paper](https://queue.acm.org/detail.cfm?id=2655736)
* Communication Costs in Real-world Networks [paper](http://www.bailis.org/blog/communication-costs-in-real-world-networks/)
* What Bugs Live in the Cloud? A Study of 3000+ Issues in Cloud Systems [paper](https://ucare.cs.uchicago.edu/pdf/socc14-cbs.pdf)
* Understanding Network Failures in Data Centers: Measurement, Analysis, and Implications [paper](http://conferences.sigcomm.org/sigcomm/2011/papers/sigcomm/p350.pdf)
* Teaching Rigorous Distributed Systems With Efficient Model Checking [paper](https://dl.acm.org/citation.cfm?id=3303947)
* Lineage-driven Fault Injection [paper](https://people.ucsc.edu/~palvaro/molly.pdf)

Correctness of consensus algorithms
* IronFleet: Proving Practical Distributed Systems Correct [paper](http://sigops.org/s/conferences/sosp/2015/current/2015-Monterey/printable/250-hawblitzel.pdf)
* Paxos Made EPR: Decidable Reasoning about Distributed Protocols [paper](https://dl.acm.org/citation.cfm?doid=3152284.3140568)
* Verdi: A framework for implementing and formally verifying distributed systems [paper](https://homes.cs.washington.edu/~ztatlock/pubs/verdi-wilcox-pldi15.pdf)
* A Proof of Correctness for Egalitarian Paxos [paper](http://www.cs.cmu.edu/~imoraru/epaxos/tr.pdf)
* Specifying Systems: The TLA+ Language and Tools for Hardware and Software Engineers [paper](https://lamport.azurewebsites.net/tla/book-02-08-08.pdf)
* Modeling Paxos and Flexible Paxos in Pluscal and TLA+ [paper](http://muratbuffalo.blogspot.com/2016/11/modeling-paxos-and-flexible-paxos-in.html)

Quorum systems
* A Majority Consensus Approach to Concurrency Control for Multiple Copy Databases [paper](https://dl.acm.org/citation.cfm?id=320076)
* Weighted Voting for Replicated Data [paper](http://pages.cs.wisc.edu/~remzi/Classes/739/Fall2015/Papers/gifford79.pdf)
* An Efficient and Fault-tolerant Solution for Distributed Mutual Exclusion [paper](https://users.soe.ucsc.edu/~scott/courses/Fall11/221/Papers/Sync/agrawal-tocs91.pdf)
* The Generalized Tree Quorum Protocol: An Efficient Approach for Managing Replicated Data [paper](https://dl.acm.org/citation.cfm?id=146935)
* The Reliability of Voting Mechanisms [paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=1676860)
* The grid protocol: a high performance scheme for maintaining replicated data [paper](https://ieeexplore.ieee.org/abstract/document/180609)
* How to Assign Votes in a Distributed System [paper](https://dl.acm.org/citation.cfm?id=4223)
* Hierarchical Quorum Consensus: A New Algorithm for Managing Replicated Data [paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=83661)
* The Load, Capacity, and Availability of Quorum Systems [paper](https://epubs.siam.org/doi/pdf/10.1137/S0097539795281232)
* A √N algorithm for mutual exclusion in decentralized systems [paper](https://dl.acm.org/citation.cfm?id=214445)
* The Availability of Quorum Systems [paper](https://pdfs.semanticscholar.org/ab7d/30f7a808173bc305d679262f9838869cb681.pdf)
* Coterie Availability in Sites [paper](https://link.springer.com/chapter/10.1007/11561927_3)
* The virtue of dependent failures in multi-site systems [paper](https://dl.acm.org/citation.cfm?id=1973401)
* Crumbling Walls: A Class of Practical and Efficient Quorum Systems [paper](https://link.springer.com/article/10.1007/s004460050027)

Reading lists
* Awesome Consensus by Damian Gryski [link](https://github.com/dgryski/awesome-consensus)
* Testing Distributed Systems by Andrey Satarin [link](https://asatarin.github.io/testing-distributed-systems/)
* An introduction to distributed systems by Kyle Kingsbury [link](https://github.com/aphyr/distsys-class)

### Future reading list
The following lists contain places to watch for new writings in the field of distributed consensus.

Blogroll
* Jepsen by Kyle Kingsbury [link](https://jepsen.io)
* Aphyr by Kyle Kingsbury [link](https://aphyr.com/posts)
* The Paper Trail [link](https://www.the-paper-trail.org)
* Brave new geek by Tyler Treat [link](https://bravenewgeek.com/archive/)
* Highly Available, Seldom Consistent by Peter Bailis [link](http://www.bailis.org/blog/)
* Christopher Meiklejohn [link](http://christophermeiklejohn.com)
* Denis Rystsov [link](http://rystsov.info)
* Metadata by Murat Demirbas [link](http://muratbuffalo.blogspot.com)
* Slash dev slash null [link](https://simbo1905.blog)
* David Turner [link](https://davecturner.github.io)
* Aleksey Charapko [link](http://charap.co)
* The Morning Paper by Adrian Colyer [link](https://blog.acolyer.org/about/)
* Hacking, Distributed by Emin Gün Sirer [link](http://hackingdistributed.com)
* All Things Distributed by Werner Vogels [link](https://www.allthingsdistributed.com)
* Decentralized Thoughts by Ittai Abraham [link](https://ittaiab.github.io/)

Academic conferences & symposiums
* ACM Symposium on Principles of Distributed Computing (PODC) [link](http://www.podc.org)
* IEEE/IFIP International Conference on Dependable Systems and Networks (DSN) [link](http://2019.dsn.org)
* IEEE International Conference on Distributed Computing Systems (ICDCS) [link](https://theory.utdallas.edu/ICDCS2019/)
* International Conference on Principles of Distributed Systems (OPODIS) [link](https://opodis2019.unine.ch)
* International Symposium on Distributed Computing (DISC) [link](http://www.disc-conference.org/wp/disc2019/)
* International Symposium on Reliable Distributed Systems (SRDS) [link](https://srds2019.projet.liris.cnrs.fr)
* ACM Symposium on Parallelism in Algorithms and Architectures (SPAA) [link](https://spaa.acm.org/2019/)
* USENIX Symposium on Networked Systems Design and Implementation (NSDI) [link](https://www.usenix.org/conference/nsdi20)
* USENIX Symposium on Operating Systems Design and Implementation (OSDI) [link](https://www.usenix.org/conference/osdi18) - Biennial evens
* ACM Symposium on Operating Systems Principles (SOSP) [link](https://sosp19.rcs.uwaterloo.ca) - Biennial odds
* USENIX Annual Technical Conference (ATC) [link](https://www.usenix.org/conference/atc19)
* European Conference on Computer Systems (EuroSys) [link](https://2019.eurosys.org)
* ACM SIGMOD/PODS Conference [link](https://sigmod2019.org)
* ACM SIGMETRICS / IFIP Performance [link](https://www.sigmetrics.org/sigmetrics2019/)
* ACM Annual Conference of the Special Interest Group on Data Communication (SIGCOMM) [link](http://sigcomm.org/events/sigcomm-conference)
* USENIX Conference on File and Storage Technologies (FAST) [link](https://www.usenix.org/conference/fast20)
* ACM SIGPLAN Conference on Programming Language Design and Implementation (PLDI) [link](https://pldi19.sigplan.org)
* International Conference on Very Large Data Bases (VLDB) [link](http://vldb.org/2019/)
* ACM Symposium on Cloud Computing (SoCC) [link](https://acmsocc.github.io/2019/)
* ACM Symposium on Theory of Computing (STOC) [link](http://acm-stoc.org/stoc2019/)

Workshops
* Workshop on Principles and Practice of Consistency for Distributed Data (PaPoC) [link](https://novasys.di.fct.unl.pt/conferences/papoc19/)
* ACM SIGOPS Workshop on Large-Scale Distributed Systems and Middleware (LADIS) [link](http://ladisworkshop.org)
* USENIX Workshop on Hot Topics in Storage and File Systems (HotStorage) [link](https://www.usenix.org/conference/hotstorage19)
* Workshop on Hot Topics in Operating Systems (HotOS) [link](https://www.sigops.org/2018/hotos2019/)
* ACM Workshop on Hot Topics in Networks (HotNets) [link](https://conferences.sigcomm.org/hotnets/2019/)
* USENIX Workshop on Hot Topics in Cloud Computing (HotCloud) [link](https://www.usenix.org/conference/hotcloud19)
* USENIX Workshop on Hot Topics in Edge Computing (HotEdge) [link](https://www.usenix.org/conference/hotedge19)

Journals & Magazines
* ACM Transactions on Computer Systems (TOCS) [link](https://tocs.acm.org)
* Journal of the ACM (JACM) [link](https://jacm.acm.org)
* Communications of the ACM (CACM) [link](https://cacm.acm.org)
* SIGOPS Operating Systems Review (OSR) [link](https://www.sigops.org/osr.html)
* ACM Computing Surveys (CSUR) [link](https://csur.acm.org)
* ACM Transactions on Database Systems (TODS) [link](https://tods.acm.org)
* ACM Queue [link](https://queue.acm.org)
* ACM SIGACT News [link](https://dl.acm.org/citation.cfm?id=J697)
* IEEE Transactions on Dependable and Secure Computing (TDSC) [link](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=8858)
* IEEE Transactions on Parallel and Distributed Systems (TPDS) [link](https://www.computer.org/csdl/journal/td)
* IEEE Transactions on Computers (TC) [link](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=12)
* IEEE Transactions on Software Engineering [link](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=32)
