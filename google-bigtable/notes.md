# BigTable Reading Notes

## Intro

Google BigTable is a Distributed Database that supports a flexible database schema, which is helpful for many use cases. 

It supports the following operations:
* Read, Write
* Single Row Transaction (Update several columns at the same time, CAS)
* Prefix Scan

It DOES NOT support multi row transactions (which is the actual distributed transaction)

It can also be used as a Map-Reduce data source.

## Architecture.

BigTable consists of the following components:
- Client SDK
- Master Server (kvmaster)
- Tablet Server (partition server)
- Chubby Service (The core of the system)

* Client SDK, each client that talk to BigTable need to have the client SDK in order to perform the location lookup and send read/write requests.

* Master Server: The place where all the METADATA information is stored. It contains the location information of all the tablets(ranges)

* Tablet Server: The actual server that serves the data to users. Each tablet server has several “tablets”(partitions). The location of the tablets are recorded in the Master Server. The master server will try to create a new tablet, it will contact serveral tablet servers to create the tablet (thus they form a new raft group).

* Chubby Service: Act as the ONLY “Central Brain” of the system, the service need to maintain very high availability, since if the service is down, the master node cannot know the “ROOT NODE” of the whole cluster.

## Tablet Server

* It supports merging and splitting the tablets. Each tablets is a range of sorted lexicgraphic ordered keys.
* Tablet Server also updates the Chubby Store.


## Answer the 10 questions

Q2: Is it a new question?
A2: Yes, and the open source project “HBase” “HDFS” is based on the BigTable paper.

## My Questions

- How does the tablet server report its location? 
- A: The tablet server do not report its location in the most of the time, the location is managed by the Master Server. even when the tablet server is splitting some tablets, the splitting result will not be guaranteed to be notified to the master server. Instead, the master server will know the split when it try to fetch the range information from the METADATA directory.

- How does the Tablet Server perform “Merge” operations.

