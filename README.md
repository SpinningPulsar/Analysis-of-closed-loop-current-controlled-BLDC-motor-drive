# Analysis-of-closed-loop-current-controlled-BLDC-motor-drive
 This project aims to create a controllable BLDC motor system that can maintain a desired speed  using closed-loop feedback while providing an  UART for user interaction.
**Project Title: Block Commutation BLDC Drive with Closed-Loop Control and UART CLI**
![WhatsApp Image 2023-08-05 at 20 46 06](https://github.com/SpinningPulsar/Analysis-of-closed-loop-current-controlled-BLDC-motor-drive/assets/17098604/3043b11b-66c7-474f-b0f0-ebb5d5228b85)


**Introduction:**

This GitHub documentation of the project presents a comprehensive implementation of a Block Commutation Brushless DC (BLDC) motor drive with closed-loop control and a Universal Asynchronous Receiver/Transmitter (UART) Command-Line Interface (CLI). The project explores the integration of various components, advanced control strategies, and signal processing techniques to achieve precise motor control and user-friendly interaction. 
This write up is a collection of notes and steps we followed to understand and learn about the BLDC Motor Drive system.

**1. BLDC Motor Control:**
The project revolves around controlling a Brushless DC (BLDC) motor. Unlike traditional brushed DC motors, BLDC motors don't have mechanical commutators and brushes. Instead, they rely on electronic commutation and permanent magnets for operation. This design offers several advantages, including higher efficiency, reduced maintenance, and longer lifespan.

**2. Block Commutation:**
The heart of the project lies in the block commutation technique. To rotate the BLDC motor's rotor, the stator windings need to be energized in a specific sequence. This sequence, known as block commutation, involves energizing the motor's three phases in a predetermined pattern. By controlling the commutation sequence, the motor can be driven forward or backward at different speeds.

**3. Closed-Loop Control:**
A key aspect of the project is achieving precise speed or position control using closed-loop feedback. Closed-loop control relies on feedback from Hall Effect sensors embedded within the motor to detect the rotor's position. The microcontroller continuously reads the Hall Effect sensor outputs and adjusts the commutation sequence accordingly. This feedback mechanism ensures that the motor's speed or position closely matches the desired setpoint, leading to accurate and stable control.

**4. PID Control Algorithm:**
To accomplish closed-loop control, the project implements a PID (Proportional-Integral-Derivative) control algorithm. The PID controller calculates an error signal based on the difference between the desired setpoint and the actual motor position. It then adjusts the motor's control signal (PWM) using three components: proportional (P), integral (I), and derivative (D) gains. The PID algorithm fine-tunes the motor control to achieve the setpoint with minimal error and overshoot.

**5. UART CLI Interface:**
To interact with the BLDC motor system, the project incorporates a UART Command-Line Interface (CLI). Through this interface, users can send commands and receive feedback from the microcontroller. By connecting an external device, such as a computer or smartphone, to the microcontroller's UART interface, users can control various aspects of the BLDC motor system conveniently.

**6. Signal Processing and Data Handling:**
The project involves signal processing techniques to ensure accurate and reliable feedback from the Hall Effect sensors. Signal filtering minimizes noise in the sensor readings, while interpolation algorithms improve the resolution of the rotor position information. Data fusion combines data from multiple sensors, enhancing the robustness of the control system.

**7. Power Electronics:**
Power electronics play a crucial role in driving the BLDC motor efficiently. The motor driver circuit, typically an H-bridge or specialized BLDC driver IC, controls the power delivered to the motor phases using PWM signals from the microcontroller. Additionally, the project may include current sensing to monitor the motor's current and protect it from overcurrent and stall conditions.

**8. Analog Circuitry:**
Analog circuitry is involved in voltage regulation to ensure a stable and clean power supply for the microcontroller and motor driver. Sensor signal conditioning circuits may be implemented to adapt the analog sensor outputs for the microcontroller's ADC. If necessary, comparator circuits convert analog Hall Effect sensor outputs into digital signals for further processing.

**9. Final steps!!**
Once all the individual components are designed and implemented, they are integrated onto a PCB or prototyping board. We designed a PCB using KiCAD- the process is fairly simple, upload the schematic, manually connect the wires, and test if the components can be fit, Thankfully, the Schematic isn’t too big and thus, it can be easily and effectively converted into a PCB.

In summary, the project results in a fully functional BLDC motor drive with precise closed-loop control using a PID algorithm. The system can be interacted with through a user-friendly UART CLI interface, making it versatile and accessible to the end user. 
![WhatsApp Image 2023-08-05 at 20 46 20](https://github.com/SpinningPulsar/Analysis-of-closed-loop-current-controlled-BLDC-motor-drive/assets/17098604/771d751e-1e67-4c09-9263-bcdb8d28b9c9)

**Components:**

1. **BLDC Motor:**
   - We used a low-voltage, low-power BLDC motor (12v) that forms the core of the project. Its specifications influence the entire design, from motor driver selection to power supply. 

2. **Microcontroller (MCU):**
   - The chosen MCU boasts PWM, ADC, and UART capabilities, serving as the project's control hub. The MCU's clock frequency and memory constraints influence software implementation decisions. We used a STM Board

3. **Motor Driver:**
   - The motor driver circuit, realized using the L298N H-bridge driver IC, provides power amplification and PWM-driven control of the BLDC motor's phases.

4. **Hall Effect Sensors:**
   - Embedded within the motor, these sensors play a pivotal role in providing rotor position feedback. The timing of commutation sequences is determined based on their outputs.

5. **Voltage Regulator:**
   - A voltage regulator circuit ensures a stable supply voltage for the MCU and motor driver, minimizing the risk of operational issues caused by voltage fluctuations.

6. **Comparator Circuit:**
   - In cases where Hall Effect sensors provide analog signals, a comparator circuit with a predefined threshold converts these analog signals into digital form, ready for processing by the MCU.

7. **Serial Communication Cable:**
   - A USB-to-UART cable establishes a reliable connection between the MCU's UART interface and external devices, enabling communication through the UART CLI.

8. **External Device (e.g., Computer):**
   - An external device equipped with a UART terminal interface, such as a computer or smartphone, serves as the means to interact with the BLDC motor drive. We used our laptop as the external device to control the speed.

**Technical Details:**

- **Motor Control and Commutation:**
   The project initiates with manual motor control and open-loop commutation. Block commutation techniques are learned and implemented. This understanding paves the way for closed-loop control, where the real-time feedback from Hall Effect sensors ensures accurate and dynamic control of the motor's speed or position.

- **PID Control:**
   Closed-loop control hinges on the implementation of a PID control algorithm. The MCU calculates the error between the desired setpoint and the actual rotor position, then adjusts the commutation sequence using proportional, integral, and derivative terms. Tuning these terms optimizes control performance.

- **UART CLI Interface:**
   The UART CLI interface acts as a bridge between the user and the motor drive system. By sending text-based commands via UART, users can set desired speeds, change directions, enable or disable the motor, and query the motor's status. Feedback from the MCU provides confirmation of command execution.

- **Signal Processing:**
   Signal processing techniques, including filtering, interpolation, and data fusion, enhance the reliability and accuracy of the Hall Effect sensor feedback. Filtering minimizes noise, interpolation enhances position resolution, and data fusion mitigates errors from individual sensors.

- **Power Electronics and Analog Circuitry:**
   The motor driver circuit, based on the L298N H-bridge driver IC, converts PWM signals from the MCU into precise phase current control. Voltage regulation ensures a consistent power supply. Additional analog circuitry, such as comparator circuits for analog sensor conversion and current sensing circuits for motor protection, contributes to the system's robustness.

**Conclusion:**

This project encapsulates a comprehensive journey through the design, implementation, and optimization of a Block Commutation BLDC Drive with Closed-Loop Control and UART CLI. By exploring components, control algorithms, signal processing, and analog circuitry, the project equips enthusiasts and learners with practical insights into electrical engineering, embedded systems, and motor control principles. 
We had a blast building this and have learned a lot on Analog Electronics, Electric Motors, Power Electronics, Signal Processing (and finally putting those Bode plots to an actual real life use!)
