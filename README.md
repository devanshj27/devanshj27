<p align="center">
  <img src="assets/banner.svg" width="100%" alt="Devansh Jaiswal, Control Systems Engineer: embedded AI, robotics, computer vision and physics simulation">
</p>

### Hi, I'm Devansh 👋

I'm a **control systems engineer** who likes taking a model out of the notebook and onto real hardware: small boards, tight memory budgets, real sensors and a real sky.

- 🚁 **Building:** [Project Seraphim Sky](https://github.com/devanshj27/seraphim-sky), real-time drone detection with the neural network running **on the camera sensor**
- 🔧 **Now:** hardening its on-device deployment on a Raspberry Pi 5 test bench ([rpi-imx500](https://github.com/devanshj27/rpi-imx500))
- 🔁 **How I work:** data → training → INT8 quantization → deployment → field tests, then round again
- 🌱 **Into:** robotics, embedded programming, physics simulation and Blender
- 📫 **Open to:** collaborations and roles in embedded AI, robotics and control systems

## 🚁 Featured: Project Seraphim Sky

<p align="center">
  <a href="https://github.com/devanshj27/seraphim-sky">
    <img src="assets/seraphim-sky-field-test.gif" width="640" alt="Outdoor field test: a drone flies in against a cloudy sky and is boxed and labelled 'drone' by the model running on the IMX500 sensor">
  </a>
  <br>
  <sub>Outdoor field test. Every detection comes from the model running on the camera sensor.</sub>
</p>

An end-to-end drone detection system for industrial-site security. I fine-tuned **YOLO11n** on the open 83k-image Seraphim drone dataset, **INT8-quantized** it with Sony's Model Compression Toolkit and flashed it onto the **Sony IMX500 AI Camera**, so inference happens on the sensor before a frame ever reaches the **Raspberry Pi 5**.

| mAP50 | Precision | Recall | Latency | Sensor memory |
|:---:|:---:|:---:|:---:|:---:|
| **0.973** | **0.965** | **0.952** | **15–17 ms** | **7.16 / 8 MB** |

<sub>Accuracy is measured before quantization. Latency is per frame, on the sensor.</sub>

**Pipeline:** 83k images → YOLO11n fine-tune (Kaggle) → INT8 post-training quantization (Sony MCT) → IMX500 converter and packager → `network.rpk` on the sensor → Picamera2 / modlib on the Pi.

**Problems I worked through**

- **Plain-sky blind spot:** texture bias in the base dataset meant almost no detections against open sky. A fine-tune on a custom sky-background set fixed it.
- **Quantized confidence:** on-device scores snap to a few fixed levels. I traced this to INT8 quantization of the confidence head under memory-limited calibration, a platform ceiling rather than a model regression.

<sub>Python · Ultralytics · Sony MCT · IMX500 Converter · Picamera2 · modlib · OpenCV · FFmpeg · Kaggle · Colab</sub>

## 🛠️ More things I've built

| Project | What it does |
|---|---|
| 🛰️ **[RaspberryPi4-GPS-NEO6M](https://github.com/devanshj27/RaspberryPi4-GPS-NEO6M)** | Reads a u-blox GPS module over UART on a Pi 4B. It finds the right serial port, parses NMEA, reverse-geocodes the fix to an address and beeps a buzzer once it has a lock.<br><sub>Python · pyserial · pynmea2 · geopy · RPi.GPIO</sub> |
| 🌡️ **[RPi-health-checkup](https://github.com/devanshj27/RPi-health-checkup)** | One-shot Raspberry Pi health report: temperature, voltages, clocks, throttling flags, CPU governor and memory split.<br><sub>Bash · vcgencmd</sub> |
| 📡 **[IP-Activity-Scanner](https://github.com/devanshj27/IP-Activity-Scanner)** | Auto-detects your subnet, ping-sweeps its DHCP range and names live devices by hostname (mDNS/NetBIOS), MAC address and vendor.<br><sub>Bash · PowerShell · nmap</sub> |
| 🎧 **[AUDIOBOOK-GENERATOR](https://github.com/devanshj27/AUDIOBOOK-GENERATOR)** | Turns EPUB, PDF and TXT files into speech or MP3, offline with pyttsx3 or with more natural voices via gTTS. Built to help people with reading difficulties, or anyone who'd rather listen.<br><sub>Python · pyttsx3 · gTTS</sub> |
| 🧮 **[Desktop Calculator](https://github.com/devanshj27/basicprojects/tree/main/project/end_project_calculator)** | A Tkinter calculator with `Decimal`-precision math, memory keys, keyboard and clipboard support, and unit tests.<br><sub>Python · Tkinter · unittest</sub> |

**Open source and learning**

- 📐 Patched series expansion of `hyper()` in **SymPy** ([fix branch for issue #26250](https://github.com/devanshj27/sympy/tree/fix_26250))
- ⚛️ Explored quantum computing through the **Qiskit Global Summer School** labs (2023, 2024)

## 🧰 Toolbox

<table>
  <tr>
    <td><b>Languages</b></td>
    <td>
      <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
      <img src="https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white" alt="Bash">
      <img src="https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white" alt="Jupyter">
    </td>
  </tr>
  <tr>
    <td><b>AI and vision</b></td>
    <td>
      <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" alt="PyTorch">
      <img src="https://img.shields.io/badge/Ultralytics_YOLO-111F68?style=flat-square&logo=ultralytics&logoColor=white" alt="Ultralytics YOLO">
      <img src="https://img.shields.io/badge/ONNX-005CED?style=flat-square&logo=onnx&logoColor=white" alt="ONNX">
      <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white" alt="OpenCV">
      <img src="https://img.shields.io/badge/Model_Compression_Toolkit-000000?style=flat-square&logo=sony&logoColor=white" alt="Sony Model Compression Toolkit">
    </td>
  </tr>
  <tr>
    <td><b>Hardware</b></td>
    <td>
      <img src="https://img.shields.io/badge/Raspberry_Pi-A22846?style=flat-square&logo=raspberrypi&logoColor=white" alt="Raspberry Pi">
      <img src="https://img.shields.io/badge/IMX500_AI_Camera-000000?style=flat-square&logo=sony&logoColor=white" alt="Sony IMX500 AI Camera">
      <img src="https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black" alt="Linux">
    </td>
  </tr>
  <tr>
    <td><b>Workflow</b></td>
    <td>
      <img src="https://img.shields.io/badge/Git-F03C2E?style=flat-square&logo=git&logoColor=white" alt="Git">
      <img src="https://img.shields.io/badge/Kaggle-20BEFF?style=flat-square&logo=kaggle&logoColor=white" alt="Kaggle">
      <img src="https://img.shields.io/badge/Google_Colab-F9AB00?style=flat-square&logo=googlecolab&logoColor=black" alt="Google Colab">
      <img src="https://img.shields.io/badge/FFmpeg-007808?style=flat-square&logo=ffmpeg&logoColor=white" alt="FFmpeg">
    </td>
  </tr>
  <tr>
    <td><b>Also into</b></td>
    <td>
      <img src="https://img.shields.io/badge/Blender-E87D0D?style=flat-square&logo=blender&logoColor=white" alt="Blender">
      physics simulation · robotics
    </td>
  </tr>
</table>

## 📡 On my radar

Counter-UAS sensing beyond cameras (Remote ID, ADS-B), ROS 2 drone autonomy with PX4 and ArduPilot, low-cost LiDAR, RF-DETR for small aerial targets, and stereo depth on edge accelerators like the Hailo-8.

---

<p align="center"><sub>Building things that see, sense and steer.</sub></p>
