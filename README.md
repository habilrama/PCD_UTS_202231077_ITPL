# UTS PENGOLAHAN CITRA DIGITAL

Nama    : Habil Rama Taufany

NIM     : 202231077

Kelas   : A
# _____________________________________
## 1. DETEKSI WARNA PADA CITRA
Kodingan yang saya gunakan untuk menjawab pertanyaan nomor satu seperti berikut:

import cv2

import matplotlib.pyplot as plt

import numpy as np

img = cv2.imread("habil.jpg")

plt.imshow(rgb)

img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

merah = img_rgb[:,:,0]

hijau = img_rgb[:,:,1]

biru = img_rgb[:,:,2]

fig, axis = plt.subplots(1, 3, figsize=(10,10))

ax = axis.ravel()

ax[0].imshow(merah, cmap='gray')

ax[0].set_title('Red Color')

ax[1].imshow(hijau, cmap='gray')

ax[1].set_title('Green Color')

ax[2].imshow(biru, cmap='gray')

ax[2].set_title('Blue Color')

plt.show()


#### penjelasan mengenai kodingan:

-import cv2: Baris ini mengimpor perpustakaan OpenCV, yang banyak digunakan untuk tugas-tugas visi komputer seperti pemrosesan dan analisis gambar.

-import matplotlib.pyplot as plt: Baris ini mengimpor modul perpustakaan Matplotlib pyplot, yang digunakan untuk membuat visualisasi seperti plot dan gambar.

-import numpy as np: Baris ini mengimpor perpustakaan NumPy, yang menyediakan kemampuan manipulasi array yang kuat yang sering digunakan dalam komputasi ilmiah dan pemrosesan gambar.

-img = cv2.imread("habil.jpg"): Baris ini membaca gambar dari file bernama "habil.jpg" menggunakan imreadfungsi dari OpenCV. Gambar yang dimuat disimpan dalam variabel img. Penting untuk dicatat bahwa OpenCV menyimpan gambar dalam format BGR (Biru, Hijau, Merah) secara default, yang berbeda dari format RGB biasa yang digunakan di perpustakaan lain seperti Matplotlib.

-img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB): Baris ini (dikomentari) mengubah gambar dari format BGR ke RGB jika perlu. Matplotlib mengharapkan gambar dalam format RGB, jadi menghapus komentar pada baris ini akan memastikan warna ditampilkan dengan benar saat menggunakan plt.imshow.

-merah = img_rgb[:,:,0]: Baris ini mengekstrak saluran merah dari img_rgbgambar (dengan asumsi saluran tersebut telah dikonversi ke RGB). Notasi [:,:,0]pengindeksan memilih semua baris dan kolom ( :,:) dari dimensi ketiga (yang terakhir, yang mewakili saluran warna) dan mengekstrak nilai pada indeks 0, yang sesuai dengan saluran merah dalam format RGB.

-hijau = img_rgb[:,:,1]: Baris ini mengekstrak saluran hijau dengan cara yang sama, memilih nilai pada indeks 1.

-biru = img_rgb[:,:,2]: Baris ini mengekstrak saluran biru, memilih nilai pada indeks 2.

-fig, axis = plt.subplots(1, 3, figsize=(10,10)): Baris ini membuat gambar ( fig) dan kisi subplot ( axis) dengan 1 baris dan 3 kolom menggunakan fungsi Matplotlib subplots. Argumen tersebut figsizemenetapkan ukuran gambar menjadi 10 inci kali 10 inci.

-ax = axis.ravel(): Baris ini meratakan kisi subplot ( axis) menjadi array satu dimensi ( ax) sehingga Anda dapat dengan mudah mengakses setiap subplot untuk pembuatan plot.

-ax[0].imshow(merah, cmap='gray'): Baris ini menampilkan saluran merah yang diekstraksi ( merah) pada subplot pertama ( ax[0]) menggunakan fungsi Matplotlib imshow. Argumennya cmap='gray'menetapkan bahwa gambar harus ditampilkan dalam skala abu-abu.

-ax[0].set_title('Red Color'): Baris ini menetapkan judul subplot pertama menjadi "Warna Merah".

-Baris serupa ( ax[1].imshow(hijau, cmap='gray'), ax[1].set_title('Green Color'), ax[2].imshow(biru, cmap='gray'), ax[2].set_title('Blue Color')) menampilkan saluran hijau dan biru pada subplot yang tersisa dan menetapkan judulnya masing-masing.

-plt.show(): Baris ini menampilkan gambar yang dibuat, yang berisi ketiga subplot yang menunjukkan saluran warna individual pada gambar.


## 2. CARILAH DAN URUTKAN AMBANG BATAS TERKECIL SAMAPAI DENGAN TERBESAR
Kodingan yang saya gunakan untuk menjawab pertanyaan nomor dua adalah seperti berikut:

import cv2
import numpy as np
import matplotlib.pyplot
import matplotlib.pyplot as plt

img = cv2.imread('habil.jpg')

hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

