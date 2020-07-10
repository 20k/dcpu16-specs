# Description

- name: Generic Clock
- hardware_id: 0x12d0b402
- hardware_version: 1
- manufacturer_id : 0xFFFFFFFB

# Starting state

- Starting state: Off
- Starting interrupt mode: Off

# Specification

Sending a hardware interrupt to this device does different things depending on the contents of the registers A and B. C is also used to store data

- A == 0 && B == 0: The clock is turned off. The interrupt mode is set to off
- A == 0 && B > 0: The clock will tick 60/B times per second
- A == 1: The number of ticks that have fully passed since the clock received an interrupt with A == 0 are stored in C
- A == 2 && B == 0: Interrupt mode is set to off
- A == 2 && B > 0: Interrupt mode is set to on. Future interrupts are triggered with the message B

When the interrupt mode is set to on, an interrupt is triggered every tick with the stored message 