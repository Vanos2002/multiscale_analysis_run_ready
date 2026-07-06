=== Adaptive Implicit Gauss Collocation Integration Comparison ===
PN order: 5 (4.5PN)
Tolerance: 1e-09
Mode: FULL ACCURACY

=== Delta-phi vs epsilon scan (p: 50 -> 20) ===
[scan config] tol=1.0e-09, phi_max_step_default=1.0e+08, max_steps_default=5.0e+07

[progress] eps index 1/9 (eps=1.0000e+00), local_tol=1.0e-09, local_phi_max_step=1.0e+08, local_max_steps=5.0e+07
    [init tilde JF] p_tilde=5.1163225550727972e+01, alpha_tilde=1.5615968502737476e-01, beta_tilde=9.8670961856561643e-02
    [target tilde JF] p_tilde_final=2.1819963991268725e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.116323e+01, alpha_tilde=1.561597e-01, beta_tilde=9.867096e-02
    [target tilde TW] p_tilde_final=2.1819963991268725e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-7.6220696412936523e-03, JF=-4.5938526083822395e-01, TW=-4.5938528077876895e-01
    [diag eff dp/dphi @start] QLT=-7.6220696412936523e-03, JF=-1.1178196501759885e+00, TW=-1.1178196359651338e+00
  eps=1.0000000000000000e+00 | phi_qlt=2.5604311582200544e+03, phi_F=4.0017458589775032e+01, phi_TW=4.0017458261953216e+01 | delta_phi_F=2.5204136996302796e+03, delta_phi_TW=2.5204136999581010e+03 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=5.8570000000000000e+03/1.0200000000000000e+02/1.0200000000000000e+02 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=5.857000e+03/1.020000e+02/1.020000e+02
    
[progress] eps index 2/9 (eps=5.0000e-01), local_tol=1.0e-09, local_phi_max_step=1.0e+08, local_max_steps=5.0e+07
    [init tilde JF] p_tilde=5.0204171391841797e+01, alpha_tilde=1.1472026930361470e-01, beta_tilde=9.9438894170518669e-02
    [target tilde JF] p_tilde_final=2.0247728120583169e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.020417e+01, alpha_tilde=1.147203e-01, beta_tilde=9.943889e-02
    [target tilde TW] p_tilde_final=2.0247728120583169e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-2.7461148884930231e-04, JF=-7.5583708110107386e-04, TW=-7.5583709593607168e-04
    [diag eff dp/dphi @start] QLT=-2.7461148884930231e-04, JF=-1.7436397570236295e-01, TW=-1.7436397570236295e-01
  eps=5.0000000000000000e-01 | phi_qlt=6.7225195940378078e+04, phi_F=2.3947362998633129e+04, phi_TW=2.3947362992805072e+04 | delta_phi_F=4.3277832941744949e+04, delta_phi_TW=4.3277832947573006e+04 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=3.5843000000000000e+04/1.2166000000000000e+04/1.2166000000000000e+04 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=3.584300e+04/1.216600e+04/1.216600e+04
    
[progress] eps index 3/9 (eps=2.5000e-01), local_tol=1.0e-09, local_phi_max_step=1.0e+08, local_max_steps=5.0e+07
    [init tilde JF] p_tilde=5.0045574145896843e+01, alpha_tilde=1.0372205413851822e-01, beta_tilde=9.9845391791249807e-02
    [target tilde JF] p_tilde_final=2.0048309541308619e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.004557e+01, alpha_tilde=1.037221e-01, beta_tilde=9.984539e-02
    [target tilde TW] p_tilde_final=2.0048309541308619e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-8.8890140615815322e-06, JF=-6.4580728227015177e-06, TW=-6.4580728442779321e-06
    [diag eff dp/dphi @start] QLT=-8.8890140615815322e-06, JF=-4.3668102023275424e-02, TW=-4.3668102023275424e-02
  eps=2.5000000000000000e-01 | phi_qlt=2.0492084949955631e+06, phi_F=2.8276545596262543e+06, phi_TW=2.8276545611362280e+06 | delta_phi_F=-7.7844606463069119e+05, delta_phi_TW=-7.7844606614066497e+05 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=2.6840900000000000e+05/3.6628300000000000e+05/3.6628300000000000e+05 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=2.684090e+05/3.662830e+05/3.662830e+05
    
