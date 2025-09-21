```markdown
# 🚗 Drowsiness Detection in Drivers

A computer vision + deep learning project that detects driver drowsiness in real time to help prevent accidents caused by fatigue.

---

## 📖 Overview
Driver fatigue is a major contributor to road accidents worldwide. This project uses **Convolutional Neural Networks (CNNs)** and **computer vision** to monitor facial cues—eye closure, blink rate, and yawning—and raise an alert when drowsiness is detected.  
If you’re using the full pipeline, it can combine classic detectors (Haar/Viola-Jones) with deep models (e.g., CNNs, MobileNet/VGG variants, or YOLO for face/eye ROI).

---

## ✨ Features
- Real-time webcam/video stream analysis with **OpenCV**
- Eye & mouth region detection (blink and yawn cues)
- Deep learning classifier for **alert vs. drowsy**
- Audible alert when drowsiness is detected
- Modular code to swap detectors/models (Haar, Dlib, YOLO, CNN)

---

## 🛠️ Tech Stack
- **Python 3.8+**
- **OpenCV** – video & image processing
- **TensorFlow / Keras** – training & inference
- **Dlib** or **Haar Cascades** – facial landmarks / classical detection (optional)
- **NumPy, Pandas** – data utilities
- **Matplotlib** – visualization (optional)

---

## 📂 Project Structure
```

drowsiness-detection/
├── data/               # Datasets (eyes open/closed, yawning frames, etc.)
├── models/             # Saved weights/checkpoints
├── src/
│   ├── detector.py     # Main real-time detection script
│   ├── train.py        # Model training / fine-tuning script
│   ├── utils.py        # Helpers: preprocessing, alerts, metrics, etc.
│   ├── configs/        # (Optional) YAML/JSON configs for experiments
├── requirements.txt    # Python dependencies
├── LICENSE             # Project license (MIT by default)
└── README.md           # You are here

````

---

## 🚀 Getting Started

### 1) Clone the repo
```bash
git clone https://github.com/<your-username>/drowsiness-detection.git
cd drowsiness-detection
````

### 2) (Recommended) Create a virtual environment

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate
```

### 3) Install dependencies

```bash
pip install -r requirements.txt
```

> If you face `dlib` build issues, you may skip it and use Haar cascades or prebuilt wheels for your OS.

### 4) Run real-time detection

```bash
python src/detector.py
```

> By default, this reads from your primary webcam (`cv2.VideoCapture(0)`).
> To run on a video file: `python src/detector.py --video path/to/video.mp4`

---

## ⚙️ Configuration (Optional)

You can pass CLI flags or config files:

```bash
python src/detector.py \
  --model_path models/cnn_best.h5 \
  --use_haar true \
  --threshold 0.6 \
  --alarm_sound assets/alarm.wav
```

Common flags:

* `--model_path`: path to trained model
* `--use_haar` / `--use_dlib` / `--use_yolo`: choose detector(s)
* `--threshold`: drowsiness probability threshold for alerts
* `--video`: input video path (omit for webcam)
* `--alarm_sound`: custom alert sound file

---

## 📊 Dataset

You can use open datasets or collect your own:

* Eye state datasets (open/closed)
* Yawn/mouth state datasets

**Tips for data quality**

* Balance classes (alert vs. drowsy)
* Include varied lighting, head poses, glasses/no-glasses
* Augment data (brightness, rotation, slight blur) for robustness

> Place raw data under `data/` in subfolders like `eyes_open/`, `eyes_closed/`, `yawn/`, `no_yawn/` (or adapt `train.py` to your structure).

---

## 🧠 Training (Optional)

Fine-tune or train from scratch:

```bash
python src/train.py \
  --data_dir ./data \
  --epochs 25 \
  --batch_size 32 \
  --img_size 224 \
  --lr 1e-4 \
  --output_dir ./models
```

Outputs: model checkpoints and training logs in `models/`.

---

## 🔊 Alerts

When the predicted drowsiness score exceeds the threshold, an alarm plays.
Change the sound or add other actuators (e.g., seat vibration, haptic) in `src/utils.py`.

---

## 🧪 Notes & Troubleshooting

* Ensure good lighting for reliable eye/mouth detection.
* If FPS is low, switch to a lighter backbone (e.g., MobileNet) or reduce image size.
* On laptops with dual GPUs, make sure TensorFlow uses the intended GPU (if available).

---

## 🎯 Roadmap / Future Work

* On-device/edge deployment (Jetson, Raspberry Pi)
* Multi-driver support & ID tracking
* Sensor fusion (eye aspect ratio + head pose + PERCLOS)
* Improved robustness with larger, diverse datasets

---

## 🤝 Contributing

Contributions are welcome!

1. Fork this repo
2. Create a feature branch: `git checkout -b feat/my-feature`
3. Commit: `git commit -m "Add my feature"`
4. Push: `git push origin feat/my-feature`
5. Open a Pull Request

---

## 📝 License

This project is licensed under the **MIT License**. See `LICENSE` for details.

---

## 🙏 Acknowledgements

* OpenCV & TensorFlow/Keras communities
* Public datasets and prior research on driver monitoring
* Classic methods (Haar/Viola-Jones) and modern detectors (YOLO) for ROI extraction

```
```
