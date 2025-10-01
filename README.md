# Tailwind CSS Temel Kullanım ve Responsive Tasarım Demoları

Bu doküman, Tailwind CSS kullanarak basit ve etkili tasarımların nasıl yapılacağını, özellikle de responsive (mobil uyumlu) tasarımın temellerini anlatmak için hazırlanmıştır. Örnekler, yazılım bilgisi olmayan birinin bile anlayabileceği sadelikte tutulmuştur.

## 1. Tailwind CSS Temel Kullanımı

Tailwind, hazır `class` (sınıf) isimlerini kullanarak HTML elemanlarına stil vermenizi sağlar. Her sınıf, belirli bir CSS özelliğini temsil eder.

**Örnek:** Basit bir kart oluşturalım.

```html
<!--
  Açıklamalar:
  - bg-slate-100: Arka plan rengini açık gri yapar.
  - p-6: İçeriden 1.5rem (24px) boşluk (padding) verir.
  - rounded-lg: Köşeleri daha belirgin şekilde yuvarlatır.
  - shadow-md: Orta boyutlu bir gölge ekler.
  - text-2xl: Yazı boyutunu büyük yapar (extra large).
  - font-bold: Yazıyı kalınlaştırır.
  - text-gray-800: Yazı rengini koyu gri yapar.
  - mt-2: Üstten 0.5rem (8px) boşluk (margin-top) bırakır.
-->
<div class="bg-slate-100 p-6 rounded-lg shadow-md">
  <h2 class="text-2xl font-bold text-gray-800">Bu Bir Başlıktır</h2>
  <p class="mt-2 text-gray-600">Bu da bir paragraf metnidir. Gördüğünüz gibi stiller doğrudan HTML içinde!</p>
</div>
```

---

## 2. Tailwind CSS ile Responsive Tasarım

Responsive tasarım, web sayfanızın farklı ekran boyutlarında (mobil, tablet, masaüstü) düzgün görünmesini sağlamaktır. Tailwind bunu **breakpoint** (kırılma noktası) adı verilen ekran boyutu ön ekleriyle çok kolay hale getirir.

**Varsayılan Breakpoint'ler:**
- `sm` (small): 640px ve üzeri (genellikle telefonların yatay modu)
- `md` (medium): 768px ve üzeri (genellikle tabletler)
- `lg` (large): 1024px ve üzeri (genellikle laptoplar)
- `xl` (extra large): 1280px ve üzeri (büyük ekranlar)

Bir sınıfın başına bu ön eklerden birini getirirseniz, o stil sadece belirtilen ekran boyutunda ve daha büyüklerinde geçerli olur. **Örnek:** `md:text-center` sınıfı, ekran 768px'den büyük olduğunda metni ortalar.

**Örnek:** Ekran büyüdükçe arka plan rengi ve metin hizalaması değişen bir kutu.

```html
<!--
  Açıklamalar:
  - Başlangıçta (mobilde): Arka plan mavi (bg-blue-200), metin solda (text-left).
  - Tablet boyutuna gelince (md): Arka plan yeşil (md:bg-green-200), metin ortada (md:text-center).
  - Laptop boyutuna gelince (lg): Arka plan turuncu (lg:bg-orange-200), metin sağda (lg:text-right).
-->
<div class="p-8 bg-blue-200 text-left md:bg-green-200 md:text-center lg:bg-orange-200 lg:text-right">
  <p class="text-lg font-semibold">
    Bu kutunun rengi ve metin hizalaması ekran boyutuna göre değişir.
  </p>
  <p class="text-sm">
    Küçük ekranda mavi, orta ekranda yeşil, büyük ekranda turuncu.
  </p>
</div>
```
*Bu kodu tarayıcıda açıp pencere boyutunu değiştirerek deneyebilirsiniz.*

---

## 3. Mobilde Gösterip, Web'de Gizleme

En çok kullanılan yöntemlerden biridir. Genellikle mobil menü butonu gibi elemanlar için tercih edilir.

**Yöntem:**
1. Elemanı varsayılan olarak görünür yapın.
2. Belirli bir breakpoint'ten sonra (`md:` gibi) elemanı `hidden` sınıfı ile gizleyin.

