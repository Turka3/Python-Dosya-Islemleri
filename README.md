# Python Dosya İşlemleri

### Python için en önemli konulardan olan **"Dosya İşlemleri"** sık olarak yazılım geliştirilirken kullanılır. Bu yazıyla birlikte konuya hakim olabileceksiniz.

### İlk olarak **Dosya** konusunu inceleyelim. **Dosyalar** cihazlarımızda düzenin sağlanması ve sistemlerin sistematik bir şekilde çalışmasını sağlayan önceden planlanmış kurulu sistemlerdir. Bilgisayarlardaki neredeyse her nesne bir dosya niteliği gösterir. Şimdi ise Python ile **Dosya** işlemlerimize bakalım.

## 1-Dosya Okuma ve Açma İşlemleri

### Dosya olarak **txt** seçtiğimizi varsayalım. Fakat unutmayalım ki **txt** yerine **png** gibi bir dosya ile de işlemlerimizi yapabiliriz. Dosya okuma işlemi ile başlayalım.

#### Dosyayı Seçme

### Aşağıdaki yöntemle dosyayı seçerek başlayalım ve işlemimizi (r-read) olarak belirtelim. Ek olarak **utf-8** diyerek karakter kodlamasını da dahil edelim.

#### Dosyayı Seçme Örneği

```python
dosya = open("dosya.txt", "r", encoding="utf-8")
```



### Dosyamızı seçtik şimdi diğer işlemlere geçebiliriz.

#### Dosyayı tümüyle konsola yazdırma 

### Dosyamızı seçtikten sonra konsolda dosya içeriğini yazdırmak isteyebiliriz. Şu şekilde kullanabiliriz.

#### Dosyayı Konsola Yazdırma Örneği

```python
dosya = open("dosya.txt", "r", encoding="utf-8")
oku = dosya.read()
print(oku)
```

### Evet bu şekilde yaparak dosya içindeki tüm verileri konsola yazdırabiliriz. Ayrıca **read()** fonksiyonuna bir sayı değeri verirsek sadece verdiğimiz sayıya kadar okuyup konsola yazacaktır.

#### Verilen Değer Veri Okuma Örneği

```python
dosya = open("dosya.txt", "r", encoding="utf-8")
oku = dosya.read(10) # Sadece ilk 10 karakter okunur.
print(oku)
```

#### Dosyayı Satır Satır Konsola Yazdırma

### Satır satır nasıl veri okuyacağımıza göz atalım. Bunun için **readline()** fonksiyonunu kullanacağız. Bu fonksiyon her çağırılışında dosyanın satır satır okunmasını sağlar. Yani iki satır okumak istiyorsak iki kere fonksiyonu kullanmamız gerekmektedir. Fonksiyonu döngü ile tüm dosyayı okuyacak hale getirebilirsiniz. 

#### Dosyayı Satır Satır Okuma Örneği

```python
dosya = open("dosya.txt", "r", encoding="utf*8")
print(dosya.readline()) # 1. satırı yazar.
print(dosya.readline()) # 2. satırı yazar.
print(dosya.readline()) # 3. satırı yazar.
```

### Döngüye soktuğumuzda dosyanın kaçıncı satırda bittiğini bilmediğimiz için döngü işlemi bizi yorabilir. Bu yüzden aşağıdaki kodu kullanmanız daha verimli olacaktır.

#### Dosyayı Satır Satır Döngü İle Konsola Yazdırma 

### İki farklı şekilde **readline()** kullanarak satır yazdırma işlemlerimizi yapabiliriz.

#### Satır Satır Döngü İle Yazdırma Örnek 1

```python
dosya = open("dosya.txt", "r")
for satir in dosya:
	print(satir)
```

#### Satır Satır Döngü İle Yazdırma Örnek 2

```python
with open("dosya.txt","r") as dosya:
	for satir in dosya:
		print(satir)
```

