# Upboard_2_project

################################################################################
                            UP-APL01
################################################################################
Microcode:
        M03506C9_00000040.PDB
        M03506CA_0000001E.PDB
        M03506CA_00000028.PDB
        M03506C9_00000048.PDB
--------------------------------------------------------------------------------
(*) Camera Support Requirement:
        1. Windows 10 RS1
        2. Driver Install manually
        3. BIOS Setting Change (Administrator Mode)
                CRB Setup -> CRB Chipset -> Uncore Configuration -> IPU Enabled/Disabled : Enabled
                CRB Setup -> CRB Chipset -> Uncore Configuration -> SA IPU ACPI Mode : IGFX Child
                Boot -> OS Selection : Windows

                OV8856 : CRB Setup -> CRB Chipset -> Uncore Configuration -> Rear Camera : IMX135
                OV2740 : CRB Setup -> CRB Chipset -> Uncore Configuration -> Front Camera : OV2740
                (H/W A1.1 : Only support one kind of camera at the same time)

(*) BIOS Flash Rule :
        1. Please flash BIOS to [UPA1AM39_FPT] first , then could be flash to [UPA1AM40] or later versions
        2. If onboard flash BIOS version from [UPA1AM61] or below to [UPA1AM62] or above, it needs to 
                update BIOS twice for CPU microcode update
        3. If onboard flash BIOS version from [UPA1AM63] or below to [UPA1AM64] or above, it needs to 
                clear CMOS to restore factory keys

(*) Note :
        1. SMBIOS(DMI) Information will be cleared after flash BIOS to [UPA1AM39]
        2. FPGA F/W are Different between A1.0 and A1.1 Motherboard
################################################################################
================================================================================
BIOS Name:      UPA1AM64                (Based on : UPA1AM63)
Build Date:     11/23/2022
Checksum:       0833h
Sign-on Message:
        UP-APL01 R6.4 (UPA1AM64)(11/23/2022)
Changes:
        1. Issue Patch: Patch Ubuntu-20.04.5-live-server can't be installed issue
        2. Issue Patch: Patch "Problem loading x5.09 certificate -65" error when install Ubuntu-20.04.5-live-server
        3. Updated BIOS logo
================================================================================
==========================================================================
BIOS Name:      UPA1AM63                (based on UPA1AM62)
Checksum:       16MB:6DCBh
Sign-on Message:
                UP-APL01 R6.3 (UPA1AM63)(03/30/2022)

Change:
        1. Move setup option "Power Limit 1 Enable" to user level
        2. Update CPU Microcode
==========================================================================
BIOS Name:      UPA1AM62                (based on UPA1AM61)
Checksum:       16MB:F831h
Sign-on Message:
                UP-APL01 R6.2 (UPA1AM62)(01/25/2022)

Change:
        1. Fixed CPU Microcode update failed when using AFU flash tool update BIOS
        2. Update CPU Microcode
==========================================================================
BIOS Name:      UPA1AM61                (based on UPA1AM60)
Checksum:       16MB:0552h
Sign-on Message:
                UP-APL01 R6.1 (UPA1AM61)(08/12/2021)

Change:
        1. Support Build-in Shell
        2. Update CPU Microcode
        3. Update GOP Bin to 1036
        4. Patch system will hang BIOS logo when connect some 4K monitor
        5. Prevent RTL8111G/H device loss when S3 resume
        6. Set PMIC IC BUCK4 VID to 1.85V for improving eMMC compatibility
==========================================================================
BIOS Name:      UPA1AM60                (based on 1ATJS061_M00)
Checksum:       16MB:42BCh
Sign-on Message:
                UP-APL01 R6.0 (UPA1AM60)(06/02/2021)

Change:
        1. Update code base to 5.12_1ATJS_RC1.5.2_061
        2. Support modify Boot priority by BIOX
==========================================================================
BIOS Name:      UPA1AM53                (based on UPA1AM52)
Checksum:       16MB:92EDh
Sign-on Message:
                UP-APL01 R5.3 (UPA1AM53)(03/31/2021)

Change:
        Fixed Memory Speed show unknown in SMBIOS Type 17
==========================================================================
==========================================================================
BIOS Name:      UPA1AM52                (based on UPA1AM51)
Checksum:       16MB:A6CDh
Sign-on Message:
                UP-APL01 R5.2 (UPA1AM52)(08/04/2020)

