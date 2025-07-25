<hr>

# Tag name:  rtm1_0_88
### Originator(s): slevis
### Date: Jul 14, 2025
### One-line Summary: Fix RTM h0i file metadata

Resolves ESCOMP/RTM#63 h0i files end up with the same metadata as h0a files

PR ESCOMP/RTM#64

<hr>

# Tag name:  rtm1_0_87
### Originator(s): slevis
### Date: Jul 03, 2025
### One-line Summary: Separate instantaneous and non-inst. history files

This is the rtm equivalent of ESCOMP/CTSM#2445.

Resolves ESCOMP/RTM#32

PR ESCOMP/RTM#61

<hr>

# Tag name:  rtm1_0_86
### Originator(s): samrabin
### Date: Jan 16, 2025
### One-line Summary: Fix izumi_nag compile

Fix so can compile and run on izumi_nag. Also add a single test to the rtm testsuite for izumi_nag

Resolves ESCOMP/RTM#60
Resolves ESCOMP/RTM#59

PR ESCOMP/RTM#58

<hr>

# Tag name:  rtm1_0_85
### Originator(s): samrabin
### Date: Jan 14, 2025
### One-line Summary: Standardize time metadata

Standardizes a dimension name of output variable time_bounds, as well as attributes for that plus mcdate, mcsec, mdcur, and mscur.

Contributors: Adam Phillips, Erik Kluzek

Resolves ESCOMP/RTM#31
Contributes to https://github.com/ESCOMP/CTSM/issues/1693

PR ESCOMP/RTM#35
Contributes to https://github.com/ESCOMP/CTSM/pull/2052

<hr>

# Tag name:  rtm1_0_84
### Originator(s): ekluzek
### Date: Jan 03, 2025
### One-line Summary: The RTM rpointer file now has the simulation timestamp in the filename

Have the restart pointer filenames for RTM with the simulation time-stamp in them. Make it backwards compatible to using filenames without the simulation time-stamp as well. This changes time-manager setup from reading in the restart time from the restart file -- to using the current time sent from the coupler. Previously you would EITHER call timemgr_init OR timemgr_restart. Now, you always call timemgr_init -- and only call timemgr_restart for a restart case, with most of what it does is to make sure the time on the restart file agrees with the time sent from the coupler.

Also remove use of shr_file_mod throughout the code.

Change the ChangeLog file into a markdown file and start using some markdown syntax.

Resolves: ESCOMP/RTM#53

Resolves: ESCOMP/RTM#46

PR
ESCOMP/RTM#57

<hr>

# Tag name:  rtm1_0_83
### Originator(s): slevis
### Date: Nov 12, 2024
### One-line Summary:Stop running 0th timestep

For consistency with CAM and CTSM.

Resolves #
Relates to CTSM issue ESCOMP/CTSM#925 and PR ESCOMP/CTSM#2084

Pull Requests:

 #37

<hr>

# Tag name:  rtm1_0_82
### Originator(s): slevis
### Date: Nov 11, 2024
### One-line Summary:Change time to equal the middle of time_bounds

For consistency with CAM and CTSM and for more intuitive history output.

Resolves #
Relates to issue #32 but does not resolve the separation of instantaneous variables onto separate history files.

Pull Requests:

 #39

<hr>

# Tag name:  rtm1_0_81
### Originator(s): ekluzek
### Date: Nov 8, 2024
### One-line Summary:Update testlist_rtm

We are keeping RTM for the use of the NoAnthro tests for Clm60, and for continuing to test the Clm45 compsets where RTM was the standard ROF model being used. There's also a Clm50 compset with RTM for the FLOOD option in RTM. Since, FLOOD is currently only working in RTM, we should continue testing it. It's also good to have at least 1850 and 2000 and possibly HIST. Since, nothing changes for RTM for transient cases, it's probably sufficient to have 1850 tests.

Resolves #54

Pull Requests:

 #55

<hr>

# Tag name:  rtm1_0_80
### Originator(s): swensosc
### Date: Jun 21, 2024
### One-line Summary:fix area scaling to correct RTM river flux to MOM6

Fix how area is applied to input runoff for rtm

Resolves #50

Pull Requests:

 #51

<hr>

# Tag name:  rtm1_0_79
### Originator(s): mvertens/erik
### Date: Jan 27, 2024
### One-line Summary:Remove MCT from RTM

This tag removes MCT code that is no longer used since it is only in the mct cap.
Also updates the testlist to be moved to Derecho, removing izumi

Erik added some changes to this that were important for RTM as a maintainer of
RTM which cover the following issues:

Resolves #45 -- failing tests
Resolves #44 -- lower testing for RTM (remove Izumi tests)
Resolves #41 -- Move testlist from Cheyenne to Derecho
Resolves #33 -- Update path to CIME tools needed for buildnml/buildlib

Pull Requests:

 #42 -- Remove MCT
 #40 -- Update README and test comments

<hr>

# Tag name:  rtm1_0_78
### Originator(s): erik
### Date: October 27, 2021
### One-line Summary:Change nuopc to default for testlist, don't require direction file if RTM not active

Fixes #28 -- if RTM is not active finitdat_rtm and frivinp_rtm aren't required

Change test list so that nuopc is the default driver, so explicit nuopc tests are
now run for MCT.

<hr>

# Tag name:  rtm1_0_77
### Originator(s): erik
### Date: July 16, 2021
### One-line Summary:Change shebang lines and abort if direction file not set

Fixes #26 -- Change shebang lines
Fixes #22 -- Rtm direction file is a directory

See https://github.com/ESCOMP/RTM/pull/27

<hr>

# Tag name:  rtm1_0_76
### Originator(s): jedwards
### Date: April 5, 2021
### One-line Summary:Support for threading with NUOPC/CMEPS

See https://github.com/ESCOMP/RTM/pull/25

