Task Breakdown:

Task 1: Setup notebook dan data preparation

- Buat file IQA_CNN_Model.ipynb
- Import libraries (tensorflow, numpy, matplotlib, seaborn, sklearn)
- Definisikan path dataset dan gabungkan 3 folder terpisah menjadi satu unified dataset menggunakan tf.keras.utils.image_dataset_from_directory dengan custom loading yang menggabungkan train/valid/test dari
  ketiga folder class
- Verifikasi jumlah gambar per kelas dan tampilkan distribusi
- Tampilkan sample gambar dari masing-masing kelas
- Demo: Notebook berjalan, menampilkan distribusi data dan sample images

  Task 2: Data loading dan preprocessing pipeline

- Buat data generator yang menggabungkan 3 folder terpisah (Normal/train, Blur/train, Lowlight/train) menjadi satu training set dengan label 0,1,2
- Lakukan hal yang sama untuk valid dan test
- Normalisasi pixel ke [0,1]
- Tambahkan prefetch dan cache untuk performa
- Demo: Data pipeline berjalan, batch shape terverifikasi (batch_size, 320, 320, 3)

  Task 3: Build CNN model architecture

- Desain arsitektur CNN ringan (cocok untuk edge device):
  - 4 blok Conv2D + BatchNorm + MaxPool + Dropout
  - GlobalAveragePooling
  - Dense layers dengan Dropout
  - Output: 3 neurons softmax

- Compile model dengan Adam optimizer, categorical crossentropy, dan metrics accuracy
- Tampilkan model summary
- Demo: Model summary terlihat, total parameters reasonable untuk edge deployment

  Task 4: Training dengan anti-overfitting strategy

- Implementasi callbacks: EarlyStopping, ReduceLROnPlateau, ModelCheckpoint
- Train model dengan epochs yang cukup (max 30, early stop patience 5)
- Monitor val_loss dan val_accuracy
- Demo: Training berjalan, loss menurun, tidak ada tanda overfitting signifikan

  Task 5: Evaluasi lengkap dan visualisasi

- Plot training & validation accuracy/loss curves
- Evaluasi pada test set
- Generate confusion matrix dengan heatmap
- Classification report (precision, recall, f1-score per kelas)
- Tampilkan sample predictions dengan gambar asli + predicted vs actual label
- Demo: Semua visualisasi tampil, akurasi test set terlihat

  Task 6: Export model (.h5 dan TFLite)

- Save model ke format .h5
- Convert ke TFLite (quantized untuk edge device)
- Verifikasi TFLite model bisa melakukan inference
- Tampilkan ukuran file model
- Demo: File iqa_model.h5 dan iqa_model.tflite tersimpan, inference TFLite berhasil

  Does this plan look good, or would you like me to adjust anything?