Change:
        1. Patch PMIC may cause system won't boot in low temperature
        2. Patch SMBIOS type 17 corruption
===========================================================================
===========================================================================
BIOS Name:      UPA1AM51                (based on UPA1AM50)
Checksum:       16MB:C225h
Sign-on Message:
                UP-APL01 R5.1 (UPA1AM51)(03/17/2020)

Change:
        1. Update CPU Microcode M03506C9_00000040, M03506CA_0000001E
        2. Add Restore AC Power Loss item in BIOS setup
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM50]              (based on [UPA1AM49])
Checksum:       [16]MB:[B0FE]h
Sign-on Message:
                UP-APL01 R5.0 (UPA1AM50)(12/17/2019)

Change:
        Control source of RTC wake function changed to By OS as default
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM49]              (based on [UPA1AM48])
Checksum:       [16]MB:[5B17]h
Sign-on Message:
                UP-APL01 R4.9 (UPA1AM49)(12/13/2019)

Change:
        Set PCIE_P3 speed as Gen 2 and PCIe Selectable De-emphasis as disable for Intel AC9260
        Added a setup item for setting the control source of RTC wake function
        Delete non-BIOS created boot option to fix issue that boot option disabled suddenly 
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM48]              (based on [UPA1AM47])
Checksum:       [16]MB:[1673]h
Sign-on Message:
                UP-APL01 R4.8 (UPA1AM48)(10/17/2019)

Change:
        Correct SMIOBS type 17 data memory type and form factor
        Remove the new DRR support of Samsung.K4F6E3S4HM-MGCJ
        Disabled the DTS to fix/workaround the issue that system hung on OS logo
        Implemented signal tuning parameters for all EMMC SKU
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM47]              (based on [UPA1AM46])
Checksum:       [16]MB:[E1DA]h
Sign-on Message:
                UP-APL01 R4.7 (UPA1AM47)(09/26/2019)

Change:
        To support new on-board memory chip, Micron.MT53E256M32D2DS-053 WT:B, Micron.MT53D512M32D2DS-053 WT:D and Samsung.K4F6E3S4HM-MGCJ.
        Update SMBIOS type 17 Manufacturer and PartNumber field.
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM46]              (based on [UPA1AM45])
Checksum:       [16]MB:[D024]h
Sign-on Message:
                UP-APL01 R4.6 (UPA1AM46)(08/14/2019)

Change:
        Set "OS reset select" as "Warm Reset" to fix issue that OS restart becomes cold reset.
        Patch issue that TPM self-test CMD is timeout sometimes.
        Enable iTCO as default.
        Intel uCode update for Intel-SA00233
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM45]              (based on [UPA1AM44])
Checksum:       [16]MB:[180B]h
Sign-on Message:
                UP-APL01 R4.5 (UPA1AM45)(07/11/2019)

Change:
        Intel microcode update
        SMBIOS and HSIO signal tuning change for F-1 stepping support
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM44]              (based on [UPA1AM43])
Checksum:       [16]MB:[B76A]h
Sign-on Message:
                UP-APL01 R4.4 (UPA1AM44)(06/27/2019)

Change:
        Spec. Change - To add iTCO function with default timer 30 seconds. iTCO is default disabled
        and can be enabled by setup item iTCO.
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM43]              (based on [UPA1AM42])
Checksum:       [16]MB:[A2B3]h
Sign-on Message:
                UP-APL01 R4.3 (UPA1AM43)(03/14/2019)

Change:
        Update microcode to support F1 CPU stepping
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM42]              (based on [UPA1AM41])
Checksum:       [16]MB:[0AF5]h
Sign-on Message:
                UP-APL01 R4.2 (UPA1AM42)(03/12/2019)

Change:
        FOR H/W Changed : Support H/W A1.1 FPGA Register MAP
        Fix issue that setup item "Core 1" cannot disable CPU core 1
        Detect EMMC size then program different signal tuning value
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM41]              (based on [UPA1AM40])
Checksum:       [16]MB:[42E2]h
Sign-on Message:
                UP-APL01 R4.1 (UPA1AM41)(09/21/2018)

