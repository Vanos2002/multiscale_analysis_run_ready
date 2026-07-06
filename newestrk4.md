=== Adaptive RK4 Integration Comparison ===
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
  eps=1.0000000000000000e+00 | phi_qlt=2.5604311633072421e+03, phi_F=4.0017509438966286e+01, phi_TW=4.0017509108699748e+01 | delta_phi_F=2.5204136538682756e+03, delta_phi_TW=2.5204136541985422e+03 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=8.3370000000000000e+03/1.1900000000000000e+02/1.1900000000000000e+02 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=8.337000e+03/1.190000e+02/1.190000e+02
    
[progress] eps index 2/9 (eps=5.0000e-01), local_tol=1.0e-09, local_phi_max_step=1.0e+08, local_max_steps=5.0e+07
    [init tilde JF] p_tilde=5.0204171391841797e+01, alpha_tilde=1.1472026930361470e-01, beta_tilde=9.9438894170518669e-02
    [target tilde JF] p_tilde_final=2.0247728120583169e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.020417e+01, alpha_tilde=1.147203e-01, beta_tilde=9.943889e-02
    [target tilde TW] p_tilde_final=2.0247728120583169e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-2.7461148884930231e-04, JF=-7.5583708110107386e-04, TW=-7.5583709593607168e-04
    [diag eff dp/dphi @start] QLT=-2.7461148884930231e-04, JF=-1.7436397570236295e-01, TW=-1.7436397570236295e-01
  eps=5.0000000000000000e-01 | phi_qlt=6.7225195948267894e+04, phi_F=2.3947404569690520e+04, phi_TW=2.3947404564614400e+04 | delta_phi_F=4.3277791378577371e+04, delta_phi_TW=4.3277791383653494e+04 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=5.1029000000000000e+04/1.7322000000000000e+04/1.7322000000000000e+04 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=5.102900e+04/1.732200e+04/1.732200e+04
    
[progress] eps index 3/9 (eps=2.5000e-01), local_tol=1.0e-09, local_phi_max_step=1.0e+08, local_max_steps=5.0e+07
    [init tilde JF] p_tilde=5.0045574145896843e+01, alpha_tilde=1.0372205413851822e-01, beta_tilde=9.9845391791249807e-02
    [target tilde JF] p_tilde_final=2.0048309541308619e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.004557e+01, alpha_tilde=1.037221e-01, beta_tilde=9.984539e-02
    [target tilde TW] p_tilde_final=2.0048309541308619e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-8.8890140615815322e-06, JF=-6.4580728227015177e-06, TW=-6.4580728442779321e-06
    [diag eff dp/dphi @start] QLT=-8.8890140615815322e-06, JF=-4.3668102023275424e-02, TW=-4.3668102023275424e-02
  eps=2.5000000000000000e-01 | phi_qlt=2.0492084957103038e+06, phi_F=2.8276985733138830e+06, phi_TW=2.8276985740127452e+06 | delta_phi_F=-7.7849007760357927e+05, delta_phi_TW=-7.7849007830244140e+05 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=3.8213900000000000e+05/5.2150800000000000e+05/5.2150800000000000e+05 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=3.821390e+05/5.215080e+05/5.215080e+05
    
[progress] eps index 4/9 (eps=1.2500e-01), local_tol=1.0e-09, local_phi_max_step=1.0e+08, local_max_steps=5.0e+07
    [init tilde JF] p_tilde=5.0011051512818540e+01, alpha_tilde=1.0093311816047591e-01, beta_tilde=9.9960454011117708e-02
    [target tilde JF] p_tilde_final=2.0011222528809359e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.001105e+01, alpha_tilde=1.009331e-01, beta_tilde=9.996045e-02
    [target tilde TW] p_tilde_final=2.0011222528809359e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-2.8022793896334899e-07, JF=-2.4906725496430814e-07, TW=-2.4906725500328907e-07
    [diag eff dp/dphi @start] QLT=-2.8022793896334899e-07, JF=-1.0932204475011531e-02, TW=-1.0932204475011531e-02
  eps=1.2500000000000000e-01 | phi_qlt=6.4788485952999756e+07, phi_F=7.2953536415183440e+07, phi_TW=7.2953536491910025e+07 | delta_phi_F=-8.1650504621836841e+06, delta_phi_TW=-8.1650505389102697e+06 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=3.0072340000000000e+06/3.3769980000000000e+06/3.3769980000000000e+06 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=3.007234e+06/3.376998e+06/3.376998e+06
    
