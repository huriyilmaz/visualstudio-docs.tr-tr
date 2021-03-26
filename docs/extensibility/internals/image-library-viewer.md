---
title: Görüntü Kitaplığı Görüntüleyici | Microsoft Docs
description: Görüntü bildirimlerini yükleyen ve aradığı ve görüntü özniteliklerini görüntülemenize ve değiştirmenize olanak tanıyan Visual Studio Görüntü Kitaplığı Görüntüleyicisi aracı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d60443e97bc557bc964d59750417b2662e4c3c8f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085981"
---
# <a name="image-library-viewer"></a>Görüntü Kitaplığı Görüntüleyicisi
Visual Studio Görüntü Kitaplığı Görüntüleyicisi Aracı, görüntü bildirimleri yükleyip arayabilir ve bu sayede, kullanıcının bunları Visual Studio ile aynı şekilde değiştirmesine izin verebilirsiniz. Kullanıcı arka plan, boyut, DPı, yüksek karşıtlık ve diğer ayarları değiştirebilir. Araç ayrıca her görüntü bildirimi için bilgileri yükleme ve görüntü bildirimindeki her bir görüntü için kaynak bilgilerini görüntüler. Bu araç için yararlı olur:

1. Hataları tanılama

2. Özel görüntü bildirimlerinde özniteliklerin doğru şekilde ayarlandığından emin olma

3. Visual Studio görüntü kataloğunda, Visual Studio uzantısının Visual Studio 'nun stiline uyan görüntüleri kullanabilmesi için resimleri arama

   ![Görüntü Kitaplığı Görüntüleyicisi Hero](../../extensibility/internals/media/image-library-viewer-hero.png "Görüntü Kitaplığı Görüntüleyicisi Hero")

   **Görüntü bilinen adı**

   Resim bilinen adı (veya Short için bilinen ad), görüntü kitaplığındaki bir görüntü varlığını veya görüntü listesi varlığını benzersiz şekilde tanımlayan bir GUID: ID çiftidir.

   **Görüntü bildirim dosyaları**

   Görüntü bildirimi (. ımagemanifest) dosyaları, bir görüntü varlıkları kümesini, bu varlıkları temsil eden bilinen adları ve her bir varlığı temsil eden gerçek görüntüyü ya da görüntüleri tanımlayan XML dosyalarıdır. Görüntü bildirimleri, eski Kullanıcı arabirimi desteği için tek başına görüntüleri veya görüntü listelerini tanımlayabilir. Ayrıca, varlık üzerinde veya her bir kıymetin arkasındaki ayrı görüntülerde ayarlanabilir öznitelikler vardır ve bu varlıkların ne zaman ve nasıl görüntüleneceğini değiştirebilirsiniz.

   **Görüntü bildirim şeması**

   Tüm görüntü bildirimi şöyle görünür:

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

 **Symbols**

 Bir okunabilirlik ve bakım Yardımcısı olarak, görüntü bildirimi öznitelik değerleri için semboller kullanabilir. Semboller şöyle tanımlanır:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**Subelement**|**Tanım**|
|-|-|
|İçeri Aktar|Geçerli bildirimde kullanılmak üzere verilen bildirim dosyasının sembollerini içeri aktarır.|
|Guid|Sembol bir GUID 'YI temsil eder ve GUID biçimlendirmesine uymalıdır.|
|ID|Sembol bir KIMLIĞI temsil eder ve negatif olmayan bir tamsayı olmalıdır.|
|Dize|Sembol rastgele bir dize değerini temsil eder.|

 Semboller büyük/küçük harfe duyarlıdır ve $ (sembol-adı) sözdizimi kullanılarak başvurulur:

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Bazı semboller tüm bildirimler için önceden tanımlanmıştır. Bunlar, \<Source> veya öğesinin URI özniteliğinde \<Import> yerel makinedeki yollara başvurmak için kullanılabilir.