**Örnek:**

```html
<!--
  Açıklamalar:
  - Bu div, varsayılan olarak görünür durumdadır.
  - "md" (768px) ekran boyutuna ulaşıldığında ve daha büyüklerinde "hidden" (gizli) olur.
  - "md:hidden" -> "Orta boy ekrandan itibaren gizle" anlamına gelir.
-->
<div class="p-4 bg-teal-500 text-white md:hidden">
  Bu yazı sadece mobil cihazlarda ve küçük ekranlarda görünür.
</div>
```

---

## 4. Web'de Gösterip, Mobilde Gizleme

Bu da yukarıdakinin tam tersidir ve genellikle geniş ekranlara özel içerikler veya menüler için kullanılır.

**Yöntem:**
1. Elemanı varsayılan olarak `hidden` (gizli) yapın.
2. Belirli bir breakpoint'ten sonra (`md:` gibi) elemanı görünür hale getirmek için `block`, `flex`, `grid` gibi bir görüntüleme sınıfı kullanın. En yaygın olanı `block`'tur.

**Örnek:**

```html
<!--
  Açıklamalar:
  - "hidden": Bu div, varsayılan olarak (mobil ekranda) gizlidir.
  - "md:block": Ekran boyutu "md" (768px) ve üzerine çıktığında görünür hale gelir ("display: block" olur).
-->
<div class="hidden p-4 bg-purple-600 text-white md:block">
  Bu yazı sadece tablet ve daha büyük ekranlarda (web) görünür.
</div>
```

Bu basit örnekler, Tailwind CSS ile responsive tasarımın temel mantığını kavramak için harika bir başlangıç noktasıdır. Tasarım yaparken en çok bu "breakpoint" ve "hidden/block" kombinasyonlarını kullanacaksınız. Başarılar!

# Gelişmiş Tailwind CSS: E-Ticaret için Responsive Tasarım Örnekleri

Bu doküman, e-ticaret sitelerinde sıkça kullanılan responsive (mobil uyumlu) tasarım desenlerini Tailwind CSS ile nasıl oluşturabileceğinizi göstermektedir. Örnekler, mobil öncelikli bir yaklaşımla hazırlanmıştır.

---

## 1. Responsive Ürün Listeleme (Grid Yapısı)

E-ticaret sitelerinin en temel sayfası ürün listeleme sayfasıdır. Ekran boyutuna göre sütun sayısını ayarlamak, kullanıcı deneyimi için kritiktir.

**Hedef:**
- **Mobilde:** Ürünler tek sütun (alt alta)
- **Tablette (`md`):** Ürünler üç sütun
- **Web'de (`lg`):** Ürünler dört sütun

**Yöntem:** CSS Grid (`grid`) ve responsive sütun (`grid-cols-*`) sınıfları kullanılır.

