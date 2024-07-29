Build
Clone the dev-sci branch of the authoritative repository:
git clone -b dev-sci https://github.com/NOAA-EMC/rrfs-workflow
Move to the sorc directory:
cd rrfs-workflow/sorc
Build the RRFS workflow:
./app_build.sh --extrn --nogtg --noifi
The above command is equal to:

./manage_externals/checkout_externals
./app_build.sh -p=[machine]
where [machine] is wcoss2, hera, jet, orion, or hercules. The --nogtg and --noifi flags avoid compilation of GTG and IFI components respectively, which only select users can compile.

Move to the home directory (rrfs-workflow):
cd ..  

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
