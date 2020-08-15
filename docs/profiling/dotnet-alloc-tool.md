---
title: .NET nesneleri için bellek kullanımını analiz etme | Microsoft Docs
ms.date: 12/9/2019
ms.topic: how-to
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 81c15753b083256b97c9f67219b64565a8db8736
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247793"
---
# <a name="analyze-memory-usage-by-using-the-net-object-allocation-tool"></a>.NET nesne ayırma aracı 'nı kullanarak bellek kullanımını analiz etme

Uygulamanızın ne kadar bellek kullandığını ve .NET nesne ayırma aracı 'nı kullanarak hangi kod yollarının en fazla bellek ayırabileceğini görebilirsiniz.

Aracı çalıştırdıktan sonra, nesnelerin ayrıldığı işlev yürütme yollarını görebilirsiniz. Daha sonra, en fazla belleği alan çağrı ağacının köküne geri dönebilirsiniz.

## <a name="setup"></a>Kurulum

1. Visual Studio 'da performans profil oluşturucuyu açmak için **alt + f2** ' yi seçin.

1. **.NET nesne ayırma izlemesi** onay kutusunu seçin.

   ![DotNet nesne ayırma Izleme aracı seçildi](../profiling/media/dotnetalloctoolselected.png "DotNet nesne ayırma Izleme aracı seçildi")

1. Aracı çalıştırmak için **Başlat** düğmesini seçin.

1. Araç çalışmaya başladıktan sonra, uygulamanızda profili eklemek istediğiniz senaryoya gidin. Ardından, **toplamayı durdur** ' u seçin veya verilerinizi görmek için uygulamanızı kapatın.

   ![Durdur toplamayı gösteren pencere](../profiling/media/stopcollectionlighttheme.png "Durdur toplamayı gösteren pencere")

1. **Ayırma** sekmesini seçin. aşağıdaki ekran görüntüsüne benzer pencere içeriği görüntülenir.

   ![Ayırma sekmesi](../profiling/media/allocationview.png "Ayırma sekmesi")

Artık nesnelerin bellek ayırmayı analiz edebilirsiniz.

Koleksiyon sırasında, izleme aracı profili oluşturulmuş uygulamayı yavaşlatabilir. İzleme aracının veya uygulamanın performansı yavaşsa ve her nesneyi izlemeniz gerekmiyorsa örnekleme hızını ayarlayabilirsiniz. Bunu yapmak için, profil oluşturucu Özeti sayfasında izleme aracının yanındaki dişli simgesini seçin.

![DotNet ayırma aracının ayarları](../profiling/media/dotnetallocsettings.png "DotNet ayırma aracının ayarları")

Örnekleme hızını istediğiniz hıza ayarlayın. Bu değişiklik, toplama ve analiz sırasında uygulamanızın performansını hızlandırmaya yardımcı olur.

![Ayarlanmış bir örnekleme hızı](../profiling/media/adjustedsamplingratedotnetalloctool.png "Ayarlanmış bir örnekleme hızı")