|**Sembol**|**Açıklama**|
|-|-|
|CommonProgramFiles|% CommonProgramFiles% ortam değişkeninin değeri|
|LocalAppData|% LocalAppData% ortam değişkeninin değeri|
|ManifestFolder|Bildirim dosyasını içeren klasör|
|MyDocuments|Geçerli kullanıcının Belgelerim klasörünün tam yolu|
|ProgramFiles|% ProgramFiles% ortam değişkeninin değeri|
|Sistem|Windows\System32 klasörü|
|Dizini|% WinDir% ortam değişkeninin değeri|

 **Görüntü**

 \<Image>Öğesi, bir bilinen ad tarafından başvurulabilen bir görüntü tanımlar. Birlikte alınan GUID ve ID, görüntü bilinen adını oluşturur. Görüntünün bilinen adı, tüm görüntü kitaplığı genelinde benzersiz olmalıdır. Birden fazla görüntüde bilinen bir ad varsa, kitaplığı oluştururken karşılaşılan ilk, korunan bir addır.

 En az bir kaynak içermesi gerekir. Boyut nötr kaynaklar çok çeşitli boyutlarda en iyi sonuçları verecektir, ancak bu zorunlu değildir. Hizmette, öğesinde tanımlı olmayan bir boyut görüntüsü istenirse \<Image> ve bir boyut nötr kaynağı yoksa, hizmet en iyi boyuta özgü kaynağı seçer ve istenen boyuta göre ölçeklendirirsiniz.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Guid|Istenir Görüntü adının GUID bölümü|
|ID|Istenir Görüntü adının KIMLIK kısmı|
|Allowcolorınversion|[İsteğe bağlı, varsayılan doğru] Görüntünün, koyu bir arka planda kullanıldığında, renkleri program aracılığıyla ters çevrimeyeceğini gösterir.|

 **Kaynak**

 \<Source>Öğesi, tek bir görüntü kaynağı varlığını (XAML ve PNG) tanımlar.

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Kullanılmamışsa|Istenir Görüntünün nereden yüklenebileceğini tanımlayan bir URI. Şunlardan biri olabilir:<br /><br /> -Application:///yetkilisini kullanan bir [paket URI 'si](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br /><br /> -Mutlak bir bileşen kaynağı başvurusu<br /><br /> -Yerel kaynak içeren bir dosyanın yolu|
|Arka Plan|Seçim Kaynağın kullanılması amaçlanan arka plan türünü gösterir.<br /><br /> Şunlardan biri olabilir:<br /><br /> - *Işık*: kaynak açık bir arka planda kullanılabilir.<br /><br /> - *Koyu*: kaynak koyu bir arka planda kullanılabilir.<br /><br /> - *Highkarşıtlıklı*: kaynak yüksek karşıtlık modundaki herhangi bir arka planda kullanılabilir.<br /><br /> - *Highdeğişken Stlight*: kaynak yüksek karşıtlık modundaki hafif bir arka planda kullanılabilir.<br /><br /> -Üst *sınır*: kaynak, yüksek karşıtlık modunda koyu bir arka planda kullanılabilir.<br /><br /> **Arka plan** özniteliği atlanırsa, kaynak herhangi bir arka planda kullanılabilir.<br /><br /> **Arka plan** hafif, *koyu*, *Ince* bir *şekilde veya daha* *ince*, kaynak renkleri hiçbir şekilde ters çevrilmez. **Arka plan** atlanırsa veya *highkontrast* olarak ayarlandıysa, kaynak renklerinin Inversion değeri görüntünün **allowcolorınversion** özniteliği tarafından denetlenir.|

 Bir \<Source> öğe, aşağıdaki isteğe bağlı alt öğeler için tam olarak birine sahip olabilir:

