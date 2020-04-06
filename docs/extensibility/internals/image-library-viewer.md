---
title: Resim Kitaplığı Görüntüleyici | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7c5eda24c235cddec99cb5177c6ed315978bc6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707744"
---
# <a name="image-library-viewer"></a>Görüntü Kitaplığı Görüntüleyicisi
Visual Studio Image Library Viewer aracı, kullanıcının bunları Visual Studio'nun yapacağı şekilde işlemesine izin vererek görüntü bildirimlerini yükleyebilir ve arayabilir. Kullanıcı arka planı, boyutları, DPI'yi, yüksek kontrastı ve diğer ayarları değiştirebilir. Araç ayrıca her görüntü manifestosu için yükleme bilgilerini görüntüler ve görüntü bildirimindeki her görüntü için kaynak bilgileri görüntüler. Bu araç aşağıdakiler için yararlıdır:

1. Hataları tanılama

2. Özel görüntü bildirimlerinde özniteliklerin doğru şekilde ayarlanmasını sağlama

3. Visual Studio uzantısı Visual Studio tarzına uygun görüntüleri kullanabilmek için Visual Studio Resim Kataloğu'nda görüntü arama

   ![Görüntü Kitaplığı Görüntüleyici Kahraman](../../extensibility/internals/media/image-library-viewer-hero.png "Görüntü Kitaplığı Görüntüleyici Kahraman")

   **Resim lakabı**

   Resim takma adı (veya kısaca takma adı), Resim Kitaplığı'ndaki bir görüntü varlığını veya resim listesi kıymetini benzersiz olarak tanımlayan bir GUID:ID çiftidir.

   **Resim manifestosu dosyaları**

   Görüntü bildirimi (.imagemanifest) dosyaları, görüntü varlıkları kümesini tanımlayan XML dosyaları, bu varlıkları temsil eden moniker'ler ve her varlığı temsil eden gerçek görüntü veya görüntülerdir. Görüntü bildirimleri, eski Web-hizmetleri desteği için bağımsız görüntüler veya resim listeleri tanımlayabilir. Ayrıca, varlık üzerinde veya her varlığın arkasındaki tek tek görüntülerde bu varlıkların ne zaman ve nasıl görüntüleneceğini değiştirmek üzere ayarlanabilen öznitelikler vardır.

   **Görüntü manifesto şeması**

   Tam bir görüntü manifestosu şuna benzer:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Sembol**

 Okunabilirlik ve bakım yardımı olarak, görüntü bildirimi öznitelik değerleri için semboller kullanabilir. Semboller şu şekilde tanımlanır:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|||
|-|-|
|**Alt öğesi**|**Tanım**|
|İçeri Aktarma|Geçerli bildirimde kullanılmak üzere verilen bildirim dosyasının sembollerini alır.|
|Guid|Sembol bir GUID'i temsil eder ve GUID biçimlendirmesini eşleştirmelidir.|
|Kimlik|Sembol bir kimliği temsil eder ve negatif olmayan bir tamsayı olmalıdır.|
|Dize|Sembol rasgele bir dize değerini temsil eder.|

 Semboller büyük/küçük harf duyarlıdır ve $(sembol adı) sözdizimi kullanılarak başvurulur:

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Bazı semboller tüm manifestolar için önceden tanımlanır. Bunlar, yerel makinedeki yollara \<başvurmak için \<Kaynak> veya Alma> öğesinin Uri özniteliğinde kullanılabilir.

