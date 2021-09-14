---
title: Görüntü Kitaplığı Görüntüleyicisi | Microsoft Docs
description: Görüntü Visual Studio yükip bu öznitelikleri görüntülemeye ve işlemeye olanak sağlayan görüntü kitaplığı görüntüleyicisi aracı hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ee92f235bc973d0929e89ceae8d24f8ca77b9865
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725781"
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

   Görüntü bildirimi (.imagemanifest) dosyaları bir görüntü varlıkları kümesi tanımlayan XML dosyaları, bu varlıkları temsil eden bilinen adlar ve her varlığı temsil eden gerçek görüntü veya görüntülerdir. Görüntü bildirimleri, eski kullanıcı arabirimi desteği için tek başına görüntüleri veya görüntü listelerini tanımlayabilir. Ayrıca, varlık üzerinde veya her varlığın arkasındaki tek tek görüntülerde, bu varlıkların ne zaman ve nasıl görüntülendiğinde değişmesi için ayarlan bir öznitelikler vardır.

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

 Simgeler büyük/küçük harfe duyarlıdır ve $(sembol-adı) söz dizimi kullanılarak başvurur:

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

 En az bir kaynak içermesi gerekir. Boyutdan bağımsız kaynaklar geniş bir boyut aralığında en iyi sonuçları verse de, bunlar gerekli değildir. Hizmet, öğesinde tanımlanmamış boyutta bir görüntü istense ve boyutdan bağımsız bir kaynak yoksa, hizmet boyuta özgü en iyi kaynağı seçer ve istenen \<Image> boyuta ölçeklendirin.

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
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Kaynak, en düşük genişlik/yükseklikten (cihaz birimleri cinsinden) en fazla genişlik/yükseklik arasındaki görüntüler için kullanılacaktır.|

 Bir \<Source> öğesi \<NativeResource> , \<Source> yönetilen bir derleme yerine yerel bir derlemeden yüklenen bir öğesini tanımlayan isteğe bağlı bir alt öğesi de olabilir.

```xml
<NativeResource Type="type" ID="int" />
```

|**Öznitelik**|**Tanım**|
|-|-|
|Tür|Istenir Yerel kaynağın türü, XAML veya PNG|
|ID|Istenir Yerel kaynağın tamsayı KIMLIĞI bölümü|

 **'I**

 \<ImageList>Öğesi, tek bir şeridinde döndürülebilecek bir görüntü koleksiyonunu tanımlar. Şerit gerektiğinde isteğe bağlı olarak oluşturulur.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Guid|Istenir Görüntü adının GUID bölümü|
|ID|Istenir Görüntü adının KIMLIK kısmı|
|Dış|[İsteğe bağlı, varsayılan yanlış] Resim adının geçerli bildirimde bir görüntüye başvuruda bulunup bulunmadığını gösterir.|

 İçerilen görüntünün bilinen adı, geçerli bildirimde tanımlanan bir görüntüye başvurmak zorunda değildir. İçerilen görüntü görüntü kitaplığında bulunamazsa, yerine boş bir yer tutucu görüntüsü kullanılır.

