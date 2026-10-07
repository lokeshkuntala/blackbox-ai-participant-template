# round-2 — Investigate

**Team:** BB-027
**Queries used:** 5 / 120

## What we concluded

We tested parameters one at a time while keeping the other parameters at the Round 2 baseline.

- `container_count` showed no detectable effect on the score across the tested values 0, 50, and 100.
- `declared_value` showed a strong effect when reduced from 50 to 0: the score increased from **0.3544 to 0.5488** (+0.1944).
- Increasing `declared_value` from 50 to 100 produced almost no change: **0.3544 → 0.3546** (+0.0002).
- Therefore, the effect of `declared_value` is not simply linear across the tested range.

## How we got there

1. **Baseline:** `container_count = 50`, score = **0.3544**.
2. Changed only `container_count` from **50 → 0**. Score remained **0.3544**.
3. Changed only `container_count` from **50 → 100**. Score remained **0.3544**.
4. Restored the baseline and changed only `declared_value` from **50 → 0**. Score increased to **0.5488** (+0.1944).
5. Changed only `declared_value` from **50 → 100**. Score was **0.3546** (+0.0002).

Each experiment changed only one parameter so that the observed score change could be attributed to that parameter.

## What we ruled out

- We ruled out a detectable effect from `container_count` within the tested range **0–100**.
- We ruled out the hypothesis that increasing `declared_value` from 50 to 100 produces a large score increase.
- We did not assume a simple linear relationship for `declared_value`, because the results at 0, 50, and 100 do not support one.

## What we are still unsure about

- We have only tested three `declared_value` points: **0, 50, and 100**. The exact shape of its effect between these values is unknown.
- We have not yet tested the remaining parameters in Round 2.
- We do not yet know whether the effects of different parameters interact.
- More experiments are required before making a complete model of the system.
