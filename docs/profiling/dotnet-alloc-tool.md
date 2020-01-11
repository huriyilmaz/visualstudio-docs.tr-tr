---
title: .NET nesneleri için bellek kullanımını analiz etme | Microsoft Docs
ms.date: 12/9/2019
ms.topic: conceptual
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9518ffd618a6d82505feca33b37b5151a3a9f961
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75898471"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>.NET nesne ayırma aracı 'nı kullanarak bellek kullanımını analiz etme

Uygulamanızın kullandığı bellek miktarını ve hangi kod yollarının .NET nesne ayırma aracı kullanılarak en fazla bellek ayırabileceğini görebilirsiniz.

Aracı çalıştırdıktan sonra, en fazla bellek miktarını alan çağrı ağacının köküne geri geçirebilmeniz için nesnelerin ayrıldığı işlev yürütme yollarını görebilirsiniz.

## <a name="setup"></a>Kurulum

1. Performans profil oluşturucuyu (**alt + f2)** Visual Studio 'da açın.
2.  **.NET nesne ayırma izleme** onay kutusunu seçin.

![DIAG hub 'ı](../profiling/media/diaghub.png "DIAG hub 'ı")

> [!NOTE]
> Başlangıç projesi varsayılan olarak **analiz hedefi** olarak seçilidir, ancak bu işlem çalışan işlem, yürütülebilir dosyalar, çalışan uygulamalar ve yükleme **hedefi** açılır menüsünü açıp kullanılabilir seçeneklerden seçim yaparak yüklü uygulamalar olarak değiştirilebilir.

   .NET nesne ayırma aracı şu anda, açılan menü ile yürütülebilir dosyaları desteklememektedir. Aracı kullanmak için exe proje sisteminden gitmeniz gerekir. Bunu yapmak için, geçerli çözümünüzü kapatın (**dosya** -> **çözümü kapat**) ve ardından **Dosya** -> **bir proje veya çözüm açın** ->. exe dosyanızı seçin.

![Analiz hedefi](../profiling/media/analysistarget.png "Analiz hedefi")

3. Aracı çalıştırmak için **Başlat** düğmesine tıklayın.

![Toplamayı durdur](../profiling/media/stopcollection.png "Toplamayı durdur")

4. Araç çalışmaya başladıktan sonra uygulamanızdaki istenen senaryoya gidin ve ardından **toplamayı durdur** ' a basın veya verilerinizi görmek için uygulamanızı kapatın.
5. **Ayırma** sekmesine tıklayın ve aşağıda gösterilene benzer bir görüntü görmeniz gerekir.

![Ayırmasını](../profiling/media/allocation.png "ayırma")

Tebrikler! Artık nesnelerin bellek ayırmayı analiz edebilirsiniz.

## <a name="understand-your-data"></a>Verilerinizi anlayın

### <a name="collection"></a>Koleksiyon

![Koleksiyon](../profiling/media/collection.png "Koleksiyon")

Koleksiyon görünümü çöp toplama sırasında kaç tane nesnenin toplandığını ve kaç tane korunduğunu görmenizi sağlar. Bu görünüm, toplanan ve nesneleri türe göre görselleştirmek için birkaç pasta grafik de sağlar.

- **Toplanan** sütunda çöp toplayıcısının toplandığı nesne sayısı gösterilir.
- **Kalan** sütun, çöp toplayıcı çalıştırıldıktan sonra kalan nesne sayısını gösterir.

### <a name="allocation"></a>ayırma

![Ayırma genişletildi](../profiling/media/allocationexpanded.png "Ayırma genişletildi")

Ayırma görünümü, bellek ayıran nesnelerin konumunu ve bu nesnelerin ne kadar bellek ayırışını görmenizi sağlar.

- **Ad** sütunu, bellek kullanan çeşitli sınıfların ve yapıların bir listesidir. Sütun içindeki her öğe, bu kategori içinde bellek alan öğeler varsa genişletilebilen bir düğümdür. (Yalnızca**ayırma** görünümü)
- **Toplam (ayırmalar)** sütunu, bellek kullanan belirli bir ayırma türü içindeki nesne sayısını gösterir. (**Ayırma**, **çağrı ağacı**ve **işlevler** görünümü)
- **Kendi kendine (ayırmalar)** sütunu, bellek oluşturan tek bir öğe içindeki nesne sayısını gösterir. (**Ayırma**, **çağrı ağacı**ve **işlevler** görünümü)
- Bu sütunların üçü sıralanabilir. **Ad** sütunu söz konusu olduğunda, öğeler alfabetik olarak sıralanır (ileri veya geri). **Toplam** ve **kendi kendine (ayırmalar)** , sayısal olarak (artan veya decreasingly) sıralayabilirsiniz.
- **Toplam Boyut (bayt)** ve **kendine ait boyut (bayt)** sütunları varsayılan olarak açık değildir. Bunları etkinleştirmek için, **ad**, **Toplam** veya **kendine (ayırmalar)** sütunlarına sağ tıklayın ve sonra **Toplam boyut** ve **kendi boyut** seçenekleri ' ne tıklayarak grafiğe ekleyin. İki sütun **Toplam (ayırmalar)** ve **kendi kendine (ayırmalar)** benzerdir, ancak belleği oluşturan nesnelerin sayısını göstermek yerine, bu nesnelerin toplam bellek miktarını bayt cinsinden gösterir. [Yalnızca ayırma görünümü]

### <a name="call-tree"></a>Çağrı ağacı

![Çağrı ağacı](../profiling/media/calltree.png "Çağrı ağacı")

**Çağrı ağacı** görünümü, çok fazla bellek ayıran nesneleri içeren işlev yürütme yollarını görmenizi sağlar.

- **İşlev adı** sütunu, İnceleme yaptığınız düğüm düzeyine göre bellek ayıran nesneleri içeren işlevin işlemini veya adını gösterir.
- **Toplam** ve **kendine (ayırmalar)** sütunları, **ayırma** görünümüyle aynı bilgileri gösterir.
- **Modül adı** sütunu, çağıran işlevi veya işlemi içeren modülü gösterir.

![Etkin yol](../profiling/media/hotpath.png "Etkin yol")

- **Etkin yolu genişlet** düğmesi, bellek ayıran çok sayıda nesne içeren bir işlev yürütme patika vurgular. Algoritma, Kullanıcı tarafından seçilen bir düğümden başlar ve en fazla ayırmaların yolunu vurgular ve bu da bir kullanıcıyı araştırmasına kılavuzluk ediyor.
- **Etkin yolu göster** düğmesi, **etkin yolun**bir parçası olduğunu belirten yangın simgelerindeki açık veya kapalı olarak geçiş yapar.

### <a name="functions"></a>İşlevler

![İşlevler](../profiling/media/functions.png "İşlevler")

**İşlevler** görünümü, bellek ayıran işlemleri, modülleri ve işlevleri gösterir.

- **Ad** sütunu, en üst düzey düğümler olarak işlemi gösterir. İşlemlerin altında modüller, modüller altında ise işlevlerdir.
- **Toplam** ve **kendine (ayırmalar)** sütunları, **ayırma** görünümüyle aynı bilgileri gösterir.

**Ayırmalar**, **çağrı ağacı**ve **işlev** görünümleri tümünü **göster yalnızca kendi kodum**, **yerel kodu göster**ve **arama** seçenekleri içerir:

![Filtre çubuğu](../profiling/media/filterbar.png "Filtre çubuğu")

- Kullanıcı kodunun odaklanabilmesi için sistemleri, çerçeveleri ve diğer kullanıcı olmayan kodu ve **[External Code]** çerçevelerine yönelik olarak **göster yalnızca kendi kodum** . Daha fazla bilgi için bkz. [yalnızca kendi kodum Kullanıcı kodunda hata ayıklama](../debugger/just-my-code.md).
- **Yerel kodu göster** seçildiğinde, Kullanıcı olmayan kod dahil olmak üzere analiz hedefi içindeki yerel kodu gösterir.
- **Filtre kutusu** , sağladığınız parametreye göre **ad** veya **işlev adı** sütununu filtrelemenizi sağlar. Yalnızca alana yazmanız gerekir ve yalnızca belirtilen dizeyi içeren türleri göstermek için tablo filtrelemelidir.
