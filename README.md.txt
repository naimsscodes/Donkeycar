# 🏎️ DonkeyCar Autonomous RC Project

This is a fully autonomous RC car project using the [DonkeyCar](https://docs.donkeycar.com) framework, Raspberry Pi 4, Python, and deep learning.

---

## 🎯 Project Goals

- Build and program an autonomous RC car from scratch
- Collect driving data (tub format)
- Train AI model to drive the car autonomously
- Deploy model on Raspberry Pi and test on real track

---

## 🛠️ Hardware Used

- Raspberry Pi 4 (4GB)
- Pi Camera or USB Webcam
- PCA9685 servo controller
- RC car chassis + motor + ESC + steering servo
- Xbox / PS4 / Generic USB controller

---

## 💻 Software & Tools

- Python 3.8
- DonkeyCar (v5.x)
- TensorFlow / PyTorch (for training)
- Visual Studio Code (for development)
- Git & GitHub

---

## ⚙️ Setup Environment (PC)

```bash
# Create virtual environment
python3 -m venv env --system-site-packages
source env/bin/activate

# Install dependencies
pip install --upgrade pip setuptools wheel
git clone https://github.com/autorope/donkeycar
cd donkeycar
git checkout release_5_0
pip install -e .[pc]

# Create project folder
donkey createcar --path mycar
```

---

## 🧠 Training Model

```bash
# After collecting data in mycar/data/
donkey train --tub data --model models/mypilot.tflite
```

---

## 🚗 Run The Car

```bash
python manage.py drive
```

Modes:  
- Manual (Joystick)
- Autonomous (using trained model)

---

## 📁 Folder Structure

```
mycar/
├── config.py           # Main settings for vehicle
├── manage.py           # Entry point for running the car
├── custom_parts.py     # Custom logic (optional)
├── models/             # Folder for trained models
└── data/               # Folder for collected driving data
```

---

## 📌 Notes

- Do not upload `models/` and `data/` folders to GitHub (they may be large/private)
- Keep your calibration values safe in `config.py`
- Check out `custom_parts.py` for advanced sensor or AI additions

---

