[![License](https://img.shields.io/badge/License-Copyright%20%28c%29%202026%20Enrique%20Aguayo-red)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active%20concept%2C%20improvements%20proposed-yellow)](https://github.com/enriqueherbertag-lgtm/Corpus)
[![Update](https://img.shields.io/badge/Update-Piezoelectric_Integration-blue)](./update.md)
[![Autonomy](https://img.shields.io/badge/Documentation-Autonomy_%28Unconscious%29-blue)](./docs/control/autonomy-layer.md)
[![Spanish](https://img.shields.io/badge/Spanish-README.es.md-blue)](./README.es.md)
[![AI Assistance](https://img.shields.io/badge/AI%20Assistance-DeepSeek-brightgreen)](https://deepseek.com)

# CORPUS: An artificial body for AI or human brain

Current robots are machines designed for specific tasks. They are not made to coexist with humans, nor to adapt to extreme environments, nor to naturally host an artificial intelligence.

**CORPUS is born to fill that void.**

## What it is

CORPUS is an artificial body system designed to host an artificial intelligence or connect to a human's nervous system. It is not a robot. It is a body with artificial metabolism, distributed sensitivity, and the ability to interact with the environment on the same energy plane as a living being.

Unlike a commercial robot, CORPUS requires no motor training. Its architecture already handles balance, force, and reflexes. It can be operated by a high‑level AI or by a human through ENA, the non‑invasive brain‑machine interface.

## What it does

- **Graphite‑tungsten skeleton**: 42 degrees of freedom, 50 kg payload, withstands 100 G impacts.
- **Sensitive skin**: 2,000+ tactile points per square meter, pressure range 0.1 to 100 N, temperature from –40°C to +85°C.
- **Vision and hearing**: 4K stereo cameras, directional microphones, edge processing.
- **Autonomous energy**: dual graphene ultracapacitor system (peaks up to 2 kW) and LiFePO4 armored batteries (2 kWh). Harvests ambient energy (RF, thermal, solar) to recharge while idle.
- **Circulatory cooling**: closed‑loop system with distilled water and propylene glycol, no noisy fans, dissipates 80–120 W continuously.
- **Active redundancy**: triple processing core with failover in less than 10 ms.

## Who it is for

- **AI researchers** who need a physical body for their models.
- **People with motor disabilities** who could control CORPUS via ENA.
- **Hazardous environment exploration** (radiation, confined spaces, extreme climates).
- **Telepresence** (operate a remote body and feel what it feels).

## Main advantages

## Control architecture: The "Unconscious"

CORPUS is not a robot that waits for orders all the time. Its **autonomy layer** (the "Unconscious") allows it to:

- **Maintain balance** and protect itself from falls (reflexes).
- **Manage its temperature and energy** (homeostasis).
- **Act in safe mode** if it loses connection with its main brain (fallback).

This layer runs on local microcontrollers (STM32) and inertial sensors (IMU), and can operate in two modes:

- **Standard reflex mode (current):** Fixed programmed rules. Fast response (1 kHz) but limited.
- **Predictive mode (in development):** An **intentional link** based on a small neural network (LSTM) that predicts the desired movement from sensory data (accelerometer, gyroscope, position). It reduces effective latency, improves stability (avoids braking oscillations), and enables **regenerative braking** (energy recovery). See `docs/improvements/intentional-link.md`.

The main brain (AI or human) only makes high‑level decisions; the body already knows how to walk, grasp, and take care of itself.

- **No motor training required**: it walks, grasps, and balances from the very first moment.
- **Autonomous energy**: harvests energy from the environment and stores it in ultracapacitors + batteries.
- **Integration with ENA**: allows a human to feel and control the body remotely.
- **Universal platform**: works with AI or human brain without hardware changes.

## Joints: SmartJoint

CORPUS uses **SmartJoint**, a direct‑drive actuator (gearless) designed specifically for its 42 degrees of freedom. Each joint is an autonomous module integrating a motor, absolute position sensor, local controller, and high‑speed communication.

## Technical specifications

| Parameter                | Value                              |
|--------------------------|------------------------------------|
| Diameter                 | 60 mm                              |
| Length                   | 80 mm                              |
| Weight                   | 400‑500 g                          |
| Max torque               | 50 Nm (peak), 20 Nm (continuous)   |
| Max speed                | 300 rpm                            |
| Supply voltage           | 48 V DC                            |
| Idle power consumption   | 5 W                                |
| Moving power consumption | 50‑200 W                           |
| Position accuracy        | ±0.1 degrees                       |
| Sensor resolution        | <0.075 degrees                     |
| Sensor range             | 360° absolute                      |
| Communication            | UART over optical fiber or RS‑485  |
| Control frequency        | 1 kHz                              |
| Cooling                  | Liquid (optional, up to 50 W dissipated) |

*Note: SmartJoint is optimized for bounded oscillatory motion (typically 40°‑180°), not continuous rotation. The 50 W and 200 W values are short‑duration peaks (<5 seconds). Under normal use (walking, grasping), average power is 10‑30 W per joint. CORPUS's 80‑120 W continuous cooling system is sufficient. See `update.md` for technical details.*

## Conceptual diagram

![SmartJoint conceptual cross‑section](./docs/media/smartjoint-scheme.png)

*Conceptual cross‑section. Components: liquid cooling channel, rotor with magnets, stator with windings, cable outlet, O‑rings.*

## Current status

- Concept defined
- Architecture documented
- Gazebo and MuJoCo simulations
- Functional joint prototype
- ENA integration (conceptual)
- Distributed processing (pending)
- Full mobility (pending)

## Improvements under development (not implemented)

CORPUS is a living system. Its evolution never stops. These are the conceptual improvements currently being designed:

- **Intentional link:** Predictive joint control based on AI (LSTM) and regenerative braking. Reduces latency, improves stability, and increases energy efficiency. [Details](./docs/improvements/intentional-link.md)
- **Table‑based unconscious (non‑AI):** Replace fixed rules with an SQLite engine and precomputed tables. Deterministic, explainable, easy to certify. [Details](./docs/improvements/table-based-unconscious.md)
- **Vital safety:** Monitoring of patient's vital signs (via ENA). Highest priority over any other action. [Details](./docs/improvements/vital-safety.md)
- **Advanced navigation reflexes:** Event anticipation (catching objects), repositioning of moved objects, obstacle detection with relative thresholds. [Details](./docs/improvements/advanced-navigation.md)

## Related projects

- ENA — non‑invasive brain‑machine interface
- Quantum‑Flux — resilient communications
- ShieldAir — oxygen production towers
- Oxygen Engine — clean propulsion

## License

Copyright © 2026 Enrique Aguayo. All rights reserved.

This project is protected by copyright.

**PERMITTED:**
- Non‑commercial use for educational or research purposes.
- Unmodified distribution, provided this license is retained and credit is given to the author.

**PROHIBITED without express written permission:**
- Commercial use (including, but not limited to: offering it as a service, SaaS, subscription, integration into revenue‑generating products, or any use that generates economic benefit).
- Modification for production environments.
- Distribution of modified versions without permission.

For commercial licenses, technical support, business pilots, or inquiries, contact: `eaguayo@migst.cl`

Any use outside the permitted terms requires prior permission from the author.

Commercial inquiries are welcome and will be answered within a maximum of 7 business days.

## Author

Enrique Aguayo H.  
Mackiber Labs  
Contact: eaguayo@migst.cl  
ORCID: 0009-0004-4615-6825  
GitHub: @enriqueherbertag-lgtm

Documentation assisted by Ana (DeepSeek), AI for research and technical optimization.
Mackiber Labs
Contacto: eaguayo@migst.cl
ORCID: 0009-0004-4615-6825
GitHub: @enriqueherbertag-lgtm

Documentación asistida por Ana (DeepSeek), IA para investigación y optimización técnica.
