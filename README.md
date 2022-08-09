# tugas_2_python_pacmann

## Tujuan Pengerjaan Tugas
Mengimplementasikan Pembelajaran Dasar Python :
1. Guess and Check Algorithm untuk melakukan Penebakan
2. Membuat Function
3. Implementasi Data berbentuk Tuples, Lists, Set, Dictionary dan Recursion

## Berikut pertanyaan dan penyelesaian yang dilakukan (untuk hasil output bisa melihat langsung file .ipynb tersebut)
1. Universitas X menerapkan sistem uang kuliah tunggal (UKT) untuk membayar kuliah, dimana terdapat tiga golongan. Setiap golongan akan membayar uang kuliah per semesternya sebagai berikut:
|Golongan|Uang Kuliah per Semester|
|------|-----|
|I|Rp 2.000.000|
|II|Rp 3.500.000|
|III|Rp 5.000.000|

Untuk melunasi uang semesteran, mahasiswa dapat memilih dua pilihan pembayaran: langsung lunas atau mencicil. Apabila mahasiswa memilih langsung lunas, maka uang semesteran hanya dibayar sekali. Apabila mahasiswa memilih mencicil, maka uang semesteran akan dicicil sebanyak dua kali dengan besar cicilan pertama sama dengan besar cicilan kedua.\
Buatlah program yang menerima input berupa golongan (`'I'/'II'/'III'`) dan pilihan pembayaran (`'L'/'C'`), dan outputnya adalah besar pembayaran (bila memilih langsung lunas (`'L'`)) atau besar cicilan (bila memilih mencicil (`'C'`)).

Apabila Budi merupakan mahasiswa golongan II dan ia memilih membayar uang semesterannya dengan mencicil, berapa cicilannya? Jawaban harus berupa integer.
```
def jawaban_1(golongan,pilihan):
    if golongan == 'I' and pilihan == 'C':
        output = int(2000000/2)
    elif golongan == 'II' and pilihan == 'C':
        output = int(3500000/2)
    elif golongan == 'III' and pilihan == 'C':
        output = int(5000000/2)
    elif golongan == 'I' and pilihan == 'L':
        output = int(2000000)
    elif golongan == 'II' and pilihan == 'L':
        output = int(3500000)
    elif golongan == 'III' and pilihan == 'L':
        output = int(5000000)
    return output
```

2. Nyatakanlah fungsi berikut $x^3 - 8$ menggunakan lambda
```
func = lambda x : x**3 - 8
```

3. Dengan menggunakan konsep fungsi epsilon, aproksimasi solusi dari fungsi lambda tadi untuk f(x)=0 dengan nilai $\varepsilon = 0.05$ dan _increment_ 0.001. Print hasilnya dengan pembulatan 3 angka di belakang koma. <br><br>
Fungsi harus menerima argumanen:
<ul>
    <li>func = Fungsi dalam bentuk lambda</li>
    <li>y = Hasil untuk fungsi(x)=y</li>
    <li>epsilon = Nilai epsilon dengan nilai default adalah 0.05</li>
    <li>increment = Nilai increment/penambahan dengan nilai default adalah 0.001</li>
    <li>max_guess = Jumlah maksimum tebakan dengan nilai default adalah 10.000</li>
</ul><br>
dan return: hasil approximasi

```
def approx(func, y, epsilon=0.05, increment=0.001, max_guess=10000):
    x = 0
    num_guess = 0
    while abs(func(x)-y) >= epsilon and num_guess <= max_guess:
        x += increment
        num_guess += 1
    return x
```

4. Jika fungsi diganti menjadi $x^9 + 2x^8 - 0.044$, berapakah aproksimasi solusi dari f(x)=10?<br>
Note: Gunakan fungsi yang telah dibuat
```
func = lambda x: x**9 + 2*x**8 - 0.044 # Isikan dengan kode yang sesuai
y = 10

print(f'{approx(func,y):.3f}')
```

```
list_ = [1,[2,3],0.4,(5,6),[7,8],9.10,11,(12,13,14),15]
```
5. Ambilah angka 6 dari list_!
```
jawaban_5 = list_[3][1]
print(jawaban_5)
```

6. Kalikan angka 8 pada list_ dengan 2 dan gantikan angka tersebut dengan hasil perkaliannya!
```
list_[4][1]=list_[4][1]*2

print(list_)
```

7. Buatlah sebuah fungsi yang akan mengembalikan tipe data dari elemen-elemen di sebuah list!<br>
Input: list <br>Output: list berisi tipe data
```
def jawaban_7(list_input):
    result=[type(x) for x in list_input]
    return result
jawaban_7(list_)
```

8. Buatlah sebuah fungsi untuk menentukan apakah sebuah kata memiliki huruf yang berulang!<br>
Hint: 
<br>1. Gunakan type casting dari string ke set untuk mendapatkan huruf unik di string kata.
<br>2. Cek apakah hasil type casting dan string kata memiliki panjang yang sama.
```
def jawaban_8(kata):
    set_kata = set(kata)
    list_kata = list(set_kata)
    if len(list(kata)) == len(list_kata):
        result = print('True')
    else:
        result = print('False')
    return result
```
```
jawaban_8('rumah')
```
```
jawaban_8('apa')
```

9. Buatlah sebuah fungsi yang menghitung kemunculan huruf di sebuah kata!
```
Input: string kata<br>
Output: dictionary dengan *key-value pair* berupa huruf-frekuensi <br>
Hint:<br>
1. Looping huruf di input kata
2. Jika huruf **tidak berada** di dictionary, maka akan membuat *key-value pair* baru
3. Jika huruf **sudah berada** di dictionary, maka akan menambahkan 1 di *value*-nya
```
```
def jawaban_9(kata):
    kata_2 = {}
    for i in kata:
        if i in kata_2:
            kata_2[i] += 1
        else:
            kata_2[i] = 1
    return kata_2
print(jawaban_9('heksakosioiheksekontaheksafobia'))
```

10. Gunakan konsep pemrograman rekursif untuk menghitung jumlah $n$ suku pertama deret harmonik. Deret harmonik adalah deret sbb:
$$H(n) = 1 + \frac{1}{2} + \frac{1}{3} + \frac{1}{4} + \frac{1}{5} + \dots + \frac{1}{n}$$
Kemudian keluarkan jumlah 4 suku pertama deret harmonik.\
_Expected output_: 2.083333333333333.
```
def harmonic(suku):
    if suku < 2:
        return 1
    else:
        return 1/suku + (harmonic(suku-1))
print(harmonic(4))
```
