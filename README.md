# Drowsiness Detection in Automobile Drivers

This project implements a **real-time computer vision system** that detects driver drowsiness using deep learning (CNN, VGG19, YOLOv3, Viola–Jones). The system monitors eyes and mouth activity, computes drowsiness metrics (PERCLOS, blink frequency, yawn detection), and triggers alerts to prevent accidents.

---

# Installation and Deployment

Click the green "<> Code" button, then **Open with GitHub Desktop**.

GitHub Desktop will prompt you for a location to download the repository. Continue with your selection to add the folder `/Drowsiness-Detection` to your system.

---

## Local Setup

### Python Environment

Create a local Python environment to avoid dependency conflicts:

```bash
cd Drowsiness-Detection
python -m venv env
# Activate environment
source env/bin/activate        # Mac/Linux
.\env\Scripts\activate         # Windows
