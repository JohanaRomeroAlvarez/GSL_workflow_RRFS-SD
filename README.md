
Difference with EMC’s dev-sci branch: 
1) rrfs-workflow/parm/FV3LAM_wflow.xml
(dependencies for the process smoke task)
2) rrfs-workflow/scripts/exrrfs_run_fcst.sh
(create dummy files for both ebb_dc options and used when RAVE is not available)
3) rrfs-workflow/scripts/exrrfs_run_prepstart.sh
(smoke and dust cycling)
4) rrfs-workflow/scripts/exrrfs_process_smoke.sh
(splitting of RAVE files, version < 2, replace interpolated files if older than 5 days, always replace the Smoke file)
5) rrfs-workflow/ush/generate_fire_emissions.py
(handles two fire emission scenarios)
6) rrfs-workflow/ush/HWP_tools.py
(handles restart files for different cycling configurations)
7) rrfs-workflow/ush/fire_emiss_tools.py
(handles two fire emission scenarios)
8) rrfs-workflow/ush/interp_tools.py
(handles two fire emission scenarios)
