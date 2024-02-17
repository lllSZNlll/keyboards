# Djinn Rev2a BOM

## PCB Manufacture

I've had some reports that JLCPCB have thrown on a $15.20 USD extra charge due to too many instances of routing.

I (@tzarc) wasn't charged, but there are now reports on Discord that JLCPCB are charging extra.

If you've been given an extra charge, feel free to ask them why you've been charged more than others with the same design... and let @tzarc know so we can keep track of whether other PCB manufacturers should be recommended instead of JLCPCB.

## Build Notes

**There are two resistors that are used to determine whether the PCB is a left-hand or a right-hand board -- R23 and R25. Populate only one; R23 for a left-hand board, R25 for a right-hand board.**

During the build, the connectors for the USB-C, and the LCD 1x09 connector **need to be mounted on the side opposite to the rest of the surface-mount components**. For ease of the build, it's best to populate and solder these onto the board last. The 1x09 LCD connector can also be soldered with the LCD screwed into the board with standoffs, in order to ensure proper alignment.

RGB underglow LEDs can be soldered on either side of the board.

Most "jellybean" components can be swapped out for whichever you've got available -- 100nF capacitors are so ubiquitous that there's no need to buy this specific part. Any other 0805 100nF capacitor will likely suffice.

The "Connector (ST-Link)" **is optional** and is not required -- this is a debugging port for an ST-Link. If you choose to do so, it can be mounted with the pins straddling the edge of the PCB.

The "IC (SPI FLASH)" **is not required** -- this is for future QMK development and the Djinn has no requirement for it to be on the board.

There is a few sets of solder bridges that need to be filled in to get certain aspects working:

* LCD_Left / LCD_Right -- 9 separate solder bridges that connect the LCD connector to the normal lines required to actually drive the LCD. You'll note that these are populated in the same location on both sides of the board -- only the side being built should have the solder bridges filled in. Left-hand should have LCD_Left soldered, right-hand should have LCD_Right soldered.

## Components listing

