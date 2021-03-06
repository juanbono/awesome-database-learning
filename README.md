# Awesome Database Learning

A list of learning materials to understand databases internals, including but not limited to:

- papers
- blogs
- courses
- talks

Please submit a pull request if there is any material that you think should be included in this collection.

## Table of Contents

<!-- vim-markdown-toc GFM -->

* [SQL & Relation Algebra](#sql--relation-algebra)
* [Query Optimizer](#query-optimizer)
    * [Planner Models](#planner-models)
    * [Cost Model](#cost-model)
    * [Statistics](#statistics)
* [Query Execution](#query-execution)
    * [Execution Framework](#execution-framework)
    * [Vectorization vs Compilization](#vectorization-vs-compilization)
    * [Join](#join)
* [DDL](#ddl)
* [Transaction](#transaction)
    * [Isolation Levels](#isolation-levels)
    * [Concurrency Control](#concurrency-control)
* [Network](#network)
* [Storage](#storage)
    * [Disk IO](#disk-io)
    * [B-Tree](#b-tree)
    * [LSM-Tree](#lsm-tree)
* [Serializing & RPC](#serializing--rpc)
* [Data Partitiioning](#data-partitiioning)
* [Replication & Consistency](#replication--consistency)
* [Consensus](#consensus)
* [Scale & Blance](#scale--blance)
* [Benchmark & Testing](#benchmark--testing)

<!-- vim-markdown-toc -->

## SQL & Relation Algebra

Courses:

- CMU [Database Systems (15-445/645)](https://15445.courses.cs.cmu.edu/fall2019/schedule.html), thanks to [Andy Pavlo](http://www.cs.cmu.edu/~pavlo/)
    - [Course Introduction and the Relational Model](https://15445.courses.cs.cmu.edu/fall2019/schedule.html#aug-26-2019)
    - [Advanced SQL](https://15445.courses.cs.cmu.edu/fall2019/schedule.html#aug-28-2019)

- UC Berkeley [Introduction to Database Systems](https://cs186berkeley.net/calendar/)
    - Introduction + SQL I
    - SQL II
    - Relational Algebra

## Query Optimizer

Blogs:

- [数据库内核杂谈](https://www.infoq.cn/theme/46), thanks to [顾仲贤](https://www.infoq.cn/profile/1780661/publish)
    - [数据库内核杂谈（七）：数据库优化器（上）](https://www.infoq.cn/article/GhhQlV10HWLFQjTTxRtA)
    - [数据库内核杂谈（八）：数据库优化器（下）](https://www.infoq.cn/article/JCJyMrGDQHl8osMFQ7ZR)
- [SQL优化器原理 - 查询优化器综述](https://yq.aliyun.com/articles/610128), thanks to [勿烦](https://yq.aliyun.com/users/kyni3qcv656rk?spm=a2c4e.11153940.0.0.6adc1a8etfb0vx)

### Planner Models

Blogs:

- [数据库内核杂谈](https://www.infoq.cn/theme/46), thanks to [顾仲贤](https://www.infoq.cn/profile/1780661/publish)
    - [数据库内核杂谈（九）：开源优化器 ORCA](https://www.infoq.cn/article/5o16eHOZ5zk6FzPSJpT2)
- [SQL 查询优化原理与 Volcano Optimizer 介绍](https://zhuanlan.zhihu.com/p/48735419), thanks to [张茄子](https://www.zhihu.com/people/chase-zh)
- [Cascades Optimizer](https://zhuanlan.zhihu.com/p/73545345), thanks to [hellocode](https://www.zhihu.com/people/hellocode-ming)

Papers:

- 1979, [Access Path Selection in a Relational Database Management System](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.71.3735&rep=rep1&type=pdf), SIGMOD
- 1979, [Query Processing in Main Memory Database Management Systems](http://15721.courses.cs.cmu.edu/spring2016/papers/p239-lehman.pdf), VLDB
- 1987, [Query Optimization by Simulated Annealing](http://ftp.cs.wisc.edu/pub/techreports/1987/TR693.pdf), SIGMOD
- 1988, [Grammar-like Functional Rules for Representing Query Optimization Alternatives](https://people.eecs.berkeley.edu/~brewer/cs262/23-lohman88.pdf), SIGMOD
- 1993, [The Volcano Optimizer Generator- Extensibility and Efficient Search](https://pdfs.semanticscholar.org/a817/a3e74d1663d9eb35b4baf3161ab16f57df85.pdf), ICDE
- 1995, [The Cascades Framework for Query Optimization](https://pdfs.semanticscholar.org/360e/cdfc79850873162ee4185bed8f334da30031.pdf), IEEE Data engineering Bulltin
- 1998, [An Overview of Query Optimization in Relational Systems](https://web.stanford.edu/class/cs345d-01/rl/chaudhuri98.pdf), PODS
- 2001, [LEO – DB2’s LEarning Optimizer](http://15721.courses.cs.cmu.edu/spring2016/papers/stillger-vldb2001.pdf), VLDB
- 2004, [Robust Query Processing through Progressive Optimization](https://www.cse.iitb.ac.in/infolab/Data/Courses/CS632/2006/Papers/sigmod04-markl.pdf), SIGMOD
- 2014, [Orca: A Modular Query Optimizer Architecture for Big Data](http://15721.courses.cs.cmu.edu/spring2016/papers/p337-soliman.pdf), SIGMOD
- 2016, [Parallelizing Query Optimization on Shared-Nothing Architectures](http://www.vldb.org/pvldb/vol9/p660-trummer.pdf), VLDB
- 2016, [The MemSQL Query Optimizer: A modern optimizer for real-time analytics in a distributed database](http://www.vldb.org/pvldb/vol9/p1401-chen.pdf), VLDB

### Cost Model

Papers:

- 1996, [Modelling Costs for a MM-DBMS](), in Real-Time Databases
- 2014, [Approximation Schemes for Many-Objective Query Optimization](https://infoscience.epfl.ch/record/219202/files/p1299-trummer.pdf), SIGMOD
- 2015, [Multi-Objective Parametric Query Optimization](http://www.vldb.org/pvldb/vol8/p221-trummer.pdf), VLDB

### Statistics

Papers:

- 2005, [An Improved Data Stream Summary: The Count-Min Sketch and its Applications](http://dimacs.rutgers.edu/~graham/pubs/papers/cm-full.pdf), Journal of Algorithms
- 2007, [New Estimation Algorithms for Streaming Data: Count-min Can Do More](http://webdocs.cs.ualberta.ca/~drafiei/papers/cmm.pdf)
- 2017, [Adaptive Statistics in Oracle 12c](http://www.vldb.org/pvldb/vol10/p1813-zait.pdf), VLDB

Books:
- [Synopses for Massive Data: Samples, Histograms, Wavelets, Sketches](https://db.cs.berkeley.edu/cs286/papers/synopses-fntdb2012.pdf)

## Query Execution

### Execution Framework

Papers:

- 1994, [Volcano-An Extensible and Parallel Query Evaluation System](https://paperhub.s3.amazonaws.com/dace52a42c07f7f8348b08dc2b186061.pdf), IEEE Transactions on Knowledge and Data EngineeringFebruary
- 2014, [Morsel-Driven Parallelism: A NUMA-Aware Query Evaluation Framework for the Many-Core Age](https://15721.courses.cs.cmu.edu/spring2019/papers/14-scheduling/p743-leis.pdf), SIGMOD

### Vectorization vs Compilization

Blogs:

- [Overhead of a Generalized Query Execution Engine](https://github.com/pivotal/blog/blob/master/content/post/codegen-gpdb-qx.md), from [The Pivotal Engineering Journal](https://github.com/pivotal/blog), thannks to the Pivotal Engineering team

Papers:

- 2005, [MonetDB/X100: Hyper-Pipelining Query Execution](http://cidrdb.org/cidr2005/papers/P19.pdf), CIDR
- 2011, [Efficiently Compiling Efficient Query Plans for Modern Hardware](https://www.vldb.org/pvldb/vol4/p539-neumann.pdf), VLDB
- 2017, [Relaxed Operator Fusion for In-Memory Databases: Making Compilation, Vectorization, and Prefetching Work Together At Last](http://www.vldb.org/pvldb/vol11/p1-menon.pdf), VLDB
- 2018, [Everything You Always Wanted to Know About Compiled and Vectorized Queries But Were Afraid to Ask](http://www.vldb.org/pvldb/vol11/p2209-kersten.pdf), VLDB

### Join

Papers:

- 2013, [Multi-Core, Main-Memory Joins: Sort vs. Hash Revisited](http://www.vldb.org/pvldb/vol7/p85-balkesen.pdf), VLDB
- 2017, [Looking Ahead Makes Query Plans Robust](http://www.vldb.org/pvldb/vol10/p889-zhu.pdf), VLDB

## DDL

- 2013, [Online, Asynchronous Schema Change in F1](https://research.google.com/pubs/archive/41376.pdf), VLDB

## Transaction

### Isolation Levels

Blogs:

- [一致性模型](https://www.jianshu.com/p/3673e612cce2), thanks to [siddontang](https://www.jianshu.com/u/1yJ3ge)

Papers:

- 1995, [A Critique of ANSI SQL Isolation Levels](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-95-51.pdf), SIGMOD

### Concurrency Control

Courses:

- CMU [Database Systems (15-445/645)](https://15445.courses.cs.cmu.edu/fall2019/schedule.html), thanks to [Andy Pavlo](http://www.cs.cmu.edu/~pavlo/)
    - [Concurrency Control Theory](https://15445.courses.cs.cmu.edu/fall2019/schedule.html#oct-23-2019)
    - [Two-Phase Locking Concurrency Control](https://15445.courses.cs.cmu.edu/fall2019/schedule.html#oct-28-2019)
    - [Timestamp Ordering Concurrency Control](https://15445.courses.cs.cmu.edu/fall2019/schedule.html#oct-30-2019)
    - [Multi-Version Concurrency Control](https://15445.courses.cs.cmu.edu/fall2019/schedule.html#nov-04-2019)

- CMU [Advanced Database Systems (15-721)](https://15721.courses.cs.cmu.edu/spring2020/schedule.html), thanks to [Andy Pavlo](http://www.cs.cmu.edu/~pavlo/)
    - [Multi-Version Concurrency Control (Design Decisions)](https://15721.courses.cs.cmu.edu/spring2020/schedule.html#jan-22-2020)
    - [Multi-Version Concurrency Control (Protocols)](https://15721.courses.cs.cmu.edu/spring2020/schedule.html#jan-27-2020)
    - [Multi-Version Concurrency Control (Garbage Collection)](https://15721.courses.cs.cmu.edu/spring2020/schedule.html#jan-29-2020)

Papers:

- 2012, [Serializable Snapshot Isolation in PostgreSQL](http://www.vldb.org/pvldb/vol4/p783-jung.pdf), VLDB
- 2015, [Fast Serializable Multi-Version Concurrency Control for Main-Memory Database Systems](https://db.in.tum.de/~muehlbau/papers/mvcc.pdf), SIGMOD
- 2017, [An Empirical Evaluation of In-Memory Multi-Version Concurrency Control](http://www.vldb.org/pvldb/vol10/p781-Wu.pdf), VLDB
- 2019, [Scalable Garbage Collection for In-Memory MVCC Systems](https://db.in.tum.de/~boettcher/p128-boettcher.pdf), VLDB

## Network

Courses:

- CMU [Advanced Database Systems (15-721)](https://15721.courses.cs.cmu.edu/spring2020/schedule.html), thanks to [Andy Pavlo](http://www.cs.cmu.edu/~pavlo/)
    - [Networking Protocols](https://15721.courses.cs.cmu.edu/spring2020/schedule.html#feb-19-2020)

Papers:

- 2016, [The End of Slow Networks: It's Time for a Redesign](http://www.vldb.org/pvldb/vol9/p528-binnig.pdf), VLDB
- 2016, [Accelerating Relational Databases by Leveraging Remote Memory and RDMA](https://15721.courses.cs.cmu.edu/spring2020/papers/11-networking/li-sigmod2016.pdf), SIGMOD
- 2017, [Don't Hold My Data Hostage: A Case for Client Protocol Redesign](http://www.vldb.org/pvldb/vol10/p1022-muehleisen.pdf), VLDB

## Storage

### Disk IO

Blogs:

- [On Disk IO, Part 1: Flavors of IO](https://medium.com/databasss/on-disk-io-part-1-flavours-of-io-8e1ace1de017), thanks to [Alex](https://twitter.com/ifesdjeen)
- [On Disk IO, Part 2: More Flavours of IO](https://medium.com/databasss/on-disk-io-part-2-more-flavours-of-io-c945db3edb13?), thanks to [Alex](https://twitter.com/ifesdjeen)
- [Read, write & space amplification - pick 2](http://smalldatum.blogspot.com/2015/11/read-write-space-amplification-pick-2_23.html), thanks to [Mark Callaghan](https://twitter.com/markcallaghandb)

Papers:

- 2016, [Design Tradeoffs of Data Access Methods](http://scholar.harvard.edu/files/stratos/files/rum-tutorial.pdf?m=1461167186), SIGMOD
- 2016, [Designing Access Methods: The RUM Conjecture](https://stratos.seas.harvard.edu/files/stratos/files/rum.pdf), EDBT

### B-Tree

Courses:

- CMU [Advanced Database Systems (15-721)](https://15721.courses.cs.cmu.edu/spring2020/schedule.html), thanks to [Andy Pavlo](http://www.cs.cmu.edu/~pavlo/)
    - [OLTP Indexes (B+Tree Data Structures)](https://15721.courses.cs.cmu.edu/spring2020/schedule.html#feb-03-2020)

### LSM-Tree

## Serializing & RPC

## Data Partitiioning

## Replication & Consistency

## Consensus

## Scale & Blance

## Benchmark & Testing
