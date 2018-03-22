# trust_HCs_CABN
Scripts for processing data from the trust game trust as reported in the manuscript.
VBA-style Q-learning and other models of modified Trust Game.
A procedure to run programs in this collection can go as follows. 
(1) run trust_fit_masterlist_vba. 
(2) After determining desired model, run trust_extract_PEs_multisession1.m 


1. trust_fit_masterlist_vba.m: gets data for all subjects in masterlist (.mat), runs a Qlearning (trust_Qlearning_ushifted_v2 or trust_Qlearning_ushifted_SVM) algorithm w/ preset parameters, saves F(it)-values in table.

2. trust_Qlearning_ushifted_v2.m: VBA fitting of Qlearning to a single subject trust data. Note that the u vector (which includes the subject's behavior +outcomes+experimental design) is shifted by one trial ahead, because enivronmental feedback on trial t-1 is what determines the value of the hidden states on trial t. Calls to f() and g() (obervation/evolution functions, respectively). Saves the figure and the results of the VBA inversion routine.

3. f_trust_Qlearn_policy_pmv.m: evolution function where reinforcement reflects counterfactual rewards (with respect to the share action)

4. f_trust_Qlearn_counter_trustee.m: simpler evolution function where reinforcement reflects counterfactual feedback from trustee (also with respect to the share actions).

5. f_trust_Qlearn_null_pmv.m: simpler evolution function where reinforcement reflects actual rewards.

6. f_trust_Qlearn_SVM1: evolution function for the Social Value Model (SVM).

7. g_trust_softmax_ks_kt: observation function w/ subject-wise and condition, or trustee-wise, bias parameters.

8. g_trust_softmax1: simpler observation function.

9. g_trust_softmax_ED1: observation function w/ single subject-wise kappa parameter for actual rewards evolution function

10. g_trust_softmax_ED2: observation function w/ single subject-wise kappa parameter for other evolution functions.

11. g_trust_SVM1: observation function for SVM.

12. trust_modelComparisons: helper code to compares F(its) between models. Uses saved tables from trust_fit_group_vba.m.
