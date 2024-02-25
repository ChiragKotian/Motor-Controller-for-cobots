Motor specs:

In a brushless motor, the parameters you listed play crucial roles in determining its performance, characteristics, and behavior. Here's a brief explanation of each parameter and how they impact the motor:

1. **Poles**: Poles refer to the number of magnetic poles in the motor. The number of poles affects the motor's speed-torque characteristics and its maximum speed.

2. **V/Hz**: This parameter refers to the voltage-to-frequency ratio and is related to the motor's control method, particularly in variable frequency drives (VFDs). It determines the ratio at which voltage and frequency should be adjusted to control the motor's speed and torque effectively.

3. **Resistance (ohm)**: Resistance represents the opposition to the flow of current in the motor windings. Higher resistance leads to more heat generation and power loss but can provide better control over the motor's behavior.

4. **Kv (rpm/V)**: Kv, or the motor velocity constant, represents the motor's speed constant. It indicates how many revolutions per minute (rpm) the motor will turn for each volt applied to it. Kv is an essential parameter for understanding the motor's speed-torque relationship.

5. **Inductance (uH)**: Inductance represents the motor winding's ability to store energy in the form of a magnetic field. It impacts the motor's electrical time constants, affecting its response to changes in current and speed.

6. **Torque constant (Nm/A)**: The torque constant relates the motor's torque output to the current flowing through its windings. It determines how much torque the motor will produce for a given amount of current.

7. **Rated current (A)**: Rated current is the maximum continuous current that the motor windings can handle without causing overheating or damaging the motor.

8. **Rated voltage (V)**: Rated voltage is the nominal voltage at which the motor is designed to operate efficiently.

9. **Rated power (W)**: Rated power is the maximum continuous mechanical power output of the motor under normal operating conditions.

10. **Rated speed (rpm)**: Rated speed is the maximum speed at which the motor can operate continuously without exceeding its design limitations.

11. **Desired torque (Nm)**: Desired torque is the torque level that the motor needs to produce to meet the requirements of a specific application.

12. **Operating current (A)**: Operating current is the actual current flowing through the motor during operation, which can vary based on the load and operating conditions.

13. **Operating speed (rpm)**: Operating speed is the actual speed at which the motor operates under given conditions.

14. **Operating power (W)**: Operating power is the mechanical power output of the motor under specific operating conditions.

15. **Coil reactance (ohm)**: Coil reactance represents the opposition to changes in current flow due to the magnetic field stored in the motor windings. It is related to the inductance and frequency of the motor's operation.

These parameters collectively define the performance, efficiency, and behavior of a brushless motor in various applications. Understanding and properly configuring these parameters are essential for optimizing motor performance and ensuring reliable operation.




Given specs:

Parameter	          :  Model
Motor	              :  Turnigy Aerodrive SK3 -4240-740kv
Poles	              :  14
V/Hz	              :  0.045420136
Resistance (ohm)	  :  0.0151
Kv (rpm/V)	          :  660.5
Inductance (uH)	      :  11.85833333
Torque constant (Nm/A):	 0.011276989
Rated current (A)	  :  50
Rated voltage (V)	  :  19
Rated power (W)	      :  870
Rated speed (rpm)	  :  12549.5
Desired torque (Nm)	  :  0.3
Operating current  (A):	 26.60284548
Operating speed (rpm) :	 3000
Operating power (W)	  :  94.24777961
Coil reactance (ohm)  :	 0.003725405

What we want:

Motor RPM: 0-3000RPM
Gearbox  : 100:1
Torque   : 30Nm
Input    : 48-60V min.40V
Min. size and weight of power cables internal to the cobot

Calculations and imp params:

Output RPM          : 0-30RPM (Motor RPM/Gearbox)
Motor Torque        : 0.3Nm (Torque/Gearbox)
Current required    : 26.603A (Motor Torque/Torque constant)
Operating power(W)	: 94.24777961
Control Hz required : (40)880.67Hz-(48)1056.8Hz-(60)1321Hz

Time Constant       : 7.85*10^-4 (Inductance/Resistance) -> 5times -> 0.003925
Resultant Freq      : 254.7Hz

High PWM frequencies for non audible operation 20kHz and also high freq less ripple


https://www.portescap.com/en/newsroom/whitepapers/2021/10/understanding-the-effect-of-pwm-when-controlling-a-brushless-dc-motor

