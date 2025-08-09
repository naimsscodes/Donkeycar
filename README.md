# 🚗 DonkeyCar Autonomous RC

DonkeyCar Autonomous RC adalah projek kereta kawalan jauh yang menggunakan **Python**, **Machine Learning**, dan **Computer Vision** untuk memandu sendiri.  
Direka supaya **mudah difahami** oleh semua peringkat — dari pelajar sekolah hingga eksekutif.

---

## 📦 Installation

1. **Clone repository**
```bash
git clone https://github.com/username/donkeycar.git
cd donkeycar
Arahan ini akan memuat turun salinan projek DonkeyCar daripada GitHub dan masuk ke dalam folder projek.

Install dependencies

bash
Copy code
pip install -r requirements.txt
Arahan ini akan memasang semua dependencies (pustaka Python) yang diperlukan untuk menjalankan projek.

Setup environment

bash
Copy code
python manage.py createcar --path ~/mycar
Arahan ini akan membuat folder projek kereta (mycar) yang mengandungi semua fail konfigurasi.

Run simulator (optional)

bash
Copy code
python manage.py drive
Arahan ini akan memulakan driving interface untuk mengawal kereta sama ada secara manual atau menggunakan model.

🏎️ Training the Model
Collect Data

bash
Copy code
python manage.py drive
Pandulah kereta secara manual untuk mengumpul data gambar track. Data akan disimpan di dalam folder ~/mycar/data.

Train Model

bash
Copy code
python manage.py train --tub <data-folder> --model models/mypilot.h5
Arahan ini akan melatih model machine learning menggunakan data yang telah dikumpul.

Test Model

bash
Copy code
python manage.py drive --model models/mypilot.h5
Arahan ini akan memandu kereta secara automatik menggunakan model yang telah dilatih.

