# RRFS Workflow Build Instructions

This repository provides instructions for building the GSL RRFS-SD workflow based on EMC's rrfs-workflow repository (last checked, July 25).

---

## Cloning the Repository

Clone the main branch of the repository:
---
```sh
---
git clone -b main https://github.com/NOAA-EMC/rrfs-workflow
---

## Building the RRFS Workflow
---
Move to the sorc directory:
---
cd rrfs-workflow/sorc
---

Build the RRFS workflow:
---
./app_build.sh --extrn --nogtg --noifi
---

The above command is equivalent to:
---
./manage_externals/checkout_externals
---
./app_build.sh -p=[machine]
---
where [machine] is one of the following: wcoss2, hera, jet, orion, or hercules.
---
The --nogtg and --noifi flags prevent the compilation of the GTG and IFI components, respectively, which only select users can compile.
---
## Move back to the home directory:
---
cd ..
---

## Differences with EMC’s dev-sci Branch
This repository includes the following modifications compared to EMC's dev-sci branch:
---
## parm:
---
rrfs-workflow/parm/FV3LAM_wflow.xml (modified dependencies for the process smoke task)
---
## Scripts:
---
rrfs-workflow/scripts/exrrfs_run_fcst.sh (creates dummy files for both ebb_dc options)
---
rrfs-workflow/scripts/exrrfs_run_prepstart.sh (cycles smoke, coarse, and dust. Distinguished smoke from the RAP model used for ICs for cold start from smoke from continue cycles)
---
rrfs-workflow/scripts/exrrfs_process_smoke.sh (splits RAVE files into hourly files for version < 2. Replaces interpolated files if older than 15 days, always replaces the Smoke file when the task is rebooted)
---
## Utilities:
---
rrfs-workflow/ush/generate_fire_emissions.py (handles two fire emission scenarios: same-day emissions and forecast)
---
rrfs-workflow/ush/HWP_tools.py (manages restart files for different cycling configurations)
---
rrfs-workflow/ush/fire_emiss_tools.py (handles two fire emission scenarios: same-day emissions and forecast)
---
rrfs-workflow/ush/interp_tools.py (handles two fire emission scenarios: same-day emissions and forecast)
---



