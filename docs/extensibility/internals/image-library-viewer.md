---
title: Görüntü Kitaplığı Görüntüleyicisi | Microsoft Docs
description: Görüntü Visual Studio yükip bu öznitelikleri görüntülemeye ve işlemeye olanak sağlayan Görüntü Kitaplığı Görüntüleyicisi aracı hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02e7c5d5ed45b7a6c19c248e949e667ec0a1bdc0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898716"
---
# <a name="image-library-viewer"></a>Görüntü Kitaplığı Görüntüleyicisi
Görüntü Visual Studio Görüntüleyicisi aracı, görüntü bildirimlerini yükp arayarak kullanıcının bunları aynı şekilde işlemesini Visual Studio. Kullanıcı arka plan, boyutlar, DPI, yüksek karşıtlık ve diğer ayarları değiştirebilir. Araç ayrıca her görüntü bildirimi için yükleme bilgilerini ve görüntü bildiriminde her görüntünün kaynak bilgilerini görüntüler. Bu araç şu için yararlıdır:

1. Hataları tanılama

2. Özniteliklerin özel görüntü bildirimlerde doğru şekilde ayarlanmış olmasını sağlama

3. Visual Studio uzantısının Visual Studio uygun görüntüleri kullana Visual Studio Görüntü Kataloğu'Visual Studio

   ![Görüntü Kitaplığı Görüntüleyicisi Hero](../../extensibility/internals/media/image-library-viewer-hero.png "Görüntü Kitaplığı Görüntüleyicisi Hero")

   **Görüntü bilinen adı**

   Görüntü bilinen adı (veya kısaca bilinen ad), Görüntü Kitaplığı'nın görüntü varlıklarını veya görüntü listesi varlıklarını benzersiz olarak tanımlayan GUID:ID çiftidir.

   **Görüntü bildirim dosyaları**

   Görüntü bildirimi (.imagemanifest) dosyaları bir görüntü varlıkları kümesi, bu varlıkları temsil eden bilinen adlar ve her varlığı temsil eden gerçek görüntü veya görüntüler tanımlayan XML dosyalarıdır. Görüntü bildirimleri, eski kullanıcı arabirimi desteği için tek başına görüntüleri veya görüntü listelerini tanımlayabilir. Ayrıca, varlık üzerinde veya her varlığın arkasındaki tek tek görüntülerde, bu varlıkların ne zaman ve nasıl görüntülendiğinde değişmesi için ayarlanabilirsiniz.

   **Görüntü bildirimi şeması**

   Eksiksiz bir görüntü bildirimi şu şekildedir:

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

|**Alt öğesi**|**Tanım**|
|-|-|
|İçeri Aktar|Geçerli bildirimde kullanmak üzere verilen bildirim dosyasının sembollerini içeri aktarır.|
|Guid|Simgesi bir GUID'yi temsil eder ve GUID biçimlendirmesi ile eşleşmesi gerekir.|
|ID|Simgesi bir kimliği temsil eder ve bir nonnegative tamsayı olmalıdır.|
|Dize|simgesi rastgele bir dize değerini temsil eder.|

 Semboller büyük/küçük harfe duyarlıdır ve $(sembol-adı) söz dizimi kullanılarak başvurur:

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Bazı semboller tüm bildirimlerde önceden tanımlanmıştır. Bunlar, yerel makinedeki yollara başvuru yapmak için veya öğesinin Uri \<Source> \<Import> özniteliğinde kullanılabilir.

|**Sembol**|**Açıklama**|
|-|-|
|CommonProgramFiles|%CommonProgramFiles% ortam değişkeninin değeri|
|Localappdata|%LocalAppData% ortam değişkeninin değeri|
|ManifestFolder|Bildirim dosyasını içeren klasör|
|Mydocuments|Geçerli kullanıcının Belgelerim klasörünün tam yolu|
|ProgramFiles|%ProgramFiles% ortam değişkeninin değeri|
|Sistem|Windows\System32 klasörü|
|WinDir|%WinDir% ortam değişkeninin değeri|

 **Görüntü**

 \<Image>öğesi, bilinen ad tarafından başvurulebilecek bir görüntüyü tanımlar. Birlikte alınan GUID ve kimlik, görüntü bilinen adıdır. Görüntünün bilinen adı, tüm görüntü kitaplığında benzersiz olmalıdır. Birden fazla görüntüde verilen bir bilinen ad varsa, kitaplığı oluşturma sırasında karşılaşılan ilk görüntü, korunur.

 En az bir kaynak içermesi gerekir. Boyutdan bağımsız kaynaklar geniş bir boyut aralığında en iyi sonuçları verse de, bunlar gerekli değildir. Hizmet, öğesinde tanımlanmamış boyutta bir görüntü istense ve boyutdan bağımsız bir kaynak yoksa, hizmet boyuta özgü en iyi kaynağı seçer ve istenen boyuta \<Image> ölçeklendirin.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Guid|[Gerekli] Görüntü bilinen adı GUID bölümü|