|||
|-|-|
|**Sembolü**|**Açıklama**|
|Ortak Program Dosyaları|%CommonProgramFiles% ortam değişkeninin değeri|
|Localappdata|%LocalAppData% ortam değişkeninin değeri|
|ManifestFolder|Bildirim dosyasını içeren klasör|
|Mydocuments|Geçerli kullanıcının Belgelerim klasörünün tam yolu|
|ProgramFiles|%ProgramFiles% ortam değişkeninin değeri|
|Sistem|Windows\System32 klasörü|
|Windir|%WinDir% ortam değişkeninin değeri|

 **Görüntü**

 \<Görüntü> öğesi, bir takma alabilen bir görüntü tanımlar. Guid ve kimlik birlikte görüntü lakabını oluşturur. Görüntünün takma adı tüm görüntü kitaplığında benzersiz olmalıdır. Birden fazla görüntüde belirli bir lakap varsa, kütüphaneyi oluştururken karşılaşılan ilk görüntü korunur.

 En az bir kaynak içermelidir. Boyut-nötr kaynaklar boyutları geniş bir yelpazede en iyi sonuçları verecek olsa da, bunlar gerekli değildir. Hizmetten \<Görüntü> öğesinde tanımlanmamış bir boyutun görüntüsü istenirse ve boyut-nötr kaynak yoksa, hizmet en büyük boyuta özgü kaynağı seçer ve istenen boyuta ölçeklendirilir.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Guid|[Gerekli] Resim lakabının GUID bölümü|
|Kimlik|[Gerekli] Resim lakabının kimlik bölümü|
|ColorInversion'a İzin Ver|[İsteğe bağlı, varsayılan true] Koyu bir arka plan da kullanıldığında görüntünün renklerini programlı olarak ters çevirip kullanamayacağını gösterir.|

 **Kaynak**

 \<Kaynak> öğesi tek bir görüntü kaynağı varlık (XAML ve PNG) tanımlar.

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Urı|[Gerekli] Görüntünün nereden yüklenebileceğini tanımlayan bir URI. Aşağıdakilerden biri olabilir:<br /><br /> - Application:/// yetkisini kullanan bir [Paket URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br /><br /> - Mutlak bileşen kaynak başvurusu<br /><br /> - Yerel kaynak içeren bir dosyaya giden yol|
|Arka plan|[İsteğe bağlı] Kaynağın hangi arka planda kullanılacağını gösterir.<br /><br /> Aşağıdakilerden biri olabilir:<br /><br /> - *Işık*: Kaynak, hafif bir arka plan üzerinde kullanılabilir.<br /><br /> - *Koyu :* Kaynak koyu bir arka plan üzerinde kullanılabilir.<br /><br /> - *HighContrast*: Kaynak Yüksek Kontrast modunda herhangi bir arka plan üzerinde kullanılabilir.<br /><br /> - *HighContrastLight*: Kaynak, Yüksek Kontrastlı modda açık arka planda kullanılabilir.<br /><br /> -*HighContrastDark*: Kaynak Yüksek Kontrast modunda koyu bir arka plan üzerinde kullanılabilir.<br /><br /> Arka **Plan** özniteliği atlanırsa, kaynak herhangi bir arka planda kullanılabilir.<br /><br /> **Arka plan** *Açık,* *Koyu*, *HighContrastLight*veya *HighContrastDark*ise, kaynağın renkleri asla ters çevrilmez. **Arka plan** atlanırsa veya *HighContrast*olarak ayarlanmışsa, kaynağın renklerinin ters çevrilmesi görüntünün **AllowColorInversion** özniteliği tarafından denetlenir.|

 Kaynak \<> öğesi tam olarak aşağıdaki isteğe bağlı alt öğelerden birine sahip olabilir:

||||
|-|-|-|
|**Öğe**|**Öznitelikler (tüm gerekli)**|**Tanım**|
|\<Boyut>|Değer|Kaynak, verilen boyutun (aygıt birimlerinde) görüntüleri için kullanılacaktır. Görüntü kare olacak.|
|\<SizeRange>|MinSize, MaxSize|Kaynak, MinSize'dan MaxSize'a (cihaz birimlerinde) kadar olan görüntüler için kapsamlı olarak kullanılacaktır. Görüntü kare olacak.|
|\<Boyutlar>|Genişlik, Yükseklik|Kaynak, verilen genişlik ve yükseklik görüntüleri için (aygıt birimlerinde) kullanılacaktır.|
|\<Boyut Aralığı>|MinWidth, MinHeight,<br /><br /> Maksimum Genişlik, Maksimum Yükseklik|Kaynak, en düşük genişlik/yükseklikten maksimum genişliğe/yüksekliğe (aygıt birimlerinde) kadar olan görüntüler için kullanılacaktır.|

 Kaynak> öğesi, yönetilen \<bir derleme yerine yerel bir \<derlemeden yüklenen kaynak> tanımlayan isteğe bağlı NativeResource> alt öğesine de sahip olabilir. \<

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Tür|[Gerekli] XAML veya PNG yerel kaynağın türü|
|Kimlik|[Gerekli] Yerel kaynağın tamsayı kimlik bölümü|

 **ımagelist**

 \<ImageList> öğesi, tek bir şeritte döndürülebilen bir görüntü koleksiyonunu tanımlar. Şerit gerektiği gibi, talep üzerine inşa edilmiştir.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Guid|[Gerekli] Resim lakabının GUID bölümü|