## <a name="how-to-use-the-tool"></a>Aracı kullanma
 **Özel görüntü bildirimini doğrulama**

 Özel bir bildirim oluşturmak için, bildirimi AutoGenerate için ManifestFromResources aracını kullanmanız önerilir. Özel bildirimi doğrulamak için, görüntü kitaplığı görüntüleyicisini başlatın ve dosya > yolu ayarla... seçeneğini belirleyin. Dizin Ara iletişim kutusunu açmak için. Araç, görüntü bildirimleri yüklemek için arama dizinlerini kullanır, ancak aynı zamanda bir bildirimde bulunan görüntüleri içeren .dll dosyalarını bulmak için bu iletişim kutusunu kullanacaktır, bu nedenle bu iletişim kutusunda hem bildirim hem de DLL dizinlerini eklediğinizden emin olun.

 ![Görüntü Kitaplığı Görüntüleyicisi arama](../../extensibility/internals/media/image-library-viewer-search.png "Görüntü Kitaplığı Görüntüleyicisi arama")

 Bildirimleri ve bunlara karşılık gelen DLL 'Leri aramak üzere yeni arama dizinleri seçmek için **Ekle...** ' ye tıklayın. Araç bu arama dizinlerini hatırlayacaktır ve bir dizini denetleyerek veya denetleyerek devre dışı bırakabilirsiniz.

 araç varsayılan olarak, Visual Studio install dizinini bulmaya çalışır ve bu dizinleri arama dizinleri listesine ekler. Aracın bulamadığı dizinleri el ile ekleyebilirsiniz.

 Tüm bildirimler yüklendikten sonra, bir kullanıcının çeşitli ayarlar için doğru şekilde işlenip işlenmeyeceğini doğrulamak üzere görüntü varlıklarını görsel olarak inceleyebilmesi için **arka plan** renklerini, **DPI**, **yüksek karşıtlık** veya **gri ölçeklendirmeyi** değiştirmek için araç kullanılabilir.

 ![Görüntü Kitaplığı Görüntüleyicisi arka planı](../../extensibility/internals/media/image-library-viewer-background.png "Görüntü Kitaplığı Görüntüleyicisi arka planı")

 Arka plan rengi, ışık, koyu veya özel bir değere ayarlanabilir. "Özel renk" seçildiğinde, bir renk seçim iletişim kutusu açılır ve daha sonra kolayca geri çekmek için arka plan Birleşik giriş kutusunun altına özel renk eklenir.

 ![Görüntü Kitaplığı Görüntüleyicisi özel rengi](../../extensibility/internals/media/image-library-viewer-custom-color.png "Görüntü Kitaplığı Görüntüleyicisi özel rengi")

 Görüntü bilinen adı seçildiğinde, sağ taraftaki görüntü ayrıntıları bölmesinde söz konusu bilinen her bir görüntüye ait bilgiler görüntülenir. Bölmesi ayrıca, kullanıcıların bir adı ada veya ham GUID: ID değerine göre kopyalamasını sağlar.

 ![Görüntü Kitaplığı Görüntüleyicisi görüntü ayrıntıları](../../extensibility/internals/media/image-library-viewer-image-details.png "Görüntü Kitaplığı Görüntüleyicisi görüntü ayrıntıları")

 Her görüntü kaynağı için görüntülenen bilgiler, bu dosyanın ne tür bir arka plan olduğunu, tema uygulanıp erişemeyeceğini veya Yüksek Karşıtlık destekleyip desteklemediğini, ne kadar geçerli olduğunu veya boyutun bağımsız olduğunu ve görüntünün yerel bir derlemeden geldiğini gösterir.

 ![Görüntü Kitaplığı Görüntüleyicisi teması olabilir](../../extensibility/internals/media/image-library-viewer-can-theme.png "Görüntü Kitaplığı Görüntüleyicisi teması olabilir")

 Bir görüntü bildirimi doğrulanırken, bildirim ve görüntü DLL 'sini gerçek dünya konumlarında dağıtmanızı öneririz. Bu, tüm göreli yolların doğru çalıştığını ve görüntü kitaplığının bildirim ve görüntü DLL 'sini bulup yükleyebildiğini doğrular.

 **Image Catalog Knowntakma adları aranıyor**

 Visual Studio stillendirme daha iyi eşleştirmek için, bir Visual Studio uzantısı, kendisini oluşturmak ve kullanmak yerine Visual Studio görüntü kataloğunda görüntüleri kullanabilir. bu, bu görüntüleri sürdürmeme avantajına sahiptir ve görüntünün, Visual Studio desteklediği tüm dpı ayarlarında doğru görünmesi için yüksek dpı olan bir yedekleme görüntüsüne sahip olmasını güvence altına alır.

 Görüntü Kitaplığı Görüntüleyicisi, bir kullanıcının bir görüntü varlığını temsil eden bilinen adı bulabilmesi ve bu bilinen adı kodda kullanması için bir bildirimin aranmasına olanak tanır. Görüntü aramak için, arama kutusuna istenen arama terimini girin ve ENTER tuşuna basın. En alttaki durum çubuğunda, tüm bildirimlerde toplam görüntüden kaç eşleşme bulunmuştur görüntülenir.

 ![Görüntü Kitaplığı Görüntüleyicisi filtresi](../../extensibility/internals/media/image-library-viewer-filter.png "Görüntü Kitaplığı Görüntüleyicisi filtresi")

 mevcut bildirimlerdeki görüntü takma adlarını ararken, yalnızca Visual Studio görüntü kataloğunun bilinen adlarını, diğer kasıtlı olarak erişilebilen diğer adları veya kendi özel ad alanınızı aramanızı ve kullanmanızı öneririz. Ortak bilinen adlar kullanırsanız, özel kullanıcı arabirimi bozulmuş olabilir veya bu ortak adlar ve görüntüler değiştirildiğinde veya güncelleştirilirse, görüntülerinin beklenmedik yollarla değiştirilmesini sağlayabilirsiniz.

 Ayrıca, GUID 'ye göre arama mümkündür. Bu arama türü, bildirim birden çok GUID içeriyorsa listenin tek bir bildirime veya bir bildirimin tek alt bölümüne göre filtrelemek için yararlıdır.

 ![Görüntü Kitaplığı Görüntüleyicisi filtre GUID 'SI](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Görüntü Kitaplığı Görüntüleyicisi filtre GUID 'SI")

 Son olarak, KIMLIĞE göre arama da mümkündür.

 ![Görüntü Kitaplığı Görüntüleyicisi filtre KIMLIĞI](../../extensibility/internals/media/image-library-viewer-filter-id.png "Görüntü Kitaplığı Görüntüleyicisi filtre KIMLIĞI")

## <a name="notes"></a>Notlar

- araç, varsayılan olarak, Visual Studio install dizininde bulunan birçok görüntü bildirimini çeker. **Microsoft. VisualStudio. ımagecatalog** bildirimi, genel olarak tüketilebilir bilinen adlar olan tek bir addır. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (özel bir bildirimde bu GUID **'yi geçersiz kılma** ) tür: knowntakma adlar

- Araç, bulduğu tüm görüntü bildirimlerini yüklemeye çalışır, bu nedenle uygulamanın gerçekten görünmesi birkaç saniye sürebilir. Bildirimler yüklenirken de yavaş veya yanıt vermiyor olabilir.

## <a name="sample-output"></a>Örnek Çıktı
 Bu araç herhangi bir çıktı oluşturmaz.