Change:
        FOR H/W Changed : Support H/W A1.1 FPGA Register MAP
        Patched : EMMC Storage will be lost when 0 degree randomly .
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM40]              (based on [UPA1AM39])
Checksum:       [16]MB:[6B83]h
Sign-on Message:
                UP-APL01 R4.0 (UPA1AM40)(08/06/2018)

Change:
        Spec. Changed : Supported Two Setup Options to Control Directions of HAT Pins ; 12 & 35
        Fixed : "Quiet Boot" will not be Reload to Default when User Press "F3" in BIOS Setup Menu
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM39]              (based on [UPA1AM38])
Checksum:       [16]MB:[513B]h
Sign-on Message:
                UP-APL01 R3.9 (UPA1AM39)(06/29/2018)

Change:
        Fixed : DP/HDMI Flickering under Windows 10 when System is Idling
        Fixed : User Level Password will be Lost after Re-load BIOS Default
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM38]              (based on [UPA1AM37])
Checksum:       [16]MB:[F4FE]h
Sign-on Message:
                UP-APL01 R3.8 (UPA1AM38)(06/20/2018)

Change:
        Spec. Changed : Support Setup Options to Control EXHAT Pin 50/52/54/58/60
        Upgrade ApolloLake CPU Microcode
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM37]              (based on [UPA1AM36])
Checksum:       [16]MB:[2A7E]h
Sign-on Message:
                UP-APL01 R3.7 (UPA1AM37)(04/18/2018)

Change:
        For H/W A1.1 Changed : birdir_EXHAT12/13/14/15 change from LPSS_I2C5/6 to LPSS_I2C2/3 - Changed for Windows 10 IoT Core & ubiLinux PinCtrol
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM36]              (based on [UPA1AM35])
Checksum:       [16]MB:[026D]h
Sign-on Message:
                UP-APL01 R3.6 (UPA1AM36)(04/10/2018)

Change:
        For H/W A1.1 Changed : LPSS_I2C0/I2C1 Mux Function birdir_HAT18/19/20/21 change from ISH_GPIO13/12/11/10 to SIO_SPI_2_FS0/SIO_SPI_2_CLK/SDIO_CLK/AVS_I2S2_MCLK
        For H/W A1.1 Changed : birdir_EXHAT12/13/14/15 change from LPSS_I2C5/6 to LPSS_I2C2/3
        Spec. Change : Request from Intel , HAT PIN 12/35 Default as Output Direction for I2S Function
        Spec. Change : Request from Intel , Change aDSP Key from cAvsImage1Manifest to cAvsImage0Manifest
        Remove Intel ISS Debug/Trace Support for Formal Release Version

Note:
        SMBIOS(DMI) Information will be cleared after flash BIOS to this version
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM35]              (based on [UPA1AM34])
Checksum:       [16]MB:[1BE6]h
Sign-on Message:
                UP-APL01 R3.5 (UPA1AM35)(02/13/2018)

Change:
        Power Consumption will be Decreased less than 1 second
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM34]              (based on [UPA1AM33])
Checksum:       [16]MB:[418A]h
Sign-on Message:
                UP-APL01 R3.4 (UPA1AM34)(01/19/2018)

Change:
        1. PM Request : CPU Power Limit to 13W
        2. Support Android-IA
        3. For H/W A1.1 Changed : Emutex Request - SMBIOS Base Board Version will be "V0.5" on H/W A1.1 Board
        4. For H/W A1.1 Changed : MIPI Camera Design Changed
        5. For Intel Security Advisory - Update CPU Microcode
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM33]              (based on [UPA1AM32])
Checksum:       [16]MB:[1749]h
Sign-on Message:
                UP-APL01 R3.3 (UPA1AM33)(01/17/2018)

Change:
        1. Spec. Changed - BIOS Logo Change
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM32.bin]          (based on [UPA1AM31])
Checksum:       [16]MB:[35CB]h
Sign-on Message:
                UP-APL01 R3.2 (UPA1AM32)(12/14/2017)

Change:
        1. Fixed : USB 3.0 key will run lower speed after updating TXE ver.3.1.50.2222
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM31.bin]          (based on [UPA1AM30])
Checksum:       [16]MB:[9C3F]h
Sign-on Message:
                UP-APL01 R3.1 (UPA1AM31)(12/12/2017)

Change:
        1. Intel Request : Support Apollo Lake DCI Debug Interface

