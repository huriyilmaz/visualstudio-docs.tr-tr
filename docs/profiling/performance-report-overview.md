---
title: Performans Raporu Genel Bakış | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 517156677a6d3711fa5dc2e4a15629a55229cfe2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772238"
---
# <a name="performance-report-overview"></a>Performans Raporu'na genel bakış
Visual Studio Team System Development Edition tümleşik geliştirme ortamının (IDE) **Performans Raporu** penceresinde performans oturumunun profil oluşturma verilerini görüntüleyebilirsiniz. Profil oluşturma verileri .vsp ve .vsps dosyalarına kaydedilir. Rapor görünümü pencereleri, uygulama performansı sorunlarını görüntülemenize ve çözümlemenize olanak tanır.

> [!CAUTION]
> Profil oluşturma veri dosyası, bilgisayar adı, işletim sisteminin sürümü, dosya yolları, bellek bilgileri ve diğer bilgisayar kurulum bilgileri gibi hassas bilgileri içerir. Hem kendi yerel hem de, verilerin dağıtımı üzerinde sıkı kontrol sağlamalısınız. *vsp* biçimi ve ne zaman bir . *csv* veya bir . *xml* dosyası.
>
> Olay izleme verileri performans oturumunun bir parçası olarak toplanırsa, olay izleme günlüğünde (.* etl*) dosyası. Bu bilgiler etki alanınızı ve kullanıcı adınızı içerir; bu nedenle, günlük dosyasının dağıtımı üzerinde sıkı denetim sağlamalısınız.

## <a name="performance-report-window"></a>Performans Raporu penceresi
 Performans Raporu penceresi, performans verilerini görüntülemek, yönetmek ve filtrelemek için kullanılan ve özelleştirilebilir bir sorgu denetimi içeren bir araç penceresidir.

 Performans Raporu penceresinin ana araç çubuğunda her görünüme erişebilirsiniz. Kullanılabilir görünümleri görüntülemek ve seçmek için **Geçerli Görünüm** listesinin yanındaki oku tıklatın.

 Performans Raporu penceresi aşağıdaki veri görünümlerini sağlar:

