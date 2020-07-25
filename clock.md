# Description

| Name | Value |
| ---- | ----- |
| name | Generic Clock |
| hardware_id | 0x12d0b402 |
| hardware_version | 1 |
| manufacturer_id | 0xFFFFFFFB |

# Starting state

- Starting state: Off
- Starting interrupt mode: Off

# Specification

Sending a hardware interrupt to this device does different things depending on the contents of the registers A and B. C is also used to store data

| A | B | Description |
|---|---:|------------|
| 0 | 0 | The clock is turned off. The interrupt mode is set to off |
| 0  | > 0 | The clock will tick 60/B times per second |
| 1 | N/A | The number of ticks that have fully passed since the clock received an interrupt with A == 0 are stored in C |
| 2 | 0 | Interrupt mode is set to off |
| 2 | > 0 | Interrupt mode is set to on. Future interrupts are triggered with the message B |

When the interrupt mode is set to on, an interrupt is triggered every tick with the stored message

# Addendum

Original spec located here: https://github.com/lucaspiller/dcpu-specifications/blob/master/clock.txt