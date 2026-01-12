Endless Bear Run (AI Powered 2D Platformer)
Bu proje, Godot Engine 4.5.1 kullanılarak geliştirilmiş, Google Dinozor oyunu mekaniklerine sahip bir sonsuz koşu (Endless Runner) oyunudur. Projenin temel amacı, Godot motorunun fizik yeteneklerini ve RayCast2D sensörleri kullanılarak oluşturulan otonom (kendi kendine oynayan) karakter mekaniğini sergilemektir.

(Not: Repoya oyunun ekran görüntüsünü yükleyip buraya linkini eklemeyi unutma!)

Proje Hakkında
Bu oyun, klasik "Endless Runner" türündedir ancak oyuncu kontrolü yerine çevresel farkındalık ön plandadır. Karakter (Ayı), önüne çıkan engelleri (Ayı Kapanları) algılar ve oyunun hızına (Global Speed) göre tepki vererek zıplar.

Temel Özellikler:

Sonsuz Döngü: Zemin ve engeller sonsuz bir döngü içinde akar.


Dinamik Zorluk: Oyun süresi ilerledikçe oyun hızı (Global.oyun_hizi) otomatik olarak artar ve oyun zorlaşır.


Otonom Kontrol (AI): Karakter, RayCast2D kullanarak engelleri görür ve çarpışma gerçekleşmeden önce zıplama kararı verir.




Rastgelelik (RNG): Engeller (Spikes/Traps) 0.8 ile 3.0 saniye arasında değişen rastgele aralıklarla spawn olur.


Kullanılan Teknoloji: Godot Engine
Bu proje, açık kaynaklı ve güçlü bir oyun motoru olan Godot Engine ile geliştirilmiştir.

Neden Godot?


GDScript: Python benzeri söz dizimi ile hızlı ve anlaşılır kodlama imkanı sunar.


Node Sistemi: Sahneler ve düğümler (Nodes) üzerinden çalışan hiyerarşik yapısı ile proje yönetimini kolaylaştırır.



2D Fizik Motoru: CharacterBody2D ve Area2D gibi hazır fizik yapıları sayesinde çarpışma ve hareket kodlamayı basitleştirir.



Hafif ve Hızlı: Düşük sistem gereksinimleri ile yüksek performanslı 2D oyunlar (Örn: Brotato) geliştirilebilir.

Teknik Detaylar ve Kod Yapısı
Oyunun arkasındaki temel algoritmalar şu şekildedir:

1. Global Hız Sistemi (Autoload)
Oyunun zorluğunu tek bir merkezden yönetmek için Global adında bir singleton (tekil) script kullanılmıştır. Zemin, engeller ve skor sistemi bu global hıza göre çalışır.

GDScript

# Hız Yönetimi
func _process(delta):
    oyun_hizi += hizlanma_miktari * delta  # Zamanla hızı arttır
2. Engel Oluşturma (Spawner Logic)
Engellerin robotik ve tahmin edilebilir olmaması için Timer düğümü ve randf_range fonksiyonu kullanılmıştır.

GDScript

# Engel Spawn Mantığı (ana_sahne.gd)
func _on_timer_timeout():
    var yeni_engel = engel_kalibi.instantiate()
    add_child(yeni_engel)
    
    # Bir sonraki engel için rastgele süre belirle (0.8sn - 1.6sn arası)
    var rastgele_sure = randf_range(0.8, 1.6) 
    timer.wait_time = rastgele_sure
    timer.start()

[Referans: Proje Kodları Satır 12-19] 

3. Yapay Zeka / Otonom Karakter
Karakterin önüne, oyun hızına bağlı olarak uzayıp kısalan bir "Lazer Göz" (RayCast2D) yerleştirilmiştir.

Gözlem: RayCast engeli algılar.

Karar: Eğer engel menzildeyse ve karakter yerdeyse jump() fonksiyonu tetiklenir.


Adaptasyon: Oyun hızlandıkça RayCast'in menzili uzar, böylece karakter daha erken zıplar (Refleks Simülasyonu).

Kurulum ve Çalıştırma
Bu repoyu bilgisayarınıza klonlayın veya ZIP olarak indirin.

Godot Engine 4.x sürümünü resmi sitesinden indirin.

Godot'u açın ve Import (İçe Aktar) butonuna tıklayın.

İndirdiğiniz klasördeki project.godot dosyasını seçin.

Editör açıldığında sağ üstteki "Play" (Oynat) tuşuna veya F5'e basarak oyunu başlatın.

Geliştirici Ekip
Bu proje, Godot Engine öğrenim süreci kapsamında aşağıdaki ekip tarafından geliştirilmiştir:


Tuna Duman - (ID: 90240000223) 


Fatih Recep Kıvrak - (ID: 90240000208)