```html
<!--
  Açıklamalar:
  - grid: Elemanı bir grid konteyneri yapar.
  - grid-cols-1: Varsayılan olarak (mobilde) 1 sütunlu bir grid oluşturur.
  - md:grid-cols-3: Ekran 768px ve üzerine çıktığında 3 sütunlu olur.
  - lg:grid-cols-4: Ekran 1024px ve üzerine çıktığında 4 sütunlu olur.
  - gap-4: Grid elemanları arasına 1rem (16px) boşluk bırakır.
-->
<div class="grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-4 p-4">
  <!-- Örnek Ürün Kartı (Bu karttan istediğiniz kadar kopyalayıp yapıştırın) -->
  <div class="border rounded-lg p-4 shadow-lg">
    <div class="bg-gray-200 h-40 rounded-md mb-2"></div> <!-- Ürün görseli için yer tutucu -->
    <h3 class="font-bold text-lg">Ürün Adı</h3>
    <p class="text-gray-600">₺199.99</p>
    <button class="mt-2 w-full bg-blue-600 text-white py-2 rounded-md hover:bg-blue-700">
      Sepete Ekle
    </button>
  </div>

  <!-- Diğer ürün kartları... (Bu bloktan 7 tane daha ekleyerek deneyin) -->
  <div class="border rounded-lg p-4 shadow-lg">
    <div class="bg-gray-200 h-40 rounded-md mb-2"></div>
    <h3 class="font-bold text-lg">Ürün Adı</h3>
    <p class="text-gray-600">₺249.99</p>
    <button class="mt-2 w-full bg-blue-600 text-white py-2 rounded-md hover:bg-blue-700">
      Sepete Ekle
    </button>
  </div>
  <div class="border rounded-lg p-4 shadow-lg">
    <div class="bg-gray-200 h-40 rounded-md mb-2"></div>
    <h3 class="font-bold text-lg">Ürün Adı</h3>
    <p class="text-gray-600">₺299.99</p>
    <button class="mt-2 w-full bg-blue-600 text-white py-2 rounded-md hover:bg-blue-700">
      Sepete Ekle
    </button>
  </div>
  <div class="border rounded-lg p-4 shadow-lg">
    <div class="bg-gray-200 h-40 rounded-md mb-2"></div>
    <h3 class="font-bold text-lg">Ürün Adı</h3>
    <p class="text-gray-600">₺349.99</p>
    <button class="mt-2 w-full bg-blue-600 text-white py-2 rounded-md hover:bg-blue-700">
      Sepete Ekle
    </button>
  </div>
</div>
```

---

## 2. Responsive Navigasyon (Hamburger Menü)

Mobil cihazlarda yerden tasarruf etmek için navigasyon menüsü genellikle bir "hamburger" ikonunun arkasına gizlenir.

**Hedef:**
- **Mobilde:** Sadece logo ve hamburger ikonu görünsün.
- **Web'de (`md`):** Logo ve navigasyon linkleri yan yana görünsün, hamburger ikonu gizlensin.

```html
<!--
  Not: Bu örnek sadece görsel yapıyı içerir. Menüyü açıp kapatmak için
  biraz JavaScript kodu eklemeniz gerekir.
-->
<nav class="bg-gray-800 text-white p-4">
  <div class="container mx-auto flex justify-between items-center">
    <!-- Logo -->
    <a href="#" class="text-xl font-bold">E-Ticaret Sitem</a>

    <!-- Mobil Menü Butonu (Hamburger) -->
    <!-- md:hidden: Orta boy ekran ve üzerinde bu butonu gizle -->
    <button class="md:hidden">
      <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path></svg>
    </button>

    <!-- Web Navigasyon Linkleri -->
    <!-- hidden: Mobilde varsayılan olarak gizli -->
    <!-- md:flex: Orta boy ekran ve üzerinde görünür yap (display: flex) -->
    <div class="hidden md:flex space-x-4">
      <a href="#" class="hover:text-gray-300">Anasayfa</a>
      <a href="#" class="hover:text-gray-300">Ürünler</a>
      <a href="#" class="hover:text-gray-300">Hakkımızda</a>
      <a href="#" class="hover:text-gray-300">İletişim</a>
    </div>
  </div>
</nav>
```

---

## 3. Ürün Detay Sayfası Düzeni

Ürün detay sayfalarında mobil cihazlarda görsel ve bilgiler alt alta gelirken, geniş ekranlarda yan yana gelmesi daha kullanışlıdır.

**Hedef:**
- **Mobilde:** Ürün görseli üstte, ürün bilgileri altta.
- **Web'de (`lg`):** Ürün görseli solda, ürün bilgileri sağda.

**Yöntem:** Flexbox'ın yönünü (`flex-col` ve `lg:flex-row`) değiştirmek.

