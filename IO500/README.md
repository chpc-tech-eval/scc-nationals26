# IO500

IO500 is a ranked list like HPL and HPCG top 500 lists, such as https://io500.org/list/isc26/production

IO500 consists of a synthetic storage benchmark suite for HPC systems consisting of various
micro-benchmarks designed to test a cluster's storage solution with a variety of different workloads.
Critically, bulk storage bandwidth and metadata storage operations.

Links:
- Read up on IO500 https://io500.org/about
- Check out the repo https://github.com/IO500/io500
- The version of the benchmark to run https://github.com/IO500/io500/releases/tag/io500-isc26_v2

# CHPC SCC 26 Storage Challenge

### Ground rules:
- We'll be running the ISC26 V2 version of the IO500 benchmark.
- The target filesystem must be backed by persistent physical storage on your own nodes (HDD, SATA SSD or NVMe).
  Memory-backed filesystems (`tmpfs`, ramdisks) are not allowed. Data must survive a reboot.
- You will be expected to have the client reading/writing to storage on at least one other node. For example,
  you may have one of your compute nodes read/write from NFS on the head node, or you may wish
  to have all nodes read and write to all nodes' storage with a distributed file system.
- The filesystem must have POSIX-style semantics (standard file operations behaving consistently
  across nodes used for storage). NFS, Lustre, BeeGFS, CephFS and others are acceptable.
- The benchmark sizing and procedure will be designed to avoid RAM-cache-dominated results.
  The data must entirely reach persistent storage.
- Fault tolerance (e.g. RAID1) is not required.

### What to expect:
- Both a read/write bandwidth and read/write metadata benchmark will be involved.
- You will be expected to document how you've set up your system (drive partitioning, 
  RAID configuration, on-disk filesystems, shared filesystem).
- Expect to get the most points by using your persistent storage hardware as well as possible
  within the typical constraints of HPC (persistently-backed, shared, POSIX-compatible file systems).

### Scoring:
You'll be submitting your benchmark outputs and scores. Your scores will need to be
reproducible, in case we come around to ask you to replicate the run :)

As you may not have been designing your clusters with I/O benchmarks in mind your
scores will be partially weighted by the limitations of your system, so you won't
win-by-default just for having bought one of the pricey SSDs, but it will help!
The exact runs and weights will be released later, but you can expect that your
score will be correlated with how much of your system's total storage bandwidth
you can leverage and how many metadata operations your cluster can do.
Weights are TBD, but expect bulk storage bandwidth (GB/s) to be weighed higher than metadata benchmarks (IOP/S).
