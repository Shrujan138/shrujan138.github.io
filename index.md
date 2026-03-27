Development of a Cyber Physical System in Real Time Bolt Defect Detection using Machine Learning based Automated Quality Control
An AI-powered cyber-physical system for real-time bolt quality inspection using YOLO object detection, Flask web interface, and Arduino hardware integration for automated quality control in manufacturing environments.

🎯 Overview
This cyber-physical system integrates machine learning with physical hardware to create an automated quality control solution for bolt manufacturing. The system combines computer vision (YOLO v8), real-time processing, web-based monitoring, and hardware integration (Arduino) to detect defects in bolts with high accuracy and speed. It bridges the digital and physical worlds by automatically triggering hardware responses based on AI detection results.

✨ Features
Cyber-Physical Integration
Real-time Detection: Live camera streaming with instant bolt classification
Hardware Integration: Arduino-based physical alerts for defective bolts
Automated Quality Control: Zero human intervention required for detection
Closed-Loop System: Detection triggers immediate hardware response
Machine Learning & AI
YOLO v8 Model: State-of-the-art object detection for accurate defect identification
AI-Powered Classification: Deep learning for good/defective bolt detection
Confidence Scoring: Probability-based detection results
Adaptive Detection: Handles various lighting and positioning conditions
Real-Time Processing
Live Streaming: Continuous video feed processing
Instant Classification: Sub-second detection response time
Fixed Detection Zone: Clearly marked area for consistent bolt positioning
Single Detection Logic: Each bolt counted only once to prevent duplicates
Web-Based Monitoring
User-Friendly Interface: Flask-based dashboard for system control
Real-Time Statistics: Live counters for good/defective bolts
Visual Feedback: Color-coded borders (Green=Good, Red=Defective)
Remote Access: Monitor from any device on the network
Multiple Input Methods
Live camera streaming
Single frame capture
Image upload for batch processing
Phone camera support (IP Webcam)
Hardware Automation
Arduino Integration: Physical world response to digital detection
Alert System: HIGH signal for defective bolts only
Scalable: Can control sorting mechanisms, reject bins, or alarms
Raspberry Pi Compatible: Optimized for embedded deployment
🏭 Cyber-Physical System Architecture
┌─────────────────────────────────────────────────────────────┐
│                    CYBER LAYER (Digital)                     │
├─────────────────────────────────────────────────────────────┤
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐  │
│  │   Camera     │───▶│  YOLO Model  │───▶│   Flask Web  │  │
│  │   Input      │    │  (AI/ML)     │    │   Interface  │  │
│  └──────────────┘    └──────────────┘    └──────────────┘  │
│         │                    │                    │          │
│         └────────────────────┴────────────────────┘          │
│                              │                               │
│                    ┌─────────▼─────────┐                    │
│                    │  Decision Logic   │                    │
│                    │  (Good/Defective) │                    │
│                    └─────────┬─────────┘                    │
└──────────────────────────────┼──────────────────────────────┘
                               │
                    ┌──────────▼──────────┐
                    │   Serial Protocol   │
                    │   (USB/UART)        │
                    └──────────┬──────────┘
                               │
