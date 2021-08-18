---
title: .NET nesneleri için bellek kullanımını analiz | Microsoft Docs
description: .NET Nesne Ayırma aracını kullanarak, uygulamanın ne kadar bellek kullandığını ve hangi kod yollarının en çok bellek ayır yaptığını görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 12/9/2019
ms.topic: how-to
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 1e44cadb3edb0d91b760b1827df3d8aa8fb3dbbd18190edb0eb18f2d2cf16ff6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442907"
---
# <a name="analyze-memory-usage-by-using-the-net-object-allocation-tool"></a>.NET Nesne Ayırma aracını kullanarak bellek kullanımını analiz etme

.NET Nesne Ayırma aracını kullanarak, uygulamanın ne kadar bellek kullandığını ve hangi kod yollarının en çok bellek ayır yaptığını anabilirsiniz.

Aracı çalıştırdıktan sonra, nesnelerin ayrılmış olduğu işlev yürütme yollarını görebilir. Daha sonra en fazla belleği alan çağrı ağacının kökünü geriye doğru takip etmek için geri dönerek.

## <a name="setup"></a>Kurulum

1. **Alt+F2'yi** seçerek Performans Profili Oluşturucu'Visual Studio.

1. **.NET Nesne Ayırma İzleme onay** kutusunu seçin.

   ![Dotnet Nesne Ayırma İzleme aracı seçildi](../profiling/media/dotnetalloctoolselected.png "Dotnet Nesne Ayırma İzleme aracı seçildi")

1. Aracı **çalıştırmak** için Başlat düğmesini seçin.

