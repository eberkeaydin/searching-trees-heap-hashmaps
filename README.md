# ds-project-3
My Data Structures Course's third project based on data structures as trees, heap etc.
Here is the problem definition in Turkish :

PROJE 3
ARAMA AĞAÇLARI, YIĞINLAR ve HASH TABLOSU: BİSİKLET KİRALAMA SİSTEMİ  
Her bir öğrenci kendi başına hazırlayacak, programlar paketlenerek sisteme yüklenecek, rapor halinde arka arkaya getirilip istenen bilgiler de yazılarak EGE Derse yüklenecektir. Raporda, her bir soru için ilgili kaynak kod ve ekran görüntüsü yer almalıdır. İstediğiniz soruda C#, istediklerinizde Java tercih edilebilir. Raporda Bölüm Numara ve Başlıkları belirgin olarak yazılmalıdır: 1. İkili Arama Ağacı (Binary Search Tree), 2. Hash Tablosu (Hash Table), 3. Yığın Ağacı (Heap), 4. Sıralama (Sorting).
Duraklar Nesnesi (Durak Adı, Boş Park, Tandem Bisiklet, Normal Bisiklet)

String[] duraklar = { “İnciraltı, 28, 2, 10”, “Sahilevleri, 8, 1, 11“, “Doğal Yaşam Parkı, 17, 1, 6”, “Bostanlı İskele, 7, 0, 5“ };
	
1)	a) duraklar dizisine 5 tane daha istasyonun bilgilerini ekleyiniz (bisim.com.tr gibi bisiklet kiralama sistemlerini araştırarak tahmini değerler yazabilirsiniz), 9’a tamamlayınız. duraklar dizisindeki string’leri sahalarına ayrıştırarak Durak Nesnelerini oluşturup, Durak Adı’na göre DurakAğacı adlı ikili arama ağacına yerleştiren kodu yazınız. Her bir Durak nesnesini ağaca eklerken, düğüme List tipinde bir veri yapısı içinde 1 ile 10 adet arasında random sayıda rastgele Müşteri (Müşteri ID, kiralama saati) ekleyiniz (Sistemde toplam 20 müşterinin kayıtlı olduğunu varsayınız ID:1 – ID:20). Boş park ve bisiklet sayılarını güncelleyiniz. Hazır ağaç kodlarından yararlanabilirsiniz. Sayısal elemanlar için uygun veri tiplerini belirleyiniz. Şekil 1’de ağacın 3 düğümlü durumu gösterilmektedir. 





b) Ağacın derinliğini bulduran metodu yazınız. Ağaçtaki tüm bilgileri (Listeye göre kaç müşterinin kiralama yaptığı bilgisi ve Liste içindeki bilgiler dahil) ekrana listeleyen metodu yazınız. (5)
c) Klavyeden verilen bir Müşteri ID’si için ağacın tüm düğümlerini dolaşarak içlerindeki listelerdeki bilgilere bakarak hangi istasyonlardan saat kaçta bisiklet kiraladığını ekrana listeleyen metodu yazınız. (5)
d) Kiralama işlemi: Adı verilen bir istasyondan, Müşteri Numarası (ID) verilen kişinin normal bir bisiklet kiralama işlemini yapıp, Listeye ilgili bilgiyi (ID + random saat) ekleyen metodu yazınız. BP sayısı da 1 artacak.  (5)
2) a) 1. Soruda belirtilen Durak Bilgilerini Durak Adı’na göre bir Hash Table’a yerleştiren kodu yazınız. (10)  [duraklar dizisini kullanabilirsiniz. Bu soruda müşteri eklemenize gerek yok]
b) Boş Park Yeri sayısı 5’ten fazla olan tüm istasyonlara 5’er tane normal bisiklet ekleyerek Hash Tablosunda güncelleyen kodu yazınız. (5)

3) a) Ders kitabı Bölüm 12’yi okuyunuz. C# / Java ile bir Heap Veri Yapısı (sınıfı) tasarlayınız ve metotları ile beraber kurşunkalemle yazınız ve yapılan işlemleri yazarak anlatınız. Altyapıda elemanlarını tutmak için dizi veya List / Vector kullanabilirsiniz. Kodlayıp çalıştırınız. (5)  

b) Sadece Normal Bisiklet sayılarına göre düğümleri bir Max. Yığın’a yani Max. Heap’e (Java’daki PriorityQueue Heap düzenindedir) yerleştiren kodu yazınız. (5) 
c) O anda en fazla Normal Bisiklet olan üç İstasyonu Heap’ten çekerek ilgili durak / istasyon bilgilerini listeleyen kodu yazınız. (5)