┌──────────────────────────────▼──────────────────────────────┐
│                   PHYSICAL LAYER (Hardware)                  │
├─────────────────────────────────────────────────────────────┤
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐  │
│  │   Arduino    │───▶│   Actuators  │───▶│   Physical   │  │
│  │ Microcontroller│   │  (LED/Relay) │    │   Response   │  │
│  └──────────────┘    └──────────────┘    └──────────────┘  │
│         │                    │                    │          │
│    ┌────▼────┐          ┌───▼────┐          ┌────▼────┐    │
│    │ Buzzer  │          │ Sorter │          │ Reject  │    │
│    │ Alert   │          │ Mech.  │          │  Bin    │    │
│    └─────────┘          └────────┘          └─────────┘    │
└─────────────────────────────────────────────────────────────┘
System Flow
Capture: Camera captures bolt image in detection zone
Process: YOLO model analyzes image for defects
Classify: AI determines Good or Defective status
Decide: System logic processes classification result
Communicate: Serial signal sent to Arduino (if defective)
Actuate: Physical hardware responds (LED, buzzer, sorter)
Monitor: Web interface displays real-time statistics
📋 Requirements
Cyber Layer (Digital Components)
Computer with webcam or USB camera
(Optional) Raspberry Pi 4 for embedded deployment
(Optional) Android phone with IP Webcam app
Physical Layer (Hardware Components)
(Optional) Arduino board (Uno/Mega/Nano) for hardware integration
(Optional) LED indicators for visual alerts
(Optional) Buzzer for audio alerts
(Optional) Relay module for controlling sorting mechanisms
(Optional) Reject bin actuator/servo
Software
Python 3.8 or higher
OpenCV
PyTorch
Flask
Ultralytics YOLO
🚀 Installation
Standard Installation (Windows/Linux/Mac)
Clone the repository:
git clone <repository-url>
cd boltFaultDet
Install dependencies:
pip install -r requirements.txt
Raspberry Pi Installation
Install system dependencies:
sudo apt-get update
sudo apt-get install libatlas-base-dev libopenblas-dev
sudo apt-get install python3-pip python3-dev
Install PyTorch (CPU-only):
pip3 install torch torchvision --index-url https://download.pytorch.org/whl/cpu
Install other requirements:
pip3 install -r requirements_rpi.txt
Memory optimization:
export PYTORCH_DISABLE_CUDA_MEMORY_CACHING=1
📁 Project Structure
boltFaultDet/
├── app.py                      # Main Flask application
├── bestFinal.pt                # YOLO model weights
├── requirements.txt            # Standard dependencies
├── requirements_rpi.txt        # Raspberry Pi dependencies
├── templates/
│   └── index.html             # Web interface template
├── static/
│   └── app.js                 # Frontend JavaScript
├── datasets/                   # Bolt training datasets
│   └── (Add your bolt images here)
├── videos/                     # Project demo videos
│   └── (Add demo videos here)
├── ui_screenshots/            # User interface screenshots
│   └── (Add UI screenshots here)
├── arduino_bolt_detector.ino  # Arduino code
├── phone_camera.py            # Phone camera integration
├── unified_camera.py          # Unified camera handler
├── camera_config.py           # Camera configuration
├── test_cameras.py            # Camera testing utility
└── test_camera_quality.py     # Camera quality testing
🎮 Usage
1. Start the Cyber-Physical System
python app.py
The server will start at http://localhost:5000

2. Web Interface (Cyber Layer Monitoring)
Open your browser and navigate to http://localhost:5000

Available Features:

Camera Selection: Choose from available cameras
Live Streaming: Start continuous detection
Single Capture: Capture and analyze one frame
Image Upload: Upload bolt images for analysis
Arduino Control: Connect/disconnect Arduino
Statistics: View detection counters
3. Arduino Integration (Physical Layer Actuation)
Setup:

Upload arduino_bolt_detector.ino to your Arduino
Connect Arduino to computer via USB
Note the COM port (e.g., COM4)
In the web interface, connect to Arduino
Cyber-Physical Communication:

Defective Bolt Detected → Arduino receives HIGH signal → Physical actuators activate
Good Bolt Detected → No signal sent (silent operation) → No physical response
Physical Responses (Configurable):

LED indicator turns ON
Buzzer sounds alert
Relay activates sorting mechanism
Servo moves reject bin
Counter increments on display
4. Phone Camera (Optional)
Install IP Webcam app on Android
Start the server in the app
Run the phone camera script:
python phone_camera.py
🔧 Configuration
Detection Zone Settings
Edit app.py to adjust detection zone:

zone_width = 450   # Width in pixels
zone_height = 400  # Height in pixels
AI Model Parameters
Adjust detection sensitivity in app.py:

conf=0.4,    # Confidence threshold (0.0-1.0)
iou=0.5,     # IoU threshold
imgsz=320,   # Input image size
Arduino Port
Change Arduino port in app.py:

arduino_port = 'COM4'  # Windows
# arduino_port = '/dev/ttyUSB0'  # Linux
# arduino_port = '/dev/tty.usbserial'  # Mac
📊 Detection Logic (Machine Learning Based Quality Control)
Automated Quality Control Process
Fixed Detection Zone: White border marks the automated inspection area
Bolt Placement: Operator/conveyor places bolt inside the detection zone
AI Analysis: YOLO v8 model analyzes the bolt using trained neural network
Machine Learning Classification:
Good Bolt → Green border + Counter increment
Defective Bolt → Red border + Arduino alert + Counter increment
Single Count Logic: Each bolt counted only once (prevents duplicate counting)
Physical Response: Arduino triggers hardware actuators for defective bolts
Remove Bolt: Operator/conveyor removes bolt to reset for next inspection
Continuous Loop: System ready for next bolt immediately
Machine Learning Model
Architecture: YOLO v8 (You Only Look Once)
Training: Custom dataset of good and defective bolts
Classes: 2 (Good_Bolt, Defective_Bolt)
Input Size: 320x320 pixels (optimized for speed)
Confidence Threshold: 0.4 (40% minimum confidence)
Inference Time: <100ms per frame
Accuracy: Depends on training dataset quality
Border Colors
White: Ready for detection / No bolt detected
Green: Good bolt detected
Red: Defective bolt detected
Yellow: Analyzing (if enabled)
Orange: Unknown object (if enabled)
🎯 Performance Optimization
Real-Time Processing Optimizations
The cyber-physical system includes several optimizations for real-time operation:

Machine Learning Optimizations:

