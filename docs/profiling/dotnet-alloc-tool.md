---
title: .NET nesneleri için bellek kullanımını analiz et | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75898471"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>.NET Nesne Ayırma aracını kullanarak bellek kullanımını analiz edin

.NET Nesne Ayırma aracını kullanarak uygulamanızın ne kadar bellek kullandığını ve en çok belleği hangi kod yollarını ayırdığını görebilirsiniz.

Aracı çalıştırdıktan sonra, en çok bellek alan çağrı ağacının köküne kadar izleyebilmeniz için nesnelerin tahsis edildiği işlev yürütme yollarını görebilirsiniz.

## <a name="setup"></a>Kurulum

1. Visual Studio'da Performans Profilleyicisini **(Alt + F2)** açın.
2.  **.NET Nesne Ayırma İzleme** onay kutusunu seçin.

![Diag Hub](../profiling/media/diaghub.png "Diag Hub")

> [!NOTE]
> Başlangıç projesi varsayılan olarak **Çözüm hedefi** olarak seçilir, ancak bu işlem, çalıştırılabilir ler, uygulamaları çalıştıran ve yüklü uygulamalara değiştirilebilir, Hedef Açılır Menüsünü **Değiştir** menüsünü açıp kullanılabilir seçeneklerden seçim yaparak.

   .NET Nesne Ayırma aracı şu anda açılır menü üzerinden yürütülebilir leri desteklemiyor. Aracı kullanmak için exe proje sisteminden geçmeniz gerekir. Bunu yapmak için geçerli çözümünüzü **(Dosya** -> **Kapatma Çözümü)** kapatın ve ardından **Dosya** -> **Aç'a bir proje veya çözüm** (> .exe dosyanızı seçin.

![Analiz Hedefi](../profiling/media/analysistarget.png "Analiz Hedefi")

3. Aracı çalıştırmak için **Başlat** düğmesini tıklatın.

![Toplamayı Durdur](../profiling/media/stopcollection.png "Toplamayı Durdur")

4. Araç çalışmaya başladığında, uygulamanızda istediğiniz senaryoyu gözden geçirin, ardından **Stop Collection** tuşuna basın veya verilerinizi görmek için uygulamanızı kapatın.
5. **Tahsis sekmesine** tıkladığınızda, aşağıda gösterilene benzer bir resim görmeniz gerekir.

![Ayırma](../profiling/media/allocation.png "Ayırma")

Tebrikler! Artık nesnelerin bellek tahsisini çözümleyebilirsiniz.

## <a name="understand-your-data"></a>Verilerinizi Anlayın

### <a name="collection"></a>Koleksiyon

![Koleksiyon](../profiling/media/collection.png "Koleksiyon")

Koleksiyon görünümü, çöp toplama sırasında kaç nesnenin toplandığını ve kaç nesnenin tutulduğunu görmenizi sağlar. Bu görünüm, toplanan ve hayatta kalan nesneleri türüne göre görselleştirmek için birkaç pasta grafiği de sağlar.

- **Toplanan** sütun, çöp toplayıcının topladığı nesne sayısını gösterir.
- **Hayatta kalan** sütun, çöp toplayıcı çalıştırıldıktan sonra hayatta kalan nesnelerin sayısını gösterir.

### <a name="allocation"></a>Ayırma

![Tahsisat Genişletildi](../profiling/media/allocationexpanded.png "Tahsisat Genişletildi")

Ayırma görünümü, bellek ayıran nesnelerin konumunu ve bu nesnelerin ne kadar bellek ayırdığını görmenizi sağlar.