Note:
1. SMBIOS Information will be lost after flash to this version .
===========================================================================

===========================================================================
BIOS Name:      [UPA1AM30.bin]          (based on [UPA1AM23])
Checksum:       [16]MB:[86DB]h
Sign-on Message:
                UP-APL01 R3.0 (UPA1AM30)(12/07/2017)

Change:
        1. Fix issue that after disabling setup item LPSS SPI#1, SPI#3 will disappear too.
        2. Fix issue that resource Hub proxy 4 contains I2C0 and I2C1 controller,
           once either one is disabled then the other one will not work (ProblemCode:51 in OS DM).
        3. Disable other funxtion under same device when function 0 is disabled on first 
           boot for SPI, UART and I2C.

        4. Fixed : Intel ME/TXE Security Issue
        5. Update Apollo Lake Intel PMC FW v03.1d.00 Release
        6. Emutex's Request : Support Setup Option Control for SPI ADC124S101 Channel 0 ~ 3
        7. Workaround : HDMI / Display Port will flickering with non-recommend resoulution under Windows 10

Note:
1. SMBIOS Information will be lost after flash to this version .
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM23.bin]          (based on [UPA1AM22])
Checksum:       [16]MB:[E407]h
Sign-on Message:
                UP-APL01 R2.3 (UPA1AM23)(11/17/2017)

Change:
        FOR Win10 IoT Core : Support WIN10 IoT core UWP (Universal Windows Platform).
        Resource Hub proxy will present only when setup OS Selection is Win10 IOT Core.
Known Issue:
        1. After disabling setup item "LPSS SPI#1", SPI#3 will disappear too.
        2. Resource Hub proxy 4 contains I2C0 and I2C1 controller, once either one 
           is disabled then the other one will not work (ProblemCode:51 in OS DM).
        3. MSFT GpioTestTool.exe will get all the 54 pins in resource Hub proxy in order.
           User will confuse with HAT GPIO pin number, because we are now 
           transferring the pin number in our OS APP.
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM22.bin]          (based on [UPA1AM21])
Checksum:       [16]MB:[6DBF]h
Sign-on Message:
                UP-APL01 R2.2 (UPA1AM22)(10/11/2017)

Change:
        Fixed : Blink Display under Windows with E0 Stepping CPU
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM21.bin]          (based on [UPA1AM20])
Checksum:       [16]MB:[1078]h
Sign-on Message:
                UP-APL01 R2.1 (UPA1AM21)(09/01/2017)

Change:
        Emutex Request : [LPSS I2C #2 Speed] default as [Standard Mode]
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM20.bin]          (based on [UPA1AM19])
Checksum:       [16]MB:[1CCA]h
Sign-on Message:
                UP-APL01 R2.0 (UPA1AM20)(08/11/2017)

Change:
        FOR Win10 IoT Core : Support Secure Boot and Disabled as default.
        Fixed : Custom SMBIOS Information will be gone after CMOS Battery lossed
        Fixed : Default Administrator Password will be gone after BIOS Restore Default
        Emutex Request : USB OTG Enabled as Default, and Override Related Register Settings
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM191.bin]         (based on [UPA1AM19])
Checksum:       [16]MB:[9B56]h
Sign-on Message:
                UP-APL01 R1.9.1 (UPA1AM19)(07/27/2017)

Change:
        Supported fTPM - Intel PTT

Note: Only for AAEON Internal
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM19.bin]          (based on [UPA1AM18])
Checksum:       [16]MB:[3B2A]h
Sign-on Message:
                UP-APL01 R1.9 (UPA1AM19)(07/05/2017)

Change:
        Custom Request : Dynamic Hide a virtual Emutex's ASL Device under Windows, depend on "OS Selection" under Setup Menu
        Fixed : CPU Frequency Incorrect when EIST Disabled
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM18.bin]          (based on [UPA1AM17])
Checksum:       [16]MB:[7E78]h
Sign-on Message:
                UP-APL01 R1.8 (UPA1AM18)(06/23/2017)

Change:
        Fixed : Incorrect EN_I2C0 / EN_I2C1 command setting
        Emutex's Request : According to I2C Function Enabled/Disabled, corresponding pins should be Hi-Z
        Support MIPI CSI Camera : OV2740 & OV8856