Testing:
Mariana Vertenstein ran
SMS_D_Ld5_Vnuopc.f10_f10_mg37.I2000Clm50BgcCropRtm.cheyenne_intel.rtm-default;
this was bit-for-bit against baselines.

<hr>

# Tag name:  rtm1_0_75
### Originator(s): mvertens
### Date: March 16, 2021
### One-line Summary:Implementation of flux area correction factors in nuopc cap

Add in area correction factors for fluxes sent in nuopc cap.

Also remove a debug option to write out coupling fields. Remove do_sum
option to state_getimport as was unused. Remove state_getfldptr which
seemed to be unused as well.

Testing:
SMS_D_Ld5_Vnuopc.f10_f10_mg37.I2000Clm50BgcCropRtm.cheyenne_intel.rtm-default
in the context of CESM's nuopc_dev branch. (No baseline comparisons done
for full set of changes.)

<hr>

# Tag name:  rtm1_0_74
### Originator(s): jedwards
### Date: December 22, 2020
### One-line Summary:Minor changes to nuopc cap, etc.

- Change to nuopc build

- Minor changes to buildnml

- Fix inst_name in pio calls

Testing: rtm test suite on cheyenne & izumi, in the context of
ctsm5.1.dev019. All tests passed and were bit-for-bit with baselines.

<hr>

# Tag name:  rtm1_0_73
### Originator(s): sacks
### Date: November 01, 2020
### One-line Summary:Change compset in test

In an upcoming CTSM tag, the compset I2000Clm50BgcCropRtmGs will be
renamed to I2000Clm50BgcCropRtm (while keeping the same meaning as
before). This tag changes a test to use the new alias, to keep RTM
compatible with this upcoming CTSM tag.

Note that this change will require the upcoming CTSM tag (probably
ctsm5.1.dev011) in order to run this test from the rtm test list.

<hr>

# Tag name:  rtm1_0_72
### Originator(s): mvertens, erik
### Date: August 06, 2020
### One-line Summary:some nuopc updates

Some nuopc updates from @mvertens. New directory nuopc_cap_share. 
SetVM is made public in rof_comp_nuopc.F90. ROF is used in rtmIO
rather than instance name.

These changes are almost identical to the latest nuopc changes 
for mosart, but not quite the same.

Also add nuopc_cap_share to the Filepath for the build.
"*txt*" files are no longer copied to the $RUNDIR.

<hr>

# Tag name:  rtm1_0_71
### Originator(s): mvertens, sacks
### Date: March 16, 2020
### One-line Summary:Add NUOPC cap

This tag brings in the necessary changes to rtm to have a new NUOPC cap
introduced.

Most changes are from Mariana Vertenstein, brought to master by Bill
Sacks.

These changes are documented in https://github.com/ESCOMP/RTM/pull/20

