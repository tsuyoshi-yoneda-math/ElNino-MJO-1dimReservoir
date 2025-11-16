Please acknowledge the use of these scripts in any publications which make use of them.

As shown in 1dimReservoir_ElNino_TYoneda.ipynb, the 22-step-ahead prediction 
(25−lag3) achieves a PCC of 0.54. This is broadly consistent with the results reported in 

<h3>
Takuya Jinno, Takahito Mitsui, Kengo Nakai, Yoshitaka Saiki, and Tsuyoshi Yoneda, Long-term prediction of El Niño–Southern Oscillation using reservoir computing with a data-driven real-time filter, Chaos 35 (2025), 053149. 
</h3>

This consistency indicates that the reservoir-computing approach combined with a data-driven filter exhibits robust performance.

Similarly, 1dimReservoir_MJO_TYoneda.ipynb shows that the 21-step-ahead prediction 
(23−lag2) achieves a PCC of 0.69. This is also consistent with the results of 

<h3>
Tamaki Suematsu, Kengo Nakai, Tsuyoshi Yoneda, Daisuke Takasuka, Takuya Jinno, Yoshitaka Saiki, and Hiroaki Miura, Machine learning prediction of the MJO extends beyond one month, submitted, arXiv:2301.01254, 
</h3>

further illustrating the robustness of the reservoir-computing framework with a data-driven filter.

########################################################

<h1>DataDrivenFilter.....TYoneda.ipynb</h1>

Optimizing the hyperparameters of the realtime-filter. 

You can set desirable ranges of the hyperparameters

- r_1: Higher end of the passing frequency range
- r_2: Lower end of the passing frequency range
- c: Parameter for the attenuation of weight function
- d_1: Amplitude of the frequency r_1
- d_2: Amplitude of the frequency r_2
- width: Length of weighted running average in past time series

The following parameters are related to the reduction of the indefinite factor of the time series.

- n_trials: Number of trials for optuna
- max_dim: Max pattern length
- min_dim: Min pattern length
- min_count: Delete patterns if occurrence is fewer than this
- n_bins: Number of partitions of range
- min_win_vote_rate: Minimum requirement for win_vote_rate

The history of bayesian optimization, the filtered time series "flt....csv" is generated.

Optimizing the hyperparameters of the echo state network model. You can set desirable ranges of the hyperparameters

- lag: Delay time
- dim: Dimension of input delay-coordinate vector
- N_x: Dimension of reservoir state vector
- beta: Regularization parameter to avoid over-fitting
- density: Rate of non-zero elements in recurrent connection matrix A
- input_scale: Scaling parameter of the input matrix
- rho: maximum Eigenvalue of the matrix A
- alpha: Leaking rate
- seed_value: Seed value to generate random matrices

The following parameters are related to training and prediction of the time series.

- n_trials: Number of times to test with optuna (generate autocorrelation for this number of times)
- T_train: Training period
- T_test: Forecast period
- test_num: Number of times for one test (to get one autocorrelation)
- discard_len: Number of steps not learned at the beginning (not important) Note that the number of reservoir node is fixed to 70 in the sample code.


##################################################################

Tsuyoshi Yoneda would like to thank Takuya Jinno for producing this readme.