Camera Support Requirement:
1. Windows 10 RS1
2. Driver Install manully
3. BIOS Setting Change (Administrator Mode)
        CRB Setup -> CRB Chipset -> Uncore Configuration -> IPU Enabled/Disabled : Enabled
        CRB Setup -> CRB Chipset -> Uncore Configuration -> SA IPU ACPI Mode : IGFX Child
        Boot -> OS Selection : Windows

        Only support one kind of camera at the same time
                OV8856 : CRB Setup -> CRB Chipset -> Uncore Configuration -> Rear Camera : IMX135
                OV2740 : CRB Setup -> CRB Chipset -> Uncore Configuration -> Front Camera : OV2740
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM17.bin]          (based on [UPA1AM16])
Checksum:       [16]MB:[B73D]h
Sign-on Message:
                UP-APL01 R1.7 (UPA1AM17)(06/14/2017)

Change:
        Emutex's Request : Re-arrange BIOS Setup Menu and BIOS Default Modification
        Emutex's Request : aDSP pubkey only supported cAvsImage1Manifest
        Fixed : Wrong Setup String of Memory Type
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM16.bin]          (based on [UPA1AM15])
Checksum:       [16]MB:[DFD3]h
Sign-on Message:
                UP-APL01 R1.6 (UPA1AM16)(06/07/2017)
Change:
        Emutex's Request : USB Device as the 1st boot priority boot device.
        Emutex's Request : All GPIOs as GPIO Drive Mode even it's multi-function pin, and default as MultiFunctions
        Emutex's Request : Built in a custom aDSP public key
        Emutex's Request : Re-arrange BIOS Setup Menu
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM15.bin]          (based on [UPA1AM14])
Checksum:       [16]MB:[133F]h
Sign-on Message:
                UP-APL01 R1.5 (UPA1AM15)(05/26/2017)

Change:
        Emutex's Request : Support FPGA initialization during BIOS POST
        Emutex's Request : Fixed GPIO Interrupt Issue
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM14.bin]          (based on [UPA1AM13])
Checksum:       [16]MB:[76B9]h
Sign-on Message:
                UP-APL01 R1.4 (UPA1AM14)(05/09/2017)

Change:         
        Emutex's Request : All GPIO Input Pins as "GPIO Driver Mode"
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM13.bin]          (based on [UPA1AM12])
Checksum:       [16]MB:[1DE1]h
Sign-on Message:
                UP-APL01 R1.3 (UPA1AM13)(04/24/2017)

Change:         
        Customer's Request (Emutex) : "Console Redirection" : Enabled
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM12.bin]          (based on [UPA1AM11])
Checksum:       [16]MB:[61FF]h
Sign-on Message:
                UP-APL01 R1.2 (UPA1AM12)(04/24/2017)

Change:         
        Customer's Request (Emutex) : "VT-d" : Enabled
        Customer's Request (Emutex) : "OS Selection" : Intel Linux
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM11.bin]          (based on [UPA1AM10])
Checksum:       [16]MB:[1968]h
Sign-on Message:
                UP-APL01 R1.1 (UPA1AM11)(04/21/2017)

Change:         
        Customer's Request (Emutex) : Emutex released a new ACPI table for bug fixed
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM10.bin]          (based on [UPA1AM09])
Checksum:       [16]MB:[4F7D]h
Sign-on Message:
                UP-APL01 R1.0 (UPA1AM10)(04/20/2017)

Change:         
        Customer's Request (Emutex) : Supported BIOS Default Password
        Customer's Request (Emutex) : Re-arrange BIOS Setup Menu
        Customer's Request (Emutex) : Built in a ACPI Table for HAT Function
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM09.bin]          (based on [UPA1AM08])
Checksum:       [16]MB:[95B8]h
Sign-on Message:
                UP-APL01 R0.9 (UPA1AM09)(04/17/2017)

Change:         
        Customer's Request (Emutex) : SMBIOS TYPE 2 - BASE BOARD "BASE_BOARD_VERSION" as V0.3
        Customer's Request (Emutex) : Expand Main BIOS Size for reserved.
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM08.bin]          (based on [UPA1AM07])
Checksum:       [16]MB:[880F]h
Sign-on Message:
                UP-APL01 R0.8 (UPA1AM08)(04/12/2017)