- **Ad** sütunu, bellek alan çeşitli sınıfların ve yapıların bir listesidir. Sütun içindeki her öğe, bu kategoride bellek alan öğeler varsa genişletilebilen bir düğümdür. ( Yalnızca**tahsisat** görünümü)
- **Toplam (Ayırmalar)** sütunu, bellek alan belirli bir ayırma türündeki nesne sayısını gösterir. (**Ayırma**, **Çağrı Ağacı**ve **Fonksiyonlar** Görünümü)
- **Benlik (Ayırmalar)** sütunu, bellek alan tek bir öğeiçindeki nesnelerin sayısını gösterir. (**Ayırma**, **Çağrı Ağacı**ve **Fonksiyonlar** Görünümü)
- Bu sütunların üçü de sıralanabilir. **Ad** sütunu söz konusu olduğunda, öğeler alfabetik olarak sıralanır (ileri veya geri). **Toplam** ve **Öz (Ayırmalar)** için, sayısal olarak sıralayabilirsiniz (giderek veya azalan).
- **Toplam Boyut (Bayt)** ve **Öz Boyut (Bayt) sütunları** varsayılan olarak açık değildir. Bunları etkinleştirmek için **Ad,** **Toplam** veya **Öz (Ayırmalar) sütunlarına** sağ tıklayın ve ardından grafiğe eklemek için **Toplam Boyut** ve Öz **Boyut** seçeneklerini tıklatın. İki sütun, bellek alan nesnelerin sayısını göstermek yerine, bu nesnelerin aldığı baytlarda toplam bellek miktarını göstermeleri dışında **Toplam (Ayırmalar)** ve **Öz (Ayırmalar)** benzer. [Yalnızca ayırma görünümü]

### <a name="call-tree"></a>Çağrı Ağacı

![Çağrı Ağacı](../profiling/media/calltree.png "Çağrı Ağacı")

**Çağrı Ağacı** görünümü, çok fazla bellek ayıran nesneler içeren işlev yürütme yollarını görmenizi sağlar.

- **İşlev adı** sütunu, incelediğiniz düğümün düzeyine bağlı olarak bellek ayıran nesneleri içeren işlevin işlemini veya adını gösterir.
- **Toplam** ve **Öz (Ayırmalar) sütunları,** **Ayırma** görünümüyle aynı bilgileri gösterir.
- **Modül adı** sütunu, çağıran işlevi veya işlemi içeren modülü gösterir.

![Sıcak Yol](../profiling/media/hotpath.png "Sıcak Yol")

- **Genişle Sıcak Yolu Genişlet** düğmesi, bellek ayıran çok sayıda nesne içeren bir işlev yürütme yolunu vurgular. Algoritma, kullanıcı tarafından seçilen bir ilgi düğümünde başlar ve çoğu ayırmanın yolunu vurgular ve kullanıcıyı araştırmalarında yönlendirir.
- **Sıcak Yolu Göster** düğmesi, hangi düğümün Hot **Path'in**bir parçası olduğunu gösteren alev simgelerini veya açmalarını gösterir.

### <a name="functions"></a>İşlevler

![Işlev](../profiling/media/functions.png "İşlevler")

**İşlevler** görünümü, belleği ayıran işlemleri, modülleri ve işlevleri gösterir.

- **Ad** sütunu işlemleri en üst düzey düğümler olarak gösterir. Altında modüller ve modüller altında fonksiyonlar vardır.
- **Toplam** ve **Öz (Ayırmalar) sütunları,** **Ayırma** görünümüyle aynı bilgileri gösterir.

**Ayırmalar**, **Çağrı Ağacı**ve **Fonksiyonlar** görünümleri yalnızca **Kodumu Göster,** **Yerel Kodu göster**ve **Arama** seçeneklerini içerir:

![Filtre Çubuğu](../profiling/media/filterbar.png "Filtre Çubuğu")

- **Yalnızca Kodum'u göster** sistemleri, çerçeveleri ve diğer kullanıcı dışı kodları ve **[Dış Kod]** çerçevelerini daraltarak kullanıcı koduna odaklanabiliyor. Daha fazla bilgi [için, Yalnızca Kodum ile Hata Ayıklama kullanıcı koduna](../debugger/just-my-code.md)bakın.
- **Yerel Kodu Göster,** seçilirse kullanıcı kodu olmayan lar da dahil olmak üzere analiz hedefi içinde yerel kodu gösterir.
- **Filtre kutusu,** sağladığınız parametreye göre **Ad** veya **İşlev adı** sütununu filtrelemenize olanak tanır. Sadece alanı yazın ve tablo sağlanan dize içeren yalnızca türleri göstermek için aşağı filtre gerekir.
