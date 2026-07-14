# cc.accuenergy.acuvim_l

Device models for Accuenergy's Acuvim-L Series multifunction power and energy
meters.

Reference: Acuvim-L Multifunction Power and Energy Meter User Manual v4.

## Supported Models

The Acuvim-L Series covers two models that share the same Modbus register
map and BACnet object list:

- **Acuvim-EL**: 0.2% accuracy class (ANSI C12.20 / IEC 62053-22 class 0.5S),
  harmonic measurement to the 63rd order, adds time-of-use (TOU) tariff
  support
- **Acuvim-CL**: 0.5% accuracy class, harmonic measurement to the 31st order

The series-level `AcuvimL*` specs are abstract; model-specific concrete
specs inherit from them. Currently only Acuvim-EL concrete specs are
defined (`AcuvimEL*`); Acuvim-CL specs are planned future work.

## Wiring Configurations

The meter supports five voltage wiring modes (register 1003H): 3LN, 1LN,
2LL, 3LL, and 1LL. The 3LN-2.5 element configuration uses the 3LN setting.
The same Modbus registers are reused across wiring modes; in 2LL/3LL modes
the voltage THD registers report line-to-line THD (V12, V31, V23) rather
than phase THD, so the voltage THD points are modeled on wiring-specific
abstract types:

- `AcuvimLElecAc1LNOr1LLOr3LNMeter`: phase voltage THD
- `AcuvimLElecAc2LLOr3LLMeter`: line-to-line voltage THD

Abstract series-level wiring types: `AcuvimLElecAc3LNMeter`,
`AcuvimLElecAc1LNMeter`, `AcuvimLElecAc1LLMeter`, `AcuvimLElecAc3LLMeter`,
`AcuvimLElecAc2LLMeter`.

Concrete Acuvim-EL types: `AcuvimELElecAc3LNMeter`, `AcuvimELElecAc1LNMeter`,
`AcuvimELElecAc1LLMeter`, `AcuvimELElecAc3LLMeter`, `AcuvimELElecAc2LLMeter`.

## Configuration Assumptions

Point scale factors assume the following meter settings:

- Real-Time Reading mode (register 101DH) set to Primary; values include
  PT/CT ratios with no external multiplier
- Energy Display mode (register 1019H) set to Secondary or Primary 0.01kWh;
  energy registers convert with Rx/1000 (`*0.001` scale)
- Power factor convention IEC (register 1015H, factory default)
- Energy calculating mode Full, so power factor points are true power factor

## Omitted BACnet Objects

- AI33 Load Type: reports an ASCII character code (R/L/C), not a sensor value
- AI44 Energy Total and AI46 Reactive Energy Total: import plus export sums
- Per-phase export apparent energy registers have no BACnet objects; AI61-63
  expose the per-phase import apparent energy registers

## Omitted Modbus Registers

- In_measure (Modicon 408603): measured neutral current, only meaningful on
  units with a neutral CT input; no BACnet object
- Itotal (Modicon 408605): sum of phase currents; no BACnet object and no
  corresponding ph.elec sensor flavor