| Type                    | Count (Total) | Count (Per PCB) | Value              | Footprint | Part Number               | Link                                                                                                                                                                                                                                                      |
|-------------------------|---------------|-----------------|--------------------|-----------|---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Capacitor (MLCC)        | 30            | 15              | 100nF              | 0805      | CL21F104ZBCNNNC           | https://lcsc.com/product-detail/Multilayer-Ceramic-Capacitors-MLCC-SMD-SMT_Samsung-Electro-Mechanics-CL21F104ZBCNNNC_C1760.html                                                                                                                           |
| Capacitor (MLCC)        | 8             | 4               | 4.7uF              | 0805      | CL21A475KAQNNNE           | https://lcsc.com/product-detail/Multilayer-Ceramic-Capacitors-MLCC-SMD-SMT_Samsung-Electro-Mechanics-CL21A475KAQNNNE_C1779.html                                                                                                                           |
| Capacitor (Tantalum)    | 16            | 8               | 100uF              | 6032      | F931C107KCC               | https://lcsc.com/product-detail/Tantalum-Capacitors_AVX-F931C107KCC_C273664.html                                                                                                                                                                          |
| Resistor                | 36            | 18              | 9.1k 1%            | 0805      | RK73H2ATTD9101F           | https://lcsc.com/product-detail/Chip-Resistor-Surface-Mount_KOA-Speer-Elec-RK73H2ATTD9101F_C317276.html                                                                                                                                                   |
| Resistor                | 22            | 11              | 68k 1%             | 0805      | AC0805FR-0768KL           | https://lcsc.com/product-detail/Chip-Resistor-Surface-Mount_YAGEO-AC0805FR-0768KL_C228958.html                                                                                                                                                            |
| Resistor                | 6             | 3               | 120ohm 1%          | 0805      | WR08X1200FTL              | https://lcsc.com/product-detail/Chip-Resistor-Surface-Mount_Walsin-Tech-Corp-WR08X1200FTL_C163960.html                                                                                                                                                    |
| Diode (Signal)          | 80            | 40              | 1N4148             | SOD-123FL | 1N4148WL                  | https://lcsc.com/product-detail/Switching-Diode_Shandong-Jingdao-Microelectronics-1N4148WL_C108804.html                                                                                                                                                   |
| Diode (TVS Protection)  | 4             | 2               | SMF5.0CA           | SOD-123FL | SMF5.0CA                  | https://lcsc.com/product-detail/TVS_MDD-Microdiode-Electronics-SMF5-0CA_C364279.html                                                                                                                                                                      |
| IC (SPI FRAM)           | 2             | 1               | 64kbit/8kB         | SOIC-8    | MB85RS64PNF-G-JNERE1      | https://lcsc.com/product-detail/FRAM_FUJITSU-MB85RS64PNF-G-JNERE1_C8741.html                                                                                                                                                                              |
| IC (SPI FLASH)          | 2 (skip)      | 1 (skip)        | -                  | SOIC-8W   | W25Q32JVSSIQ              | Not required for Djinn, do not populate, used for future QMK development                                                                                                                                                                                  |
| IC (Voltage Regulator)  | 2             | 1               | 3.3V               | SOT-23-5  | AP2127K-3.3TRG1           | https://lcsc.com/product-detail/Dropout-Regulators-LDO_Diodes-Incorporated-AP2127K-3-3TRG1_C156285.html                                                                                                                                                   |
| IC (Op-Amp)             | 2             | 1               | -                  | SOT-23-5  | LMV321B-TR or LMV321      | https://lcsc.com/product-detail/Low-Power-OpAmps_3PEAK-LMV321B-TR_C248567.html or https://lcsc.com/product-detail/Low-Power-OpAmps_IDCHIP-LMV321_C395459.html                                                                                             |
| IC (Current Limiter)    | 4             | 2               | -                  | SOT-23-6  | TPS2553DBVR or AP2553W6-7 | https://lcsc.com/product-detail/PMIC-Power-Distribution-Switches_Texas-Instruments-TPS2553DBVR_C55266.html or https://lcsc.com/product-detail/PMIC-Power-Distribution-Switches_Diodes-Incorporated_AP2553W6-7_Diodes-Incorporated-AP2553W6-7_C212302.html |
| Diode (ESD Protection)  | 4             | 2               | -                  | SOT-23-6  | AZC199-04S.R7G or SRV0504 | https://lcsc.com/product-detail/TVS_AMAZING-AZC199-04S-R7G_C356821.html or https://lcsc.com/product-detail/TVS_Leiditech-SRV0504_C384888.html                                                                                                             |
| IC (MCU)                | 2             | 1               | -                  | LQFP-64   | STM32G474RET6             | https://au.mouser.com/ProductDetail/STMicroelectronics/STM32G474RET6?qs=%2Fha2pyFaduhBp7B0yN03ycB%252BZ%252BLXFeacrURrEXR6i%252Bv3eck5WgVsdQ%3D%3D                                                                                                        |
| Resettable Fuse         | 2             | 1               | 3.0A               | 1206      | MF-NSMF150-2              | https://lcsc.com/product-detail/PTC-Resettable-Fuses_BOURNS-MF-NSMF150-2_C89655.html                                                                                                                                                                      |
| Resettable Fuse         | 2             | 1               | 1.5A               | 1206      | MF-NSMF075-2              | https://lcsc.com/product-detail/PTC-Resettable-Fuses_BOURNS-MF-NSMF075-2_C89653.html                                                                                                                                                                      |
| Switch (Hotswap Socket) | 64            | 32              | -                  | -         | Kailh Hotswap             | https://www.aliexpress.com/item/32903471019.html                                                                                                                                                                                                          |
| Switch (5-way Tactile)  | 2             | 1               | -                  | 10x10mm   | K1-1506DN-01              | https://lcsc.com/product-detail/5-way-Tactile-Switches_Korean-Hroparts-Elec-K1-1506DN-01_C145911.html                                                                                                                                                     |
| Switch (Cap)            | 2             | 1               | -                  | -         | 6JBLK                     | https://lcsc.com/product-detail/Switch-accessories-or-Caps_E-Switch-6JBLK_C273384.html                                                                                                                                                                    |
| Switch (Rotary Encoder) | 2             | 1               | -                  | -         | EC11N1525404              | https://lcsc.com/product-detail/Coded-Rotary-Switches_ALPS-Electric-EC11N1525404_C470748.html                                                                                                                                                             |
| Connector (USB-C)       | 4             | 2               | -                  | -         | TYPE-C-31-M-12            | https://lcsc.com/product-detail/USB-Connectors_Korean-Hroparts-Elec-TYPE-C-31-M-12_C165948.html                                                                                                                                                           |
| Inductor                | 26            | 13              | 100ohm @ 100MHz 4A | 0805      | MPZ2012S101AT000          | https://lcsc.com/product-detail/Ferrite-Beads_TDK-MPZ2012S101AT000_C15957.html                                                                                                                                                                            |
| Connector (LCD)         | 2             | 1               | -                  | 1x09      | C39576                    | https://lcsc.com/product-detail/Pin-Header-Female-Header_BOOMELE-Boom-Precision-Elec-C39576_C39576.html                                                                                                                                                   |
| Piezo Buzzer            | 2             | 1               | -                  | 16x16mm   | KLJ-1625                  | https://lcsc.com/product-detail/Buzzers_KELIKING-KLJ-1625_C201041.html                                                                                                                                                                                    |
| Switch (Microswitch)    | 2             | 1               | -                  | -         | TSA451G50-250             | https://lcsc.com/product-detail/Tactile-Switches_BRIGHT-TSA451G50-250_C294483.html                                                                                                                                                                        |
| RGB LED                 | 86            | 43              | -                  | 6028      | SK6812Mini-E              | https://www.aliexpress.com/item/4000475685852.html                                                                                                                                                                                                        |
| MOSFET                  | 8             | 4               | -                  | SOT-23-3  | AO3401A                   | https://lcsc.com/product-detail/MOSFET_UMW-Youtai-Semiconductor-Co-Ltd-AO3401A_C347476.html                                                                                                                                                               |
| MOSFET                  | 4             | 2               | -                  | SOT-23-3  | 2N7002                    | https://lcsc.com/product-detail/MOSFET_MDD-Microdiode-Electronics-2N7002_C472906.html                                                                                                                                                                     |
| Transistor (Pre-biased) | 2             | 1               | -                  | SOT-23-3  | MMUN2133LT1G              | https://lcsc.com/product-detail/Digital-Transistors_ON-Semiconductor-MMUN2133LT1G_C86182.html                                                                                                                                                             |
| Transistor (Pre-biased) | 2             | 1               | -                  | SOT-23-3  | MMUN2233LT1G              | https://lcsc.com/product-detail/Transistors-NPN-PNP_ON-Semiconductor-MMUN2233LT1G_C86932.html                                                                                                                                                             |
| Connector (ST-Link)     | 2 (optional)  | 1 (optional)    | -                  | 2x05      | MTF185-205SY3             | https://lcsc.com/product-detail/Pin-Header-Female-Header_MINTRON-MTF185-205SY3_C358738.html                                                                                                                                                               |
| LCD                     | 2             | 1               | -                  | 1x09      | 2.2" No Touch             | https://www.aliexpress.com/item/4000219159401.html                                                                                                                                                                                                        |

