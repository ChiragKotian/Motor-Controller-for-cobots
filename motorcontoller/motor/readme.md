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
_Control Hz required : (40)880.67Hz-(48)1056.8Hz-(60)1321Hz_**Don't consider**

Time Constant       : 7.85*10^-4 (Inductance/Resistance) -> 5times -> 0.003925
Resultant Freq      : 254.7Hz <-Large ripple

High PWM frequencies for non audible operation 20kHz and also high freq less ripple

For high efficiency always keep pwm far from 50% duty cycle

PWM higher than 50kHz and above 80kHz for motors with very small electrical time constant.

Increase inductance, reduces ripple, inductance varies depending on PWM freq. 


https://www.portescap.com/en/newsroom/whitepapers/2021/10/understanding-the-effect-of-pwm-when-controlling-a-brushless-dc-motor

**Use a PWM frequency as high as possible considering driver circuit limitations and switching losses** as ripple will be minimum


Determining the PWM (Pulse Width Modulation) frequency for a brushless motor involves considering several factors including motor characteristics, drive circuitry, and control requirements. While there isn't a single mathematical formula that universally determines the PWM frequency for all brushless motors, there are guidelines and considerations to help determine an appropriate PWM frequency.

Here are some general guidelines and factors to consider:

1. **Motor Characteristics**: The PWM frequency should be high enough to ensure smooth motor operation and minimize audible noise, especially at low speeds. However, it should not be excessively high to avoid increasing switching losses in the motor driver circuitry.

2. **Switching Losses**: Higher PWM frequencies result in increased switching losses in the motor drive circuitry, which can reduce overall efficiency and increase heat generation. Therefore, the PWM frequency should strike a balance between minimizing switching losses and ensuring smooth motor operation.

3. **Control System Requirements**: The PWM frequency should be compatible with the control system's sampling rate and response time requirements. Choosing a PWM frequency that aligns with the control system's dynamics can help optimize motor performance and response.

4. **Drive Circuitry**: The drive circuitry, including the motor driver ICs and power transistors, may have recommended or maximum PWM frequency specifications. It's important to ensure that the selected PWM frequency is within the limits specified by the drive circuitry to prevent damage and ensure reliable operation.

5. **Noise Considerations**: PWM frequency can affect electromagnetic interference (EMI) and audible noise produced by the motor and drive electronics. Selecting a PWM frequency that minimizes EMI and audible noise interference is important, especially in applications where electromagnetic compatibility (EMC) is critical.

6. **Application Requirements**: Consider the specific requirements and constraints of the application, such as speed range, torque control, and dynamic response. The PWM frequency should be selected to meet the performance and efficiency requirements of the application.

As for a mathematical formula, there isn't a single formula to determine the PWM frequency for all brushless motors due to the variability in motor characteristics and application requirements. Instead, the PWM frequency is typically determined through experimentation, simulation, or reference to motor driver datasheets and application notes.

Datasheets for motor drivers and control ICs often provide recommendations and guidelines for selecting an appropriate PWM frequency based on the specific characteristics of the motor and drive circuitry.

To determine the PWM frequency, you may consider starting with a moderate frequency (e.g., a few kHz) and then adjusting it based on performance, efficiency, and noise considerations specific to your application and motor system.

Therefore, while I can't provide a specific mathematical formula, the determination of the PWM frequency involves a consideration of various factors and may require iterative experimentation and optimization based on the specific requirements and constraints of your application.

Certainly! While there isn't a universally applicable formula for determining the PWM frequency of brushless motors, there are some approximate guidelines you can use to determine a starting point for your PWM frequency selection:

1. **Switching Losses and Efficiency**: 
   - As a general guideline, PWM frequencies in the range of a few kHz to tens of kHz are commonly used for brushless motor control applications.
   - Higher frequencies typically result in lower switching losses but may increase electromagnetic interference (EMI) and audible noise.
   - Lower frequencies reduce EMI and audible noise but may increase switching losses and reduce efficiency.

2. **Electromagnetic Interference (EMI)**:
   - For applications sensitive to EMI, consider starting with PWM frequencies in the lower range (e.g., 10 kHz or lower) and adjust as necessary to minimize EMI interference.

3. **Audible Noise**:
   - Audible noise from motor and drive electronics can be minimized by selecting PWM frequencies above the audible range (20 kHz and higher).

4. **Drive Circuitry Recommendations**:
   - Check the datasheets and application notes provided by the motor driver and control IC manufacturers for recommended PWM frequency ranges.
   - Some motor driver ICs may have maximum or recommended PWM frequency specifications that you should adhere to.

5. **Motor Dynamics**:
   - Consider the speed range and dynamic response requirements of your application.
   - Higher PWM frequencies can provide better dynamic response and smoother operation, especially at lower speeds.

6. **Thermal Considerations**:
   - Consider the thermal characteristics of your motor and drive circuitry.
   - Higher PWM frequencies may result in increased heat generation in the drive circuitry, so ensure that the components can handle the thermal load.

Based on these considerations, you can start with a PWM frequency in the range of a few kHz to tens of kHz and then adjust based on performance, efficiency, and noise considerations specific to your application.

For example, a starting point could be a PWM frequency of 10 kHz, and then you can adjust it higher or lower based on your specific requirements and constraints.

Remember that the optimal PWM frequency may vary depending on your application and system requirements, so it's essential to experiment and evaluate the performance of different PWM frequencies to find the most suitable one for your application.