[progress] eps index 4/9 (eps=1.2500e-01), local_tol=1.0e-09, local_phi_max_step=1.0e+08, local_max_steps=5.0e+07
    [init tilde JF] p_tilde=5.0011051512818540e+01, alpha_tilde=1.0093311816047591e-01, beta_tilde=9.9960454011117708e-02
    [target tilde JF] p_tilde_final=2.0011222528809359e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.001105e+01, alpha_tilde=1.009331e-01, beta_tilde=9.996045e-02
    [target tilde TW] p_tilde_final=2.0011222528809359e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-2.8022793896334899e-07, JF=-2.4906725496430814e-07, TW=-2.4906725500328907e-07
    [diag eff dp/dphi @start] QLT=-2.8022793896334899e-07, JF=-1.0932204475011531e-02, TW=-1.0932204475011531e-02
  eps=1.2500000000000000e-01 | phi_qlt=6.4788485768877663e+07, phi_F=7.2954015337684751e+07, phi_TW=7.2954015335410669e+07 | delta_phi_F=-8.1655295688070878e+06, delta_phi_TW=-8.1655295665330067e+06 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=2.1122250000000000e+06/2.3719660000000000e+06/2.3719660000000000e+06 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=2.112225e+06/2.371966e+06/2.371966e+06
    
[progress] eps index 5/9 (eps=6.2500e-02), local_tol=3.0e-07, local_phi_max_step=1.0e+09, local_max_steps=1.0e+08
    [init tilde JF] p_tilde=5.0002741500815461e+01, alpha_tilde=1.0023344197941385e-01, beta_tilde=9.9990057669853874e-02
    [target tilde JF] p_tilde_final=2.0002752189526241e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.000274e+01, alpha_tilde=1.002334e-01, beta_tilde=9.999006e-02
    [target tilde TW] p_tilde_final=2.0002752189526241e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-8.7763216193655243e-09, JF=-8.5090780841703542e-09, TW=-8.5090780842449973e-09
    [diag eff dp/dphi @start] QLT=-8.7763216193655243e-09, JF=-2.7340405495124287e-03, TW=-2.7340405495124287e-03
  eps=6.2500000000000000e-02 | phi_qlt=2.0670005350282085e+09, phi_F=2.1323394803392406e+09, phi_TW=2.1323394803195610e+09 | delta_phi_F=-6.5338945311032057e+07, delta_phi_TW=-6.5338945291352510e+07 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=5.9898150000000000e+06/6.1749460000000000e+06/6.1749460000000000e+06 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=5.989815e+06/6.174946e+06/6.174946e+06
    
[progress] eps index 6/9 (eps=3.1250e-02), local_tol=1.0e-06, local_phi_max_step=1.0e+10, local_max_steps=3.0e+08
    [init tilde JF] p_tilde=5.0000684039113523e+01, alpha_tilde=1.0005837064167035e-01, beta_tilde=9.9997510928541547e-02
    [target tilde JF] p_tilde_final=2.0000684707158754e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.000068e+01, alpha_tilde=1.000584e-01, beta_tilde=9.999751e-02
    [target tilde TW] p_tilde_final=2.0000684707158754e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-2.7441020935853756e-10, JF=-2.7227586797838125e-10, TW=-2.7227586797852632e-10
    [diag eff dp/dphi @start] QLT=-2.7441020935853756e-10, JF=-6.8357053351064678e-04, TW=-6.8357053351064678e-04
  eps=3.1250000000000000e-02 | phi_qlt=6.6094308274250153e+10, phi_F=6.6615661094051331e+10, phi_TW=6.6615661097392487e+10 | delta_phi_F=-5.2135281980117798e+08, delta_phi_TW=-5.2135282314233398e+08 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=4.1030902000000000e+07/4.1347502000000000e+07/4.1347502000000000e+07 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=4.103090e+07/4.134750e+07/4.134750e+07
    
[progress] eps index 7/9 (eps=1.5625e-02), local_tol=1.0e-05, local_phi_max_step=2.0e+10, local_max_steps=5.0e+09
    [init tilde JF] p_tilde=5.0000170926272716e+01, alpha_tilde=1.0001459329450486e-01, beta_tilde=9.9999377514087870e-02
    [target tilde JF] p_tilde_final=2.0000170968025550e+01 (from p_final=2.0000000000000000e+01)