|Kimlik|[Gerekli] Resim lakabının kimlik bölümü|
|Dış|[İsteğe bağlı, varsayılan yanlış] Resim lakabının geçerli bildirimde bir görüntüye başvurup başvurulmadığını gösterir.|

 İçe sahip görüntünün takma başlığı, geçerli bildirimde tanımlanan bir görüntüye başvurmak zorunda değildir. İçerdiği görüntü görüntü kitaplığında bulunamıyorsa, yerine boş bir yer tutucu görüntüsü kullanılır.

## <a name="how-to-use-the-tool"></a>Aracı nasıl kullanılır?
 **Özel bir görüntü bildirimini doğrulama**

 Özel bir bildirim oluşturmak için, bildirimi otomatik oluşturmak için ManifestFromResources aracını kullanmanızı öneririz. Özel bildirimi doğrulamak için Resim Kitaplığı Görüntüleyici'yi başlatın ve Dosya > Yolları'nı seçin... Arama Dizinleri iletişim kutusunu açmak için. Araç, görüntü bildirimlerini yüklemek için arama dizinlerini kullanır, ancak bir bildirimdeki görüntüleri içeren .dll dosyalarını bulmak için bunları da kullanır, bu nedenle bu iletişim kutusuna hem manifesto hem de DLL dizinleri eklediğinden emin olun.

 ![Resim Kitaplığı Görüntüleyici Arama](../../extensibility/internals/media/image-library-viewer-search.png "Resim Kitaplığı Görüntüleyici Arama")

 Bildirimleri ve karşılık gelen DL'leri aramak için yeni arama dizinlerini seçmek için **Ekle...** seçeneğini tıklatın. Araç bu arama dizinlerini hatırlar ve bir dizinin işaretlerini işaretleyerek veya denetlemeden açılabilir veya kapatılabilir.

 Varsayılan olarak, araç Visual Studio yükleme dizinini bulmaya çalışır ve bu dizinleri arama dizinleri listesine ekler. Aracın bulamadığı dizinleri el ile ekleyebilirsiniz.

 Tüm bildirimler yüklendikten sonra, araç **arka plan** renklerini, **DPI'yi,** **yüksek kontrastı**veya görüntü için gri **ölçeklendirmeyi** değiştirmek için kullanılabilir, böylece kullanıcı görüntü varlıklarını çeşitli ayarlar için doğru şekilde işlendiğini doğruolarak denetleyebilir.

 ![Resim Kitaplığı Görüntüleyici Arka Planı](../../extensibility/internals/media/image-library-viewer-background.png "Resim Kitaplığı Görüntüleyici Arka Planı")

 Arka plan rengi Açık, Koyu veya özel bir değer olarak ayarlanabilir. "Özel Renk" seçeneğinin seçilmesi bir renk seçimi iletişim kutusunu açar ve daha sonra kolayca geri çağırmak için bu özel rengi arka plan açılan kutusunun altına ekler.

 ![Resim Kitaplığı Görüntüleyici Özel Renk](../../extensibility/internals/media/image-library-viewer-custom-color.png "Resim Kitaplığı Görüntüleyici Özel Renk")

 Görüntü lakabını seçmek, sağdaki Görüntü Ayrıntıları bölmesinde o takma anın arkasındaki her gerçek görüntüye ait bilgileri görüntüler. Bölme ayrıca, kullanıcıların bir takma adı ada veya ham GUID:ID değerine göre kopyalamasına da olanak tanır.

 ![Resim Kitaplığı GörüntüLeyici Görüntü Ayrıntıları](../../extensibility/internals/media/image-library-viewer-image-details.png "Resim Kitaplığı GörüntüLeyici Görüntü Ayrıntıları")

 Her görüntü kaynağı için görüntülenen bilgiler, görüntülenecek arka plan türünü, temalı olup olmadığını veya Yüksek Karşıtlığı destekleyip desteklemediğini, hangi boyutlarda geçerli olduğunu veya boyut açısından nötr olup olmadığını ve görüntünün yerel bir derlemeden gelip gelmediğini içerir.

 ![Resim Kitaplığı Görüntüleyici Can Teması](../../extensibility/internals/media/image-library-viewer-can-theme.png "Resim Kitaplığı Görüntüleyici Can Teması")

 Bir görüntü bildirimini doğrularken, manifesto ve görüntü DLL'yi gerçek dünya konumlarında dağıtmanızı öneririz. Bu, göreli yolların doğru çalıştığını ve görüntü kitaplığı nın manifesto yu ve görüntü DLL'yi bulup yükleyebileceğini doğrular.

 **Resim kataloğu KnownMonikers aranıyor**

 Visual Studio stilini daha iyi eşleştirmek için Visual Studio uzantısı, kendi tasarımını oluşturmak ve kullanmak yerine Visual Studio Resim Kataloğu'ndaki görüntüleri kullanabilir. Bu, bu görüntüleri korumak zorunda kalmama avantajına sahiptir ve visual studio'nun desteklediği tüm DPI ayarlarında doğru görünmesi için görüntünün yüksek DPI destekli bir görüntüye sahip olacağını garanti eder.

 Görüntü kitaplığı görüntüleyici, kullanıcının görüntü kıymetini temsil eden lakabı bulabilmesi ve bu lakabı kodda kullanabilmesi için bir bildirimin aranmasına izin verir. Görüntüleri aramak için arama kutusuna istediğiniz arama terimini girin ve Enter tuşuna basın. Alttaki durum çubuğu, tüm bildirimlerdeki toplam görüntülerden kaç eşleşme bulunduğunu görüntüler.

 ![Resim Kitaplığı Görüntüleyici Filtresi](../../extensibility/internals/media/image-library-viewer-filter.png "Resim Kitaplığı Görüntüleyici Filtresi")

 Mevcut manifestolarda görüntü monikers ararken, arama ve sadece Visual Studio Image Catalog monikers, diğer kasıtlı olarak kamuya açık monikers veya kendi özel monikers kullanmanızı öneririz. Herkese açık olmayan moniker kullanıyorsanız, özel Kullanıcı Arabirimi bozulabilir veya bu genel olmayan monikers ve görüntüler değiştirilir veya güncelleştirildiğinde beklenmedik şekillerde görüntüleri değiştirilebilir.

 Ayrıca, GUID ile arama yapmak mümkündür. Bu arama türü, listeyi tek bir bildirime veya bu bildirimin birden çok GUID içeriyorsa tek bir bildirimin tek bir alt bölümüne filtrelemek için yararlıdır.

 ![Resim Kitaplığı Görüntüleyici Filtre GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Resim Kitaplığı Görüntüleyici Filtre GUID")

 Son olarak, kimlikle arama yapmak da mümkündür.

 ![Resim Kitaplığı Görüntüleyici Filtre Kimliği](../../extensibility/internals/media/image-library-viewer-filter-id.png "Resim Kitaplığı Görüntüleyici Filtre Kimliği")

## <a name="notes"></a>Notlar

- Varsayılan olarak, araç Visual Studio yükleme dizininde bulunan çeşitli görüntü bildirimlerini çeker. Kamuya açık monikers olan tek **Microsoft.VisualStudio.ImageCatalog** bildirimidir. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (özel bir manifesto bu GUID geçersiz **kılma)** Türü: BilinenMonikers

- Araç bulduğu tüm görüntü bildirimlerini yüklemek için başlatmayı dener, bu nedenle uygulamanın gerçekten görünmesi birkaç saniye sürebilir. Ayrıca, bildirimleri yüklerken yavaş veya yanıt vermeyen olabilir.

## <a name="sample-output"></a>Örnek Çıktı
 Bu araç herhangi bir çıktı oluşturmaz.