```html
<!--
  Açıklamalar:
  - flex: Flexbox konteyneri yapar.
  - flex-col: Varsayılan olarak (mobilde) elemanları dikeyde (sütun) hizalar.
  - lg:flex-row: Geniş ekran ve üzerinde elemanları yatayda (satır) hizalar.
-->
<div class="container mx-auto p-4 flex flex-col lg:flex-row gap-8">
  <!-- Sol Taraf: Ürün Görseli -->
  <!-- lg:w-1/2: Geniş ekranda konteynerin %50 genişliğini kaplar -->
  <div class="lg:w-1/2">
    <div class="bg-gray-200 h-96 rounded-lg"></div> <!-- Ana ürün görseli -->
  </div>

  <!-- Sağ Taraf: Ürün Bilgileri -->
  <!-- lg:w-1/2: Geniş ekranda konteynerin %50 genişliğini kaplar -->
  <div class="lg:w-1/2">
    <h1 class="text-3xl font-bold">Modern Koltuk Takımı</h1>
    <p class="text-2xl text-red-600 my-4">₺4,999.00</p>
    <p class="text-gray-700 mb-4">
      Bu koltuk takımı, evinize modern bir dokunuş katacak. Yüksek kaliteli malzemeden üretilmiştir ve uzun ömürlüdür.
    </p>
    <button class="w-full bg-green-600 text-white py-3 rounded-lg text-lg hover:bg-green-700">
      Hemen Satın Al
    </button>
  </div>
</div>
```

Bu örnekler, bir e-ticaret sitesi geliştirirken karşılaşacağınız en yaygın responsive tasarım senaryolarını kapsamaktadır. Bu yapıları kullanarak projenizi kolayca farklı ekran boyutlarına uyumlu hale getirebilirsiniz.

# Tailwind CSS ile E-Ticaret Ana Sayfa Bileşenleri: Banner ve Bilgi Alanları

Bu doküman, bir e-ticaret sitesinin ana sayfasında kullanıcıyı karşılamak, kampanyaları duyurmak ve önemli bilgileri vurgulamak için kullanılan modern ve responsive bileşenlerin nasıl oluşturulacağını gösterir.

---

## 1. Üst Bilgi Duyuru Banner'ı (Announcement Bar)

Sitelerin en tepesinde yer alan ve genellikle "Ücretsiz Kargo" gibi duyuruları içeren ince şerit.

**Hedef:**
- **Tüm Cihazlarda:** Ekranın en üstünde, dikkat çekici ama sade bir şerit olarak görünür.
- **Kapatma İkonu:** Kullanıcının banner'ı gizlemesine olanak tanır (ikonun işlevselliği için JavaScript gerekir).

```html
<!--
  Açıklamalar:
  - relative: Kapatma butonunu konumlandırmak için ana kapsayıcı.
  - bg-indigo-600: Arka plan rengi.
  - text-white: Metin rengi.
  - px-4 py-2: Yatay ve dikey iç boşluklar.
  - flex items-center justify-center: İçeriği dikey ve yatayda ortalar.
  - text-sm: Küçük ekranlar için ideal metin boyutu.
  - md:text-base: Orta boy ekran ve üzerinde metni biraz büyütür.
-->
<div class="relative bg-indigo-600 text-white px-4 py-2">
  <div class="flex items-center justify-center text-center">
    <p class="text-sm font-medium md:text-base">
      🎉 500 TL ve Üzeri Tüm Siparişlerde Kargo BEDAVA! 🎉
    </p>
  </div>
  <!-- Kapatma Butonu -->
  <div class="absolute inset-y-0 right-0 flex items-center pr-4">
    <button class="p-1 rounded-md hover:bg-indigo-500 focus:outline-none focus:ring-2 focus:ring-white">
      <!-- Heroicons'tan X ikonu -->
      <svg class="h-5 w-5" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
      </svg>
    </button>
  </div>
</div>
```

---

## 2. Ana Karşılama Alanı (Hero Section)

Ana sayfanın en dikkat çekici bölümüdür. Genellikle büyük bir görsel, etkileyici bir başlık ve "Hemen Keşfet" gibi bir eylem çağrısı (Call to Action) butonu içerir.

**Hedef:**
- **Mobilde:** İçerik ortalanmış ve dikey olarak hizalanmıştır.
- **Web'de (`md`):** İçerik sola yaslanmış, daha fazla boşlukla ferah bir görünüm sunar.