### <a name="summary-view"></a>Özet Görünümü
 Varsayılan olarak, profil oluşturma verileri Özet görünümünde görüntülenir. Bu görünüm, performans sorunları yla ilgili araştırmanızda bir başlangıç noktasıdır. Özet görünümündeki her satırdan, işlev veya modül adını sağ tıklatarak daha ayrıntılı görünümlere geçebilirsiniz. Daha fazla bilgi için [Özet Görünümü'ne](../profiling/summary-view.md)bakın.

### <a name="callercallee-view"></a>Arayan/Aranan görünümü
 Arayan/Callee görünümü, tek bir işlev için bir çağrı ağacı görüntüler. Görünüm üç bölüme ayrılmıştır:

- Hedef işlev görünümün ortasında görüntülenir.

- İşlev (arayanlar) olarak adlandırılan işlevler hedef işlevin üzerinde görüntülenir.

- Hedef işlev (callees) tarafından çağrılan işlevler hedefin altında görüntülenir.

  Çağrılan listedeki veya çağrı listesindeki herhangi bir işlevi çift tıklatarak farklı bir işlev seçebilirsiniz. Daha fazla bilgi için [Bkz. Arayan/Callee Görünümü.](../profiling/caller-callee-view.md)

### <a name="call-tree-view"></a>Çağrı Ağacı Görünümü
 Çağrı Ağacı görünümü, profilli uygulamada geçen işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamanın veya bileşenin giriş noktasıdır. Her işlev düğümü, aradığı tüm işlevleri ve bu işlev çağrılarıyla ilgili performans verilerini listeler.

 Çağrı Ağacı görünümü, en çok zaman tüketilen veya en sık örneklenmiş bir işlevin yürütme yolunu genişletebilir ve vurgulayabilir. En etkin yolu görüntülemek için işlevi sağ tıklatın ve ardından **Sıcak Yolu Genişlet'i**tıklatın. Daha fazla bilgi için [Bkz. Çağrı Ağacı Görünümü.](../profiling/call-tree-view.md)

### <a name="process-view"></a>İşlem Görünümü
 İşlem görünümü, profillenmiş her işlem ve iş parçacığı için performans verilerini görüntüler. Daha fazla bilgi için [Bkz. İşlem Görünümü.](../profiling/process-view.md)

### <a name="modules-view"></a>Modüller Görünümü
 Modüller görünümü projedeki modülleri listeler ve her modül için profil oluşturma verilerini sunar. İşlev profil oluşturma verilerini görüntülemek için modül adını genişletin veya daraltın. Veriler örnekleme kullanılarak toplandığında, kaynak kod satırı ve yönerge işaretçisi profil oluşturma verileri de kullanılabilir. Daha fazla bilgi için [Modüller Görünümü'ne](../profiling/modules-view.md)bakın.

### <a name="functions-view"></a>İşlevler Görünümü
 İşlevler görünümü profil oluşturma sırasında çağrılan işlevleri listeler. Daha fazla bilgi için [Bkz. İşlevler Görünümü.](../profiling/functions-view.md)

### <a name="line-view"></a>Çizgi Görünümü
 Satırlar görünümü, örnekleme profil oluşturma sırasında yürütülen belirli kaynak kodu satırlarını görüntülemenizi sağlar. Daha fazla bilgi için [Bkz. Satır Görünümü.](../profiling/lines-view.md)

### <a name="instruction-pointer-ip-view"></a>Yönerge İşaretçisi (IP) Görünümü
 Yönerge İşaretçisi görünümü, profil oluşturma sırasında yürütülen belirli yönergeleri görüntülemenizi sağlar. Daha fazla bilgi için [Bkz. Yönerge İşaretçileri (IP) Görünümü.](../profiling/instruction-pointers-ips-view.md)

### <a name="allocation-view"></a>Tahsisat Görünümü
 **Performans Oturumu** özellikleri iletişim kutusunun **Genel** sayfasında **Topla .NET nesne ayırması** seçiliyse Tahsisat görünümü kullanılabilir. Bkz. [Performans oturumuna genel bakış.](../profiling/performance-session-overview.md) Tahsisat görünümü, uygulama veya bileşen tarafından ayrılan .NET nesnelerini listeler. Nesne satırı genişletildiğinde, bir çağrı ağacı görüntülenir. Çağrı ağacı, nesnenin oluşturulmasıyla sonuçlanan yürütme yollarını gösterir. Arama ağacındaki her işlev için kapsayıcı ve özel ayırma sayısı hakkında da bilgiler görüntülenir. Ayırma görünümü, en çok sayıda nesne ayıran bir işlevin yürütme yolunu da genişletebilir ve vurgulayabilir. En etkin yolu görüntülemek için işlevi sağ tıklatın ve ardından **Sıcak Yolu Genişlet'i**tıklatın. Daha fazla bilgi için [bkz.](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) [Allocations View](../profiling/dotnet-memory-allocations-view.md)

### <a name="objects-lifetime-view"></a>Nesneler Ömür Boyu Görünümü
 **Performans Oturumu** özellikleri iletişim kutusunun **Genel** sayfasında **.NET nesne ayırma bilgilerini topla** ve **ayrıca .NET nesne yaşam boyu bilgilerini toplavarsa** Object Lifetime görünümü kullanılabilir.

 Object Lifetime görünümü, her türdeki toplam örnek sayısını ve her çöp toplama oluşturma da toplanan nesne sayısını görüntüler. Daha fazla bilgi için [Object Lifetime View'a](../profiling/object-lifetime-view.md)bakın.

## <a name="customizable-filter-control"></a>Özelleştirilebilir filtre kontrolü
 Özelleştirilebilir filtre denetimi aşağıdaki seçeneklere sahiptir:

- **Filtreyi Aktar** - daha önce kaydedilmiş özel bir sorgu alır.

- **Dışa Aktarma Filtresi** - özel sorguyu belirtilen konuma kaydeder.

- **Sorguyu Yürüt** - sorguyu özel sorgu denetiminde gösterildiği gibi çalıştırın.

- **Sorgu'u Durdur** - çalışan bir sorgunun yürütülmesini durdurur. Sorgu çalışmıyorsa bu düğme kullanılamaz.

- **Sorguyu Göster** - özel sorgu denetimini gösterir/gizler.

- **Analiz kaydet** - raporu .vsps dosyası olarak geçerli çözümlemesi ile birlikte kaydeder.

- **Dışa aktarma** - geçerli raporu . CVS biçimli veya . XML biçimli dosya, farklı görünümleri kaydetmek için seçenekleri ile.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
