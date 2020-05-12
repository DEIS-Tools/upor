# upor
Urgent Partial Order Reduction
==================================

The repository contains case study models and prototype binary for ATVA paper submission.

The binary assumes 64-bit Linux distribution.

Example
========

Evaluate a deadlock check on simple FireAlarm instance with 16 sensors execute the following:

```bash
time ./bin/verifyta -squ FireAlarm/fireAlarm_16.xml FireAlarm/AGnotdeadlock.q

Verifying formula 1 at FireAlarm/AGnotdeadlock.q:1
 -- Formula is satisfied.
 -- States stored : 65583 states
 -- States explored : 65583 states
 -- CPU user time used : 4430 ms
 -- Virtual memory used : 79272 KiB
 -- Resident memory used : 28236 KiB

real    0m4,482s
user    0m4,465s
sys     0m0,017s
```

Evaluate a deadlock check on the same instance with **Partial Order Reduction** turned on, set the environment variables `UPPAAL_UPOR` and `UPPAAL_REACHABLEACT`, for example:

```bash
UPPAAL_REACHABLEACT=1 UPPAAL_UPOR=1 time ./bin/verifyta -squ FireAlarm/fireAlarm_16.xml FireAlarm/AGnotdeadlock.q 

Verifying formula 1 at FireAlarm/AGnotdeadlock.q:1
 -- Formula is satisfied.
 -- States stored : 184 states
 -- States explored : 184 states
 -- CPU user time used : 10 ms
 -- Virtual memory used : 72248 KiB
 -- Resident memory used : 11956 KiB
0.02 user, 0.00 kernel, 0.02 elapsed, 0:00.02 wall-clock, 12244 kb_MaxRSS
```
