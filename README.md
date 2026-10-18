# OmniEdge-3588: Rugged Edge AI & Teleoperation Box for ROVs, UGVs & Heavy Machinery

[![SoC](https://img.shields.io/badge/SoC-Rockchip_RK3588-blue.svg)]()
[![NPU](https://img.shields.io/badge/Edge_AI-6_TOPS_INT8-green.svg)]()
[![Boot](https://img.shields.io/badge/Cold_Boot-2.3_Seconds-orange.svg)]()
[![Video](https://img.shields.io/badge/Video-8--Ch_1080P_AHD-red.svg)]()

**OmniEdge-3588** is an industrial-grade Embedded Linux & Edge AI hardware stack designed specifically for **unmanned ground vehicles (UGVs), underwater ROVs, agricultural machinery, and heavy equipment retrofitting**. 

We built this platform after getting frustrated with **NVIDIA Jetson Orin Nano's** missing hardware video encoder (NVENC), 40-second slow Ubuntu boot times, fragile MIPI ribbon cables, and filesystem corruption upon sudden battery disconnect.

---

## 🔥 Why OmniEdge-3588 vs. Standard SBCs / Jetson?

| Feature | NVIDIA Jetson Orin Nano | Standard Raspberry Pi 5 | **OmniEdge-3588 Stack** |
| :--- | :--- | :--- | :--- |
| **Hardware Video Encoding** | ❌ None (CPU Software Encode) | ⚠️ Limited (1080p60 max) | ✅ **8-Ch 1080P H.264/H.265 VPU (<12% CPU)** |
| **Camera Cabling** | ❌ Fragile 15cm MIPI / USB | ❌ Fragile MIPI / USB | ✅ **8x Waterproof Coax AHD (Up to 30m, EMI-Immune)** |
| **Cold Boot to Live Video** | ❌ ~40s (Standard JetPack) | ⚠️ ~15-25s | ✅ **2.3s Ultra-Fast Custom Linux BSP** |
| **Sudden Power-Cut Safety** | ❌ Corrupts MP4 & RootFS | ❌ Corrupts SD Card | ✅ **Power-Loss Safe Recording & Read-Only RootFS** |
| **Native Industrial I/O** | ❌ Requires external adapters | ❌ Requires HATs | ✅ **Onboard CAN-Bus, RS485, Dual GbE, M.2 NVMe, 4G/GPS** |

---

## 🎬 Live Benchmarks & Demos *(Uploading Soon)*

* **[WIP - Benchmark 1] 2.3s Instant Cold Boot:** Power-on directly to 4/8-channel live view + Qt/LVGL instrument cluster.
* **[WIP - Benchmark 2] 4-Ch 1080P H.265 + YOLOv8 NPU Inference:** Simultaneous multi-camera AI obstacle detection (6 TOPS NPU) + hardware RGA OSD overlay + NVMe logging at **<15% total CPU load**.
* **[WIP - Benchmark 3] <75ms Glass-to-Glass Teleoperation:** Ultra-low latency RTSP/WebRTC streaming paired with real-time CAN-Bus (J1939/CANopen) actuation.

---

## 🛠️ Hardware Architecture & I/O Specifications

Built around a rock-solid **Rockchip RK3588** core (Quad Cortex-A76 + Quad Cortex-A55, 6 TOPS NPU), our Gen-1 Carrier Board integrates everything required for harsh field deployments:

* **Vision Inputs:** 2x `AHDX4` headers supporting up to **8x 1080P@30fps AHD cameras** (via dual onboard AHD-to-MIPI bridge ICs). Long-distance, waterproof, and immune to motor EMI.
* ** Dual Gigabit Ethernet:** 
  * `ETH0 (RGMII)` + `ETH1 (PCIe)` — Ideal for isolating high-bandwidth **3D LiDAR / Depth Cameras** from the main vehicle radio/telemetry network.
* **Vehicle & Robotics Control:**
  * `CAN 0` & `RS485` interfaces for direct connection to motor drivers, hydraulic valves, and vehicle ECUs.
  * 2x UART (`UART7`, `UART8`) + 24x GPIO (`3x GPIOX8` headers) for ultrasonic sensors, relays, and emergency stops.
* **High-Speed Edge Storage & Connectivity:**
  * `M.2 NVMe PCIe SSD` slot for high-bitrate multi-camera dataset logging (Blackbox mode).
  * Mini-PCIe `4G/5G Cellular` slot + onboard `GPS Antenna` interface + Dual-band Wi-Fi/BT for remote fleet teleoperation.
* **Display Outputs:** Native `MIPI-DSI` (paired with our 8-inch 1200x1920 high-brightness touch display), `HDMI Out`, `LVDS`, and `eDP`.

---

## 🤝 Work With Us (DevKits & Custom Engineering)

We are an embedded full-stack engineering studio (Hardware PCB + MCU + Linux BSP + Edge AI). Whether you are building a prototype or scaling to production, we can accelerate your hardware roadmap:

1. **Order a Gen-1 Engineering DevKit:** Get the complete turnkey kit (RK3588 mainboard + 4x waterproof 1080P AHD cameras + 8" touch display + pre-flashed fast-boot AI SDK) to test on your robot or vehicle immediately.
2. **Custom Carrier Board Design:** Need a specific form factor to fit your enclosure, 9-36V automotive power with supercapacitors, GMSL2 cameras, or PoE? We spin custom PCBA prototypes in **2–3 weeks**.
3. **Linux BSP & Edge AI Consulting:** Fast-boot optimization, custom camera sensor drivers, RKNN model quantization (trained on our local RTX 5090 cluster), and zero-copy video pipelines.

📫 **Contact Our Engineering Lead:**
* **Email:** `wleovm@gmail.com`
* **Reddit:** [u/OmniEdgeAI](https://www.reddit.com/user/OmniEdgeAI)
