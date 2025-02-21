# FPGA Timer Project

## Overview
This project implements a timer using an FPGA, designed as a Digital Systems Design (DSD) first-year project. The timer allows users to set and control time using a set of buttons and displays the time on a seven-segment BCD display.

![Screenshot 2025-02-21 202806](https://github.com/user-attachments/assets/508e0a34-8fc3-4680-a083-0ba7b989f6d5)

## Features
- **6 BCD 7-segment displays**: Displays minutes, seconds, and alarm time.
- **Max time display**: 99 minutes and 59 seconds.
- **Button controls**:
  - `M` (Minutes) and `S` (Seconds) buttons to set the time.
  - `START/STOP` button to start, stop, and resume the timer.
  - `SET_ALARM` button to configure the alarm.
- **Automatic countdown**: Timer counts down once set and activated.
- **Alarm system**: A blinking LED serves as an alarm once the timer reaches zero.
- **Clock synchronization**: Uses FPGA’s 100 MHz clock, converted to 1 Hz.
- **Reset functionality**: Holding `M` and `S` resets the timer.

## Design
![Image](https://github.com/user-attachments/assets/4b1cf440-331c-48ca-812b-bcc393797622)
### Black Box Model
- **Inputs**:
  - Clock (CLK) from the FPGA
  - User control buttons (M, S, START/STOP, SET_ALARM)
  - Reset signal
- **Outputs**:
  - LED indicators (mode waiting, counter running, alarm active)
  - 7-segment BCD display (time display)

### Control and Execution Units
- **Control Unit (CU)**: Handles user inputs and determines state transitions.
- **Execution Unit (EU)**: Implements the timer logic, counting mechanisms, and alarm control.
- **State Machine**: Defines behavior based on current mode (idle, counting, paused, alarm triggered).

### Key Resources Used
1. **Frequency Divider**: Converts FPGA's 100 MHz clock to 1 Hz.
2. **Counters**:
   - Seconds counter (modulo 60)
   - Minutes counter (modulo 100)
3. **Registers**: Stores alarm settings and allows resetting of values.
4. **Binary-to-BCD Converter**: Converts counter values for display.
5. **Button Debouncer**: Ensures stable input from physical buttons.

## User Manual
1. **Start the timer**: Press `START` to initialize the system.
2. **Set the alarm**: Use `SET_ALARM` and wait for the desired time to display.
3. **Start/Stop the timer**: Press `START/STOP` to begin countdown.
4. **Modify time**:
   - Press `M` to increment minutes.
   - Press `S` to increment seconds.
   - Press `START/STOP` after setting time to start countdown.
5. **Reset timer**: Hold `M` and `S` together.
6. **Alarm Activation**: Once time reaches 00:00, the LED blinks.

## Future Developments
- Adding millisecond precision.
- Supporting multiple independent timers.
- Saving timestamps for event tracking.

## References
- Nexys 4 FPGA Documentation
- VHDL-based timer design tutorials
- Seven-segment LED control guides

