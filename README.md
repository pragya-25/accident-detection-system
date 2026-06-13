# accident-detection-system
"AI-Powered Vehicle Accident Detection and Emergency Alert System using YOLOv8"
An end-to-end deep learning system that detects vehicle accidents in real-time video footage using a custom-trained YOLOv8 model, classifies severity (Severe/Moderate), automatically locates the nearest hospital, and triggers an emergency alert through a web dashboard.

M.Tech by Research Project | Computer Science & Engineering


🎯 Features


Real-time accident detection using a custom-trained YOLOv8 model (97.5% mAP50)
Severity classification — Severe vs Moderate accidents
Frame-voting algorithm — eliminates false positives (15% → 0%)
Automatic hospital lookup via OpenStreetMap Overpass API (no API key needed)
Web dashboard with live alerts, incident logging, and audio notifications
Simulated multi-camera network across Delhi-NCR (3 locations)
SQLite database for incident history



🏗️ Architecture

Video Input → YOLOv8 Detection → Frame Voting → Hospital Lookup → Emergency Alert Dashboard

StageDescriptionVideo InputUpload video file or live camera feedYOLOv8 ModelDetects and classifies accidents per frameFrame VotingRequires 5/10 consecutive frames to confirm accidentHospital LookupFinds nearest hospital via OpenStreetMapAlert SystemDisplays incident details on dashboard with sound alert


📊 Model Performance

ClassPrecisionRecallmAP50mAP50-95All (combined)95.0%96.0%97.5%88.1%Severe98.4%97.2%99.4%90.9%Moderate91.6%94.8%95.6%85.3%

Dataset: 11,780 images (Roboflow Universe)
Training: 30 epochs, YOLOv8n, 416x416, batch=4, Tesla T4 GPU, 2.13 hours


🛠️ Tech Stack


AI Model: YOLOv8n (Ultralytics)
Backend: Python, Flask, OpenCV
Frontend: HTML5, CSS3, JavaScript
Database: SQLite
Hospital API: OpenStreetMap Overpass API
Deployment: Google Colab (T4 GPU) + ngrok



🚀 How to Run

1. Train / Load the Model

Open Accident_Detection.ipynb in Google Colab:

Runtime → Change runtime type → T4 GPU
Run cells in order: 1 → 3 → 4 → 7 → 5 (Flask server)

2. Get the Server URL

Cell 5 prints an ngrok public URL like:

https://xxxx-xx-xxx-xx-xx.ngrok-free.app

3. Connect the Dashboard

Open accident_dashboard.html in a browser, update the API_URL variable with your ngrok URL, then upload a video to test!


📁 Repository Structure

accident-detection-system/
├── Accident_Detection.ipynb      # Main Colab notebook (training + detection + server)
├── accident_dashboard.html        # Web dashboard UI
├── Project_Report.docx        # Full project report
|── Presentation.pptx           # Project presentation slides
└── README.md


🔮 Future Enhancements


Replace YOLOv8 with RT-DETR (transformer-based detection)
Integrate Twilio API for automated emergency calls
Support live RTSP CCTV streams
Train on night-vision and adverse weather datasets
Mobile app for traffic police / hospital staff
