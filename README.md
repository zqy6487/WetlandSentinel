# WetlandSentinel

## An Ellipsoidal Amphibious Robot for Wetland Ecological Monitoring

**Qiyun Zheng**  
Shanghai Foreign Language School Affiliated to SISU, Shanghai, China

[**Read the paper online**](https://zqy6487.github.io/WetlandSentinel/) · [**Download the PDF**](https://zqy6487.github.io/WetlandSentinel/WetlandSentinel_Qiyun_Zheng.pdf)

WetlandSentinel is a remotely operated amphibious robot designed to support wetland observation across shallow water and terrestrial terrain. It combines an ellipsoidal body, an internally driven rotating shell, movable-mass steering, LoRa communication, and modular water-quality and vision sensing.

This repository shares the research paper and a summary of the prototype and its evaluation.

## System Overview

- **Amphibious mobility:** an internal DC motor drives the outer shell through a three-stage gear transmission. Shell rotation enables rolling on land and drives peripheral blades in water.
- **Movable-mass steering:** a stepper-driven sliding counterweight shifts the center of mass to produce a roll bias for directional control.
- **Attitude control:** Kalman-based attitude estimation and fuzzy gain-scheduled PID regulate pitch and roll, with an inner PI motor-speed loop.
- **Water-quality sensing:** modular pH and turbidity probes measure local water conditions; pH processing rejects the minimum and maximum from a 40-sample buffer before averaging.
- **Onboard vision:** a K210 module performs local visual inference through a protected camera interface.
- **Remote operation:** ESP32 controllers and SX1278 LoRa transceivers connect the robot to a handheld terminal for commands and sensor feedback.

## Reported Evaluation

| Test | Result | Evaluation conditions |
| --- | --- | --- |
| pH sensing | Mean absolute error: **0.025 pH**; maximum absolute error: **0.05 pH** | Separate cup-based bench test; 54 readings across pH 4.00, 7.00, and 10.00 standards |
| Turbidity sensing | Maximum relative deviation: **1.00%** | Separate cup-based bench test; 54 readings across 5, 30, and 80 NTU standards |
| Obstacle traversal | Maximum normalized lateral deviation: **2.6%**, equivalent to **7.8 cm** over a 3 m path | Controlled tank trials with no obstacle, 5 cm stones, and synthetic vegetation; five trials per condition |
| LoRa remote control | Maintained at approximately **600 m** separation | Open-area, line-of-sight field test |
| Enclosure sealing | **No visible internal water ingress** after 3 h; electronics remained operational | Separate enclosure test at approximately 15 cm working water depth |

All reported obstacle-traversal trials reached the endpoint without recorded entrapment. The 10 mm blade configuration was selected based on the lateral-displacement comparison described in the paper.

### Evaluation Scope

The quantitative results describe the stated bench, tank, and field-test conditions. Water-quality bench validation was conducted separately from locomotion. Vision evidence comes from controlled image-display tests. A separate wetland field trial provided qualitative evidence of in situ sensing feasibility.

Future work includes broader field evaluation, LoRa packet-delivery and signal-strength characterization, GPS-tagged water-quality mapping, and independent labeled evaluation of vision performance.

## Prototype Hardware

| Component | Configuration |
| --- | --- |
| Body dimensions | 420 × 420 × 640 mm |
| Mass | Approximately 13 kg |
| Shell drive | MG540 DC geared motor; three-stage transmission with nominal output/input speed ratio of 1:10 |
| Steering | 35 mm stepper motor, rack, and linear guide |
| Attitude sensing | MPU6050 IMU |
| Water-quality probes | SEN0161 pH sensor and TS-300B turbidity sensor |
| Vision | Sentry2 K210 module |
| Controllers and communication | ESP32 and SX1278 LoRa |

## Repository Contents

- [`WetlandSentinel_Qiyun_Zheng.pdf`](WetlandSentinel_Qiyun_Zheng.pdf): the research paper.
- `README.md`: project overview and reported evaluation.

Firmware, CAD files, and experimental datasets are not currently included in this repository.

## Citation

If you refer to this work, please cite:

> Qiyun Zheng. *WetlandSentinel: An Ellipsoidal Amphibious Robot for Wetland Ecological Monitoring.*

[Paper PDF](WetlandSentinel_Qiyun_Zheng.pdf) · [Author's GitHub profile](https://github.com/zqy6487)