biru_1 = np.array([100, 43, 46])
biru_2 = np.array([130, 255, 255])
merah_1 = np.array([160, 43, 46])
merah_2 = np.array([180, 255, 255])
hijau_1 = np.array([36, 43, 46])
hijau_2 = np.array([70, 255, 255])

biru_mask = cv2.inRange(hsv, biru_1, biru_2)
merah_mask = cv2.inRange(hsv, merah_2, merah_2)
hijau_mask = cv2.inRange(hsv, hijau_1, hijau_2)

biru_piksel = cv2.bitwise_and(img, img, mask=biru_mask)
merah_piksel = cv2.bitwise_and(img, img, mask=merah_mask)
hijau_piksel = cv2.bitwise_and(img, img, mask=hijau_mask)

plt.figure(figsize=(10, 5))

 Red-Green-Blue:

plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Red-Green-Blue')
plt.axis('off')

Blue:

plt.subplot(2, 2, 2)
plt.imshow(cv2.cvtColor(biru_piksel, cv2.COLOR_BGR2RGB))
plt.title('Blue')
plt.axis('off')

Red:

plt.subplot(2, 2, 3)
plt.imshow(cv2.cvtColor(merah_piksel, cv2.COLOR_BGR2RGB))
plt.title('Red')
plt.axis('off')

None:

plt.subplot(2, 2, 4)
plt.imshow(cv2.cvtColor(hijau_piksel, cv2.COLOR_BGR2RGB))
plt.title('None')
plt.axis('off')
plt.tight_layout()
plt.show()

### penjelasan mengenai kodingan:

-import cv2: Baris ini mengimpor perpustakaan OpenCV, yang banyak digunakan untuk tugas-tugas visi komputer seperti pemrosesan dan analisis gambar.

-import matplotlib.pyplot as plt: Baris ini mengimpor modul perpustakaan Matplotlib pyplot, yang digunakan untuk membuat visualisasi seperti plot dan gambar.

-import numpy as np: Baris ini mengimpor perpustakaan NumPy, yang menyediakan kemampuan manipulasi array yang kuat yang sering digunakan dalam komputasi ilmiah dan pemrosesan gambar.

-img = cv2.imread("nama.jpg"): Baris ini membaca gambar dari file bernama "nama.jpg" menggunakan imreadfungsi dari OpenCV. Gambar yang dimuat disimpan dalam variabel img. Penting untuk dicatat bahwa OpenCV menyimpan gambar dalam format BGR (Biru, Hijau, Merah) secara default, yang berbeda dari format RGB biasa yang digunakan di perpustakaan lain seperti Matplotlib.

-img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB): Baris ini (dikomentari) mengubah gambar dari format BGR ke RGB jika perlu. Matplotlib mengharapkan gambar dalam format RGB, jadi menghapus komentar pada baris ini akan memastikan warna ditampilkan dengan benar saat menggunakan plt.imshow.

-merah = img_rgb[:,:,0]: Baris ini mengekstrak saluran merah dari img_rgbgambar (dengan asumsi saluran tersebut telah dikonversi ke RGB). Notasi [:,:,0]pengindeksan memilih semua baris dan kolom ( :,:) dari dimensi ketiga (yang terakhir, yang mewakili saluran warna) dan mengekstrak nilai pada indeks 0, yang sesuai dengan saluran merah dalam format RGB.

-hijau = img_rgb[:,:,1]: Baris ini mengekstrak saluran hijau dengan cara yang sama, memilih nilai pada indeks 1.

-biru = img_rgb[:,:,2]: Baris ini mengekstrak saluran biru, memilih nilai pada indeks 2.

-fig, axis = plt.subplots(1, 3, figsize=(10,10)): Baris ini membuat gambar ( fig) dan kisi subplot ( axis) dengan 1 baris dan 3 kolom menggunakan fungsi Matplotlib subplots. Argumen tersebut figsizemenetapkan ukuran gambar menjadi 10 inci kali 10 inci.

-ax = axis.ravel(): Baris ini meratakan kisi subplot ( axis) menjadi array satu dimensi ( ax) sehingga Anda dapat dengan mudah mengakses setiap subplot untuk pembuatan plot.

-ax[0].imshow(merah, cmap='gray'): Baris ini menampilkan saluran merah yang diekstraksi ( merah) pada subplot pertama ( ax[0]) menggunakan fungsi Matplotlib imshow. Argumennya cmap='gray'menetapkan bahwa gambar harus ditampilkan dalam skala abu-abu.

-ax[0].set_title('Red Color'): Baris ini menetapkan judul subplot pertama menjadi "Warna Merah".

-Baris serupa ( ax[1].imshow(hijau, cmap='gray'), ax[1].set_title('Green Color'), ax[2].imshow(biru, cmap='gray'), ax[2].set_title('Blue Color')) menampilkan saluran hijau dan biru pada subplot yang tersisa dan menetapkan judulnya masing-masing.

-plt.show(): Baris ini menampilkan gambar yang dibuat, yang berisi ketiga subplot yang menunjukkan saluran warna individual pada gambar.