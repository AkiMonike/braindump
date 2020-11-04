+++
title = "When Bloom filters don't bloom"
author = ["Jethro Kuan"]
draft = false
+++

Modern CPUs are really good at sequential memory access, whet it's
possible to predict memory fetch patterns. Random memory access is
very costly.

Modern computers require cache-optimized algorithms. When working with
large datasets, not fitting L3 cache, prefer optimizing for reduced
number loads, over optimizing the amount of memory used.

[Bloom Filters]({{< relref "bloom_filter" >}}) are great, as long as they fit into the L3 cache. They
are optimized for memory usage, not memory access. A nice alternative
is [Cuckoo Filters]({{<relref "cuckoo_filters.md" >}}).
