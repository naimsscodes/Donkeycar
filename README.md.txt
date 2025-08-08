# Donkeycar Autonomous Vehicle

This is a fully autonomous RC car built using the Donkeycar framework and Raspberry Pi 4.

# Donkeycar Autonomous RC Project

This is a full-stack autonomous RC car project using Donkeycar framework, Raspberry Pi 4, Python, and a trained deep learning model.

---

## 🚀 Features

- RC car with Raspberry Pi + camera + PCA9685 servo controller
- Manual & autonomous driving modes
- Tub data collection (images + joystick input)
- Model training (CNN using TensorFlow)
- Full track testing with real-time inference

---

## ⚙️ Environment Setup

### 📍 On PC (Training Machine)

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

# Create project
donkey createcar --path ~/mycar

# System update
sudo apt-get update --allow-releaseinfo-change
sudo apt-get upgrade

# Setup env
python3 -m venv env --system-site-packages
echo "source ~/env/bin/activate" >> ~/.bashrc
source ~/.bashrc

# Install Donkeycar
git clone https://github.com/autorope/donkeycar
cd donkeycar
git checkout release_5_0
pip install -e .[pi]

# Create car project folder
donkey createcar --path ~/mycar

# Calibrate steering (channel 0)
donkey calibrate --channel 0

# Calibrate throttle (channel 1)
donkey calibrate --channel 1

# Start car control (manual)
python manage.py drive

# On PC (after collecting tub data)
donkey train --tub data --model models/mypilot.tflite

# On Raspberry Pi
python manage.py drive --model models/mypilot.tflite