|ID|[Gerekli] Görüntü bilinen değerinin kimlik bölümü|
|AllowColorInversion|[İsteğe bağlı, varsayılan true] Görüntünün renklerini koyu arka planda kullanılırken program aracılığıyla ters çevirip ters çevirenin olmadığını gösterir.|

 **Kaynak**

 öğesi \<Source> tek bir görüntü kaynak varlığı (XAML ve PNG) tanımlar.

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Urı|[Gerekli] Görüntünün nereden yüklenemiyor olduğunu tanımlayan bir URI. Şunlardan biri olabilir:<br /><br /> - Application:/// yetkilisini kullanan bir Pack [URI'sı](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br /><br /> - Mutlak bileşen kaynak başvurusu<br /><br /> - Yerel kaynak içeren bir dosyanın yolu|
|Arka Plan|[İsteğe bağlı] Kaynağın ne tür bir arka plan üzerinde kullanılmaya yönelik olduğunu gösterir.<br /><br /> Şunlardan biri olabilir:<br /><br /> - *Açık:* Kaynak, açık arka planda kullanılabilir.<br /><br /> - *Koyu:* Kaynak, koyu arka planda kullanılabilir.<br /><br /> - *HighContrast:* Kaynak, herhangi bir arka plan üzerinde herhangi bir Yüksek Karşıtlık kullanılabilir.<br /><br /> - *HighContrastLight:* Kaynak, açık bir arka plan üzerinde Yüksek Karşıtlık kullanılabilir.<br /><br /> -*HighContrastDark:* Kaynak, arka planda koyu renkli modda Yüksek Karşıtlık kullanılabilir.<br /><br /> Background **özniteliği** atlanırsa, kaynak herhangi bir arka planda kullanılabilir.<br /><br /> Arka **Plan** *Açık,* *Koyu,* *HighContrastLight* veya *HighContrastDark* ise kaynağın renkleri hiçbir zaman ters çevirilir. **Background atlanırsa** veya *HighContrast* olarak ayarlanırsa, kaynağın renklerinin ters çevirmesi görüntünün **AllowColorInversion** özniteliği tarafından denetlenr.|

 Bir \<Source> öğe, aşağıdaki isteğe bağlı alt öğelerden tam olarak biri olabilir:

|**Öğe**|**Öznitelikler (tüm gerekli)**|**Tanım**|
|-|-|-|
|\<Size>|Değer|Kaynak, verilen boyuttaki görüntüler (cihaz birimlerinde) için kullanılır. Görüntü kare olur.|
|\<SizeRange>|MinSize, MaxSize|Kaynak, MinSize'dan MaxSize'a (cihaz birimlerinde) dahil görüntüler için kullanılır. Görüntü kare olur.|
|\<Dimensions>|Genişlik, Yükseklik|Kaynak, verilen genişlik ve yükseklik (cihaz birimleri) görüntüleri için kullanılır.|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Kaynak, minimum genişlik/yükseklik ile en yüksek genişlik/yükseklik (cihaz birimleri olarak) arasında bir değere kadar olan görüntüler için kullanılır.|

 Bir öğe, yönetilen bir derleme yerine yerel bir derlemeden yüklenen bir tanımlayan isteğe bağlı \<Source> bir alt öğesi de \<NativeResource> \<Source> olabilir.

```xml
<NativeResource Type="type" ID="int" />
```

