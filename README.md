# 📱 Praktikum Flutter — Manajemen Plugin

**Mata Kuliah:** Pemrograman Mobile
**Nama:** Iga Ramadana Sahputra  
**NIM:** 2341760083  
**Kelas:** SIB 3C  
**No Absen:** 15

## **Repository:** [PMB_JS05 - Manajemen Plugin](https://github.com/igaramadana/flutter_plugin_pubdev)

---

## Langkah 1: Buat Project Baru

## ![project baru](images/1.png)

## Langkah 2: Menambahkan Plugin

```dart
flutter pub add auto_size_text
```

Plugin auto_size_text adalah package Flutter yang secara otomatis menyesuaikan ukuran font teks agar sesuai dengan batasan yang diberikan.

## Langkah 3: Buat file red_text_widget.dart

```dart
import 'package:flutter/material.dart';

class RedTextWidget extends StatelessWidget {
  const RedTextWidget({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container();
  }
}
```

## Langkah 4: Tambah Widget AutoSizeText

```dart
return AutoSizeText(
      text,
      style: const TextStyle(color: Colors.red, fontSize: 14),
      maxLines: 2,
      overflow: TextOverflow.ellipsis,
);
```

Setelah menambahkan kode diatas akan mendapatkan error karena variabel text tidak dideklarasikan
Dart Compiler Tidak Menemukan Definisi
Compiler Dart mencari variabel text dalam scope:
✅ Local variables dalam method build - Tidak ada
✅ Instance variables dalam class RedTextWidget - Tidak ada
✅ Static variables - Tidak ada
✅ Global variables - Tidak ada
❌ Result: "Undefined name 'text'"

---

## Langkah 5: Buat Variabel text dan parameter di constructor

```dart
import 'package:flutter/material.dart';
import 'package:auto_size_text/auto_size_text.dart';

class RedTextWidget extends StatelessWidget {
  final String text;

  const RedTextWidget({Key? key, required this.text}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return AutoSizeText(
      text,
      style: const TextStyle(color: Colors.red, fontSize: 14),
      maxLines: 2,
      overflow: TextOverflow.ellipsis,
    );
  }
}
```

---

## Langkah 6: Tambahkan widget di main.dart

Buka file main.dart lalu tambahkan di dalam children: pada class \_MyHomePageState

```dart
Container(
   color: Colors.yellowAccent,
   width: 50,
   child: const RedTextWidget(
             text: 'You have pushed the button this many times:',
          ),
),
Container(
    color: Colors.greenAccent,
    width: 100,
    child: const Text(
           'You have pushed the button this many times:',
          ),
),
```

---

## Output yang dihasilkan dari praktikum

![Hasil run](images/2.png)

---

## Tugas Praktikum

1. Selesaikan Praktikum tersebut, lalu dokumentasikan dan push ke repository Anda berupa screenshot hasil pekerjaan beserta penjelasannya di file README.md!
   Jawab: https://github.com/igaramadana/flutter_plugin_pubdev

2. Jelaskan maksud dari langkah 2 pada praktikum tersebut!
   Jawab: Pada langkah ini, kita akan menambahkan **plugin `auto_size_text`** ke dalam proyek Flutter.  
   Plugin ini digunakan untuk **menyesuaikan ukuran teks secara otomatis** agar sesuai dengan ruang yang tersedia di dalam widget.  
   Dengan plugin ini, teks tidak akan terpotong meskipun panjangnya melebihi batas tampilan.

3. Jelaskan maksud dari langkah 5 pada praktikum tersebut!
   _Jawab:_ Pada langkah ini, kita akan menambahkan **variabel `text`** dan **parameter di constructor** pada widget kustom bernama `RedTextWidget`.  
   Langkah ini bertujuan agar widget dapat **menerima data teks dari luar**, sehingga konten yang ditampilkan menjadi **dinamis dan mudah digunakan kembali (reusable)**.

4. Pada langkah 6 terdapat dua widget yang ditambahkan, jelaskan fungsi dan perbedaannya!
   _Jawab:_ Pada langkah ini:

- RedTextWidget digunakan untuk menampilkan teks dengan gaya khusus (misalnya warna merah).
- Text digunakan untuk menampilkan teks standar tanpa modifikasi.
  Keduanya ditempatkan di dalam Container dengan warna dan lebar berbeda agar mudah dibedakan pada tampilan aplikasi.

5. Jelaskan maksud dari tiap parameter yang ada di dalam plugin auto*size_text berdasarkan tautan pada dokumentasi ini !
   \_Jawab:*
   Plugin **`auto_size_text`** digunakan untuk **menyesuaikan ukuran teks secara otomatis** agar muat dalam batas ruang yang tersedia di widget.  
   Plugin ini bekerja dengan cara **mengubah ukuran font** secara dinamis berdasarkan lebar atau tinggi kontainer tempat teks berada.
   Contoh Dasar Penggunaan

```dart
AutoSizeText(
  'Contoh teks panjang yang akan menyesuaikan ukuran secara otomatis.',
  style: TextStyle(fontSize: 40),
  maxLines: 2,
  minFontSize: 14,
  maxFontSize: 40,
  overflow: TextOverflow.ellipsis,
  textAlign: TextAlign.center,
)

```