Testing: rtm test suite (cheyenne & izumi), in the context of a CTSM
checkout (https://github.com/ESCOMP/CTSM/pull/939). Baseline comparisons
done against ctsm1.0.dev085.

<hr>

# Tag name:  rtm1_0_70
### Originator(s): erik
### Date: Nov 08, 2019
### One-line Summary:Rename uses of SHR_KIND_CL to CL for a cime update

    Change wallclock time in tests and change hobart for izumi

    Add Code of Conduct.
    
    Have all instances of SHR_KIND_CL use CL that is renamed from SHR_KIND_CL.
    This is important for a recent cime update.

<hr>

# Tag name:  rtm1_0_69
### Originator(s): erik
### Date: Jun 03, 2019
### One-line Summary:Fix cold-starts and remove mosart from files

You couldn't set finidat_rtm to blank to indicate a cold start should
be done. This fixes that issue. It now both indicates that a cold start
should happen, AND it doesn't search for an empty filename from inputdata.

Also added a cold-start test to make sure this continues to work.

mosart was in a few places and it was changed to refer to "rtm" now.
For example the list of files needed was mosart.input_data_files now
it's properly rtm.input_data_files.

Fixes: #14, #15

   Fixes #14 -- Can't set finidat_rtm to blank indicating a cold-start
   Fixes #15 -- mosart is used in the title of some files
Testing:
   rtm testlist on hobart and cheyenne (PASS)

<hr>

# Tag name:  rtm1_0_68
### Originator(s): erik
### Date: Jun 11, 2019
### One-line Summary:buildlib changes to be compatable with cime5.8

buildlib changes from @jedwards to be compatable with cime5.8.
Ran testing with cime tag branch_tags/cime5.8.3_chint17-02.

Testing:
   rtm testlist on hobart and cheyenne (PASS)

<hr>

# Tag name:  rtm1_0_67
### Originator(s): erik
### Date: May 07, 2019
### One-line Summary:Move release-cesm2.0.02 to master

basetype wasn't declared and needed to be. Also add more "implicit none"
statements in. Remove the deletion of "rtm.input_data_list" file, as cime
now does this. Remove the option of setting single-precision
history output, as it sometimes has numerical conversion issues. The
real solution for it should be to keep a single-precision history
buffer that then outputs at the same precision as stored, rather than
converting just before. This would trigger issues with the conversion
earlier.

Changes ported from mosart/#15 to rtm. Run pylint through buildlib/buildnml,
changes for fill value needed for pio2. Also use the floor operator
for a specific integer divide as python3 turns it into reals.

Add CODE_OF_CONDUCT.md

Testing:
   rtm testlist on hobart and cheyenne (PASS)

<hr>

# Tag name:  rtm1_0_66
### Originator(s): erik
### Date: May 15, 2018
### One-line Summary: Add model_doi_url

Move RTM config_archive to it's own cime_config. Add in model_doi_url 
read in from infodata from coupler. Remove old rof_comp_esmf interface. 
Remove revision_id from output files.

Pull Request -- #7

https://github.com/ESCOMP/mosart/pull/11/files

 A  cime_config/config_archive.xml
 M  docs/index.html
 D  src/cpl/rof_comp_esmf.F90
 M  src/cpl/rof_comp_mct.F90
 M  src/riverroute/RtmHistFile.F90
 M  src/riverroute/RtmRestFile.F90
 M  src/riverroute/RtmVar.F90

<hr>

# Tag name:  rtm1_0_65
### Originator(s): erik
### Date: Jan 23, 2018
### One-line Summary:Put testlist options under test rather than machines

 M  cime_config/testdefs/testlist_rtm.xml

<hr>

# Tag name:  rtm1_0_64
### Originator(s): erik
### Date: Jan 17, 2018
### One-line Summary:Convert test list to version 2 format and remove ys

Convert the test list to version 2 format, add comments and wallclock to it.
Remove ys tests. Remove aux_clm tests (put those in CLM itself).

Add buildnmlc to .gitignore

 M  cime_config/testdefs/testlist_rtm.xml

<hr>

# Tag name:  rtm1_0_63
### Originator(s): erik
### Date: Oct 3, 2017
### One-line Summary:Upgrade config_component to version 3, allow output file format
                  to change, fix so REFCASE will check for files with or without
                  instance name


M    src/riverroute/RtmIO.F90 --------- Changes from Jim Edwards
        to change NetCDF output file format, also make io_type not public
M    cime_config/buildnml ------------- Fix bug 2477 for RTM so that
        if NINST_RTM > 1, will check if REFCASE has instance name
        in it and then use it, but if not use it without instance name
M    cime_config/config_component.xml - Upgrade to version 3 format

<hr>

# Tag name:  rtm1_0_62
### Originator(s): andre
### Date: July 5, 2017
### One-line Summary:update compset names in testlist

Update the rtm testlist to use clm5 compset alias naming conventions.

M cime_config/testdefs/testlist_rtm.xml

<hr>

# Tag name:  rtm1_0_61
### Originator(s): andre
### Date: March 17, 2017
### One-line Summary:histfile pointer bugfix bugz-2184

Bugfix from bugzilla issue 2184. The histfile infrastructure rtm
inherited from clm needs to use pointers to refer to pio/netcdf file
handles. Bug 2184 has never occured in rtm, but the same problem
existed.

Testing:

    NOTE: testing done with a franken-branch of clm4_5_14_r229 and
    rtm1_0_60.

    rtm - pass - yellowstone gnu, intel, pgi. baseline rtm1_0_60_clm4_5_14_r229.

    aux_clm4{0,5}: ok vs clm4_5_14_r229 baselines, yellowstone gnu, intel, pgi

	Notes: Expected failures from clm + expected failures from rtm1_0_60.

	ERP_D.f19_g16.IRCP85CN.yellowstone_pgi.clm-40default
	ERP_P180x2_Ld5.f19_g16.I1850CN.yellowstone_pgi.clm-40default
	SMS.f19_g16.IRCP45CN.yellowstone_pgi
	SSP_D_Ld10.f19_g16.I1850CLM45BGC.yellowstone_intel.clm-default
	SSP_Ld10.f19_g16.I1850CLM45BGC.yellowstone_pgi.clm-default


Modified files: fix for bugzilla #2184

    components/rtm/src/riverroute/RtmHistFile.F90


<hr>

# Tag name:  rtm1_0_60
### Originator(s): mvertens, andre
### Date: March 14, 2017
### One-line Summary:cime5 python namelist generation

Changes from Mariana Vertenstein to convert namelist generation to use
the cime5 python namelist infrastructure.

Testing:

  aux_clm4{0,5}: ok vs clm4_5_14_r227 baseline

	Notes: new expected failures for clm. The new namelist
	infrastructure does not support automatically setting up cases
	where rtm reads initial conditions from the clm file. The
	functionality is discouraged from being used in the future. The
	following tests in the clm test suites are new expected failures
	because of this change in behavior:

	ERP_D.f19_g16.IRCP85CN.yellowstone_pgi.clm-40default
	ERP_P180x2_Ld5.f19_g16.I1850CN.yellowstone_pgi.clm-40default
	SMS.f19_g16.IRCP45CN.yellowstone_pgi
	SSP_D_Ld10.f19_g16.I1850CLM45BGC.yellowstone_intel.clm-default
	SSP_Ld10.f19_g16.I1850CLM45BGC.yellowstone_pgi.clm-default


  rtm: pass vs clm4_5_14_r227 baseline

Deleted files: old perl build namelist and xml files.
   bld
   bld/build-namelist
   bld/namelist_files
   bld/namelist_files/namelist_defaults_rtm.xml
   bld/namelist_files/namelist_definition_rtm.xml

Added files: new python buildnml and xml files

   cime_config/namelist_definition_rtm.xml
   cime_config/buildlib
   cime_config/buildnml
   cime_config/config_component.xml

Modified files: update tests to use xmlchange, bugfix rtm_effvel not
                being set correctly in some tests.

    cime_config/testdefs/testmods_dirs/rtm/rtmOnFloodOnEffvelOff/shell_commands
    cime_config/testdefs/testmods_dirs/rtm/rtmOnFloodOnEffvelOff/user_nl_rtm
    cime_config/testdefs/testmods_dirs/rtm/rtmOnFloodOnEffvelOn/shell_commands
    cime_config/testdefs/testmods_dirs/rtm/rtmOnFloodOnEffvelOn/user_nl_rtm
    cime_config/testdefs/testmods_dirs/rtm/rtmOnIceOff/shell_commands
    cime_config/testdefs/testmods_dirs/rtm/rtmOnIceOff/user_nl_rtm
    cime_config/testdefs/testmods_dirs/rtm/rtmOff/shell_commands
    cime_config/testdefs/testmods_dirs/rtm/rtmOff/user_nl_rtm
    cime_config/testdefs/testmods_dirs/rtm/rtmOnIceOn/shell_commands
    cime_config/testdefs/testmods_dirs/rtm/rtmOnIceOn/user_nl_rtm


<hr>

# Tag name:  rtm1_0_59
### Originator(s): swenson, sacks
### Date: Oct 17, 2016
### One-line Summary:Treat irrigation specially, tweak volr

(1) Together with corresponding cime and clm changes, treats irrigation as a
    separate flux. The point of this is to map irrigation withdrawals normalized
    by volr, to help prevent river channels from going to negative volumes.

(2) Tweaks the volr field sent to the coupler. Sean Swenson expected this to
    have an effect, although it appears not to, at least from the rtm and
    aux_clm45 test suite.

Requires the cime changes from https://github.com/ESMCI/cime/pull/681

In order for the new irrigation changes to have an effect, also requires the CLM
changes from the branch
https://svn-ccsm-models.cgd.ucar.edu/clm2/branches/limitirrig - although this
code will work correctly without the CLM changes (in this case, irrigation will
simply be 0, and the irrigation flux will be folded in to a different runoff
flux).

Changes are from Sean Swenson; reviewed, tested and brought to the trunk by Bill
Sacks.

Testing: rtm test suite (on yellowstone), from
https://svn-ccsm-models.cgd.ucar.edu/clm2/branch_tags/limitirrig_tags/limitirrig_n10_clm4_5_12_r196

All tests passed and were bit-for-bit with testing from clm4_5_12_r196 with cime
at d321e4b (the baseline for the relevant cime branch).

Also ran aux_clm45 test suite; most tests passed; I'm looking into remaining
failures and will update rtm if it turns out it was the source of any problems.

M       src/riverroute/RtmHistFlds.F90
M       src/riverroute/RunoffMod.F90
M       src/riverroute/RtmMod.F90
M       src/cpl/rtm_cpl_indices.F90
M       src/cpl/rof_import_export.F90

<hr>

# Tag name:  rtm1_0_58
### Originator(s): erik
### Date: Sep 13, 2016
### One-line Summary:Add time period frequency to output history files

M       src/riverroute/RtmHistFile.F90

<hr>

# Tag name:  rtm1_0_57
### Originator(s): erik
### Date: Jul 01, 2016
### One-line Summary:Remove ESMF test

M       cime_config/testdefs/testlist_rtm.xml

<hr>

# Tag name:  rtm1_0_56
### Originator(s): erik
### Date: Apr 14, 2016
### One-line Summary:Turn off for CLM_ACCELERATED_SPINUP="on" and fix a few bugs

Have RTM react to CLM_ACCELERATED_SPINUP setting from CLM and turn itself off
by default if it's "on".

Also fix following bugs:

1674 -- assumes history files are no_leap calendar
2230 -- for RTM delt_save not initialized

M       bld/build-namelist ---- Check CLM_ACCELERATED_SPINUP, read do_rtm from
           defaults file and check based on CLM_ACCELERATED_SPINUP and MOSART_MODE
M       bld/namelist_files/namelist_defaults_rtm.xml  - add do_rtm settings
M       src/riverroute/RtmHistFile.F90 -- Increase filename length to 255
           check calendar type before writing to history file
M       src/riverroute/RtmIO.F90 -------- initialize delt_save (2230)
M       src/riverroute/RtmMod.F90 ------- Increase string length to 255
M       src/riverroute/RtmRestFile.F90 -- Increase string length to 255
M       src/riverroute/RtmTimeManager.F90 Add NO_LEAP_C and GREGORIAN_C as public constants (2307)

<hr>

# Tag name:  rtm1_0_55
### Originator(s): andre
### Date: Oct 13, 2015
### One-line Summary:negative runoff remove direct to ocean runoff from Sean Swenson

- Remove directo to ocean runnoff (Sean Swenson)
- add error checking on history file name length.
- add default test mod with hourly output from rtm

A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnFloodOnEffvelOff/include_user_mods
A  +    cime_config/testdefs/testmods_dirs/rtm/default
A  +    cime_config/testdefs/testmods_dirs/rtm/default/user_nl_rtm
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnFloodOnEffvelOn/include_user_mods
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnIceOff/include_user_mods
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOff/include_user_mods
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnIceOn/include_user_mods
M       cime_config/testdefs/testlist_rtm.xml
M       src/riverroute/RtmHistFlds.F90
M       src/riverroute/RtmHistFile.F90
M       src/riverroute/RunoffMod.F90
M       src/cpl/rtm_cpl_indices.F90
M       src/cpl/rof_import_export.F90

<hr>

# Tag name:  rtm1_0_54
### Originator(s): andre
### Date: Oct 13, 2015
### One-line Summary:Direct to ocean runoff from Sean Swenson

Testing against branch based on clm4_5_3_r135:

  SMS_D_Ld3.f10_f10.ICRUCLM50BGC.yellowstone_intel.clm-default
  ERS_D_Ld5.f10_f10.ICRUCLM50BGC.yellowstone_intel.clm-default

  Not expected to be bit for bit with previous tag.

  src/riverroute/RtmHistFlds.F90
  src/riverroute/RunoffMod.F90
  src/cpl/rof_import_export.F90

<hr>

# Tag name:  rtm1_0_53
### Originator(s): mvertens
### Date: Sept 20, 2015
### One-line Summary:Updated trunk to be compatible with cime3.0.3 and later APIs

Migrated the following branch to the trunk
  https://svn-ccsm-models.cgd.ucar.edu/rivrtm/branch_tags/cime_refactor_tags/cime_refactor_n01_rtm1_0_52

The results are bfb with cesm1_4_alpha07e baselines
	
D       bld/rtm.buildlib
D       bld/rtm.buildnml
M       bld/build-namelist
D       bld/user_nl_rtm
M       bld/namelist_files/namelist_defaults_rtm.xml
A  +    cime_config
A  +    cime_config/testdefs
A  +    cime_config/testdefs/testmods_dirs
A  +    cime_config/testdefs/testmods_dirs/rtm
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnFloodOnEffvelOff
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnFloodOnEffvelOff/user_nl_rtm
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnFloodOnEffvelOn
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnFloodOnEffvelOn/user_nl_rtm
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnIceOff
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnIceOff/user_nl_rtm
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOff
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOff/user_nl_rtm
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnIceOn
A  +    cime_config/testdefs/testmods_dirs/rtm/rtmOnIceOn/user_nl_rtm
A  +    cime_config/testdefs/testlist_rtm.xml
A  +    cime_config/buildlib
A  +    cime_config/buildnml
A  +    cime_config/config_component.xml
A  +    cime_config/user_nl_rtm
D       cimetest
D       cimetest/testmods_dirs
D       cimetest/testmods_dirs/rtm
D       cimetest/testmods_dirs/rtm/rtmOnFloodOnEffvelOff
D       cimetest/testmods_dirs/rtm/rtmOnFloodOnEffvelOff/user_nl_rtm
D       cimetest/testmods_dirs/rtm/rtmOnFloodOnEffvelOn
D       cimetest/testmods_dirs/rtm/rtmOnFloodOnEffvelOn/user_nl_rtm
D       cimetest/testmods_dirs/rtm/rtmOnIceOff
D       cimetest/testmods_dirs/rtm/rtmOnIceOff/user_nl_rtm
D       cimetest/testmods_dirs/rtm/rtmOff
D       cimetest/testmods_dirs/rtm/rtmOff/user_nl_rtm
D       cimetest/testmods_dirs/rtm/rtmOnIceOn
D       cimetest/testmods_dirs/rtm/rtmOnIceOn/user_nl_rtm
D       cimetest/testlist_rtm.xml
	
<hr>

# Tag name:  rtm1_0_52
### Originator(s): erik
### Date: Aug 19, 2015
### One-line Summary:Move goldbach tests to hobart and only one node

Move the goldbach tests to hobart, and only run on one node.

M       cimetest/testlist_rtm.xml

<hr>

# Tag name:  rtm1_0_51
### Originator(s): erik
### Date: Aug 13, 2015
### One-line Summary:Fix bug 2199 continuation line in middle of string

Fix so a line isn't continued in the middle of a character string.

M  src/riverroute/RtmMod.F90

<hr>

# Tag name:  rtm1_0_50
### Originator(s): erik
### Date: Aug 03, 2015
### One-line Summary:Don't assume that direction files are global

Figure out grid edges from the direction file grid, don't assume
it's global. Report on the edge values if the grid is NOT
global. Checked to ensure global grid edges are the same as
before.

M   src/riverroute/RtmMod.F90

<hr>

# Tag name:  rtm1_0_49
### Originator(s): cacraig
### Date: June 25, 2015
### One-line Summary:NAG6.0 requires additional pointers to be nullified

M       src/riverroute/RunoffMod.F90

<hr>

# Tag name:  rtm1_0_48
### Originator(s): jedwards
### Date: Apr 25, 2015
### One-line Summary:readnamelist on mastertask only

M   src/riverroute/RtmMod.F90

<hr>

# Tag name:  rtm1_0_47
### Originator(s): erik
### Date: Mar 18, 2015
### One-line Summary:Add cimetest directory that was under clm before

A       cimetest
A       cimetest/testlist_rtm.xml
A       cimetest/testmods_dirs
A  +    cimetest/testmods_dirs/rtm
	
<hr>

# Tag name:  rtm1_0_46
### Originator(s): mvertens
### Date: Mar 10, 2015
### One-line Summary:fixes for new scripts directory structure
	
M       bld/build-namelist
	
<hr>

# Tag name:  rtm1_0_45
### Originator(s): mvertens
### Date: Mar 10, 2015
### One-line Summary:more changes needed for scripts/testing refactor

This is required for cesm1_3_beta18
	
M       bld/build-namelist
	
<hr>

# Tag name:  rtm1_0_44
### Originator(s): mvertens
### Date: Feb 21, 2015
### One-line Summary:more changes needed for scripts/testing refactor

This is required for cesm1_3_beta18
	
M       bld/build-namelist
M       bld/rtm.buildlib
M       bld/rtm.buildnml
	
<hr>

# Tag name:  rtm1_0_43
### Originator(s): mvertens
### Date: Feb 21, 2015
### One-line Summary:changes needed for scripts/testing refactor

This is required for cesm1_3_beta18
	
M       bld/build-namelist
D       bld/rof.cpl7.template
D       bld/rtm.buildexe.csh
A  +    bld/rtm.buildlib
A  +    bld/rtm.buildnml
D       bld/rtm.buildnml.csh
D       bld/rtm.cpl7.template
	
M       src/riverroute/RtmMod.F90
	- very minor change for output 
<hr>

# Tag name:  rtm1_0_41
### Originator(s): jedwards
### Date: Nov 30, 2014
### One-line Summary:PIO2 Compatibility changes 

M         src/riverroute/RtmMod.F90
M         src/riverroute/RtmHistFile.F90
M         src/riverroute/RtmIO.F90


<hr>

# Tag name:  rtm1_0_40
### Originator(s): muszala
### Date: Nov 03, 2014
### One-line Summary:patch RtmIo to address valgrind errors found by Santos

example change:
-          status = pio_inq_vardimid(ncid,vardesc, dids)
+          status = pio_inq_vardimid(ncid,vardesc, dids(1:ndims))

M       src/riverroute/RtmIO.F90

<hr>

# Tag name:  rtm1_0_39
### Originator(s): erik
### Date: Oct 03, 2014
### One-line Summary:Prevent cesm_setup from aborting if can't find files

Fix bug 2032 rtm.buildnml.csh kills cesm_setup if GET_REFCASE is FALSE

M       bld/rtm.buildnml.csh

<hr>

# Tag name:  rtm1_0_38
### Originator(s): muszala
### Date: May 23, 2014
### One-line Summary:add code to handle deallocations based on valgrind errors

Address errors found with valgrind that originate in src/riverroute.  Change some
pointers to allocables.
Note: use with esmf_wrf_timemgr_140523 or later.

! add RtmHistFileFinalize() which cleans up hbuf and nacs
M       src/riverroute/RtmHistFile.F90
! add ncd_finalize() which cleans up some members of iodesc_list
M       src/riverroute/RtmIO.F90
! add RunoffFinalize() which cleans up the members of the runoff type
M       src/riverroute/RunoffMod.F90
! add  RtmRestFinalize( ) which calls ncd_finalize
M       src/riverroute/RtmRestFile.F90
! change some pointers to allocatables, clean up fluxout,sfluxin, ddist, evel
M       src/riverroute/RtmMod.F90
! call ESMF clock clean up routine
M       src/riverroute/RtmTimeManager.F90
! new module that calls other RTM finalize routines
A  +    src/riverroute/RtmFinalizeAll.F90
! add call to  RtmFinalizeMemory() and deallocate totrunin
M       src/cpl/rof_comp_mct.F90
! add call to  RtmFinalizeMemory()
M       src/cpl/rof_comp_esmf.F90
! totrunin actual argument now totrunin( runoff%begr: ,: )
M       src/cpl/rof_import_export.F90

<hr>

# Tag name:  rtm1_0_37
### Originator(s): muszala
### Date: Dec 27, 2014
### One-line Summary:add SHR_ASSERT macros

Replace call shr_assert with SHR_ASSERT_ALL macros for Santos.  Add shr_assert.h.

M       src/riverroute/RtmMod.F90

<hr>

# Tag name:  rtm1_0_36
### Originator(s): tcraig
### Date: Dec 27, 2013
### One-line Summary:fix multi instance hybrid/branch filenames

M       bld/rtm.buildnml.csh

<hr>

# Tag name:  rtm1_0_35
### Originator(s): tcraig
### Date: Oct 28, 2013
### One-line Summary:fix rtm namelist for initial files set from the REFCASE

M       bld/rtm.buildnml.csh

<hr>

# Tag name:  rtm1_0_34
### Originator(s): mvertens
### Date: Oct 2, 2013
### One-line Summary:removed mct2esmf calls from rof_comp_esmf.F90

M       src/cpl/rof_comp_esmf.F90

<hr>

# Tag name:  rtm1_0_33
### Originator(s): mvertens
### Date: Sep 25, 2013
### One-line Summary:Coupler interface refactor

migration of cpl_share/, cpl_esmf/ and cpl_mct code into 
new cpl/ and introduction of rof_import_export.F90

M       bld/rtm.buildexe.csh
D       src/cpl_share
D       src/cpl_share/rtm_cpl_indices.F90
D       src/cpl_mct
D       src/cpl_mct/rof_comp_mct.F90
D       src/cpl_esmf
D       src/cpl_esmf/rof_comp_mct.F90
D       src/cpl_esmf/rof_comp_esmf.F90
A  +    src/cpl
A  +    src/cpl/rof_comp_mct.F90
A  +    src/cpl/rof_comp_esmf.F90
A  +    src/cpl/rtm_cpl_indices.F90
A  +    src/cpl/rof_import_export.F90

<hr>

# Tag name:  rtm1_0_32
### Originator(s): muszala
### Date: Sep 19, 2013
### One-line Summary:fix fthresh bug and refactor RtmFloodInit

runoff%fthresh was passed via argument list but then used
within RtmFloodInit.  Fix initialization of some runoff fields.
Refactor RtmFloodInit so that everything is passed via argument
list.  Move global use statements so that they are local.

M       src/riverroute/RtmMod.F90
M       src/riverroute/RunoffMod.F90

<hr>

# Tag name:  rtm1_0_31
### Originator(s): tcraig
### Date: Sep 5, 2013
### One-line Summary:merge cplupa branch to trunk

update runoff coupling field names for consistency with driver
modify intents on init/run/finalize coupling interfaces
add ifdef USE_ESMF_METADATA around esmf attribute calls
add rof to ice control logic
convert volr coupling field from state to flux

M       src/cpl_share/rtm_cpl_indices.F90
M       src/cpl_mct/rof_comp_mct.F90
M       src/cpl_esmf/rof_comp_esmf.F90
<hr>

# Tag name:  rtm1_0_30
### Originator(s): erik
### Date: Aug 26, 2013
### One-line Summary:Fix bug 1777 (multi-instance) and 1789 (problem with branching)

Change .r. in restart files to .r${inst_string}. as needed.
Put needed "nrevsn_rtm='" in setting of nrevsn for branches.

M       bld/rtm.buildnml.csh

<hr>

# Tag name:  rtm1_0_29
### Originator(s): muszala 
### Date: May 14, 2013
### One-line Summary:fix 1x1_camdenNJ tests and use message

M       bld/rtm.buildnml.csh
   Fix from Erik K. that ignores the initial/restart file setting if the grid is
   null...fixes bug with ERI_D.1x1_camdenNJ.ICLM45CNTEST.yellowstone_intel.
	See bug 1734 in bugzilla
M       bld/build-namelist
  fix use message error found by Sean Santos.

<hr>

# Tag name:  rtm1_0_28
### Originator(s): muszala 
### Date: May 14, 2013
### One-line Summary:VOLR area correction

M       src/cpl_mct/rof_comp_mct.F90
M       src/cpl_esmf/rof_comp_esmf.F90

<hr>

# Tag name:  rtm1_0_27
### Originator(s): erik
### Date: May 22, 2013
### One-line Summary:Initial conditions for 1850/2000 and fix logic for startup files

Fix bugs: 1707, and 1708

M       bld/rtm.buildnml.csh -- Fix bug 1707 where logic for setting hybrid
                 or branch startup file was wrong.
M       bld/build-namelist ---- Add ability to set simyr and finidat_rtm file
M       bld/namelist_files/namelist_defaults_rtm.xml -- Add r05 1850/2000
                 finidat_rtm files

<hr>

# Tag name:  rtm1_0_26
### Originator(s): jedwards
### Date: May 14, 2013
### One-line Summary:fix multi-inst. support 

M       bld/rtm.buildnml.csh

<hr>

# Tag name:  rtm1_0_25
### Originator(s): muszala
### Date: May 10, 2013
### One-line Summary:add multi-inst. support 

M       bld/rtm.buildnml.csh
<hr>

# Tag name:  rtm1_0_24
### Originator(s): muszala
### Date: May 10, 2013
### One-line Summary:add 'null' as option to grid check in rtm.buildnml.csh

M       bld/rtm.buildnml.csh
<hr>

# Tag name:  rtm1_0_23
### Originator(s): tcraig
### Date: May 3, 2013
### One-line Summary:add some grid checks

M       bld/rtm.buildnml.csh
<hr>

# Tag name:  rtm1_0_22
### Originator(s): muszala
### Date: Mar 18, 2013
### One-line Summary:esmf volr addition and volrlnd init fix

M    src/riverroute/RunoffMod.F90 
M    src/cpl_esmf/rof_comp_esmf.F90

<hr>

# Tag name:  rtm1_0_21
### Originator(s): tcraig
### Date: Mar 13, 2013
### One-line Summary: minor cleanup and fix to RTM_MODE setting

M       bld/rtm.buildnml.csh
M       bld/build-namelist
<hr>

# Tag name:  rtm1_0_20
### Originator(s): muszala
### Date: Feb 21, 2013
### One-line Summary: mods to a few lines for NAG port from Santos

M       nag_rtm1_0_19/src/riverroute/RtmSpmd.F90
M       nag_rtm1_0_19/src/riverroute/RtmTimeManager.F90

<hr>

# Tag name:  rtm1_0_19
### Originator(s): muszala
### Date: Feb 19, 2013
### One-line Summary: bring in tws, Volr, r01 rdric file

   Bring VOLR through coupler to CLM.  New r01 rdirc file.  
   Added rtm tests in CLM (test_system).

M    bld/namelist_files/namelist_defaults_rtm.xml
M    src/cpl_share/rtm_cpl_indices.F90
M    src/cpl_mct/rof_comp_mct.F90
M    src/riverroute/RtmMod.F90
M    src/riverroute/RtmHistFlds.F90
M    src/riverroute/RtmHistFile.F90


<hr>

# Tag name:  rtm1_0_18
### Originator(s): muszala
### Date: Feb 4, 2013
### One-line Summary:change rtm_effvel to NULL as default for Erik

   Change rtm_effvel to 'NULL' so 40 is the default physics behavior.
   This is a change from what effvel was set to in rtm1_0_14.

M       src/riverroute/RtmMod.F90

<hr>

# Tag name:  rtm1_0_17
### Originator(s): muszala
### Date: Feb 1, 2013
### One-line Summary: fix esmf synch error & add RTM_NAMELIST_OPTS/RTM_BLDNML_OPTS 

   Fix bug in esmf clock sync error.  Add  RTM_NAMELIST_OPTS/RTM_BLDNML_OPTS
   to build-namelist in prep. for clm4_0_60 in which 40 and 45 source are
   broken out.  This tag needs to be paired with scripts4_130130.

M       bld/rtm.buildnml.csh
M       src/cpl_esmf/rof_comp_esmf.F90

<hr>

# Tag name:  rtm1_0_16
### Originator(s): muszala
### Date: Jan 11, 2013
### One-line Summary: add fix for restarts and add history file vars.

	Put in fix from mvertens for restarts.  Add RTMTHRESH and RTMFLOOD as default 
	netcdf output variables.

M       src/riverroute/RtmTimeManager.F90
M       src/riverroute/RtmHistFlds.F90

<hr>

# Tag name:  rtm1_0_15
### Originator(s): muszala
### Date: Jan 8, 2013
### One-line Summary: add fix for h0 output and change comments in RtmMod.F90

   Put in a fix from mvertens for h0 history file output.  the last rtm hist file
	wasn't being written.  change some confusing comments in RtmMod.F90

M       src/cpl_mct/rof_comp_mct.F90
M       src/riverroute/RtmMod.F90

<hr>

# Tag name:  rtm1_0_14
### Originator(s): muszala
### Date: Jan 2, 2013
### One-line Summary: change default effvel value to that needed in sci45 branch

  The namelist variable, rtm_effvel is now preset to ACTIVE and effvel_active is set to 
  true.  This forces rtm to use slope in the velocity calculation.  If a user wants
  backward compatibilty with clm4_0_* tags, rtm_effvel will have to be set to NULL.

M    rtm/src/riverroute/RtmMod.F90

<hr>

# Tag name:  rtm1_0_13
### Originator(s): muszala
### Date: Nov 28, 2012
### One-line Summary: Add effVel as namelist.  cleanup RtmFloodInit logic

	- Add effective velocity as a namelist variable.
	- Change rdirc file.
	- Add RTM tests to test_system batch CLM tests.
	- Clean up logic in RtmFloodInit so R01 works without SLOPE and MAX_VOLR.
	- The modification to effvel (for the default case) changes the amount
	    of runoff (r2x_Forr_roff & r2x_Forr_ioff) in the system and does change climate.
	    The value is what is in CLM4.5
   - Change rdirc file to rdirc_0.5x0.5_simyr2000_slpmxvl_c120717.nc which is
	    correct and contains FLOOD and MAX_VOLR.  This fixes an error in choice
	    of rdirc file from clm4_0_55 / rtm1_0_10

M    rtm/bld/namelist_files/namelist_defaults_rtm.xml
M    rtm/bld/namelist_files/namelist_definition_rtm.xml
M    rtm/src/riverroute/RtmMod.F90
M    rtm/src/riverroute/RtmVar.F90

<hr>

# Tag name:  rtm1_0_12
### Originator(s): tcraig
### Date: Nov 25, 2012
### One-line Summary:fix esmf coupling, update rtm and flood active logic
 - fix esmf coupling
 - modify rtm and flood active logic for better reuse and robustness
 - add rtm_mode and flood_mode to namelist, remove do_rtm and do_rtmflood
 - remove some redundant command line arguments to rtm build-namelist

M       bld/rtm.buildnml.csh
M       bld/build-namelist
M       bld/user_nl_rtm
M       bld/namelist_files/namelist_definition_rtm.xml
M       doc/ChangeLog
M       src/riverroute/RtmMod.F90
M       src/cpl_esmf/rof_comp_mct.F90
M       src/cpl_esmf/rof_comp_esmf.F90

<hr>

# Tag name:  rtm1_0_11
### Originator(s): mvertens
### Date: Nov 23, 2012
### One-line Summary:Rewrite RtmFloodInit to use pio_darray not
	global arrays  
	
M       src/riverroute/RtmMod.F90
	- rewrite rtmfloodinit to remove use of global arrays
	
M       src/cpl_mct/rof_comp_mct.F90
M       src/riverroute/RtmVar.F90
	- introduced rtm_active and flood_active in RtmVar.F90 
	  to be consistent with changes coming into rtm1_0_12

	verified that results were bit-for-bit with rtm1_0_10
	with and without flooding on

<hr>

# Tag name:  rtm1_0_10
### Originator(s): muszala
### Date: Nov 13, 2012
### One-line Summary:Rewrite RtmFloodInit to read SLOPE and MAX_VOLR
  from file and change to newer rdirc file

M       models/ro/rtm/src/riverroute/RtmMod.F90
M       models/rof/rtm/src/bld/namelist_files/namelist_defaults_rtm.xml

<hr>

# Tag name:  rtm1_0_09
### Originator(s): mvertens
### Date: Sep 24, 2012
### One-line Summary:fixed bug when RTM ran on different processors
	          from CLM

M       src/riverroute/RtmHistFile.F90
A       src/riverroute/RtmDateTime.F90
M       src/riverroute/RtmRestFile.F90

<hr>

# Tag name:  rtm1_0_08
### Originator(s): mvertens
### Date: Sep 24, 2012
### One-line Summary:removed references to finidat, fatmlndfrc and nrevsn
                  and clm_rtm_inparm   

M       riverroute/RtmMod.F90
	
<hr>

# Tag name:  rtm1_0_07
### Originator(s): mvertens
### Date: Sep 24, 2012
### One-line Summary:update documentation in config_definition.xml
	          and user_nl_rtm

M       bld/user_nl_rtm
M       bld/namelist_files/namelist_definition_rtm.xml
	
M       src/riverroute/RtmMod.F90
        - no longer output fatmlndfrc to standard out

<hr>

# Tag name:  rtm1_0_06
### Originator(s): tcraig
### Date: Sep 24, 2012
### One-line Summary:fix rtm_nsteps usage when rtm if off

M       src/riverroute/RtmMod.F90
<hr>

# Tag name:  rtm1_0_05
### Originator(s): mvertens
### Date: Sep 23, 2012
### One-line Summary:bugfix for rtm history restarts files using pnetcdf

fixed reference to finc and fexcl - plus other minor cleanups	

M       src/riverroute/RtmMod.F90
M       src/riverroute/RtmHistFile.F90
M       src/cpl_esmf/rof_comp_esmf.F90
	
<hr>

# Tag name:  rtm1_0_04
### Originator(s): tcraig
### Date: Sep 13, 2012
### One-line Summary:updates from clm4_0_44 to clm4_0_46 for rtm

M       bld/namelist_files/namelist_defaults_rtm.xml
M       src/riverroute/RtmMod.F90
<hr>

# Tag name:  rtm1_0_03
### Originator(s): tcraig
### Date: Mon Sep 4, 2012
### One-line Summary:add budget check, minor cleanup

M       src/cpl_mct/rof_comp_mct.F90
M       src/riverroute/RtmMod.F90
M       src/riverroute/RunoffMod.F90
	
<hr>

# Tag name:  rtm1_0_02
### Originator(s): tcraig
### Date: Mon Aug 27, 2012
### One-line Summary:Clean up, flood_present=false, remove land_frac
  usage, fix sign convention, set mask global, fix multi-instance,
  fix esmf.

M       src/cpl_share/rtm_cpl_indices.F90
M       src/cpl_mct/rof_comp_mct.F90
M       src/riverroute/RtmMod.F90
M       src/riverroute/RtmIO.F90
M       src/riverroute/RunoffMod.F90
M       src/cpl_esmf/rof_comp_mct.F90
M       src/cpl_esmf/rof_comp_esmf.F90
<hr>

# Tag name:  rtm1_0_01
### Originator(s): mvertens (Mariana Vertenstein)
### Date: Mon Aug 4
### One-line Summary:First commit of rtm as a separate component

Purpose of changes:

First commit of rtm as a separate component

Requirements for tag:
    Requirements: test on bluefire (CESM)

Test level of tag: std-test

Bugs fixed (include bugzilla ID):

Known bugs (include bugzilla ID):
	
Known Limitations:
	
Describe any changes made to build system: 
   New introductin of cesm build scripts
	
Describe any changes made to the namelist: Yes!
   New introductin of namelist scripts

Describe any substantial timing or memory changes: No

Code reviewed by: self

List all files eliminated: None

List all files added and what they do:

List all existing files that have been modified, and describe the changes:

CESM or CLM tag used for the baseline comparison tests if applicable: 

Changes answers relative to baseline: Yes

<hr>
