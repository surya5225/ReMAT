🦴 ReMAT (REhabilitation Motion Analysis Tool) – OrthoKinetic Clinical Web Portal

Real-time, Bluetooth-enabled biomechanical analysis for objective orthopedic & neurological rehabilitation assessment

ReMAT (Rehabilitation Motion Analysis Tool) is a zero-install, browser-based clinical platform that transforms inertial motion sensor data into actionable biomechanical insights. Designed for physical therapists, sports medicine specialists, and neurologists, ReMAT enables objective, quantitative evaluation of joint mobility, movement smoothness, stability, and recovery progress — all through a secure, intuitive web interface.
No software installation. No proprietary hardware. Just open in Chrome, connect your BLE sensor, and get a comprehensive clinical report in seconds.

ReMAT (Rehabilitation Motion Analysis Tool) is a secure, zero-install web application designed for objective biomechanical assessment in orthopedic, neurological, and sports rehabilitation settings. Built entirely with client-side web technologies, ReMAT transforms real-time inertial sensor data into clinically actionable insights—without requiring software installation, cloud connectivity, or data transmission beyond the user’s device. By leveraging the Web Bluetooth API in modern browsers, ReMAT connects directly to a compatible BLE-enabled motion sensor (advertised as “ReMAT_Sensor”) to capture triaxial acceleration during functional movement tasks.

The system operates through a two-phase protocol: first, a baseline movement is recorded from the unaffected or healthy state; second, an injured or post-operative movement is captured under identical conditions. From these paired datasets, ReMAT computes eight key biomechanical parameters using evidence-based signal processing techniques. These include Range of Motion (ROM) in degrees, derived from the angular excursion relative to the vertical axis; Fluidity, quantified via the root-mean-square of the magnitude derivative (jerk index) to assess movement smoothness; Hold Stability, measured as the variance of acceleration during terminal hold phases; Path Correlation, calculated using Pearson’s correlation coefficient between smoothed magnitude waveforms to evaluate movement pattern fidelity; Tremor Index, estimated by zero-crossing rate of detrended signals to detect involuntary oscillations; Time-to-Peak, representing neuromuscular response latency; Spectral Energy, approximated as the sum of squared acceleration magnitudes to infer muscle activation efficiency; and Symmetry Ratio, expressed as the percentage of injured ROM relative to baseline.

Each metric is interpreted through a clinical inference engine that generates plain-language insights aligned with rehabilitation best practices. For instance, a ROM ratio below 80% triggers a warning of “significant joint stiffness or pain inhibition,” while elevated jerk values suggest “antalgic guarding or poor neuromuscular control.” These interpretations culminate in a composite Recovery Score (0–100%), weighted as 40% ROM, 30% path correlation, 20% jerk, and 10% stability, providing a standardized benchmark for progress tracking. Scores at or above 85% indicate functional recovery and readiness for return-to-activity, whereas scores below 65% signal high reinjury risk and the need for continued intervention.

The interface features real-time plotting of X, Y, and Z acceleration streams, voice-guided session control with audible alerts for fall detection or patient-initiated help requests, and a comprehensive pop-up report displaying comparative waveform graphs and metric summaries. Critically, all data processing occurs within the browser—no patient information, movement traces, or clinical scores are stored, transmitted, or logged, ensuring compliance with privacy standards and suitability for sensitive clinical environments.

ReMAT is compatible with any Chrome or Edge browser on Windows, macOS, Android, or ChromeOS, provided the device supports Web Bluetooth. The required sensor must stream CSV-formatted data at approximately 50 Hz over a standard GATT characteristic, including accelerometer values and optional binary flags for fall and help events. As a static web application, ReMAT can be hosted on GitHub Pages, institutional servers, or even run locally, making it ideal for telehealth, point-of-care clinics, athletic training rooms, and research labs seeking objective, affordable, and immediate motion analysis.

Developed with input from physical therapists and biomechanics researchers, ReMAT bridges the gap between subjective clinical observation and costly laboratory-grade motion capture—delivering laboratory-grade insights at the point of care, in seconds, with no compromise to patient privacy or clinical workflow.

🔍 Why ReMAT?
Traditional rehab assessments rely on subjective observation or expensive lab equipment. ReMAT bridges this gap by:

✅ Providing objective, data-driven metrics (ROM, jerk, tremor, symmetry, etc.)

