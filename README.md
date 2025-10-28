---

# Delta Robot Simulation in MATLAB/Simulink

This project develops the **kinematic and dynamic modeling** of a **Delta-type parallel robot**, implemented in **MATLAB/Simulink**. It includes a PD controller with gravity compensation and a visual simulation of the CAD model exported from SolidWorks.

A more detailed discussion of the robot’s kinematic and dynamic analysis can be found in the accompanying **report.pdf** file.

---

## Overview

The Delta robot is a parallel manipulator with three closed kinematic chains that enable fast and precise motion of the end-effector.
This work addresses:

* **Forward and inverse kinematic modeling**
* **Dynamic modeling** using the **Euler-Lagrange** formulation
* **PD control implementation**
* **Full simulation in Simulink**
* **Integrated CAD visualization** of the robot

---

## Project Components

1. **Kinematic Modeling:**
   The position equations for the three arms were derived using vector analysis.

2. **Dynamic Modeling:**
   Based on the Euler-Lagrange equations, the required torques for each actuator were obtained.

3. **PD Control with Gravity Compensation:**
   Tuned with:

   ```matlab
   Kp = 323.6
   Kv = 2 * sqrt(Kp)
   ```

4. **Simulink Simulation:**
   The main diagram includes the following blocks:

   * `qd`: Trajectory generator
   * `Inverse Kinematics`
   * `PD Control`
   * `Dynamic Plant`
   * `Delta Robot CAD Model`

---

## Robot Parameters

| Parameter          | Symbol | Value        |
| ------------------ | ------ | ------------ |
| Fixed base length  | sp     | 200 mm       |
| Moving base length | sb     | 576 mm       |
| Arm length         | L      | 270 mm       |
| Forearm length     | l      | 690 mm       |
| Arm mass           | ma     | 0.290 kg     |
| Forearm mass       | mb     | 0.280 kg     |
| Motor inertia      | Im     | 3.8e-6 kg·m² |

---

## Test Trajectory

The end-effector follows an **epicycloid**-type trajectory, defined by:

```matlab
x(t) = -(R - r)*cos(t) + r*cos((R - r)/r * t)
y(t) =  (R - r)*sin(t) - r*sin((R - r)/r * t)
```

With:

```
R = 0.25
r = 0.20
```

---

## Results

The PD controller achieves a tracking error between **-0.2 and 0.1**, indicating stable and precise system performance.

---

## Screenshots

![Simulink Diagram](https://github.com/user-attachments/assets/d77ba514-0a82-44c0-9e8a-6b062497a93f)
*Main Simulink diagram.*

![Trajectory](https://github.com/user-attachments/assets/d2cb34ff-b8c9-4c68-a940-472ad529c82b)
*Desired end-effector trajectory.*

![CAD Model](https://github.com/user-attachments/assets/bf9889e6-be89-4df7-a88f-987926fd284a)
*Delta robot model exported from SolidWorks.*

---

## How to Run

1. Open the `.slx` file in MATLAB.
2. Make sure the paths to all blocks and functions are correct.
3. Run the simulation and observe the results in the scopes.
4. (Optional) Modify the trajectory in the `qd` block.

---

## Conclusions

The project demonstrates the importance of **accurate kinematic modeling** and respecting the **workspace** of the Delta robot to ensure stable simulations.
The model can serve as a foundation for developing advanced controllers or trajectory planning methods.

---

## Author

**Oscar León Rodríguez**
Faculty of Electronic Sciences
Academic project: Delta Robot Simulation in MATLAB.

---
