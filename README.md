**Pasang Donkeycar di Linux**
Nota: Telah diuji pada **Ubuntu 20.04 LTS** dan **22.04 LTS**  

https://docs.donkeycar.com/guide/install_software/#step-2-install-software-on-donkeycar (website rasmi donkeycar)

1. **Buka aplikasi Terminal.**
2. **Pasang Miniconda Python 3.11** (64-bit).
3.**buat dalam Command Prompt**

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-py311_24.4.0-0-Linux-x86_64.sh
bash ./Miniconda3-py311_24.4.0-0-Linux-x86_64.sh
```
1 . Sediakan **persekitaran conda Donkey** anda dengan
```bash
conda create -n donkey python=3.11
conda activate donkey
```
Sekarang ada dua jenis pemasangan yang boleh dibuat.
Kebiasaannya, anda akan memilih **(*User install*)**. Selepas itu, anda akan jalankan langkah **User install**.

Kalau anda mahu **(debug)** atau **Change Source code**, anda perlu buat pemasangan yang lebih advance iaitu **Developer install**.
Namun, anda hanya boleh pilih **satu sahaja** daripada kedua-duanya.

2. **Pemasangan Pengguna (User install)**
Memandangkan anda sudah mengaktifkan *environment* donkey yang baru, anda hanya perlu taip:
```bash
pip install donkeycar[pc]
```
Ini akan memasang keluaran (*release*) terkini.
Nota: Jika anda menggunakan **ZSH**, anda perlu *escape* simbol **\[** dan **]**, iaitu:

```bash
pip install donkeycar\[pc\]
```
3. **Developer install**
Kat sini kau boleh pilih nak pasang branch atau tag mana, dan kau pun boleh edit atau debug kod tu sekali, dengan cara download source code dari GitHub.

Buat satu folder projek yang kau nak guna sebagai “kepala” untuk semua projek kau, masuk dalam folder tu, lepastu download dan install donkeycar dari GitHub.(buat line by line)
```bash
mkdir projects
cd projects
git clone https://github.com/autorope/donkeycar
cd donkeycar
git checkout main
pip install -e .[pc]
```
Nota: Kalau kau guna ZSH (kau akan tahu kalau kau guna), kau tak boleh terus run pip install -e .[pc].
Kau kena escape bracket tu dan run:
```bash
pip install -e .\[pc\]
```
4.Kalau ini bukan kali pertama kau install, update Conda dulu dan buang donkey lama.
```bash
conda update -n base -c defaults conda
conda env remove -n donkey
```
5.Versi TensorFlow yang baru dah siap dibina dengan sokongan GPU.
Kalau kau ada **GPU Nvidia**, pasang **Cuda 12** ikut arahan yang ada dekat laman web Nvidia.
https://developer.nvidia.com/cuda-toolkit-archive

**Pasang Coral Edge TPU Compiler (Pilihan)**
Kalau kau ada **Google Coral Edge TPU**, kau mungkin nak compile model. Untuk tu, kau kena pasang `edgetpu_compiler` executable. Ikut je arahan daripada pihak mereka.

6.**Konfigurasi PyTorch guna GPU (Pilihan) – hanya untuk kad grafik Nvidia**
Kalau kau guna kad **Nvidia**, pastikan kau update driver ke versi paling baru dan pasang **Cuda SDK**.
Selain tu, kau kena ubah kod di beberapa tempat supaya boleh guna GPU — jadi kau memang kena buat **Developer install**.
```bash
conda install cudatoolkit=11 -c pytorch
```
7. Create your local working dir:
```bash
donkey createcar --path ~/mycar
```
---------------------------------------------------------------------------------------------------------------------------------------------------------

**DonkeyCar Setup Guide**
**1. Software to Install**

Pastikan anda install aplikasi berikut pada PC anda:

Visual Studio Code (https://code.visualstudio.com/docs/setup/linux)

Raspberry Pi Imager (https://www.raspberrypi.com/software/)
---------------------------------------------------------------------------------------------------------------------------------------------------------
**2. Visual Studio Code Setup**
Pasang Visual Studio Code.

Buka Visual Studio Code dan pergi ke tab Extensions.

Cari dan pasang extension Remote - SSH.
---------------------------------------------------------------------------------------------------------------------------------------------------------
**3. Raspberry Pi Imager Setup**
Pasang Raspberry Pi Imager.

Buka aplikasi Raspberry Pi Imager.

Klik Choose Device dan pilih Raspberry Pi 4.

Klik Choose OS → Raspberry Pi OS (Other) →
Pilih Raspberry Pi OS (Legacy, 64-bit) Full (Debian Bullseye Version).

Klik Choose Storage dan pilih memory card untuk tulis OS image.
---------------------------------------------------------------------------------------------------------------------------------------------------------
**4. Configure OS Image Settings (Raspberry Pi Imager)**
Klik Next → Edit Settings:

Di tab General:

Aktifkan Set username and password

Aktifkan Configure wireless LAN

Aktifkan Set locale settings

Masukkan username, password, Wi-Fi, timezone, dan keyboard layout.

Tukar ke tab Services:

Aktifkan SSH

Pilih Use password authentication

Klik Save untuk simpan tetapan.

Klik Yes untuk mula tulis OS ke memory card.

Jika diminta format memory card, pilih Yes.
---------------------------------------------------------------------------------------------------------------------------------------------------------
**5. Install DonkeyCar on Host PC (Linux)**
nstall virtualenv:
```bash
sudo apt install python3.8-venv
```
Buat folder environment Python dan aktifkan:(buat line by line(jangan copy semua sekali))
```bash
mkdir <your_folder_name>
cd <your_folder_name>
python3 -m venv <your_environment_folder_name> --system-site-packages
source <your_environment_folder_name>/bin/activate
```
Periksa environment aktif (nama environment akan muncul di terminal).

Upgrade pip dan pasang keperluan:
```bash
pip install --upgrade pip setuptools wheel
```
Clone DonkeyCar dan pasang:(buat line by line(jangan copy semua sekali))
```bash
mkdir ~/projects
cd ~/projects
git clone https://github.com/autorope/donkeycar
cd donkeycar
git checkout release_5_0
pip install -e .[pc]
```
Buat folder projek DonkeyCar:
```bash
donkey createcar --path ~/<your_folder_name>/mycar
```
Gantikan <your_folder_name> ikut folder projek anda.
---------------------------------------------------------------------------------------------------------------------------------------------------------
***6. Setup DonkeyCar on Raspberry Pi**
Masukkan memory card dengan OS yang dibakar ke dalam Raspberry Pi dan boot.

Buka terminal dan update sistem:
```bash
sudo apt-get update --allow-releaseinfo-change
sudo apt-get upgrade
```
Konfigurasikan Raspberry Pi:
```bash
sudo raspi-config
```
Pergi ke Interfacing Options → aktifkan I2C.

Pergi ke Advanced Options → pilih Expand Filesystem.
Reboot Raspberry Pi:
```bash
sudo reboot
```
---------------------------------------------------------------------------------------------------------------------------------------------------------
***7. Set Up DonkeyCar Environment on Raspberry Pi**
Buka terminal dan buat virtual environment Python:
```bash
python3 -m venv env --system-site-packages
```
Set supaya environment aktif secara automatik semasa startup:
```bash
echo "source ~/env/bin/activate" >> ~/.bashrc
source ~/.bashrc
```
Pasang keperluan sistem:
```bash
sudo apt install libcap-dev libhdf5-dev libhdf5-serial-dev
pip install --upgrade setuptools wheel pip
```
---------------------------------------------------------------------------------------------------------------------------------------------------------
**8. Install DonkeyCar Python Code on Raspberry Pi**
Clone dan pasang DonkeyCar:
```bash
mkdir ~/projects
cd ~/projects
git clone https://github.com/autorope/donkeycar
cd donkeycar
git checkout release_5_0
pip install -e .[pi]
```
Verify TensorFlow:
```bash
python -c "import tensorflow; print(tensorflow.__version__)"
```
Buat folder projek DonkeyCar:
```bash
donkey createcar --path ~/mycar
```
---------------------------------------------------------------------------------------------------------------------------------------------------------
**DonkeyCar App & Calibration Guide**
**1. Connect to Raspberry Pi via SSH**
Selepas reboot Raspberry Pi 4, buka terminal pada Pi dan taip:
```bash
ifconfig
```
Cari alamat IP di bawah wlan0 pada inet dan catat alamat IP tersebut.

Pada PC, buka terminal dan sambungkan ke Raspberry Pi melalui SSH:
```bash
ssh <your_pi_username>@<raspberry_pi_ip_address>
```
Tekan Enter. Jika berjaya, terminal PC kini tersambung ke Raspberry Pi.
---------------------------------------------------------------------------------------------------------------------------------------------------------
**2. Pasang I2C Tools & Sahkan Sambungan Servo Driver**
Pada Raspberry Pi melalui SSH, pasang I2C tools:
```bash
sudo apt-get install -y i2c-tools
```
Jalankan arahan untuk kesan peranti I2C:
```bash
sudo i2cdetect -y 1
```
Anda akan lihat grid dengan alamat I2C (biasanya 0x40) jika PCA9685 servo driver disambungkan dengan betul.
---------------------------------------------------------------------------------------------------------------------------------------------------------
**3. Steering Calibration (Kalibrasi Stereng)**
Dalam terminal Raspberry Pi (SSH), jalankan kalibrasi stereng:
```bash
donkey calibrate --channel 0 --bus=
```
Masukkan nilai PWM antara 0 hingga 1500 untuk cari nilai paling kiri dan paling kanan stereng.

Buka Visual Studio Code dan sambungkan ke Raspberry Pi melalui Remote - SSH.

Buka folder projek mycar di direktori home Raspberry Pi.

Dalam folder mycar, buka fail config.py.

Dalam config.py:

Pergi ke baris 83 untuk PWM_STEERING_THROTTLE

Pergi ke baris 98 untuk I2C_SERVO

Kemas kini nilai berikut mengikut kalibrasi:

STEERING_RIGHT_PWM

STEERING_LEFT_PWM
---------------------------------------------------------------------------------------------------------------------------------------------------------
**4.Throttle Calibration (Kalibrasi Throttle)**
Dalam terminal Raspberry Pi (SSH), jalankan kalibrasi throttle:
```bash
donkey calibrate --channel 1 --bus=
```
Masukkan nilai PWM antara 0 hingga 1500 untuk kenal pasti nilai throttle ke hadapan, berhenti (center), dan reverse.

Buka Visual Studio Code dan sambungkan ke Raspberry Pi via Remote - SSH.

Buka folder mycar di direktori home dan buka fail config.py.

Dalam config.py:

Pergi ke baris 83 (PWM_STEERING_THROTTLE)

Pergi ke baris 98 (I2C_SERVO)

Kemas kini nilai berikut mengikut kalibrasi:

THROTTLE_FORWARD_PWM

THROTTLE_STOPPED_PWM

THROTTLE_REVERSE_PWM
---------------------------------------------------------------------------------------------------------------------------------------------------------
**DonkeyCar Web Controller (WebView) Setup**
**1. Mulakan Web Controller**
Pada terminal Raspberry Pi, pergi ke folder projek DonkeyCar:
```bash
cd ~/mycar/
```
Untuk mulakan web server dengan sokongan joystick atau RC controller, jalankan:
```bash
python manage.py drive --js
```
Jika hanya menggunakan kawalan papan kekunci (keyboard), jalankan:
```bash
python manage.py drive
```
---------------------------------------------------------------------------------------------------------------------------------------------------------
**2. Akses Web Controller**
Pada PC atau telefon, buka browser web dan pergi ke url bar:
```bash
http://<your_pi_ip_address>:8888
```






