[progress] eps index 5/9 (eps=6.2500e-02), local_tol=3.0e-07, local_phi_max_step=1.0e+09, local_max_steps=1.0e+08
    [init tilde JF] p_tilde=5.0002741500815461e+01, alpha_tilde=1.0023344197941385e-01, beta_tilde=9.9990057669853874e-02
    [target tilde JF] p_tilde_final=2.0002752189526241e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.000274e+01, alpha_tilde=1.002334e-01, beta_tilde=9.999006e-02
    [target tilde TW] p_tilde_final=2.0002752189526241e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-8.7763216193655243e-09, JF=-8.5090780841703542e-09, TW=-8.5090780842449973e-09
    [diag eff dp/dphi @start] QLT=-8.7763216193655243e-09, JF=-2.7340405495124287e-03, TW=-2.7340405495124287e-03
  eps=6.2500000000000000e-02 | phi_qlt=2.0670142305366707e+09, phi_F=2.1323559653224759e+09, phi_TW=2.1323559652628298e+09 | delta_phi_F=-6.5341734785805225e+07, delta_phi_TW=-6.5341734726159096e+07 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=8.2717050000000000e+06/8.5273740000000000e+06/8.5273740000000000e+06 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=8.271705e+06/8.527374e+06/8.527374e+06
    
[progress] eps index 6/9 (eps=3.1250e-02), local_tol=1.0e-06, local_phi_max_step=1.0e+10, local_max_steps=3.0e+08
    [init tilde JF] p_tilde=5.0000684039113523e+01, alpha_tilde=1.0005837064167035e-01, beta_tilde=9.9997510928541547e-02
    [target tilde JF] p_tilde_final=2.0000684707158754e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.000068e+01, alpha_tilde=1.000584e-01, beta_tilde=9.999751e-02
    [target tilde TW] p_tilde_final=2.0000684707158754e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-2.7441020935853756e-10, JF=-2.7227586797838125e-10, TW=-2.7227586797852632e-10
    [diag eff dp/dphi @start] QLT=-2.7441020935853756e-10, JF=-6.8357053351064678e-04, TW=-6.8357053351064678e-04
  eps=3.1250000000000000e-02 | phi_qlt=6.6105303124494293e+10, phi_F=6.6626977876705566e+10, phi_TW=6.6626977876481781e+10 | delta_phi_F=-5.2167475221127319e+08, delta_phi_TW=-5.2167475198748779e+08 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=5.4716896000000000e+07/5.5139302000000000e+07/5.5139302000000000e+07 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=5.471690e+07/5.513930e+07/5.513930e+07
    
[progress] eps index 7/9 (eps=1.5625e-02), local_tol=1.0e-05, local_phi_max_step=1.0e+12, local_max_steps=5.0e+09
    [init tilde JF] p_tilde=5.0000170926272716e+01, alpha_tilde=1.0001459329450486e-01, beta_tilde=9.9999377514087870e-02
    [target tilde JF] p_tilde_final=2.0000170968025550e+01 (from p_final=2.0000000000000000e+01)
    [init tilde TW] p_tilde=5.000017e+01, alpha_tilde=1.000146e-01, beta_tilde=9.999938e-02
    [target tilde TW] p_tilde_final=2.0000170968025550e+01 (from p_final=2.0000000000000000e+01)
    [diag raw dp/dphi @start] QLT=-8.5764924689598655e-12, JF=-8.5597271199326276e-12, TW=-8.5597271199329120e-12
    [diag eff dp/dphi @start] QLT=-8.5764924689598655e-12, JF=-1.7089973880501930e-04, TW=-1.7089973880501930e-04
  eps=1.5625000000000000e-02 | phi_qlt=2.1250321592159050e+12, phi_F=2.1292638697138196e+12, phi_TW=2.1292638697601125e+12 | delta_phi_F=-4.2317104979145508e+09, delta_phi_TW=-4.2317105442075195e+09 | reached(QLT/F/TW)=Y/Y/Y
    [progress] p_phys(QLT/F/TW)=2.0000000000000000e+01/2.0000000000000000e+01/2.0000000000000000e+01 | progress(QLT/F/TW)=1.0000000000000000e+00/1.0000000000000000e+00/1.0000000000000000e+00 | steps(QLT/F/TW)=3.0219605100000000e+08/3.0278461000000000e+08/3.0278461000000000e+08 | qlt_stop_reason=reached_target
    [projection] est_steps_to_target(QLT/F/TW)=3.021961e+08/3.027846e+08/3.027846e+08
    
[progress] eps index 8/9 (eps=7.8125e-03), local_tol=3.0e-05, local_phi_max_step=5.0e+12, local_max_steps=1.0e+10
    [init tilde JF] p_tilde=5.0000042726349079e+01, alpha_tilde=1.0000364836325527e-01, beta_tilde=9.9999844364894147e-02
    [target tilde JF] p_tilde_final=2.0000042728958629e+01 (from p_final=2.0000000000000000e+01)