Reduced AI input size (320px) for faster inference
Single-pass detection (no multiple fallbacks)
Optimized confidence threshold (0.4) for speed vs accuracy balance
CPU-optimized PyTorch for consistent performance
Image Processing Optimizations:

Lower JPEG quality (50-70) for faster encoding
Minimal buffer size for lowest latency
Simplified detection logic for faster decisions
Frame-by-frame processing without queuing
Hardware Communication Optimizations:

Direct serial communication (9600 baud)
Unidirectional signaling (computer → Arduino)
No acknowledgment required (fire-and-forget)
Minimal protocol overhead
Raspberry Pi Optimization
Headless OpenCV (no GUI dependencies)
CPU-only PyTorch
Memory caching disabled
Optimized camera settings
🏭 Industrial Applications
Manufacturing Quality Control
Automated bolt inspection on production lines
Real-time defect detection without human intervention
Integration with conveyor systems
Automatic sorting of good/defective parts
Cyber-Physical Integration Benefits
Zero Latency: Immediate hardware response to AI detection
24/7 Operation: Continuous automated quality control
Consistency: No human fatigue or error
Traceability: Digital logs of all inspections
Scalability: Easy to replicate across multiple stations
Use Cases
Automotive manufacturing (engine bolts)
Aerospace industry (critical fasteners)
Construction materials (structural bolts)
Electronics assembly (precision fasteners)
Quality assurance laboratories
📸 Datasets
Add your bolt training datasets to the datasets/ folder:

datasets/
├── good_bolts/
│   ├── bolt_001.jpg
│   ├── bolt_002.jpg
│   └── ...
└── defective_bolts/
    ├── defect_001.jpg
    ├── defect_002.jpg
    └── ...
🎥 Demo Videos
Add project demonstration videos to the videos/ folder:


## 🐛 Troubleshooting

### Camera Not Working
```bash
python test_cameras.py
Model Not Loading
Ensure bestFinal.pt is in the project root
Check PyTorch installation
Verify model compatibility
Arduino Not Connecting
Check COM port in Device Manager (Windows)
Verify Arduino is connected via USB
Ensure correct baud rate (9600)
Try different USB ports
Slow Performance
Reduce camera resolution
Lower AI confidence threshold
Use Raspberry Pi optimized version
Close other applications
📝 API Endpoints
GET / - Main web interface
POST /capture - Capture single frame
POST /upload - Upload image for detection
POST /start_auto_capture - Start live streaming
POST /stop_auto_capture - Stop live streaming
POST /connect_arduino - Connect to Arduino
POST /disconnect_arduino - Disconnect Arduino
POST /reset_counters - Reset detection counters
GET /get_latest_detection - Get latest detection data
GET /get_counts - Get current statistics
🔐 Security & Safety Notes
Cyber Security
System designed for local network use only
Do not expose to public internet without proper security measures
Implement authentication for production environments
Regular security updates recommended
Physical Safety
Arduino signals are unidirectional (computer → Arduino)
Implement emergency stop mechanisms for physical actuators
Follow electrical safety standards for hardware integration
Use proper isolation for high-voltage/high-current applications
Regular maintenance of physical components
Data Privacy
No sensitive data is stored or transmitted
Detection images can be logged for quality assurance (optional)
Comply with workplace monitoring regulations
Secure access to web interface in production
🎓 Research & Development
This cyber-physical system demonstrates:

Integration of AI/ML with physical hardware
Real-time decision making and actuation
Automated quality control in manufacturing
Industry 4.0 principles and smart manufacturing
Edge computing for industrial applications
Academic Applications
Research in cyber-physical systems
Machine learning for quality control
Real-time embedded systems
Industrial automation studies
Computer vision applications
🙏 Acknowledgments
YOLO by Ultralytics (Machine Learning Framework)
OpenCV community (Computer Vision Library)
Flask framework (Web Interface)
PyTorch team (Deep Learning Framework)
Arduino community (Physical Hardware Integration)
Cyber-Physical Systems research community
🔬 Keywords
Cyber-Physical Systems, Machine Learning, Automated Quality Control, Real-Time Detection, YOLO, Object Detection, Industrial Automation, Arduino Integration, Computer Vision, Deep Learning, Manufacturing, Quality Assurance, Industry 4.0, Smart Manufacturing, Edge Computing

Project Title: Development of a Cyber Physical System in Real Time Bolt Defect Detection using Machine Learning based Automated Quality Control
Version: 1.0.0
Last Updated: March 2026

License
This project is open-source and free to use for educational and research purposes.

Status: Production Ready
Category: Cyber-Physical Systems, Industrial Automation, Quality Control

👨‍💻 Author
Shrujan M
📧 Contact: mshrujan.28@gmail.com 🔗 LinkedIn: https://www.linkedin.com/in/shrujan-m-804842361/?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app%20
