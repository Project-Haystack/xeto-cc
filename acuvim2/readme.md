## Introduction

This library defines Xeto device specs for the Acuvim II Series Power Meter.  Data points modeled so far are "real-time measurements" described in the following locations of the Acuvim II user manual:

 * Modbus register maps (Tables 6-19, 6-20, and 6-27)
 * BACnet objects (Table 6-85)

Note: "real-time measurements" referenced in Section 6.3.7 of the Acuvim II user manual are different than 50ms or 100ms metering parameters.

[Acuvim II user manual](https://accucdn.accuenergy.com/wp-content/uploads/Acuvim-II-Power-Meter-User-Manual-1040E1303.pdf)

## Meter configuration requirements

These configuration settings must be applied to the Acuvim II for the Xeto specs to be semantically correct:

 * Setting called "VAR/PF Convention" must be set to "IEC" (Acuvim II User Manual Section 4.8.4)
 * Setting called "VAR Calculation Method" must be set to "True Method" (Acuvim II User Manual Section 4.8.4)
 * Parameter mode for reading analog measurements must be set to "Primary Mode" (Acuvim II User Manual Section 6.3.7)
 * Voltage input wiring config must be set to 1LN, 1LL, 2LL, 3LL, 3LN-2.5, or 3LN (Acuvim II User Manual Section 2.3.2)

**Note:**  The Xeto spec chosen from this library shall be based on the voltage input wiring config as well.

## Notes

 * Table 6-20 shows "R/W" as the access property for modbus registers.  These registers are modeled as having read only access at this time.
 * A subset of the BACnet addresses in Table 6-85 do not describe the semantic differences between wiring configs as shown for Table 6-27.