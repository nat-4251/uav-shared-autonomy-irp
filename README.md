# Adaptive Shared-Control Framework for Low-Cost Fixed-Wing UAVs
Investigating adaptive shared-control systems for low-cost fixed-wing UAVs using telemetry-derived pilot instability metrics.

# Problem statement / Motivation for this project
Beginners in RC flight commonly experience struggles include overcorrection, perceiving orientation of the aircraft and a low budget. These issues may make the learning curve into piloting RC planes too steep or costly for some.

While previous solutions such as internal gyroscopes exist to counter this exact problem, stabilisation systems may reduce skill transfer to manual flight in some cases. Similarly, while flight simulators do exist, may not fully capture real-world wind disturbances as they lack real-world complexities such as changing wind speeds or lacking real-world locations. 

Hence, this project sets out to develop an AI-driven software that adapts along with the pilot as they learn, in other words, a system which compensates for their skill level. This aims to decrease the steepness of the learning curve while simultaneously not allowing pilots to be over-reliant on an existing system (such as a gyroscope). This software aims to reduce the amount of crashes a amateur pilot goes through, making the process of upskilling less energy and monetarily expensive.

# Research question
How effectively can pilot instability be inferred from low-cost fixed-wing UAV telemetry and used to implement adaptive shared-control that improves flight stability while preserving pilot intent in novice-operated flights?

# Overview
This project investigates adaptive authority-sharing between human pilots and AI-assisted stabilization systems in low-cost fixed-wing UAV platforms.
The system aims to infer pilot instability using onboard telemetry and dynamically regulate control authority while preserving pilot intent.
The software aims to simplify training in new fixed-wing RC plane pilots by sharing pilot's control with an AI algorithm.

# Systems overview
A short explanation of the system's architecture: 
Pilot → AI Authority Layer → INAV Flight Controller → Aircraft

The pilot of a certain skill level will be providing the raw control commands from the ground. The AI Authority Layer estimates a continuous pilot instability score (PIS) derived from telemetry features such as control input variance, angular velocity oscillation, and deviation from stable flight states. This score is used to scale control authority rather than replace pilot intent. These factors will be used by the AI to generate a refined output which would be transmitted to the INAV flight controller which will then implement the output. However, the AI can only reduce how aggressively the plane responds, but must NOT change where the pilot wants to go.

In summary, the AI cannot generate flight commands independently, rather, it takes the pilot's input and scales and filters it instead.

# Hardware stack
- INAV flight controller (Matek F405v2 wing controller)
- 2217 950kV motor equipped with a 8x4 propeller
- 3S 950mAh LiPo battery
- Foam RC Plane airframe
- 4x 9g micro servos
- 30A ESC (5V@3A BEC)
- Radiomaster pocket transmitter and receiver (ELRS)
- (Raspberry Pi) - to be determined

To comply with Singapore government restrictions on UAV:
- B-RID module

# Software stack
- INAV software and logs
- Python (main programming language)
- scikit-learn (machine learning)
- numpy (math)

# Evaluation metrics
**Primary metrics:**
- Crash rate reduction
- Flight time
- Roll variance reduction (%)
- Oscillation frequency reduction
  
**Secondary metrics:**
- Pilot workload (qualitative survey)


# Methodology
This project is split into 5 parts, namely:
Part A: Aircraft construction and baseline flight testing
Part B: Integrate INAV flight stabilisation
Part C: Telemetry data collection under varied pilot inputs,
Part D: Training of pilot instability model,
Part E: Data collection on platform with model installed,
Part F: Comparative analysis using stability metrics.


# Current state 
**Overall phase: Part A - Aircraft construction and baseline flight testing**

**1. Airframe status**
- Foam fixed-wing airframe complete
- Carbon fibre rods installed as spars for rigidity
- Control surfaces tested on the ground
- Center of gravity not yet tested in flight

**2. Software status**
- Matek F405-Wing V2 not yet installed / awaiting integration
- Motor system pending installation
- ESC and servos prepared but not flight-tested
- Radio system configured (ELRS bound confirmed / pending)

**3. Software Status**
- GitHub repository created
- INAV firmware not yet configured
- logging pipeline not implemented
- ML pipeline not started
- Feature definitions drafted

**4. Data Status**
- No flight telemetry collected yet
- No labelled dataset exists
- Data schema defined but not populated


# Log of the project:

**(2026-05-04 to 2026-05-19)**
- Initiated construction of a low-cost fixed-wing UAV platform intended for telemetry-based shared-control experiments.
- Completed fabrication of foam airframe, including installation of control surfaces and structural reinforcement.
- Installed propulsion system consisting of RS2205 2300KV motor with matching propeller selection for initial flight testing baseline.
- Integrated servos and basic mechanical control linkages for aileron, elevator, and rudder actuation.
- Added carbon fibre reinforcement rods to wing structure to enforce dihedral angle stability and improve passive roll stability characteristics.
- Installed additional reinforcement in the tail section to improve longitudinal stability during unpowered glide phases.
- Procured and integrated power system components including a 3S 950mAh LiPo battery and charging system (B6neo+ charger).
- Established electrical interfacing using XT30–XT60 conversion to ensure compatibility between power distribution and ESC input.
  
**(2026-05-16 to 2026-05-17)**
- Conducted component selection for propulsion system optimization, including motor and propeller matching for expected airframe weight class and flight envelope.
- Reviewed regulatory requirements for UAV operation in Singapore, including B-RID compliance and registration constraints relevant to outdoor flight testing.

**(2026-05-18)**
- Received and integrated transmitter system (RadioMaster Pocket).
- Completed receiver binding and control surface mapping.
- Performed initial trim adjustments to achieve stable neutral flight control response.
- Verified basic end-to-end control loop: transmitter → receiver → servo actuation.
  
**(2026-05-19)**
- Conducted control surface calibration and refined mechanical linkages for consistent deflection response.
- Performed preliminary tuning of control responsiveness to reduce asymmetry in flight response.
- Began structured documentation of project cost breakdown and system components for traceability and research reporting.
- Iteratively refined airframe appearance (non-functional modifications) without altering aerodynamic structure.

**(2026-05-21)**
- Established formal research framework for adaptive shared-control UAV system.
- Defined core research question focusing on telemetry-derived pilot instability estimation and adaptive control authority scaling.
- Structured system architecture consisting of pilot input layer, AI-based instability estimation layer, and INAV flight control execution layer.
- Formalised Pilot Instability Score (PIS) concept as a continuous variable derived from telemetry features such as control input variance and angular oscillation behaviour.
- Defined evaluation metrics including crash rate reduction, roll variance reduction, and oscillation frequency reduction.
- Organised project into phased methodology covering airframe construction, flight testing, telemetry collection, model training, and comparative evaluation.
