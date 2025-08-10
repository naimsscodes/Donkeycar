**Pasang Donkeycar di Linux**
Nota: Telah diuji pada **Ubuntu 20.04 LTS** dan **22.04 LTS**

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