#### Dosyanın Tüm Satırlarınız Diziye Eklemek

### **readline()** fonksiyonu her çağırıldığında dosyayı satır satır okumamıza olanak sağlıyordu. Şimdi ise **readlines()** fonksiyonunu çağırdığımızda dosyanın tüm satırlarını bir diziye atarak okuma işlemini göreceğiz. Bu fonksiyon ile dosyanın her satırı bir dizi elemanı olur.

#### **readlines()** Fonksiyonu ile Dizin Ekleme

```python
dosya = open("dosya.txt", "r")
dizi = dosya.readlines()
print(dizi)
```

#### Ekran Çıktısı:

```python
['K\n', 'O\n', 'D\n']
```

### Okuduğumuz her satırda bir alt satıra geçmek için kullanılan "\n" yazısını görebilirsiniz. Bunu görmek istemiyorsanız, **rstrip("\n")** fonksiyonunu kullanabilirsiniz.

## Dosyaya Yazma İşlemleri

### Dosya okuma işlemlerimizi yapabiliyoruz. Şimdi ise dosyalarımıza nasıl yazılar yazacağımızı öğrenelim.

#### Dosya kipleri:

```python
r = Mevcut dosyayı okumak amacıyla açar.
w = Dosya yoksa oluşturur, varsa içeriği silerek sıfır dosya açar.
a = Dosya yoksa oluşturur, varsa dosyanın sonunda imleçten itibaren ekleme yapar.
r+ = Dosyayı hem okuma, hem de yazma modunda açar.
```

### Şimdi **w** ve **a** modlarını kullanarak işlemlerimize başlayalım.

#### **w** Moduyla Dosyaya Veri Yazmak

### **w** kipiyle açtığımız dosyalar yok ise dizinde oluşturulur. Varsa dosyanın içeriği tamamen silinerek yazmak istediğimiz veriler eklenir. Eski verilerin yerini yeni veriler alır.

#### Dosyaya Yazdırma

```python
dosya = open("dosya.txt","w",encoding="utf-8")
dosya.write("Türker ile Python \n")
dosya.write("2.satıra geçildi")
dosya.write("2.satırdan devam ediyoruz")
```


### Yukarıdaki yapılan işlemlerden sonra dosya açılırsa yazılan yazıları görebilirsiniz. Dosyayı kapatana dek yazma işlemine devam edilebilir.

#### **a** Modu İle Dosyaya Veri Yazmak

### **a** modu ile tekrar aynı şekilde dosyanın içerisine veri yazabiliriz fakat yapılan değişiklikler dosyadaki verinin üstüne yazılır. Yani dosyadan veri silinmez. Dosyanın sonundan itibaren veri eklenmeye devam edilir.

#### **a** İle Dosyaya Veri Yazma

```python
dosya = open("dosya.txt","a",encoding="utf-8")
dosya.write("Türker ile Python \n")
dosya.write("2.satır")
dosya.write("2.satırdan devam")
```

### **Dosya.txt** içerisinde önceden olan verilerin silinmediğini sizde denediğiniz de göreceksiniz.

### Dosyalarda satır atlamak için **\\n** kullanabilirsiniz.

## Dosyaları Kapatmak 

### Dosyalar üzerinde işlemlerimizi tamamladıktan sonra kapatmamız daha verimli olacaktır. Burda devreye **close()** fonksiyonu girmekte.

#### **close()** İle Dosya Kapatma Örneği

```python
dosya = open("dosya.txt", "a", encoding="utf-8")
dosya.close()
```

### Dosyaları sürekli olarak manuel olarak kapatmaktansa aşağıdaki yöntemi kullanabilirsiniz.

#### **with** İle Dosyaları Otomatik Kapatma

```python
with open("dosya.txt","a", encoding="utf-8") as dosya:
	#İşlemler buraya gelecek.
```

### Böylelikle Python ile Dosya işlemlerimizi bitirmiş olduk.



 
