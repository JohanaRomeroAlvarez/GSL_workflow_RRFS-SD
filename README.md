RRFS Workflow Build Instructions
This repository provides instructions for building the GSL RRFS-SD workflow based on EMC's rrfs-workflow repository (last checked, July 25).

Cloning the Repository
Clone the main branch of the repository:

git clone -b main https://github.com/NOAA-EMC/rrfs-workflow

Building the RRFS Workflow
Move to the sorc directory:
cd rrfs-workflow/sorc

Build the RRFS workflow:
./app_build.sh --extrn --nogtg --noifi

The above command is equivalent to:
./manage_externals/checkout_externals
./app_build.sh -p=[machine]
where [machine] is one of the following: wcoss2, hera, jet, orion, or hercules.

The --nogtg and --noifi flags prevent the compilation of the GTG and IFI components, respectively, which only select users can compile.

Move back to the home directory:
cd ..


Differences with EMC’s dev-sci Branch
This repository includes the following modifications compared to EMC's dev-sci branch:

Workflow Parameters:

rrfs-workflow/parm/FV3LAM_wflow.xml (dependencies for the process smoke task)

Scripts:
rrfs-workflow/scripts/exrrfs_run_fcst.sh (creates dummy files for both ebb_dc options and is used when RAVE is not available)
rrfs-workflow/scripts/exrrfs_run_prepstart.sh (smoke and dust cycling)
rrfs-workflow/scripts/exrrfs_process_smoke.sh (splits RAVE files, version < 2, replaces interpolated files if older than 5 days, always replaces the Smoke file)

Utilities:
rrfs-workflow/ush/generate_fire_emissions.py (handles two fire emission scenarios)
rrfs-workflow/ush/HWP_tools.py (manages restart files for different cycling configurations)
rrfs-workflow/ush/fire_emiss_tools.py (handles two fire emission scenarios)
rrfs-workflow/ush/interp_tools.py (handles two fire emission scenarios)
