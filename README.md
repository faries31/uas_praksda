# 🏛️ UAS PRAKTIKUM STRUKTUR DATA & ALGORITMA
[![GitHub](https://badgen.net/badge/icon/github?icon=github&label)](https://github.com)[![Visual Studio](https://badgen.net/badge/icon/visualstudio?icon=visualstudio&label)](https://visualstudio.microsoft.com)   ![Google Chrome](https://img.shields.io/badge/Google%20Chrome-4285F4?style=for-the-badge&logo=GoogleChrome&logoColor=white)![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white)![Windows 11](https://img.shields.io/badge/Windows%2011-%230079d5.svg?style=for-the-badge&logo=Windows%2011&logoColor=white)

##  💻 KELOMPOK III : Sistem Analisis dan Perbandingan Gaji Berdasarkan Gender untuk Mengidentifikasi Ketimpangan Upah
1. MUHAMMAD RAFIE AL GHIFARI (250810701100013)
2. MUHAMMAD FARIS ZUFAR      (250810701100058)
3. THAHIRATUL FARHATI (250810701100010)
4. M. RAFA NUGRAHA (250810701100096)
---

## 📶 Fitur Utama Aplikasi

1. **Validasi Input Kuat:** Membatasi jumlah input karyawan secara dinamis dengan rentang aman 1 hingga 50 data.
2. **Analisis Kesenjangan Gaji Otomatis:** Menghitung rata-rata gaji per gender dan menganalisis persentase ketimpangan pendapatan menggunakan rumus:
   $$Selisih\% = \left| \frac{Rata_L - Rata_P}{Rata_{tertinggi}} \right| \times 100\%$$
3. **Format Rupiah Realistis:** Mengonversi data integer mentah menjadi format mata uang Rupiah yang rapi (misal: `Rp2.500.000`).

---
## 📊 Rumus Persentase Kesenjangan Gaji

Persentase kesenjangan dihitung menggunakan formula **Gender Pay Gap** standar:

$$
\text{Kesenjangan (\%)} = \frac{\text{Rata-rata Gaji Tertinggi} - \text{Rata-rata Gaji Terendah}}{\text{Rata-rata Gaji Tertinggi}} \times 100\%
$$

> Penyebut selalu menggunakan **rata-rata gender yang lebih tinggi**, sehingga hasil persentase merepresentasikan seberapa jauh gender dengan gaji lebih rendah tertinggal dari yang tertinggi.

---

### 🧮 Contoh Perhitungan

Misalkan terdapat data karyawan sebagai berikut:

| No | Nama | Gender | Gaji |
|----|------|--------|------|
| 01 | Budi | L | Rp5.000.000 |
| 02 | Andi | L | Rp6.000.000 |
| 03 | Siti | P | Rp4.500.000 |
| 04 | Rina | P | Rp4.000.000 |

**Langkah 1 — Hitung rata-rata per gender:**

$$\text{Rata-rata L} = \frac{5.000.000 + 6.000.000}{2} = \text{Rp5.500.000}$$

$$\text{Rata-rata P} = \frac{4.500.000 + 4.000.000}{2} = \text{Rp4.250.000}$$

**Langkah 2 — Hitung persentase kesenjangan:**

$$\text{Kesenjangan} = \frac{5.500.000 - 4.250.000}{5.500.000} \times 100\% = \frac{1.250.000}{5.500.000} \times 100\% \approx 22{,}73\%$$

**Langkah 3 — Kesimpulan:**

> Perempuan menerima rata-rata **22,73% lebih rendah** dari laki-laki.
>
> ✅ **Kesimpulan: Terdapat kesenjangan gaji berdasarkan gender.**

---
### 📟 Implementasi dalam Kode (C)

```c
// Jika rata-rata laki-laki lebih tinggi:
selisihPersen = ((rataL - rataP) / rataL) * 100;

// Jika rata-rata perempuan lebih tinggi:
selisihPersen = ((rataP - rataL) / rataP) * 100;
```

## 🧠 Implementasi Struktur Data & Algoritma

Sebagai core dari praktikum Strukdat, aplikasi ini menerapkan 3 algoritma utama untuk manipulasi *Array of Struct*:

| Fungsi / Algoritma | Jenis Alogaritma | Berdasarkan Parameter | Deskripsi |
| :--- | :--- | :--- | :--- |
| `selectionSort()` | **Sorting** | Gaji (`int`) | Mengurutkan data karyawan dari gaji terkecil (*ascending*) ke terbesar untuk memenuhi prasyarat pencarian biner. |
| `linearSearch()` | **Searching** | Nama (`char[]`) | Mencari data karyawan berdasarkan nama dengan menelusuri array satu per satu (efektif untuk data tidak terurut). |
| `binarySearch()` | **Searching** | Gaji (`int`) | Mencari data karyawan dengan membagi dua ruang pencarian secara efisien (bekerja setelah data diurutkan oleh Selection Sort). |


---

## 💻 Alur Tampilan Aplikasi (Preview)

```
Jumlah karyawan (maksimal 50): 3

[Data Karyawan Ke-1]
Nama         : Budi
Gender (L/P) : L
Gaji         : 5000000

[Data Karyawan Ke-2]
Nama         : Siti
Gender (L/P) : P
Gaji         : 4500000

[Data Karyawan Ke-3]
Nama         : Rina
Gender (L/P) : P
Gaji         : 4000000

======================= HASIL ANALISIS =======================
* Rata-rata gaji laki-laki     : Rp5.000.000
* Rata-rata gaji perempuan     : Rp4.250.000
* Persentase kesenjangan gaji  : 15.00%
Perempuan menerima rata-rata 15.00% lebih rendah dari laki-laki.
Kesimpulan: Terdapat kesenjangan gaji berdasarkan gender.
==============================================================

=========================================
       DATA KARYAWAN TERURUT
=========================================
No   Nama       Gender   Gaji
-----------------------------------------
01   Rina       P        Rp4.000.000
02   Siti       P        Rp4.500.000
03   Budi       L        Rp5.000.000

Masukkan nama yang dicari: Siti

Data ditemukan:
Nama   : Siti
Gender : P
Gaji   : Rp4.500.000

Masukkan gaji yang dicari: 5000000

Data ditemukan:
Nama   : Budi
Gender : L
Gaji   : Rp5.000.000

---
```

## 🔄 Alur Lengkap Jalannya Program Dan Penjelasan
```c
1. Bagian Library & Definisi Struktur Data (`Struct`)
#include <stdio.h>
#include <string.h>

struct Karyawan {
    char nama[50];
    char gender;
    int gaji;
};
Penjelasan:
    #include <stdio.h> & #include <string.h>
Library wajib dalam bahasa C. stdio.h digunakan untuk menangani fungsi input-output standar seperti printf dan scanf. Sedangkan string.h wajib di-import karena program menggunakan fungsi strcmp untuk membandingkan kesamaan teks (nama).

struct Karyawan
    Ini adalah struktur data non-primitif (tipe data bentukan). Kita membuat sebuah objek baru bernama Karyawan yang bertindak sebagai wadah untuk mengelompokkan 3 variabel berbeda jenis (nama, gender, gaji) menjadi satu kesatuan data utuh.

2. Fungsi Pengurutan (`Selection Sort`)

void selectionSort(struct Karyawan data[], int n) {
    int i, j, min;
    struct Karyawan temp;

    for(i = 0; i < n - 1; i++) {
        min = i;
        for(j = i + 1; j < n; j++) {
            if(data[j].gaji < data[min].gaji) {
                min = j;
            }
        }
        temp = data[i];
        data[i] = data[min];
        data[min] = temp;
    }
}
Penjelasan Teknis:
    Logika Kerja: Algoritma ini menyisir data untuk mencari elemen dengan nilai gaji paling kecil di dalam array, kemudian menukarnya (swap) dengan elemen yang berada di posisi paling depan (i). Proses ini diulang terus untuk posisi berikutnya hingga seluruh data terurut.

    Variabel temp: Berfungsi sebagai tempat penitipan atau penampung sementara bagi objek struct Karyawan saat proses penukaran terjadi agar data asli tidak terhapus atau tertimpa.

    Tujuan: Mengurutkan data karyawan berdasarkan nominal gajinya secara ascending (dari kecil ke besar).

3. Fungsi Pencarian Nama (Linear Search)

int linearSearch(struct Karyawan data[], int n, char namaCari[]) {
    int i;
    for(i = 0; i < n; i++) {
        if(strcmp(data[i].nama, namaCari) == 0) {
            return i; // Mengembalikan indeks jika ketemu
        }
    }
    return -1; // Mengembalikan -1 jika tidak ketemu
}

    📂Penjelasan Teknis:
    Logika Kerja: Program melakukan perulangan dari indeks 0 sampai indeks terakhir (n-1) untuk mencocokkan nama yang dicari dengan nama karyawan di dalam data satu per satu secara berurutan.

    strcmp(data[i].nama, namaCari) == 0: Fungsi bawaan dari library <string.h>. Jika kedua teks yang dibandingkan bernilai persis sama (identik), fungsi ini akan mengembalikan angka 0.

    Output Fungsi: Jika data ditemukan, fungsi akan langsung mengirimkan nomor posisi indeksnya (return i). Namun jika perulangan selesai dan data tidak ada yang cocok, fungsi akan mengembalikan nilai -1.

4. Fungsi Pencarian Gaji (Binary Search)

int binarySearch(struct Karyawan data[], int n, int target) {
    int kiri = 0;
    int kanan = n - 1;

    while(kiri <= kanan) {
        int tengah = (kiri + kanan) / 2;

        if(data[tengah].gaji == target) {
            return tengah;
        }
        else if(data[tengah].gaji < target) {
            kiri = tengah + 1;
        }
        else {
            kanan = tengah - 1;
        }
    }
    return -1;
}

    📂 Penjelasan Teknis:
    Logika Kerja: Teknik pencarian efisien dengan cara membelah wilayah array menjadi dua bagian terus-menerus:

    Menghitung nilai titik tengah. Jika nilai di posisi tengah sama dengan target, pencarian selesai.

    Jika nilai tengah lebih kecil dari target, pencarian dialihkan penuh ke sisi kanan dengan menggeser batas kiri = tengah + 1.

    Jika nilai tengah lebih besar dari target, pencarian dialihkan ke sisi kiri dengan menggeser batas kanan = tengah - 1.

    Syarat Mutlak: Fungsi Binary Search ini hanya dapat bekerja dan menghasilkan data yang valid karena array data sebelumnya sudah diproses dan diurutkan oleh fungsi selectionSort.

5. Fungsi Format Mata Uang (tampilRupiah)

void tampilRupiah(int angka) {
    if (angka >= 1000000)
        printf("Rp%d.%03d.%03d", angka / 1000000, (angka / 1000) % 1000, angka % 1000);
    else if (angka >= 1000)
        printf("Rp%d.%03d", angka / 1000, angka % 1000);
    else
        printf("Rp%d", angka);
}

    📂 Penjelasan Teknis:
    ogika Kerja: Fungsi pembantu (helper) untuk memformat angka mentah biasa (integer) agar tampil menjadi format akuntansi mata uang Rupiah yang mudah dibaca manusia.

    %03d: Sebuah penanda format (format specifier) yang memaksa compiler untuk mencetak angka minimal sebanyak 3 digit angka. Jika hasil matematika di bawah 3 digit (misal angka 5), sistem akan otomatis menambahkan nol di depannya sehingga tercetak 005. Pemecahan nominal jutaan dan ribuan dilakukan memanfaatkan operasi pembagian (/) dan sisa bagi (%).

6. Fungsi Utama (main)
    Di dalam fungsi utama, terdapat tiga blok kerja besar yang dieksekusi secara berurutan:

    A. Validasi Input do-while

    do {
        printf("Jumlah karyawan (maksimal 50): ");
        scanf("%d", &n);
        if(n < 1 || n > 50) {
        printf("Jumlah karyawan harus antara 1 sampai 50!\n");
        }
    } while(n < 1 || n > 50);
    Keterangan: Blok ini menggunakan struktur perulangan do-while untuk menjamin interaksi pengguna yang aman. Program tidak akan mengizinkan user melangkah ke tahap pengisian data sebelum memasukkan angka jumlah karyawan yang valid di rentang 1 sampai 50 (sesuai batas alokasi memori array).

    B. Kalkulasi & Analisis Kesenjangan Gaji

    for(i = 0; i < n; i++) {
    if(data[i].gender == 'L' || data[i].gender == 'l') {
        totalL += data[i].gaji;
        jumlahL++;
    }
    // ... Logika yang sama diimplementasikan untuk gender 'P'
    }
        Penyaringan Data: Program melakukan looping untuk mengumpulkan total komparatif. Gaji karyawan laki-laki dan perempuan dipisah ke variabel penampung masing-masing untuk dihitung total nominal pendapatan beserta total kepala (jumlah orang).

        Type Casting (float): Baris rataL = (float) totalL / jumlahL; sengaja disisipkan tipe desimal (float) agar pembagian angka bulat tidak dipotong ke bawah oleh compiler C, sehingga angka desimal di belakang koma hasil rata-rata tetap akurat.

        Persentase Kesenjangan: Program membandingkan nilai rata-rata tertinggi, menghitung selisih persentase ketimpangan pendapatannya, dan secara otomatis mencetak kesimpulan kesetaraan gender di layar terminal.

    C. Urutan Eksekusi Akhir Proyek
        Program memanggil fungsi selectionSort(data, n) untuk merapikan seluruh isi data.

        Program mencetak ringkasan laporan dalam bentuk tabel terstruktur menggunakan fungsi format tampilRupiah.

        Program mengeksekusi pencarian string menggunakan fungsi linearSearch.

        Program menutup rangkaian dengan pencarian nilai numerik efisien via fungsi binarySearch.


