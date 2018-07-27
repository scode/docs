Reading lists
=============

JVM garbage collection
----------------------

* `Uniprocessor Garbage Collection Techniques
  <https://people.cs.umass.edu/~emery/memory/papers/wils94/paper.pdf>`__
  is a good introduction to some core theoretical concepts. This is
  the paper I read many many years ago and originally helped me become
  interested in garbage collection.

* `A Generational Mostly-concurrent Garbage Collector
  <http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.5.2665&rep=rep1&type=pdf>`__
  is what I think of as "the CMS" paper. It describes the CMS
  (concurrent mark/sweep) collector in HotSpot. For many ears this was
  the best option for trying to achieve low latency. It's a
  non-copying non-compacting old generation collector.

* `Garbage-First Garbage Collection
  <http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.63.6386&rep=rep1&type=pdf>`__
  is "the G1" paper. G1 is a newer garbage collector than CMS. This
  time, it is responsible for both the young generation and the old
  generation and it's a copying and compacting collector.


* Azul collectors (these apply to Azul's JVM which AFAIK
  has never been freely available).

  * `The Pauseless GC Algorithm
    <https://www.usenix.org/legacy/events/vee05/full_papers/p46-click.pdf>`__
    describes the theory behing the C4 garbage collector used in the
    Azul JVMs.

  * `C4: The Continuously Concurrent Compacting Collector
    <https://www.azul.com/files/c4_paper_acm2.pdf>`__ is a follow-up
    paper on the previous one, going into a lot more implementation detail.

* Current (2018) "state of the art" with respect to GC in freely
  available HotSpot are `zgc
  <https://wiki.openjdk.java.net/display/zgc/Main>`__ and `shenandoah
  <https://wiki.openjdk.java.net/display/shenandoah/Main>`__.

Relatedly, you may be interested in `scode/lrugctest
<https://github.com/scode/lrugctest>`__ which is designed to stress a
garbage collector using a very simple simulation of a worst-case (for
the GC) LRU cache. As of mid 2018, zgc and shenandoah are the only
freely available HotSpot GCs that are capable of low (< 10 ms) pause
times under that workload.
