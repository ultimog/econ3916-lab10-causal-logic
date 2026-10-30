# econ3916-lab10-causal-logic
# Correlation & Causality: Confounders, Colliders and the Limits of Controls

## Objective
I tested when controlling for a variable removes bias, when it creates bias, and why the data alone can't tell the difference.

## Methodology
- I simulated three worlds (true causation, pure confounding and pure selection) whose correlations all come out near 0.65, although the true effects are 2.0, 0.0 and 0.0.
- I drew a confounder, a collider and a mediator as directed graphs with networkx.
- I showed that controlling for a confounder recovers the true effect, while controlling for a collider creates a large, highly significant association between two independent variables.
- I built an M-bias structure in which a control measured before treatment still biases the estimate.
- I wrote a small function, coef_on_d(), that returns the coefficient on the treatment for any list of controls, and used it to show that also controlling for one of the hidden causes closes the path again.
- I reproduced the LaLonde (1986) contrast: the randomised experiment against a comparison group from the CPS, then measured how much of the gap covariate adjustment closes.

## Key Findings
- The three worlds had correlations of 0.654, 0.664 and 0.632, even though only the first has a real causal effect.
- Controlling for a collider gave an estimate of -0.592 where the truth is 0.
- M-bias gave -0.191 from a control measured before treatment, and 0.006 once I also controlled for u1.
- LaLonde: the experiment gives $1,794, the naive CPS comparison gives -$8,498, and adding controls gives $699, closing 89% of the gap. Getting closer to the benchmark doesn't prove the adjustment is valid.