## Fasteners / Hardware

| Type                  | Count (Total) | Count (Per side) | Model        | Link                                               |
|-----------------------|---------------|------------------|--------------|----------------------------------------------------|
| Knob (Rotary Encoder) | 2             | 1                | 25x15.5x6mm  | https://www.aliexpress.com/item/32802067713.html   |
| Screw                 | 26            | 13               | M3x3 D7x0.7  | https://www.aliexpress.com/item/32998579840.html   |
| Screw                 | 26            | 13               | M3x8 D7x0.7  | https://www.aliexpress.com/item/32998579840.html   |
| Screw                 | 8             | 4                | M3x12 D7x0.7 | https://www.aliexpress.com/item/32998579840.html   |
| Screw                 | 8             | 4                | M3x5 D7x0.7  | https://www.aliexpress.com/item/32998579840.html   |
| Standoff              | 52 (or 60)    | 26 (or 30)       | M3x3x4.2     | https://www.aliexpress.com/item/4000153040875.html |
| Standoff              | 8             | 4                | M3x12x4.2    | https://www.aliexpress.com/item/4000153040875.html |
| Standoff              | 8             | 4                | M3x4x4.2     | https://www.aliexpress.com/item/4000153040875.html |
| Washer                | 26            | 13               | M3           | https://www.aliexpress.com/item/33000267180.html   |