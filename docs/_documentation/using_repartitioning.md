---
title: Repartitioning
position: 12
---

## Repartitioning

Throughput of event type is defined by default statistic, which basically sets number of partitions for the event
 type (although it does not represent it clearly). Number of partitions is a scaling unit for Nakadi publishing and
  consumption. In order to change number of partitions one have to repartition event type by changing
   read_parallelism and write_parallelism. Nakadi takes for repartitioning the maximum of read_parallelism and
    write_parallelism.

### Important caveats

- Publishing events to event type with hash partition strategy will change the partitions in which they were appearing
 before
- Nakadi guarantees ordering per partition per batch, repartitioning event types from 1 partitions to more will break
 total order of events
- Repartitioning allows to only increase number of partitions
- Consuming subscriptions are disconnected once repartitioning is finished