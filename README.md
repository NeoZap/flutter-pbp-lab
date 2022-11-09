# Tugas 7: Counter
###### Aushaaf Fadhilah Azzah - 2106630063
## 1. Stateless widget vs Stateful widget

Stateless widget adalah widget yang tidak memiliki state, sehingga widget tersebut tidak akan pernah berubah sekalipun meski user berinteraksi.

Stateful widget adalah kebalikannya, yakni widget yang memiliki state, yang berarti ia dapat berubah saat user melakukan interaksi yang mengubah suatu state dalam widget tersebut.

## 2. Widget yang digunakan

Widget yang digunakan adalah sebagai berikut:

  * `MaterialApp`: Widget yang digunakan untuk membuat aplikasi yang menggunakan material design.
  * `ThemeData`: Widget yang digunakan untuk mengatur tema aplikasi.
  * `Scaffold`: Widget yang digunakan untuk membuat layout dari aplikasi.
  * `AppBar`: Widget yang digunakan untuk membuat app bar (bar yang terletak di atas, mirip navbar).
  * `Center`: Widget yang digunakan untuk menempatkan child widget di tengah-tengah parent.
  * `Text`: Widget yang digunakan untuk menampilkan teks.
  * `FloatingActionButton`: Widget yang digunakan untuk membuat tombol yang tampak mengambang / melayang.
  * `Container`: Widget yang digunakan untuk menempatkan widget lainnya, dapat mengakses atribut box model.
  * `Column`: Widget yang digunakan untuk menempatkan widget lainnya secara vertikal.
  * `Row`: Widget yang digunakan untuk menempatkan widget lainnya secara horizontal.
  * `Spacer`: Widget yang digunakan untuk memberikan jarak dengan mengambil semua ruang yang tersisa antar widget lainnya.

## 3. setState()

Fungsi dari `setState()` adalah untuk mengubah nilai dari state yang ada di dalam stateful widget. Variabel yang dapat terdampak dengan fungsi tersebut adalah state pada stateful widget yang diubah di dalam `setState()`.

## 4. Const vs. Final

`Const` dan `Final` keduanya merupakan variabel yang nilainya tidak dapat diubah. `Const` digunakan untuk variabel yang nilainya sudah diketahui sejak awal, sedangkan `Final` digunakan untuk variabel yang nilainya belum diketahui sejak awal, namun nilainya akan diketahui setelah aplikasi dijalankan.

## 5. Implementasi

1. Ubah `title` pada `AppBar` menjadi `Program Counter`.
```dart
home: const MyHomePage(title: 'Program Counter'),
```
2. Gunakan ternary operator untuk menentukan nilai widget `Text` pada method `build` di class `MyHomePage` sehingga menampilkan `GENAP` warna merah jika `_counter` adalah bilangan genap, dan `GANJIL` warna biru jika `_counter` adalah bilangan ganjil.
```dart
Text(
    _counter % 2 == 0 ? 'GENAP' : 'GANJIL',
    style: TextStyle(
        color: _counter % 2 == 0 ? Colors.red : Colors.blue),
),
```
3. Buat `floatingActionButton` yang mengandung 2 tombol untuk increment dan decrement counter yang tersusun secara _space around_.
```dart
floatingActionButton: Container(
    padding: const EdgeInsets.only(left: 32),
    child: Row(
        mainAxisAlignment: MainAxisAlignment.spaceAround,
        children: [
        if (_counter > 0)
            FloatingActionButton(
            onPressed: _decrementCounter,
            tooltip: 'Decrement',
            child: const Icon(Icons.remove),
            ),
        const Spacer(),
        FloatingActionButton(
            onPressed: _incrementCounter,
            tooltip: 'Increment',
            child: const Icon(Icons.add),
        ),
        ],
    ),
    ), // This trailing comma makes auto-formatting nicer for build methods.
);
```
4. Buat method handler `_incrementCounter` dan `_decrementCounter` untuk mengubah nilai `_counter` dengan menggunakan `setState()`.
```dart
void _incrementCounter() {
    setState(() {
        _counter++;
    });
}

void _decrementCounter() {
    setState(() {
        _counter--;
    });
}
```