Aracı nasıl daha verimli hale getirmek hakkında daha fazla bilgi için bkz. [Profil Oluşturucu ayarlarını iyileştirme](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Verilerinizi anlayın

![DotNet ayırma aracı için bir grafik](../profiling/media/graphdotnetalloc.png "DotNet ayırma aracı için bir grafik")

Önceki grafik görünümünde, üstteki grafik uygulamanızdaki canlı nesne sayısını gösterir. En alttaki **nesne Delta** grafiğinde, uygulama nesnelerinin yüzde değişikliği gösterilmektedir. Kırmızı çubuklar çöp toplamanın ne zaman sürdüğünü gösterir.

![DotNet ayırma zamanının filtrelenmiş bir grafiği](../profiling/media/graphdotnetalloctimefiltered.png "DotNet ayırma zamanının filtrelenmiş bir grafiği")

Yalnızca belirli bir zaman aralığı için etkinliğin görüntüleneceği tablo verilerini filtreleyebilirsiniz. Ayrıca, grafiği de yakınlaştırabilir veya kapatabilirsiniz.

### <a name="allocation"></a>Ayırma

![Genişletilmiş ayırma görünümü](../profiling/media/allocationexpandedlight.png "Genişletilmiş ayırma görünümü")

**Ayırma** görünümü, bellek ayıran nesnelerin konumunu ve bu nesnelerin ne kadar bellek ayırışını gösterir.

-  **Tür**   sütunu, bellek kullanan sınıfların ve yapıların bir listesidir. Geri izlemeyi ters çevrilmiş çağrı ağacı olarak görüntülemek için bir türe çift tıklayın. Yalnızca **ayırma** görünümünde, seçili kategoride bellek alan öğeleri görebilirsiniz.

-  **Tahsisatlar**   sütunu, belirli bir ayırma türü veya işlevi içinde belleği alan nesne sayısını gösterir. Bu sütun yalnızca **ayırma**, **çağrı ağacı**ve **işlev**   görünümlerinde görünür.

-  **Bayt**   ve **Ortalama Boyut (bayt)**   sütunları varsayılan olarak görünmez. Bunları göstermek için **tür**   veya **ayırmalar**   sütununa sağ tıklayın ve ardından **Bytes**   bunları grafiğe eklemek için bayt ve **Ortalama Boyut (bayt)**   seçeneklerini belirleyin. 

   İki sütun **Toplam (ayırmalar)** ve **kendine (ayırmalar)** benzerdir, ancak belleği alan nesne sayısı yerine, alınan bellek miktarını gösterir. Bu sütunlar yalnızca **ayırma** görünümünde görünür.

-  **Modül adı**   sütunu, çağıran işlevi veya işlemi içeren modülü gösterir.

Bu sütunların hepsi sıralanabilir.  **Tür** ve **Modül adı** sütunları için öğeleri alfabetik olarak artan veya azalan sırada sıralayabilirsiniz.  **Ayırmalar**, **baytlar**   ve **Ortalama Boyut (bayt)** için, sayısal değeri artırarak veya azaltarak öğeleri sıralayabilirsiniz.

#### <a name="symbols"></a>Simgeleri

**Ayırma**, **çağrı ağacı**ve **işlevler** sekmelerinde aşağıdaki semboller görünür:

- ![Değer türü symbol](../profiling/media/valuetypeicon.png "Değer türü simgesi") -Integer gibi bir değer türü

- ![Değer türü toplama simgesi](../profiling/media/valuetypecollectionicon.png "Değer türü koleksiyon simgesi") -tamsayılar dizisi gibi bir değer türü koleksiyon

- ![Başvuru türü simgesi](../profiling/media/referencetypeicon.png "Başvuru türü simgesi") -dize gibi bir başvuru türü

- ![Başvuru türü koleksiyon simgesi](../profiling/media/referencetypecollectionicon.png "Başvuru türü koleksiyon simgesi") -dizeler dizisi gibi bir başvuru türü koleksiyon

### <a name="call-tree"></a>Çağrı ağacı

![Çağrı ağacı görünümü](../profiling/media/calltreelight.png "Çağrı ağacı görünümü")

 **Çağrı ağacı**   görünümü, çok fazla bellek ayıran nesneleri içeren işlev yürütme yollarını gösterir.

-  **Işlev adı**   sütunu, bellek ayıran nesneleri içeren işlevin işlemini veya adını gösterir. Görüntü, İnceleme yaptığınız düğümün düzeyini temel alır.
-  **Toplam (ayırmalar)** ve **Toplam Boyut (bayt)**   sütunları, ayrılan nesne sayısını ve bir işlev tarafından kullanılan bellek miktarını ve çağrı yaptığı diğer tüm işlevleri gösterir.
- **Kendi kendine (ayırmalar)** ve **kendi kendine boyut (bayt)** sütunları, ayrılan nesne sayısını ve tek bir seçili işlev veya ayırma türü tarafından kullanılan bellek miktarını gösterir.
- **Ortalama Boyut (bayt)** sütunu, **ayırma** görünümündeki ile aynı bilgileri gösterir.
-  **Modül adı**   sütunu, çağıran işlevi veya işlemi içeren modülü gösterir.

   ![Genişletilmiş etkin yol](../profiling/media/hotpathlight.png "Genişletilmiş etkin yol")

- **Etkin yolu genişlet** düğmesi, bellek ayıran çok sayıda nesne içeren bir işlev yürütme patika vurgular. Algoritma seçtiğiniz bir düğümden başlar ve en fazla ayırmaların yolunu vurgular ve bu da araştırmanızda size rehberlik ediyor.
- **Etkin yolu göster** düğmesi, hangi düğümlerin etkin yolun parçası olduğunu belirten yangın sembollerini gösterir veya gizler.

### <a name="functions"></a>İşlevler

![Işlevler görünümü](../profiling/media/functionslight.png "Işlevler görünümü")

**İşlevler** görünümü, bellek ayıran işlemleri, modülleri ve işlevleri gösterir.

- **Ad** sütunu, en üst düzey düğümler olarak işlemi gösterir. İşlemlerin altında modüller, modüller altında ise işlevlerdir.
- Bu sütunlar, **ayırma** ve **çağrı ağacı** görünümlerinde olduğu gibi aynı bilgileri gösterir:

  - **Toplam (ayırmalar)**
  - **Kendi kendine (ayırmalar)**
  - **Toplam Boyut (bayt)**
  - **Kendinden boyut (bayt)**
  - **Ortalama Boyut (bayt)**

### <a name="collection"></a>Koleksiyon

![Koleksiyon görünümü](../profiling/media/collectionlight.png "Koleksiyon görünümü")

**Koleksiyon** görünümü çöp toplama sırasında toplanan veya tutulan nesne sayısını gösterir. Bu görünüm, toplanan ve nesneleri türe göre görselleştirmek için pasta grafikleri de gösterir.

- **Toplanan** sütunda çöp toplayıcısının toplandığı nesne sayısı gösterilir.
- **Kalan** sütun, çöp toplayıcı çalıştırıldıktan sonra kalan nesne sayısını gösterir.

### <a name="filtering-tools"></a>Filtreleme araçları

**Ayırmalar**, **çağrı ağacı**ve **işlev** görünümleri tümünü **göster yalnızca kendi kodum** ve **yerel kod** seçeneklerini ve bir filtre kutusunu gösterir.

- Yalnızca kodunuza odaklanabilmeniz için sistemleri, çerçeveleri ve diğer kullanıcı olmayan kodu **[harici kod]** çerçevelerine göre daraltır **yalnızca kendi kodum** . Daha fazla bilgi için bkz. [yalnızca kendi kodum Kullanıcı kodunda hata ayıklama](../debugger/just-my-code.md).
- **Yerel kodu göster** , analiz hedefi içindeki yerel kodu gösterir ve Kullanıcı olmayan kod içerebilir.
- Filtre kutusuyla, sağladığınız değere göre **ad** veya **işlev adı** sütununu filtreleyebilirsiniz. Kutuya bir dize değeri girin. Tablo daha sonra yalnızca o dizeyi içeren türleri gösterir.