|**Öğe**|**Öznitelikler (tüm gerekli)**|**Tanım**|
|-|-|-|
|\<Size>|Değer|Kaynak, verilen boyutun (cihaz birimlerinde) görüntüleri için kullanılacaktır. Resim kare olacak.|
|\<SizeRange>|MinSize, MaxSize|Kaynak, MinSize ' den MaxSize 'a (cihaz birimlerinde) dahil olmak üzere, dahil edilecek görüntüler için kullanılacaktır. Resim kare olacak.|
|\<Dimensions>|Genişlik, yükseklik|Kaynak, belirtilen genişlik ve yüksekliğin (cihaz birimlerinde) görüntüleri için kullanılacaktır.|
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

 Özel bir bildirim oluşturmak için, bildirimi AutoGenerate için ManifestFromResources aracını kullanmanız önerilir. Özel bildirimi doğrulamak için, görüntü kitaplığı görüntüleyicisini başlatın ve dosya > yolu ayarla... seçeneğini belirleyin. Dizin Ara iletişim kutusunu açmak için. Araç, görüntü bildirimleri yüklemek için arama dizinlerini kullanır, ancak aynı zamanda bir bildirimde bulunan görüntüleri içeren. dll dosyalarını bulmak için bu iletişim kutusunu kullanacaktır, bu nedenle bu iletişim kutusunda hem bildirim hem de DLL dizinlerini eklediğinizden emin olun.

 ![Görüntü Kitaplığı Görüntüleyicisi arama](../../extensibility/internals/media/image-library-viewer-search.png "Görüntü Kitaplığı Görüntüleyicisi arama")

 Bildirimleri ve bunlara karşılık gelen DLL 'Leri aramak üzere yeni arama dizinleri seçmek için **Ekle...** ' ye tıklayın. Araç bu arama dizinlerini hatırlayacaktır ve bir dizini denetleyerek veya denetleyerek devre dışı bırakabilirsiniz.

 Araç, varsayılan olarak Visual Studio install dizinini bulmaya çalışır ve bu dizinleri arama dizinleri listesine ekler. Aracın bulamadığı dizinleri el ile ekleyebilirsiniz.

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

 Visual Studio stilini daha iyi eşleştirmek için, Visual Studio uzantısı kendi oluşturup kullanmak yerine Visual Studio görüntü kataloğunda görüntüleri kullanabilir. Bu, bu görüntüleri sürdürmeme avantajına sahiptir ve görüntünün, Visual Studio 'Nun desteklediği tüm DPı ayarlarında doğru görünmesi için yüksek DPı olan bir yedekleme görüntüsüne sahip olmasını güvence altına alır.

 Görüntü Kitaplığı Görüntüleyicisi, bir kullanıcının bir görüntü varlığını temsil eden bilinen adı bulabilmesi ve bu bilinen adı kodda kullanması için bir bildirimin aranmasına olanak tanır. Görüntü aramak için, arama kutusuna istenen arama terimini girin ve ENTER tuşuna basın. En alttaki durum çubuğunda, tüm bildirimlerde toplam görüntüden kaç eşleşme bulunmuştur görüntülenir.

 ![Görüntü Kitaplığı Görüntüleyicisi filtresi](../../extensibility/internals/media/image-library-viewer-filter.png "Görüntü Kitaplığı Görüntüleyicisi filtresi")

 Mevcut bildirimlerdeki görüntü takma adlarını ararken, yalnızca Visual Studio görüntü kataloğu 'nun bilinen adlarını, diğer kasıtlı olarak erişilebilen diğer adları veya kendi özel takma adlarını aramanızı ve kullanmanızı öneririz. Ortak bilinen adlar kullanırsanız, özel kullanıcı arabirimi bozulmuş olabilir veya bu ortak adlar ve görüntüler değiştirildiğinde veya güncelleştirilirse, görüntülerinin beklenmedik yollarla değiştirilmesini sağlayabilirsiniz.

 Ayrıca, GUID 'ye göre arama mümkündür. Bu arama türü, bildirim birden çok GUID içeriyorsa listenin tek bir bildirime veya bir bildirimin tek alt bölümüne göre filtrelemek için yararlıdır.

 ![Görüntü Kitaplığı Görüntüleyicisi filtre GUID 'SI](../../extensibility/internals/media/image-library-viewer-filter-guid.png "Görüntü Kitaplığı Görüntüleyicisi filtre GUID 'SI")

 Son olarak, KIMLIĞE göre arama da mümkündür.

 ![Görüntü Kitaplığı Görüntüleyicisi filtre KIMLIĞI](../../extensibility/internals/media/image-library-viewer-filter-id.png "Görüntü Kitaplığı Görüntüleyicisi filtre KIMLIĞI")

## <a name="notes"></a>Notlar

- Araç, varsayılan olarak Visual Studio Install dizininde birçok görüntü bildirimini çeker. **Microsoft. VisualStudio. ımagecatalog** bildirimi, genel olarak tüketilebilir bilinen adlar olan tek bir addır. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (özel bir bildirimde bu GUID **'yi geçersiz kılma** ) tür: knowntakma adlar

- Araç, bulduğu tüm görüntü bildirimlerini yüklemeye çalışır, bu nedenle uygulamanın gerçekten görünmesi birkaç saniye sürebilir. Bildirimler yüklenirken de yavaş veya yanıt vermiyor olabilir.

## <a name="sample-output"></a>Örnek Çıktı
 Bu araç herhangi bir çıktı oluşturmaz.
