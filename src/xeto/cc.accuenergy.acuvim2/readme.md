## Introduction

This library defines Xeto device specs for the Acuvim II Series Power Meter.

Please note not all points supported by the Acuvim II are defined.  These specs are preliminary and subject to change.

There are Project Haystack community initiatives to validate and improve these specs so that system integrators can have confidence in using them.  Also, we would welcome any feedback that you have to improve these specs.

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
 * Might need to support sunspec scale factors (example modbus address 450102)
