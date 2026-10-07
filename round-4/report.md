# round-4 — Reconstruct

**Team:** BB-031
**Queries used:** 70 / 80 budget

## What we concluded

The system can be approximated reasonably well by smooth relationships for much of the tested input space, but the held-out evaluation revealed an important exception: Port C behaves like a distinct or unstable regime.

Ridge achieved 96.875% decision accuracy on 32 unseen points, correctly classifying 31/32 decisions. Kernel Ridge with an RBF kernel achieved 93.75%, correctly classifying 30/32. Despite the high decision accuracy, both models had their largest score errors on the Port C point.

Removing the Port C point dramatically improved the regression fit. Ridge improved from R²=0.532 and MAE=0.0566 to R²=0.952 and MAE=0.031. Kernel Ridge improved from R²=0.601 and MAE=0.051 to R²=0.931 and MAE=0.028.

This suggests that most of the system follows a relatively smooth relationship, while Port C represents a separate regime, interaction, or boundary that a single global smooth model does not capture well.

## How we got there

We first evaluated two different regression approaches on a held-out set of 32 points: linear Ridge regression and Kernel Ridge regression using an RBF kernel.

Ridge achieved 31 correct decisions out of 32, corresponding to 96.875% decision accuracy. Kernel Ridge achieved 30/32, corresponding to 93.75%.

Although the decision accuracy was high, the score-level metrics revealed a problem. Ridge had an R² of 0.5316 and a worst miss of 0.8544. Kernel Ridge had an R² of 0.6008 and a worst miss of 0.7677.

The largest error for both models corresponded to the Port C point. We therefore tested whether this point was disproportionately responsible for the poor regression fit.

After removing only the Port C point, Ridge improved to R²=0.952 with MAE=0.031. Kernel Ridge improved to R²=0.931 with MAE=0.028.

The large improvement from removing a single point indicates that the error is concentrated in Port C rather than being evenly distributed across the held-out set.

## What we ruled out

We ruled out the idea that the lower regression performance was simply caused by a globally poor choice of model. Both a linear Ridge model and a nonlinear RBF Kernel Ridge model achieved high decision accuracy, and both showed the same problematic Port C point.

We also ruled out the idea that the regression error was uniformly distributed across the held-out data. Removing one Port C point caused a very large improvement in both models' R² and MAE.

The evidence therefore points toward a localized behavior or regime change rather than a general inability of the models to approximate the system.

## What we are still unsure about

We do not yet know whether Port C itself is responsible for the unusual behavior or whether Port C interacts with another input feature.

The experiment does not reveal the internal rule used by the system. The Port C point could represent a genuine conditional rule, an interaction, or a sparsely sampled part of the input space.

We also cannot conclude from one Port C point that every Port C input behaves differently. More controlled Port C experiments would be required to determine whether the behavior generalizes across different ages, credit histories, loan amounts, and other features.

The main conclusion is therefore that Port C is a high-priority region for further investigation, not that a universal Port C rule has been proven.