1. Araç çalışmaya başladıktan sonra uygulamanıza profil oluşturmak istediğiniz senaryoyu takip edin. Ardından Koleksiyonu **durdur'ı** seçin veya verilerinizi görmek için uygulamanızı kapatın.

   ![Koleksiyonu durdur'ları gösteren pencere](../profiling/media/stopcollectionlighttheme.png "Koleksiyonu durdur'ları gösteren pencere")

1. Ayırma **sekmesini** seçin. Aşağıdaki ekran görüntüsüne benzer pencere içerikleri görüntülenir.

   ![Ayırma sekmesi](../profiling/media/allocationview.png "Ayırma sekmesi")

Artık nesnelerin bellek ayırmasını analizebilirsiniz.

Toplama sırasında, izleme aracı profili yapılan uygulamayı yavaşlatabilirsiniz. İzleme aracının veya uygulamanın performansı yavaşsa ve her nesneyi izlemenizi gerektir yoksa örnekleme oranını ayarlayabilirsiniz. Bunu yapmak için profil oluşturma özeti sayfasında izleme aracının yanındaki dişli simgesini seçin.

![Ayarlar Dotnet Ayırma aracı için yeni bir araç](../profiling/media/dotnetallocsettings.png "Ayarlar Dotnet Ayırma aracı için yeni bir araç")

Örnekleme oranını istediğiniz hıza ayarlayın. Bu değişiklik, toplama ve analiz sırasında uygulama performansının hızlandır toplanmasına yardımcı olur.

![Ayarlanmış örnekleme oranı](../profiling/media/adjustedsamplingratedotnetalloctool.png "Ayarlanmış örnekleme oranı")

Aracı daha verimli hale getirme hakkında daha fazla bilgi için bkz. [Profiler ayarlarını iyileştirme.](../profiling/optimize-profiler-settings.md)

## <a name="understand-your-data"></a>Verilerinizi anlama

![Dotnet Ayırma aracı için grafik](../profiling/media/graphdotnetalloc.png "Dotnet Ayırma aracı için grafik")

Yukarıdaki grafik görünümünde üst grafikte uygulamadaki canlı nesnelerin sayısı gösterilir. En **alttaki Nesne delta** grafiği, uygulama nesnelerinin yüzde değişikliğini gösterir. Kırmızı çubuklar, çöp toplamanın ne zaman olduğunu ifade ediyor.

![Dotnet Ayırma zamanlarının filtrelenmiş grafiği](../profiling/media/graphdotnetalloctimefiltered.png "Dotnet Ayırma zamanlarının filtrelenmiş grafiği")

Tablosal verileri yalnızca belirli bir zaman aralığına göre etkinlik görüntülemek üzere filtreleyebilirsiniz. Ayrıca grafı yakınlaştırabilir veya uzaklaştırabilirsiniz.

### <a name="allocation"></a>Ayırma

![Genişletilmiş Ayırma görünümü](../profiling/media/allocationexpandedlight.png "Genişletilmiş ayırma görünümü")

Ayırma **görünümü,** bellek tahsis eden nesnelerin konumunu ve bu nesnelerin ne kadar bellek ayırmasını gösterir.

- Tür **sütunu,** bellek alan sınıfların ve yapıların listesidir. Geri izlemesini ters çağrı ağacı olarak görüntülemek için bir türe çift tıklayın. Yalnızca **Ayırma** görünümünde, seçilen kategori içinde bellek alan öğeleri görüntüebilirsiniz.

- Ayırmalar **sütunu,** belirli bir ayırma türü veya işlevi içinde bellek alan nesne sayısını gösterir. Bu sütun yalnızca Ayırma, **Çağrı** Ağacı **ve İşlevler** **görünümlerde** görünür.

- Bayt **ve** **Ortalama Boyut (Bayt)** sütunları varsayılan olarak görünmez. Bunları göstermek için Tür  veya  Ayırmalar sütununa sağ  tıklayın ve ardından Baytlar ve Ortalama Boyut **(Bayt)** seçeneklerini seçerek bunları grafikte ekleyin. 

   İki sütun Toplam **(Ayırmalar)** ve Kendi **Kendine (Ayırmalar)** sütunlarına benzer, ancak bunlar bellek alan nesne sayısı yerine alınan bellek miktarını gösterir. Bu sütunlar yalnızca Ayırma **görünümünde** görünür.

- Modül **adı sütunu,** çağıran işlevi veya işlemi içeren modülü gösterir.

Bu sütunların hepsi sıralanabilir. Tür **ve Modül** **Adı sütunları** için öğeleri artan veya azalan düzende alfabetik olarak sıralayabilirsiniz. **Ayırmalar,** **Baytlar** ve **Ortalama Boyut (Bayt)** için, öğeleri sayısal değeri artırarak veya azaltarak sıraabilirsiniz.

#### <a name="symbols"></a>Simgeleri

Ayırma, Çağrı Ağacı ve **İşlevler** **sekmelerinde** aşağıdaki **semboller** görünür:

- ![Değer türü simgesi](../profiling/media/valuetypeicon.png "Değer türü simgesi") - Tamsayı gibi bir değer türü

- ![Değer türü koleksiyon simgesi](../profiling/media/valuetypecollectionicon.png "Değer türü koleksiyon simgesi") - Tamsayı dizisi gibi bir değer türü koleksiyonu

- ![Başvuru türü simgesi](../profiling/media/referencetypeicon.png "Başvuru türü simgesi") - Dize gibi bir başvuru türü

- ![Başvuru türü koleksiyon simgesi](../profiling/media/referencetypecollectionicon.png "Başvuru türü koleksiyon simgesi") - Dize dizisi gibi bir başvuru türü koleksiyonu

### <a name="call-tree"></a>Çağrı Ağacı

![Çağrı Ağacı görünümü](../profiling/media/calltreelight.png "Çağrı ağacı görünümü")

Çağrı **Ağacı görünümü,** çok fazla bellek alan nesneleri içeren işlev yürütme yollarını gösterir.

- İşlev **Adı sütunu,** bellek ayıran nesneleri içeren işlevin işlemini veya adını gösterir. Görüntü, incelemekte olduğunuz düğümün düzeyine göredir.
- **Toplam (Ayırmalar)** ve Toplam Boyut **(Bayt)** sütunları, ayrılan nesnelerin sayısını ve bir işlev ve çağıran diğer tüm işlevler tarafından kullanılan bellek miktarını gösterir.
- Kendi **Kendine (Ayırmalar)** ve Kendi Kendine **Boyut (Bayt)** sütunları, ayrılan nesnelerin sayısını ve seçilen tek bir işlev veya ayırma türü tarafından kullanılan bellek miktarını gösterir.
- Ortalama **Boyut (Bayt)** sütunu, Ayırmalar görünümündekiyle **aynı bilgileri** gösterir.
- Modül **adı sütunu,** çağıran işlevi veya işlemi içeren modülü gösterir.

   ![Genişletilmiş bir hot path](../profiling/media/hotpathlight.png "Genişletilmiş etkin yol")

- Çalışma **Yolunu Genişlet** düğmesi, bellek alan birçok nesne içeren bir işlev yürütme yolunu vurgular. Algoritma, sizin seçen bir düğümde başlar ve araştırmanıza yol gösteren en fazla ayırma yolunu vurgular.
- Hot **Path Göster düğmesi,** hangi düğümlerin hot yolunun parçası olduğunu belirten simge simgelerini gösterir veya gizler.

### <a name="functions"></a>İşlevler

![İşlevler görünümü](../profiling/media/functionslight.png "Işlevler görünümü")

**İşlevler** görünümü, bellek alan işlemleri, modülleri ve işlevleri gösterir.

- Ad **sütunu** işlemleri en üst düzey düğümler olarak gösterir. İşlemlerin altında modüller, altında ise işlevler bulunur.
- Bu sütunlar Ayırma ve Çağrı ağacı görünümlerine **ilişkin bilgilerle** **aynı bilgileri** gösterir:

  - **Toplam (Ayırmalar)**
  - **Kendi Kendine (Ayırmalar)**
  - **Toplam Boyut (Bayt)**
  - **Kendi Kendine Boyut (Bayt)**
  - **Ortalama Boyut (Bayt)**

### <a name="collection"></a>Koleksiyon

![Koleksiyon görünümü](../profiling/media/collectionlight.png "Koleksiyon görünümü")

Toplama **görünümü,** çöp toplama sırasında kaç nesne toplanmış veya korunu olduğunu gösterir. Bu görünüm ayrıca toplanan ve hayatta kalan nesneleri türe göre görselleştirmek için pasta grafiklerini gösterir.

- Toplanan **sütunu,** atık toplayıcının topladığı nesne sayısını gösterir.
- **Survived sütunu,** atık toplayıcı çalıştırıldıktan sonra hayatta kalan nesne sayısını gösterir.

### <a name="filtering-tools"></a>Filtreleme araçları

**Ayırmalar,** Çağrı **Ağacı** ve **İşlevler** görünümlerinde, Yerel Kodu **Göster Yalnızca kendi kodum** ve **bir** filtre kutusu vardır.

- **Tek Yalnızca kendi kodum** sistemleri, çerçeveleri ve diğer kullanıcı olmayan kodu **[Dış Kod]** çerçevelerine daraltarak yalnızca kodunuz üzerinde odaklanmanızı sağlar. Daha fazla bilgi için bkz. Yalnızca kendi kodum ile [kullanıcı kodunda hata ayıklama.](../debugger/just-my-code.md)
- **Yerel Kodu Göster,** analiz hedefinin içindeki yerel kodu gösterir ve kullanıcı dışı kod içerebilir.
- Filtre kutusuyla, Ad veya İşlev  adı **sütununu,** sağ istediğiniz değere göre filtreleebilirsiniz. Kutuya bir dize değeri girin. Tablo daha sonra yalnızca bu dizeyi içeren türleri gösterir.
