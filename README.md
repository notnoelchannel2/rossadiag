# RossaDiag

A UEFI diagnostics app for [edk2-rossa](https://github.com/notnoelchannel2/edk2-rossa)
(edk2 on the Samsung Galaxy Core Prime LTE, rossa, SM-G360F, MSM8916). It
shows what the firmware sees, read-only, and is safe to start from the boot
manager menu.

- CPU, generic timer, GIC, PMIC, display, touch, disks
- CPU cores brought up by MpParkDxe ("Cores n of 4")
- Battery and charger (RT5033)
- SD controller capabilities and the bus mode the firmware settled on
- Vibration motor test, live key test (Vol+ / Vol- / Power / Home)

Based on J5DiagApp from edk2-rossa (Galaxy J5 2016 port) by jimkoutso2008.

## Build

It is an edk2 application and builds inside edk2-rossa, where it already lives
as `Msm8916Pkg/Application/RossaDiagApp` and is included in the rossa image
(`./build.sh rossa DEBUG`). To add it elsewhere, put `RossaDiagApp/` under
`Msm8916Pkg/Application/`, list `RossaDiagApp.inf` in the platform `.dsc`
`[Components]` and in the `.fdf`. It needs Msm8916Pkg's libraries and protocols
(LKEnvLib, QcomPm8x41, the RT5033 battery protocol).