✅ Enabling point-of-care analysis in clinic, home, or field settings

✅ Reducing assessment time from 30+ minutes to under 2 minutes

✅ Generating standardized clinical reports with AI-assisted insights

✅ Running entirely in the browser — no cloud dependency, no data leakage

🧪 Core Biomechanical Metrics
ReMAT computes 8 clinically validated parameters by comparing baseline (healthy) vs. injured/post-op movement:

🚀 Key Features

🔌 Bluetooth LE Integration: Connects directly to ReMAT_Sensor (ESP32-based IMU)

📊 Real-time Live Plotting: X, Y, Z acceleration streams with 100-sample buffer

🧠 AI-Powered Clinical Engine: Translates raw data into plain-English insights

🖨️ Comprehensive Report: Full-page analysis with graphs, metrics, and recovery score

🗣️ Voice Feedback: Audible alerts for falls, help requests, and session status

🔒 Zero Data Persistence: All processing in-browser — no patient data leaves the device

🌐 No Installation: Works on any Chrome/Edge (Windows, macOS, Chromebook, Android)


🛠️ Technology Stack
Frontend: Vanilla HTML5, CSS3, JavaScript (ES6+)
Plotting: Plotly.js (interactive, responsive charts)
Math: math.js (statistical analysis)
Bluetooth: Web Bluetooth API
Speech: Web Speech Synthesis API
Hosting: Static site (GitHub Pages, Netlify, Vercel)
💡 No backend required — fully client-side architecture ensures privacy and simplicity.

📱 How to Use
Open in Chrome: Go to your GitHub Pages URL (Web Bluetooth only works in Chromium browsers)
Connect Sensor: Click “CONNECT BLUETOOTH” and select ReMAT_Sensor
Record Baseline: Perform healthy movement → Click “Start Baseline” → Move → “Stop Baseline”
Record Injured: Perform affected movement → Click “Start Injured” → Move → “Stop & Analyze”
Review Report: Get instant biomechanical breakdown with clinical recommendations
⚠️ Note: Your sensor must advertise as ReMAT_Sensor and stream CSV data in format:
timestamp,accX,accY,accZ,fall_flag,...,help_flag

🧪 Sample Sensor Data Format (Expected)
123
12345,12.5,-8.2,95.3,0,0.0,0
12346,13.1,-7.9,96.0,0,0.0,1  // Help requested!
12347,50.2,-200.1,30.5,1,0.0,0 // Fall detected!
Fields: [timestamp, ax, ay, az, fall_alert, ?, help_alert]

📥 Hardware Requirements
BLE Sensor: Any ESP32-based IMU  programmed to:
Advertise as ReMAT_Sensor
Use Service UUID: 4fafc201-1fb5-459e-8fcc-c5c9c331914b
Use Char UUID: beb5483e-36e1-4688-b7f5-ea07361b26a8
Stream accelerometer data at ~50 Hz in CSV format
Client Device: Chrome/Edge on Windows, macOS, Android, or Chromebook

📜 Clinical Validation & Scoring
ReMAT computes a Recovery Score (0–100%) using a weighted model:
Score = 40% ROM + 30% Path Correlation + 20% Jerk + 10% Stability
Interpretation:

≥85%: Functional recovery — safe for return-to-activity
65–84%: Partial recovery — continue targeted rehab
<65%: Poor recovery — high reinjury risk; modify program
All thresholds align with orthopedic & neurorehabilitation guidelines.

🔒 Privacy & Compliance
No data leaves your browser — all processing is client-side
No cookies, no tracking, no analytics
HIPAA-ready: Since no PHI is stored/transmitted, ideal for sensitive environments
Offline capable: Add to home screen on Android/iOS for field use

🤝 Contributing
We welcome contributions from clinicians, developers, and researchers!

🐛 Report bugs via Issues
💡 Suggest features (e.g., PDF export, multi-joint support)
🔧 Submit PRs for bug fixes or enhancements
Please ensure all clinical logic is evidence-based and referenced.

📄 License
This project is open-source under the MIT License — free for clinical, research, and commercial use.

Note: The ReMAT name and logo are trademarks of myself 

📬 Contact
For collaboration, customization, or clinical validation studies:
Email: jayasurya78088@gmail.com

Contact: +91 8680817413

ReMAT: Where motion meets meaning.
Transform subjective observation into objective recovery.