Change:         
        FOR UP^2, Support Setup Items to Control HAT 40 Pins.
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM07.bin]          (based on [UPA1AM06])
Checksum:       [16]MB:[668F]h
Sign-on Message:
                UP-APL01 R0.7 (UPA1AM07)(03/22/2017)
Change:         
        H/W Design: FOR UP-APL01, FAN from PWM2 only supported On or Off
        H/W Design Changed: Support PCIe / mSATA Switch by GPIO Pin
        PM Product Spec. Requirement: FOR UP-APL01, Support Power Button Notify from Wake State
        PM Product Spec. Requirement: FOR UP-APL01, Support USB wake from S3 & S4.
        Upgrade to the latest AAEON CRB Code
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM06.bin]          (based on [UPA1AM05])
Checksum:       [16]MB:[5688]h
Sign-on Message:
                UP-APL01 R0.6 (UPA1AM06)(02/21/2017)

Change:         
        Support Uefi PXE boot (Network Stack)
        Support USB ports ejectable feature
        Support Console Redirection feature (HSUART0 only)
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM05.bin]          (based on [UPA1AM04])
Checksum:       [16]MB:[E329]h
Sign-on Message:
                UP-APL01 R0.5 (UPA1AM05)(02/10/2017)

Change:         
        FOR H/W A0.3 design changed, re-define SoC GPIO multifunction pins
        FOR FAN default enabled, PWM0 / PWM1 / PWM2 / PWM3 default as GPO High
        "GPIO_37 PWM3" was not floating anymore
        Support CPU DTS temperature
        Arrange BIOS setup
        Fixed: There's a yellow mark under windows(SD Controller)
        H/W A0.3 Changed, DDI0 changed from HDMI to DP
        Built in LPSS Device ASL code
        Only support 1 LPSS UART
        Remove unnecessary ASL devices
        Core Base Upgrade
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM04.bin]          (based on [UPA1AM03])
Checksum:       [16]MB:[8AE3]h
Sign-on Message:
                UP-APL01 R0.4 (UPA1AM04)(01/03/2017)

Change:         
        Fine-tuned, Integrated Graphics Power will not be dropped when running Intel TAT Gfx workload
        Adjust SATA Port 0 TX Voltage Swing according to SI's test result.
        Upgrade to the latest AAEON CRB Code
        
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM03.bin]          (based on [UPA1AM02])
Checksum:       [16]MB:[BE6B]h
Sign-on Message:
                UP-APL01 R0.3 (UPA1AM03)(12/08/2016)

Changes:
        FOR Apollolake Platform, support GPIO Power Button SCI
        FOR UP-APL01, CPU Frequency Should be Capable to Reach to the Maximum
        Correct SMBIOS Data
        Support OnBoard Flash BIOS under EFI Shell
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM02.bin]          (based on [UPA1AM01])
Checksum:       [16]MB:[B613]h
Sign-on Message:
                R0.2 (UPA1AM02)(12/02/2016)

Changes:
        BIOS Default Modification. Cont.
        BIOS Default Modification
        PCIe Ports CLKREQs Routing
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM01.bin]          (based on [UPA1AM00])
Checksum:       [16]MB:[9F52]h
Sign-on Message:
                R0.1 (UPA1AM01)(11/29/2016)

Changes:
        PCIe Ports CLKREQs Routing
        FOR UP-APL01, VBIOS Porting in Project Level
        H/W Design Changed from 8MB to 16MB
        FOR UP-APL01, SoC GPIO MultiFunction Pins Porting
        TXE Configuration
===========================================================================
===========================================================================
BIOS Name:      [UPA1AM00.bin]          (based on [1ATJS024_M0B])
Checksum:       [8]MB:[D0C2]h
Sign-on Message:
                R0.0 (UPA1AM00)(11/24/2016)

Changes:
        Support Memory Down on UP-APL01, cont. (for UP-APL01 4GB memory down, 1GB x 4)
        FOR UP-APL01, support more than 1 memory down configurations
        Migrate SoC GPIO Pins Configurations to Project Level
        Power Solution : PMIC for UP-APL01
        Override BOARDID for UP-APL01, and FLASH SIZE as 8MB temporarily
        Support Memory Down on UP-APL01, override SMIP F/W
===========================================================================
