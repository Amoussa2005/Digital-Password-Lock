# Digital Password Lock Using Logic ICs

A digital password verification system designed and implemented entirely using digital logic ICs, without a microcontroller.

## Features

- Three push-button inputs: A, B, and C
- Fixed password: **ABC**
- **Red LED** indicates the initial state and incorrect password entry
- **Green LED** indicates successful authentication
- 7-segment display shows the number of consecutive incorrect attempts
- Automatic lockout after three consecutive incorrect attempts
- Green LED remains OFF after lockout, even if the correct password is subsequently entered
- Approximately 2-second buzzer alert when the system locks
- Dedicated hardware reset button
- Designed in Proteus and physically implemented on a breadboard

## Main Components

- 7474 D Flip-Flops
- 74161 Binary Counters
- CD4511 BCD-to-7-Segment Decoder
- 7408, 7411, 7414 and other logic gates
- NE555 Timer
- 2N2222 Transistor
- Common-Cathode 7-Segment Display
- Push Buttons, LEDs, Buzzer, Resistors and Capacitors

## Working Principle

The user enters the predefined password **ABC** using three push buttons.

The D flip-flops verify the entered sequence, while binary counters track the number of inputs and incorrect attempts.

### Initial State

- The red LED is ON.
- The green LED is OFF.
- The 7-segment display shows 0.
- The system is ready to accept a password.

### Correct Password

When the correct sequence **ABC** is entered:

- The green LED turns ON.
- The red LED turns OFF.

### Incorrect Password

When an incorrect sequence is entered:

- The red LED turns ON.
- The green LED remains OFF.
- The wrong-attempt counter increments by 1.
- The updated number of incorrect attempts is displayed on the 7-segment display.

### Three-Attempt Lockout

After three consecutive incorrect password attempts:

- The 7-segment display shows 3.
- The system enters a locked state.
- A buzzer sounds for approximately 2 seconds using a 555 timer.
- The green LED remains OFF, **even if the correct password ABC is subsequently entered**.
- Further password attempts cannot unlock the system.

### Hardware Reset

A dedicated **RESET push button** is used to reinitialize the circuit.

Pressing RESET:

- Clears the wrong-attempt counter to 0.
- Resets the password-verification flip-flops.
- Clears the lockout condition.
- Turns the green LED OFF and restores the red LED to ON.
- Allows the user to enter a new password sequence.

## Clock Timing and Race Condition Prevention

During physical implementation, timing issues were encountered due to differences in propagation delays between the combinational logic and sequential components.

In particular, the D inputs and clock signals of the flip-flops could change nearly simultaneously, causing incorrect data to be captured.

To improve reliability:

- Schmitt-trigger inverters (7414) were used to produce clean digital transitions.
- Clock polarity and timing were adjusted to allow the D inputs to stabilize before the active clock edge.
- The timing of password verification and wrong-attempt counting was carefully tested to prevent unintended counter increments.

These adjustments helped address race conditions and improve the reliability of the breadboard implementation.

## Breadboard Implementation

![Breadboard Implementation](Digital%20Password%20Lock/Breadboard.jpeg)

## Demonstration

[Watch the Demonstration](Digital%20Password%20Lock/Demo.mp4)

## Challenges and Learning Outcomes

- Sequential digital logic and password verification
- D flip-flop setup and hold timing requirements
- Race conditions and propagation-delay analysis
- RC delay networks and clock synchronization
- Push-button debouncing using Schmitt triggers
- Binary counters and BCD display decoding
- Three-attempt lockout implementation
- 555 timer monostable operation
- Troubleshooting unintended resets and clock triggering
- Translating a simulated circuit into physical hardware

## Author

Ali Moussa

Electrical & Electronics Engineering Student