```html
<!--
  Açıklamalar:
  - relative: İçerideki metin bloğunu konumlandırmak için.
  - bg-cover bg-center: Arka plan görselinin tüm alanı kaplamasını ve ortalanmasını sağlar.
  - h-[60vh]: Yüksekliği ekran yüksekliğinin %60'ı yapar.
  - bg-black bg-opacity-50: Görsel üzerine siyah, %50 şeffaf bir katman ekleyerek metnin okunurluğunu artırır.
  - text-center md:text-left: Metni mobilde ortalar, web'de sola yaslar.
  - md:items-start: İçeriği web'de dikeyde başlangıç noktasına (sola) hizalar.
-->
<div class="relative h-[60vh] bg-gray-700 bg-cover bg-center" style="background-image: url('https://images.unsplash.com/photo-1524758631624-e2822e304c36?auto=format&fit=crop&w=1470&q=80');">
  <!-- Okunurluk için overlay -->
  <div class="absolute inset-0 bg-black bg-opacity-50"></div>

  <!-- İçerik -->
  <div class="relative z-10 flex h-full items-center justify-center md:justify-start">
    <div class="container mx-auto px-6 text-center md:text-left md:px-12">
      <h1 class="text-3xl font-extrabold text-white md:text-5xl lg:text-6xl">
        Yeni Sezon Koleksiyonu
      </h1>
      <p class="mt-4 max-w-lg mx-auto md:mx-0 text-lg text-gray-200 md:text-xl">
        Tarzınızı yansıtan en trend parçalarla gardırobunuzu yenileyin.
      </p>
      <div class="mt-6">
        <a href="#" class="bg-white text-gray-900 font-bold py-3 px-6 rounded-lg text-lg hover:bg-gray-200 transition duration-300">
          Hemen Keşfet
        </a>
      </div>
    </div>
  </div>
</div>
```

---

## 3. İkili Banner (Split Banner)

Genellikle "Kadın" ve "Erkek" gibi iki ana kategoriyi vurgulamak için kullanılan, ekranı ikiye bölen tasarımdır.

**Hedef:**
- **Mobilde:** İki banner alt alta durur.
- **Web'de (`md`):** İki banner yan yana durarak ekranı doldurur.

```html
<!--
  Açıklamalar:
  - grid grid-cols-1 md:grid-cols-2: Mobilde tek sütun, web'de iki sütunlu bir grid yapısı oluşturur.
  - h-80: Her bir banner'ın yüksekliği.
  - hover:scale-105: Fare üzerine gelince banner'ı hafifçe büyütür.
  - transition-transform: Büyüme efektini pürüzsüz hale getirir.
-->
<div class="grid grid-cols-1 md:grid-cols-2">
  <!-- Sol Banner - Kadın -->
  <div class="relative h-80 bg-cover bg-center group overflow-hidden" style="background-image: url('https://images.unsplash.com/photo-1509319117193-57bab727e09d?auto=format&fit=crop&w=687&q=80');">
    <div class="absolute inset-0 bg-black bg-opacity-40 flex items-center justify-center">
      <div class="text-center">
        <h2 class="text-4xl font-bold text-white">KADIN</h2>
        <a href="#" class="mt-2 inline-block text-white font-semibold border-b-2 border-white">
          Koleksiyonu Gör
        </a>
      </div>
    </div>
    <div class="absolute inset-0 bg-cover bg-center transition-transform duration-500 group-hover:scale-105" style="background-image: inherit;"></div>
  </div>

  <!-- Sağ Banner - Erkek -->
  <div class="relative h-80 bg-cover bg-center group overflow-hidden" style="background-image: url('https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?auto=format&fit=crop&w=687&q=80');">
    <div class="absolute inset-0 bg-black bg-opacity-40 flex items-center justify-center">
      <div class="text-center">
        <h2 class="text-4xl font-bold text-white">ERKEK</h2>
        <a href="#" class="mt-2 inline-block text-white font-semibold border-b-2 border-white">
          Koleksiyonu Gör
        </a>
      </div>
    </div>
    <div class="absolute inset-0 bg-cover bg-center transition-transform duration-500 group-hover:scale-105" style="background-image: inherit;"></div>
  </div>
</div>
```

Bu bileşenler, modern bir e-ticaret sitesinin ana sayfasını oluşturmak için güçlü ve esnek temeller sağlar. Farklı arka plan görselleri ve metinlerle kolayca özelleştirebilirsiniz.