|**Öznitelik**|**Tanım**|
|-|-|
|Tür|[Gerekli] Yerel kaynağın türü (XAML veya PNG)|
|ID|[Gerekli] Yerel kaynağın tamsayı kimliği bölümü|

 **ımagelist**

 \<ImageList>öğesi, tek bir şeritte döndürülen görüntü koleksiyonunu tanımlar. Şerit, gerektiğinde isteğe bağlı olarak inşa edilmiştir.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Guid|[Gerekli] Görüntü bilinen adı GUID bölümü|
|ID|[Gerekli] Görüntü bilinen değerinin kimlik bölümü|
|Dış|[İsteğe bağlı, varsayılan false] Görüntü bilinen adı'nın geçerli bildirimdeki bir görüntüye başvurarak başvurup gönderme olmadığını gösterir.|

 Bulunan görüntünün bilinen adı, geçerli bildirimde tanımlanan bir görüntüye başvurarak kullanılamaz. Bulunan görüntü görüntü kitaplığında bulunamazsa yerine boş bir yer tutucu görüntü kullanılır.

## <a name="how-to-use-the-tool"></a>Aracı kullanma
 **Özel görüntü bildirimini doğrulama**

 Özel bir bildirim oluşturmak için ManifestFromResources aracını kullanarak bildirimi otomatik olarak oluşturmanızı öneririz. Özel bildirimi doğrulamak için Görüntü Kitaplığı Görüntüleyicisi'ni açın ve Dosya Kitaplığı Yolunu Ayarla... >'yi seçin. arama dizinleri iletişim kutusunu açın. Araç, görüntü bildirimlerini yüklemek için arama dizinlerini kullanır, ancak bunları kullanarak bir bildirimde görüntüleri içeren .dll dosyalarını da bulur, bu nedenle hem bildirim hem de DLL dizinlerini bu iletişim kutusuna dahil edin.

 ![Görüntü Kitaplığı Görüntüleyici arama](../../extensibility/internals/media/image-library-viewer-search.png "Görüntü Kitaplığı Görüntüleyici arama")

 Bildirim ve ilgili URL'leri aramak için **Ekle...** seçeneğine tıklar ve yeni arama dizinlerini seçin. Araç bu arama dizinlerini anımsar ve bir dizin denetlenerek veya işaretini kaldırarak açık veya kapalı olabilir.

 Varsayılan olarak, araç yükleme dizinini Visual Studio ve bu dizinleri arama dizinleri listesine eklemeye girişiminde bulunur. Aracın bulamadıları dizinleri el ile ekleyebilirsiniz.

 Tüm bildirim yüklendiktan sonra, kullanıcı çeşitli ayarlar için  doğru şekilde işleniyor olduğunu  doğrulamak üzere görüntü varlıklarını görsel olarak inceleyene kadar, arka plan renklerini, **DPI'yi,** yüksek karşıtlığı veya görüntüler için gri ölçeklendirmeyi değiştirmek için araç kullanılabilir.

 ![Görüntü Kitaplığı Görüntüleyicisi Arka Planı](../../extensibility/internals/media/image-library-viewer-background.png "Görüntü Kitaplığı Görüntüleyicisi Arka Planı")

 Arka plan rengi Açık, Koyu veya özel bir değer olarak ayarlanmış olabilir. "Özel Renk"i seçmek bir renk seçimi iletişim kutusu açar ve daha sonra kolayca anımsanma için bu özel rengi arka plan birleşik giriş kutusunun en altına ekler.

 ![Görüntü Kitaplığı Görüntüleyicisi Özel Rengi](../../extensibility/internals/media/image-library-viewer-custom-color.png "Görüntü Kitaplığı Görüntüleyicisi Özel Rengi")

 Bir görüntü bilinen adı seçmek, bu bilinen adın arkasındaki her gerçek görüntüye ilişkin bilgileri sağ bölmede Görüntü Ayrıntıları bölmesinde görüntüler. Bölme ayrıca kullanıcıların bir bilinen adı adına veya ham GUID:ID değerine göre kopyalamalarına da olanak sağlar.

 ![Görüntü Kitaplığı Görüntüleyicisi Görüntü Ayrıntıları](../../extensibility/internals/media/image-library-viewer-image-details.png "Görüntü Kitaplığı Görüntüleyicisi Görüntü Ayrıntıları")

 Her görüntü kaynağı için görüntülenen bilgiler, ne tür bir arka plan görüntülendiğinden, Yüksek Karşıtlık'i destekleyip destekleyene, hangi boyutlar için geçerli olduğunu veya boyuttan bağımsız olup olmadığını ve görüntünün yerel bir derlemeden gelip olmadığını içerir.

 ![Görüntü Kitaplığı Görüntüleyicisi Tema Olarak Ekleyebilirsiniz](../../extensibility/internals/media/image-library-viewer-can-theme.png "Görüntü Kitaplığı Görüntüleyicisi Tema Olarak Ekleyebilirsiniz")

 Bir görüntü bildirimini doğrularken, bildirim ve görüntü DLL'sini gerçek dünya konumlarına dağıtmanız önerilir. Bu, tüm göreli yolların düzgün çalıştığını ve görüntü kitaplığının bildirim ile görüntü DLL'sini bulup yükleyemediklerini doğrular.

 **Bilinen Bilinen Adlar görüntü kataloğunu arama**

 Bir Visual Studio daha iyi eşleşmesi için, Visual Studio uzantısı kendi Visual Studio oluşturmak ve kullanmak yerine Visual Studio Görüntü Kataloğu'daki görüntüleri kullanabilir. Bu, bu görüntülerin bakımını yapmak zorunda kalmama avantajına sahip olur ve görüntünün yüksek DPI destekleyen bir görüntüye sahip olacağını garantiler, böylece görüntünün desteklediği tüm DPI ayarlarında doğru Visual Studio olur.

 Görüntü kitaplığı görüntüleyicisi, bir kullanıcının bir görüntü varlığı temsil eden bilinen adı bularak kodda bu bilinen adı kullana bir bildirimin aranmalarını sağlar. Görüntüleri aramak için arama kutusuna istediğiniz arama terimini girin ve Enter tuşuna basın. Alttaki durum çubuğu, bildirimlerin tamamında yer alan toplam görüntülerden kaç eşleşme olduğunu gösterir.

 ![Görüntü Kitaplığı Görüntüleyici Filtresi](../../extensibility/internals/media/image-library-viewer-filter.png "Görüntü Kitaplığı Görüntüleyici Filtresi")

 Mevcut bildirimlerde görüntü bilinen adlarını ararken, yalnızca Visual Studio Görüntü Kataloğu'nun bilinen adlarını, kasıtlı olarak genel olarak erişilebilen diğer bilinen adlar veya kendi özel bilinen adlarınızı aramanızı ve kullanmanızı öneririz. Yayımlanmamış bilinen adlar kullanıyorsanız, özel kullanıcı arabirimi bozuk olabilir veya bu yayımlanmamış bilinen adlar ve görüntüler değiştirildiği ya da güncelleştirildiği zaman özel kullanıcı arabiriminin görüntülerinin beklenmedik şekilde değiştirilmiş olması gerekir.

 Ayrıca GUID'ye göre arama da mümkündür. Bu tür bir arama, listeyi tek bir bildirime veya birden çok GUID içeriyorsa bir bildirimin tek alt bölüme filtrelemek için kullanışlıdır.

 ![Görüntü Kitaplığı Görüntüleyici Filtresi GUID'si](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Görüntü Kitaplığı Görüntüleyici Filtresi GUID'si")

 Son olarak, kimlikle arama da mümkündür.

 ![Görüntü Kitaplığı Görüntüleyicisi Filtre Kimliği](../../extensibility/internals/media/image-library-viewer-filter-id.png "Görüntü Kitaplığı Görüntüleyicisi Filtre Kimliği")

## <a name="notes"></a>Notlar

- Varsayılan olarak, araç yükleme dizininde mevcut olan çeşitli Visual Studio çeker. Genel olarak değiştirilebilir bilinen adlara sahip olan tek **ad, Microsoft.VisualStudio.ImageCatalog bildirimidir.** GUID: ae27a6b0-e345-4288-96df-5eaf394ee369  (özel bir bildirimde bu GUID'yi geçersiz kılma) Tür: KnownMonikers

- Araç, bulduğu tüm görüntü bildirimlerini yüklemek için başlatmayı dener, bu nedenle uygulamanın gerçekten görünmesi birkaç saniye sürebilir. Bildirimleri yüklerken de yavaş veya yanıt vermiyor olabilir.

## <a name="sample-output"></a>Örnek Çıktı
 Bu araç herhangi bir çıkış oluşturmaz.
