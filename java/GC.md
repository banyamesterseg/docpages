## Comparison of Java Garbage Collection algorithms

### Quick-and-dirty comparison chart

| GC name              | Flags | Availability | Details | Further reading |
| :------------------- | :---- | :----------- | :------ | :-------------- |
| SerialGC             |       |              |         |                 |
| ParallelGC           |       |              |         |                 |
| ParallelOldGC        |       |              |         |                 |
| ConcMarkSweepGC      |       |              |         |                 |
|   - incremental mode |       |              |         |                 |
| G1GC                 |       |              |         |                 |
| ShenandoahGC         |       |              |         |                 |
|   - incremental mode |       |              |         |                 |
| ZGC                  |       |              |         |                 |

### Proto-GCs
naive algorithms never used on their own, but may be used by other GCs
Understanding them is required to understand most used GC algorithms

### SerialGC
### ParallelGC
### ParallelOldGC
### ConcMarkSweepGC
### G1GC
### ShenandoahGC
### ZGC

Basic algos, never used on their own as GC
                             fires when a heap space use watermark is reached
                             has to stop every thread while mark run
  mark-sweep               - as simple as it gets: mark used objects, delete what isn't marked
                             This would cause OOMError when you try to allocate more than the largest gap between existing objects
  mark-sweep-compact       - de-fragment empty memory by moving objects to the start to alleviate the OOMError problem
                             compact stops threads too
  mark-copy                - needs 2x the RAM, copy live objects to the other half, empty first half
                             Switching the semi-spaces still halts all threads

  CMS, ConcMarkSweepGC     - three generations, young, old, permanent; new allocations go into young
                             mark-copy on young periodically and on high water mark, multiple parallel threads; stops affected only
                             mark-sweep on old & permanent, triggered only by high water mark, concurrent threads
                             https://docs.oracle.com/javase/8/docs/technotes/guides/vm/gctuning/cms.html
  iCMS, CMSIncrementalMode - a mode of CMS; only does a little bit of m&s on old/permanent every time; depr in SE 8
                             https://docs.oracle.com/javase/8/docs/technotes/guides/vm/gctuning/cms.html
Shenandoah                 - backported to SE 8, requires build-time flag in SE 11, so may or may not be available in your flavor of older OpenJDK versions; enabled by default in current releases
                             https://wiki.openjdk.java.net/display/shenandoah/Main
