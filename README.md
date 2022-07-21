# Master-Thesis

This master thesis studied an exploratory version of the mean-variance (MV) problem formulated as an entropy-regularized, relaxed stochastic control problem. We derived the exploratory MV (EMV) algorithm by H. Wang \& X. Y. Zhou in [25]([https://www.google.com](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3706168) to solve this problem. Our goal was to implement the EMV algorithm, analyze its learning performance in a simulation study, and compare its out-of-sample performance to other methods in an empirical study.


In the first part of the thesis, we presented the MV problem of finding an investment strategy that minimizes the variance of the final payoff while targeting a prespecified mean return. We solved this problem under some crucial assumptions.


In the next part, we motivated and stated an exploratory formulation of the EMV problem. Further, we derived the optimal feedback control law to solve this problem.


Consequently, we could compare the MV and the EMV problem and their solutions. It turned out that the optimal terminal wealth's under the respective
optimal feedback controls of the two problems have the same mean. Further, we proved the solvability equivalence between the problems and showed that the EMV converges to the MV problem as the exploration weight decreases to 0. Moreover, we saw that the cost of exploration is linearly dependent with respect to the exploration weight $\lambda$ and to the time horizon $T$.


Next, we stated a policy improvement theorem and a convergence result on whose base we derived the EMV algorithm. We presented the pseudo-code and the actual implementation in Python 3.8.8.


Then, we analyzed the learning performance for simulated stock prices in a stationary and a non-stationary market case. The results were convincing since, in most market scenarios, a strategy was learned that approximately achieved the investment target with a relatively low standard deviation of the final payoffs. However, we observed that the EMV method has more difficulty learning successfully in market scenarios with nearly no drift or high volatility. Besides, we investigated the approximation accuracy of the EMV approach by comparing the learned $\rho^2$ with the ground truth value. The results showed that the algorithm has trouble approximating the parameter $\rho^2$.


To examine the efficiency of the EMV algorithm on real data with multiple assets, we derived the multi-dimensional EMV algorithm based on similar results as in the one-dimensional case. Again, we presented the pseudo-code and the actual implementation in Python.


Finally, in the last part of this thesis, we analyzed the out-of-sample performance of the EMV algorithm on S\&P stock data over different time horizons and rebalancing frequencies. We compared the annualized mean return and the standard deviation of the final payoffs with the equally weighted method and the Markowitz approach. We observed that the EMV method performs exceptionally well in all experiments over a 10-years horizon with monthly rebalancing. However, the leverage used to achieve these results was unrealistically high. Therefore, we introduced a leverage constraint variant of the EMV method. Compared to the benchmark approaches, the constraint versions with a leverage level of $200\%$ and $100\%$ generated a high annualized return for all experiments.


Further, we analyzed the EMV algorithm over a one-year horizon with daily rebalancing. For the sake of reality, we included trading costs in these experiments. The results were not as good as over the 10-year horizon since there was a too big difference between the market trend during the training and testing phase. We concluded that the EMV algorithm is more successful if the fundamental behavior of the market is similar in the training and testing period. Therefore, it works better over more extended investment periods.
However, overall, the EMV algorithm and its leverage constraint variants are certainly an improvement compared to non-RL algorithms that estimate the market parameters.
