## TI-RSLK Robot Platform

**Project description:** This code was written during the robotics laboratory course for my minor in robotics & autonomous systems. The implemented code was written in C and involved low-level hardware interaction with the robot platform. The TI-RSLK consists of a 2-motor wheelbase, an 8-point IR sensor, and several limit switches used as bump sensors. I implemented functions that:
  - Generated PWM signals from timers and interrupts
  - Controlled motors using PWM signals
  - Enabled line-following behavior using a finite state machine and the IR sensor
  - and more!
The code involved modifying particular registers for various ports as well as doing bitwise operations in order to enable things like the Nested Vectored Interrupt Controller (NVIC) with particular parameters.

The code can be found on my GitHub page.
