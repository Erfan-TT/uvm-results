# Windowed register-file result summary

| Metric | Result |
| --- | ---: |
| Scoreboard | 1,058 checks, 0 mismatches |
| Functional coverage | 69/69 bins |
| Statement coverage | 36/38 (94.73%) |
| Branch coverage | 35/37 (94.59%) |
| Toggle coverage | 438/438 |
| Assertion coverage | 100% |
| Filtered overall coverage | 97.86% |
| Post-synthesis functional coverage | 69/69 bins |
| Clock constraint | 3.00 ns |
| Worst timing slack | 1.36 ns, met |

The 69/69 functional result applies to the current covergroup after nine operation-by-CWP combinations are ignored. Seven reset/nonzero-CWP combinations are structurally impossible. CALL at sampled CWP 0 and RET at sampled CWP 112 are absent under the implemented boundary behavior and relate to the defect.

Code coverage exposed the RTL defect: its only misses were the upward and downward CWP wrap assignments. Investigation showed that spill/fill moves SWP while CWP and the allocation counters remain frozen, making those assignments unreachable. A specification-oriented model and directed LOCAL-register test then confirmed that an overflowing call leaves the callee mapped to the caller's window.
