This file contains a list of papers in the field of distributed consensus. Many of the papers fit into more than one section, however, for simplicity, each paper is listed only in the most relevant section.

### Papers on distributed consensus

Theoretical results relating to distributed consensus
* [Impossibility of Distributed Consensus with One Faulty Process](https://groups.csail.mit.edu/tds/papers/Lynch/jacm85.pdf)
  * aka the FLP result
* [Unreliable Failure Detectors for Reliable Distributed Systems](https://www.cs.utexas.edu/~lorenzo/corsi/cs380d/papers/p225-chandra.pdf)
* [Time, Clocks, and the Ordering of Events in a Distributed System](https://lamport.azurewebsites.net/pubs/time-clocks.pdf)
* [The Weakest Failure Detector for Solving Consensus](http://www.cs.utexas.edu/~lorenzo/corsi/cs380d/papers/weakestfd.pdf)
* [Omega Meets Paxos: Leader Election and Stability without Eventual Timely Links](https://www.microsoft.com/en-us/research/wp-content/uploads/2005/09/paxos-leader.pdf)
* [Lower Bounds for Asynchronous Consensus](https://lamport.azurewebsites.net/pubs/lower-bound.pdf)
* [On the Minimal Synchronism Needed for Distributed Consensus](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.456.4362&rep=rep1&type=pdf)
* [The implementation of reliable distributed multiprocess systems](https://www.microsoft.com/en-us/research/publication/implementation-reliable-distributed-multiprocess-systems/)

Surveys, tutorials & evaluations of consensus algorithms
* [Classic Paxos vs. Fast Paxos: Caveat Emptor](http://www.sysnet.ucsd.edu/sysnet/miscpapers/hotdep07.pdf)
* [Vive La Difference: Paxos vs. Viewstamped Replication vs. Zab](https://www.cs.cornell.edu/fbs/publications/vivaLaDifference.pdf)
* [The ABCD’s of Paxos](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.595.4829&rep=rep1&type=pdf)
* [Paxos Made Simple](https://lamport.azurewebsites.net/pubs/paxos-simple.pdf)
  * describes single-degree Paxos as well as Multi-Paxos from SMR
* [Revisiting the PAXOS algorithm](https://groups.csail.mit.edu/tds/papers/DePrisco/paxos-tcs.pdf)
* [Total order broadcast and multicast algorithms: Taxonomy and survey](https://dl.acm.org/citation.cfm?id=1041682)
* [The Performance of Paxos in the Cloud](https://www.cs.cornell.edu/projects/Quicksilver/public_pdfs/SRDS14.pdf)
* [How to Build a Highly Available System Using Consensus](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.72.5429&rep=rep1&type=pdf)
* [Consensus in the Cloud: Paxos Systems Demystified](https://cse.buffalo.edu/tech-reports/2016-02.pdf)
* [Paxos Made Moderately Complex](http://www.cs.cornell.edu/courses/cs7412/2011sp/paxos.pdf)
* [Tutorial Summary: Paxos Explained from Scratch](http://www.ux.uis.no/~meling/papers/2013-paxostutorial-opodis.pdf)
* [A Modular Approach to Fault-Tolerant Broadcasts and Related Problems](http://csis.pace.edu/~marchese/CS865/Papers/hadzilacos_ps.ps)

Algorithms for distributed consensus
* [Consensus in the Presence of Partial Synchrony](https://dl.acm.org/citation.cfm?id=42283)
* [The Part-Time Parliament](https://lamport.azurewebsites.net/pubs/lamport-paxos.pdf)
* [Viewstamped Replication: A New Primary Copy Method to Support Highly-Available Distributed Systems](http://pmg.csail.mit.edu/papers/vr.pdf)
* [Viewstamped Replication Revisited](http://pmg.csail.mit.edu/papers/vr-revisited.pdf)
* [Efficient Message Ordering in Dynamic Networks](https://dl.acm.org/citation.cfm?id=248062)
* [Stoppable Paxos](https://www.microsoft.com/en-us/research/wp-content/uploads/2008/04/stoppableV9.pdf)
* [Fast Paxos](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-2005-112.pdf)
* [Consensus on Transaction Commit](https://lamport.azurewebsites.net/video/consensus-on-transaction-commit.pdf)
* [Generalized Consensus and Paxos](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-2005-33.pdf)
* [Vertical Paxos and Primary-Backup Replication](https://www.microsoft.com/en-us/research/wp-content/uploads/2009/05/podc09v6.pdf)
* [Disk Paxos](https://lamport.azurewebsites.net/pubs/disk-paxos.pdf)
* [Cheap Paxos](https://lamport.azurewebsites.net/pubs/web-dsn-submission.pdf)
* [Paxos Made Practical](http://www.scs.stanford.edu/~dm/home/papers/paxos.pdf)
* [Reconfiguring a State Machine](https://lamport.azurewebsites.net/pubs/reconfiguration-tutorial.pdf)
* [Reliable communication in the presence of failures](https://dl.acm.org/citation.cfm?id=7478)
* [Efficient message ordering in dynamic networks](https://dl.acm.org/citation.cfm?id=248062)
* [On Collision-fast Atomic Broadcast](https://infoscience.epfl.ch/record/100857/files/CFAbcastTR.pdf)
* [Dynamic atomic storage without consensus](https://dl.acm.org/citation.cfm?id=1944348)
* [Specifying and Using a Partitionable Group Communication Service](https://groups.csail.mit.edu/tds/papers/Lynch/TOCS.pdf)
* [Active Disk Paxos with infinitely many processes](https://groups.csail.mit.edu/tds/papers/Chockler/podc-02.pdf)
* [CASPaxos: Replicated State Machines without logs](https://arxiv.org/pdf/1802.07000.pdf)
* [Multicoordinated Paxos](https://dl.acm.org/citation.cfm?id=1281150)
* [Paxos Quorum Leases: Fast Reads Without Sacrificing Writes](https://www.cs.cmu.edu/~dga/papers/leases-socc2014.pdf)
  * extends the idea of master read leases to allow the master to promise to use a specified subset of acceptors in every majority quorum. Acceptors in this quorum can then serve reads locally.
  * similar to master read leases, it relies on clock synchrony.

Implementing consensus using specialist hardware, SDN, IP-multicast, RDMA etc
* [Paxos Made Switch-y](https://www.sigcomm.org/sites/default/files/ccr/papers/2016/April/0000000-0000002.pdf)
* [NetPaxos: consensus at network speed](https://dl.acm.org/citation.cfm?id=2774999)
* [Consensus in a Box: Inexpensive Coordination in Hardware](https://www.usenix.org/system/files/conference/nsdi16/nsdi16-paper-istvan.pdf)
* [Ring Paxos: A high-throughput atomic broadcast protocol](https://ieeexplore.ieee.org/document/5544272)
* [Multi-Ring Paxos](https://ieeexplore.ieee.org/document/6263916)
* [Taming uncertainty in distributed systems with help from the network](http://www.cs.utexas.edu/falcon/papers/albatross-eurosys2015.pdf)
* [Derecho: Group Communication at the Speed of Light](https://www.cs.cornell.edu/projects/Quicksilver/public_pdfs/Derecho-Protocols.pdf)
* [Groups, Subgroups and Auto-Sharding in Derecho: A Customizable RDMA Framework for Highly Available Cloud Services](https://pdfs.semanticscholar.org/5dc4/ac5ac578fae726adcc5776d2a277f09dd9b5.pdf?_ga=2.198677487.1756250239.1559555537-1469340531.1559555537)
* [Derecho: Fast State Machine Replication for Cloud Services](https://dl.acm.org/citation.cfm?id=3302258)
* [Just say NO to Paxos Overhead: Replacing Consensus with Network Ordering](https://www.usenix.org/system/files/conference/osdi16/osdi16-li.pdf)
* [AllConcur: Leaderless Concurrent Atomic Broadcast](https://spcl.inf.ethz.ch/Publications/.pdf/poke2017allconcur.pdf)
* [DARE: High-Performance State Machine Replication on RDMA Networks](https://spcl.inf.ethz.ch/Research/Parallel_Programming/DARE/dare-TR.pdf)

Implementing consensus for geo-distributed systems
* [MDCC: Multi-Data Center Consistency](http://mdcc.cs.berkeley.edu/mdcc.pdf)
* [Canopus: A Scalable and Massively Parallel Consensus Protocol](https://cs.uwaterloo.ca/~bernard/Canopus.pdf)
* [There Is More Consensus in Egalitarian Parliaments](https://www.cs.cmu.edu/~dga/papers/epaxos-sosp2013.pdf)
* [DPaxos: Managing Data Closer to Users for Low-Latency and Mobile Applications](https://nawab.me/Uploads/Nawab_DPaxos_SIGMOD2018.pdf)
* [SDPaxos: Building Efficient Semi-Decentralized Geo-replicated State Machines](https://www.microsoft.com/en-us/research/publication/sdpaxos-building-efficient-semi-decentralized-geo-replicated-state-machines/)
* [FleetDB: Follow-the-workload Data Migration for Globe-Spanning Databases](https://cse.buffalo.edu/tech-reports/2018-02.pdf)
* [Mencius: Building Efficient Replicated State Machines for WANs](https://www.usenix.org/legacy/event/osdi08/tech/full_papers/mao/mao.pdf)
* [Geo-replicated storage with scalable deferred update replication](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.724.1706&rep=rep1&type=pdf)
* [Multileader WAN Paxos: Ruling the Archipelago with Fast Consensus](https://cse.buffalo.edu/tech-reports/2017-01.pdf)
* [Scalable Consistency in Scatter](https://homes.cs.washington.edu/~tom/pubs/scatter.pdf)
* [GlobalFS: A Strongly Consistent Multi-Site File System](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7794339)
* [CalvinFS: Consistent WAN Replication and Scalable Metadata Management for Distributed File Systems](https://www.usenix.org/system/files/conference/fast15/fast15-paper-thomson.pdf)
* [Modelling Paxos performance in wide area](http://charap.co/modeling-paxos-performance-in-wide-area-part-3/)
* [Low-Latency Multi-Datacenter Databases using Replicated Commit](http://www.vldb.org/pvldb/vol6/p661-mahmoud.pdf)
* [FaunaDB: An Architectural Overview](https://fauna-assets.s3.amazonaws.com/public/FaunaDB-Technical-Whitepaper.pdf)

Distributed consensus in production
* [Paxos Made Live - An Engineering Perspective](https://www.cs.utexas.edu/users/lorenzo/corsi/cs380d/papers/paper2-1.pdf)
* [The Chubby lock service for loosely-coupled distributed systems](https://static.googleusercontent.com/media/research.google.com/en//archive/chubby-osdi06.pdf)
* [Megastore: Providing Scalable, Highly Available Storage for Interactive Services](http://cidrdb.org/cidr2011/Papers/CIDR11_Paper32.pdf)
  * seems to use an unusual definition of Multi-Paxos where each instance is district but the 1a/1b messages for slot i is piggybacked onto 2a2/b for i-1  
  * uses SMR with witnesses, replicas with participate in log replication but do not run a state machine and read-only replicas which only run a state machine.
* [Zab: High-performance broadcast for primary-backup systems](https://knowably-attachments.s3.amazonaws.com/u/55b69a1ce4b00ab397d67250/7c8734d3cf02154499a9b3161ef9f575/Zab_2011.pdf)
* [ZooKeeper: Wait-free coordination for Internet-scale systems](https://www.usenix.org/legacy/event/atc10/tech/full_papers/Hunt.pdf)
  * Widely utilized Apache licensed open source project written in Java [[project website]](https://zookeeper.apache.org)
  * Architecture is similar to Google's Chubby but unlike Chubby is described in detail and open source
  * Writes are linearizable, reads may be stale unless sync is called first
  * Clients may have multiple outstanding requests, they will be handled FIFO
  * Uses primary-backup replication instead of state machine replication
* [PaxosStore: High-availability Storage Made Practical in WeChat](http://www.vldb.org/pvldb/vol10/p1730-lin.pdf)
* [Windows Azure Storage: a highly available cloud storage service with strong consistency](https://dl.acm.org/citation.cfm?id=2043571)
* [Distributed Coordination Engine (DConE)](https://www.wandisco.com/assets/blt1d792cb4d9252692/WANdisco_DConE_White_Paper.pdf)
* [Bizur: A Key-value Consensus Algorithm for Scalable File-systems](https://arxiv.org/pdf/1702.04242.pdf)

Implementations of consensus
* [Replication and fault-tolerance in the ISIS system](https://ecommons.cornell.edu/handle/1813/6508)
* [The ISIS project: real experience with a fault tolerant programming system](https://dl.acm.org/citation.cfm?id=122133)
* [In Search of an Understandable Consensus Algorithm (Extended Version)](https://raft.github.io/raft.pdf)
  * aka the RAFT consensus paper
  * algorithm implemented by [etcd](https://etcd.io)
    * open sourced and widely utilized including by [kubernetes](https://kubernetes.io)
    * written in golang
  * implemented by [CockroachDB](https://www.cockroachlabs.com/docs/stable/)
* [Consensus: Bridging Theory and Practice](https://github.com/ongardie/dissertation)
  * PhD thesis describing RAFT consensus in more detail
* [S-Paxos: Offloading the Leader for High Throughput State Machine Replication](https://infoscience.epfl.ch/record/179912/files/2012_SPaxos-CameraReady.pdf)
* [Optimizing Paxos with batching and pipelining](https://infoscience.epfl.ch/record/189440/files/TCS.pdf)
* [Paxos for System Builders: An Overview](http://www.cnds.jhu.edu/pub/papers/psb_ladis_08.pdf)
* [Partitioned Paxos via the Network Data Plane](https://arxiv.org/abs/1901.08806meni)
* [The SMART Way to Migrate Replicated Stateful Services](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/eurosys2006.pdf)
* [Boxwood: Abstractions as the Foundation for Storage Infrastructure](https://www.usenix.org/legacy/event/osdi04/tech/full_papers/maccormick/maccormick.pdf)
* [Replication in the Harp File System](http://www.pmg.csail.mit.edu/papers/harp.pdf)
* [CORFU: A Distributed Shared Log](https://dl.acm.org/citation.cfm?id=2535930)
* [Tango: Distributed data structures over a shared log](http://www.cs.cornell.edu/~taozou/sosp13/tangososp.pdf)
* [The Farsite Project: A Retrospective](https://www.microsoft.com/en-us/research/wp-content/uploads/2007/04/OSR2007-4aa.pdf)
* [Using Paxos to Build a Scalable, Consistent, and Highly Available Datastore](https://dl.acm.org/citation.cfm?id=1938549)
* [Paxos replicated state machines as the basis of a high-performance data store](https://dl.acm.org/citation.cfm?id=1972472)
* [Granola: Low-Overhead Distributed Transaction Coordination](https://www.usenix.org/system/files/conference/atc12/atc12-final118.pdf)
* [Making Fast Consensus Generally Faster](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7579738)
* [Scalable State-Machine Replication](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6903591)
* [Calvin: Fast Distributed Transactions for Partitioned Database Systems](http://cs.yale.edu/homes/thomson/publications/calvin-sigmod12.pdf)
* [Paxos made transparent](https://dl.acm.org/citation.cfm?doid=2815400.2815427)
* [Designing Distributed Systems Using Approximate Synchrony in Data Center Networks](https://syslab.cs.washington.edu/papers/specpaxos-nsdi15.pdf)
* [No compromises: distributed transactions with consistency, availability, and performance](https://pdos.csail.mit.edu/6.824/papers/farm-2015.pdf)
* [Building Consistent Transactions with Inconsistent Replication](https://irenezhang.net/papers/tapir-sosp15.pdf)
  * Weakly consistent key-val store with support for linearizability as requested
  * Useful related blog post [Lessons learned from TAPIR(s)](https://irenezhang.net/blog/2015/04/02/tapir.html)
  * geo-distributed performance is evaluated
* [Commodifying Replicated State Machines with OpenReplica](https://ecommons.cornell.edu/handle/1813/29009)


### Papers on related topics

Linearizability & SMR
* [Implementing Fault-Tolerant Services Using the State Machine Approach: A Tutorial](https://www.cs.cornell.edu/fbs/publications/SMSurvey.pdf)
* [Linearizability: A Correctness Condition for Concurrent Objects](https://cs.brown.edu/~mph/HerlihyW90/p463-herlihy.pdf)
* [Implementing Linearizability at Large Scale and Low Latency](https://dl.acm.org/citation.cfm?id=2815416)
* [Cheap and Available State Machine Replication](https://www.usenix.org/system/files/conference/atc16/atc16_paper-shi.pdf)

Weaker consistency models
* [Existential Consistency: Measuring and Understanding Consistency at Facebook](http://sigops.org/s/conferences/sosp/2015/current/2015-Monterey/printable/240-lu.pdf)
* [What consistency does your key-value store actually provide?](https://www.usenix.net/legacy/events/hotdep10/tech/full_papers/Anderson.pdf)
  * offline consistency checking of key-value traces
* [TAO: Facebook’s Distributed Data Store for the Social Graph](https://www.usenix.org/system/files/conference/atc13/atc13-bronson.pdf)
* [Consistency in Non-Transactional Distributed Storage Systems](http://www.vukolic.com/consistency-survey.pdf)
* [Dynamo: Amazon’s Highly Available Key-value Store](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)
* [Bigtable: A Distributed Storage System for Structured Data](https://static.googleusercontent.com/media/research.google.com/en//archive/bigtable-osdi06.pdf)
* [Spanner: Google’s Globally-Distributed Database](https://static.googleusercontent.com/media/research.google.com/en//archive/spanner-osdi2012.pdf)
  * Provides linearizability but it assumes a bounded clock drift
  * Google implement this using Truetime, GPS and atomic clocks in their data centers instead of NTP
  * Closed source but now available as a cloud service, [Cloud Spanner](https://cloud.google.com/spanner/)
* [Cassandra - A Decentralized Structured Storage System](https://www.cs.cornell.edu/projects/ladis2009/papers/lakshman-ladis2009.pdf)
  * not discussion in paper but Cassandra now uses Paxos for [lightweight transactions](https://docs.datastax.com/en/archived/cassandra/3.0/cassandra/dml/dmlLtwtTransactions.html).
* [Spanner, TrueTime & The CAP Theorem](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45855.pdf)
* [Towards Robust Distributed Systems](https://people.eecs.berkeley.edu/~brewer/cs262b-2004/PODC-keynote.pdf)
  * PODC keynote in which Eric Brewer proposed the now infamous CAP theorem
* [Quantifying eventual consistency with PBS](http://www.bailis.org/papers/pbs-vldbj2014.pdf)
* [Eventual Consistency Today: Limitations, Extensions, and Beyond](https://queue.acm.org/detail.cfm?id=2462076)
* [Fine-grained consistency for geo-replicated systems](https://www.usenix.org/system/files/conference/atc18/atc18-li_cheng.pdf)
* [The many faces of consistency](http://sites.computer.org/debull/A16mar/p3.pdf)
* [Benchmarking Cloud Serving Systems with YCSB](https://www2.cs.duke.edu/courses/fall13/compsci590.4/838-CloudPapers/ycsb.pdf)
  * Popular benchmarking tool for key-values stores
  * Actively maintained [open source project](https://github.com/brianfrankcooper/YCSB/wiki) with support for various data stores
* [Leases: An Efficient Fault-Tolerant Mechanism for Distributed File Cache Consistency](https://web.stanford.edu/class/cs240/readings/89-leases.pdf)
  * This paper introduced the idea of leases for distributed caches. This idea is used in master leases and read quorum leases

Failures & Bugs
* [The Network is Reliable: An informal survey of real-world communications failures](https://queue.acm.org/detail.cfm?id=2655736)
* [Communication Costs in Real-world Networks](http://www.bailis.org/blog/communication-costs-in-real-world-networks/)
* [What Bugs Live in the Cloud? A Study of 3000+ Issues in Cloud Systems](https://ucare.cs.uchicago.edu/pdf/socc14-cbs.pdf)

Correctness of consensus algorithms
* [IronFleet: Proving Practical Distributed Systems Correct](http://sigops.org/s/conferences/sosp/2015/current/2015-Monterey/printable/250-hawblitzel.pdf)
* [Paxos Made EPR: Decidable Reasoning about Distributed Protocols](https://dl.acm.org/citation.cfm?doid=3152284.3140568)
* [Verdi: A framework for implementing and formally verifying distributed systems](https://homes.cs.washington.edu/~ztatlock/pubs/verdi-wilcox-pldi15.pdf)
* [A Proof of Correctness for Egalitarian Paxos](http://www.cs.cmu.edu/~imoraru/epaxos/tr.pdf)
* [Specifying Systems: The TLA+ Language and Tools for Hardware and Software Engineers](https://lamport.azurewebsites.net/tla/book-02-08-08.pdf)
* [Modeling Paxos and Flexible Paxos in Pluscal and TLA+](http://muratbuffalo.blogspot.com/2016/11/modeling-paxos-and-flexible-paxos-in.html)

Quorum systems
* [A Majority Consensus Approach to Concurrency Control for Multiple Copy Databases](https://dl.acm.org/citation.cfm?id=320076)
* [Weighted Voting for Replicated Data](http://pages.cs.wisc.edu/~remzi/Classes/739/Fall2015/Papers/gifford79.pdf)
* [An Efficient and Fault-tolerant Solution for Distributed Mutual Exclusion](https://users.soe.ucsc.edu/~scott/courses/Fall11/221/Papers/Sync/agrawal-tocs91.pdf)
* [The Generalized Tree Quorum Protocol: An Efficient Approach for Managing Replicated Data](https://dl.acm.org/citation.cfm?id=146935)
* [The Reliability of Voting Mechanisms](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=1676860)
* [The grid protocol: a high performance scheme for maintaining replicated data](https://ieeexplore.ieee.org/abstract/document/180609)
* [How to Assign Votes in a Distributed System](https://dl.acm.org/citation.cfm?id=4223)
* [Hierarchical Quorum Consensus: A New Algorithm for Managing Replicated Data](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=83661)
* [The Load, Capacity, and Availability of Quorum Systems](https://epubs.siam.org/doi/pdf/10.1137/S0097539795281232)
* [A √N algorithm for mutual exclusion in decentralized systems](https://dl.acm.org/citation.cfm?id=214445)
* [The Availability of Quorum Systems](https://pdfs.semanticscholar.org/ab7d/30f7a808173bc305d679262f9838869cb681.pdf)
* [Coterie Availability in Sites](https://link.springer.com/chapter/10.1007/11561927_3)
* [The virtue of dependent failures in multi-site systems](https://dl.acm.org/citation.cfm?id=1973401)
* [Crumbling Walls: A Class of Practical and Efficient Quorum Systems](https://link.springer.com/article/10.1007/s004460050027)

Reading lists
* [Testing Distributed Systems by Andrey Satarin](https://asatarin.github.io/testing-distributed-systems/)
* [An introduction to distributed systems by Kyle Kingsbury](https://github.com/aphyr/distsys-class)

### Future reading list
The following lists contain places to watch for new writings in the field of distributed consensus.

Blogroll
* [Jepsen by Kyle Kingsbury](https://jepsen.io)
* [Aphyr by Kyle Kingsbury](https://aphyr.com/posts)
* [The Paper Trail](https://www.the-paper-trail.org)
* [Brave new geek by Tyler Treat](https://bravenewgeek.com/archive/)
* [Highly Available, Seldom Consistent by Peter Bailis](http://www.bailis.org/blog/)
* [Christopher Meiklejohn](http://christophermeiklejohn.com)
* [Denis Rystsov](http://rystsov.info)
* [Metadata by Murat Demirbas](http://muratbuffalo.blogspot.com)
* [Slash dev slash null](https://simbo1905.blog)
* [David Turner](https://davecturner.github.io)
* [Aleksey Charapko](http://charap.co)
* [The Morning Paper by Adrian Colyer](https://blog.acolyer.org/about/)
* [Hacking, Distributed by Emin Gün Sirer](http://hackingdistributed.com)
* [All Things Distributed by Werner Vogels](https://www.allthingsdistributed.com)

Academic conferences & symposiums
* [ACM Symposium on Principles of Distributed Computing (PODC)](http://www.podc.org)
* [IEEE/IFIP International Conference on Dependable Systems and Networks (DSN)](http://2019.dsn.org)
* [IEEE International Conference on Distributed Computing Systems (ICDCS)](https://theory.utdallas.edu/ICDCS2019/)
* [International Conference on Principles of Distributed Systems (OPODIS)](https://opodis2019.unine.ch)
* [International Symposium on Distributed Computing (DISC)](http://www.disc-conference.org/wp/disc2019/)
* [International Symposium on Reliable Distributed Systems (SRDS)](https://srds2019.projet.liris.cnrs.fr)
* [ACM Symposium on Parallelism in Algorithms and Architectures (SPAA)](https://spaa.acm.org/2019/)
* [USENIX Symposium on Networked Systems Design and Implementation (NSDI)](https://www.usenix.org/conference/nsdi20)
* [USENIX Symposium on Operating Systems Design and Implementation (OSDI)](https://www.usenix.org/conference/osdi18) - Biennial evens
* [ACM Symposium on Operating Systems Principles (SOSP)](https://sosp19.rcs.uwaterloo.ca) - Biennial odds
* [USENIX Annual Technical Conference (ATC)](https://www.usenix.org/conference/atc19)
* [European Conference on Computer Systems (EuroSys)](https://2019.eurosys.org)
* [ACM SIGMOD/PODS Conference](https://sigmod2019.org)
* [ACM SIGMETRICS / IFIP Performance](https://www.sigmetrics.org/sigmetrics2019/)
* [ACM Annual Conference of the Special Interest Group on Data Communication (SIGCOMM)](http://sigcomm.org/events/sigcomm-conference)
* [USENIX Conference on File and Storage Technologies (FAST)](https://www.usenix.org/conference/fast20)
* [ACM SIGPLAN Conference on Programming Language Design and Implementation (PLDI)](https://pldi19.sigplan.org)
* [International Conference on Very Large Data Bases (VLDB)](http://vldb.org/2019/)
* [ACM Symposium on Cloud Computing (SoCC)](https://acmsocc.github.io/2019/)
* [ACM Symposium on Theory of Computing (STOC)](http://acm-stoc.org/stoc2019/)

Workshops
* [Workshop on Principles and Practice of Consistency for Distributed Data (PaPoC)](https://novasys.di.fct.unl.pt/conferences/papoc19/)
* [ACM SIGOPS Workshop on Large-Scale Distributed Systems and Middleware (LADIS)](http://ladisworkshop.org)
* [USENIX Workshop on Hot Topics in Storage and File Systems (HotStorage)](https://www.usenix.org/conference/hotstorage19)
* [Workshop on Hot Topics in Operating Systems (HotOS)](https://www.sigops.org/2018/hotos2019/)
* [ACM Workshop on Hot Topics in Networks (HotNets)](https://conferences.sigcomm.org/hotnets/2019/)
* [USENIX Workshop on Hot Topics in Cloud Computing (HotCloud)](https://www.usenix.org/conference/hotcloud19)
* [USENIX Workshop on Hot Topics in Edge Computing (HotEdge)](https://www.usenix.org/conference/hotedge19)

Journals & Magazines
* [ACM Transactions on Computer Systems (TOCS)](https://tocs.acm.org)
* [Journal of the ACM (JACM)](https://jacm.acm.org)
* [Communications of the ACM (CACM)](https://cacm.acm.org)
* [SIGOPS Operating Systems Review (OSR)](https://www.sigops.org/osr.html)
* [ACM Computing Surveys (CSUR)](https://csur.acm.org)
* [ACM Transactions on Database Systems (TODS)](https://tods.acm.org)
* [ACM Queue](https://queue.acm.org)
* [ACM SIGACT News](https://dl.acm.org/citation.cfm?id=J697)
* [IEEE Transactions on Dependable and Secure Computing (TDSC)](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=8858)
* [IEEE Transactions on Parallel and Distributed Systems (TPDS)](https://www.computer.org/csdl/journal/td)
* [IEEE Transactions on Computers (TC)](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=12)
* [IEEE Transactions on Software Engineering](https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=32)
