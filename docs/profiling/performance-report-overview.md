---
title: Performans raporuna genel bakış | Microsoft Docs
description: Profil oluşturma verilerini, Visual Studio Team System Development Edition tümleşik geliştirme ortamının performans raporu penceresinde görüntüleyin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2e775c91759326407918befba3dd4bb52e19dd0e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922287"
---
# <a name="performance-report-overview"></a>Performans raporuna genel bakış
Bir performans oturumunun profil oluşturma verilerini, Visual Studio Team System Development Edition tümleşik geliştirme ortamının (IDE) **Performans raporu** penceresinde görüntüleyebilirsiniz. Profil oluşturma verileri. vsp ve. vsps dosyalarına kaydedilir. Rapor görünümü pencereleri, uygulama performansı sorunlarını görüntülemenizi ve analiz etmenize olanak tanır.

> [!CAUTION]
> Profil oluşturma veri dosyası, bilgisayar adı, işletim sistemi sürümü, dosya yolları, bellek bilgileri ve diğer bilgisayar kurulum bilgileri gibi hassas bilgileri içerir. Verilerin dağıtılması üzerinde, hem yerel hem de tam denetim korumanız gerekir. *VSP* biçimi ve öğesine aktarıldığında. *CSV* veya. *XML* dosyası.
>
> Olay izleme verileri performans oturumunun bir parçası olarak toplanırsa, olay izleme günlüğünde ek bilgiler görünebilir (.*ETL*) dosyası. Bu bilgiler, etki alanınızı ve Kullanıcı adınızı içerir; Bu nedenle, günlük dosyasının dağıtılması üzerinde kesin denetim korumanız gerekir.

## <a name="performance-report-window"></a>Performans raporu penceresi
 Performans raporu penceresi, performans verilerini görüntülemek, yönetmek ve filtrelemek için kullanılan ve özelleştirilebilir bir sorgu denetimi içeren bir araç penceresidir.

 Performans raporu penceresinin ana araç çubuğunda her bir görünüme erişebilirsiniz. **Geçerli görünüm** listesinin yanındaki oka tıklayarak kullanılabilir olan ayrı görünümleri görüntüleyin ve seçin.

 Performans raporu penceresi aşağıdaki veri görünümlerini sağlar:

### <a name="summary-view"></a>Özet Görünümü
 Profil oluşturma verileri varsayılan olarak Özet görünümünde görüntülenir. Bu görünüm, performans sorunlarına yönelik araştırmanızın bir başlangıç noktasıdır. Özet görünümündeki her satırdan, işleve veya modül adına sağ tıklayarak daha ayrıntılı görünümlere geçebilirsiniz. Daha fazla bilgi için bkz. [Özet görünümü](../profiling/summary-view.md).

### <a name="callercallee-view"></a>Arayan/Aranan görünümü
 Arayan/çağrılan görünümü tek bir işlev için çağrı ağacı görüntüler. Görünüm üç parçaya ayrılmıştır:

- Hedef işlev, görünümün ortasında görüntülenir.

- İşlevi (çağıranlar) çağıran işlevler, hedef işlevin üzerinde görüntülenir.

- Hedef işlev (Callet 'ler) tarafından çağrılan işlevler hedefin altında görüntülenir.

  Çağrılan listede veya aranan listesinde herhangi bir işleve çift tıklayarak farklı bir işlev seçebilirsiniz. Daha fazla bilgi için bkz. [arayan/çağrılan görünümü](../profiling/caller-callee-view.md).

### <a name="call-tree-view"></a>Çağrı Ağacı Görünümü
 Çağrı ağacı görünümü, profili oluşturulmuş uygulamada geçen işlev yürütme yollarını görüntüler. Ağacın kökü, uygulamanın veya bileşenin giriş noktasıdır. Her işlev düğümü, çağırdığı tüm işlevleri ve bu işlev çağrıları ile ilgili performans verilerini listeler.

 Çağrı ağacı görünümü Ayrıca en çok kullanılan veya en sık örneklendiği bir işlevin yürütme yolunu genişletebilir ve vurgulayabilir. En etkin yolu göstermek için, işlevine sağ tıklayın ve ardından **etkin yolu genişlet**' e tıklayın. Daha fazla bilgi için bkz. [çağrı ağacı görünümü](../profiling/call-tree-view.md).

### <a name="process-view"></a>İşlem Görünümü
 Işlem görünümü, profili oluşturulan her işlem ve iş parçacığı için performans verilerini görüntüler. Daha fazla bilgi için bkz. [Işlem görünümü](../profiling/process-view.md).

### <a name="modules-view"></a>Modüller Görünümü
 Modüller görünümü projedeki modülleri listeler ve her modül için profil oluşturma verilerini gösterir. İşlev profil oluşturma verilerini göstermek için modül adını genişletin veya daraltın. Veriler örnekleme kullanılarak toplandığında, kaynak kodu satırı ve yönerge işaretçisi profil oluşturma verileri de mevcuttur. Daha fazla bilgi için bkz. [modüller görünümü](../profiling/modules-view.md).

### <a name="functions-view"></a>İşlevler Görünümü
 Işlevler görünümü profil oluşturma sırasında çağrılan işlevleri listeler. Daha fazla bilgi için bkz. [Işlevler görünümü](../profiling/functions-view.md).

### <a name="line-view"></a>Satır görünümü
 Satırlar Görünümü Örnekleme profili oluşturma sırasında yürütülen belirli kaynak kodu satırlarını görüntülemenize olanak sağlar. Daha fazla bilgi için bkz. [çizgiler görünümü](../profiling/lines-view.md).

### <a name="instruction-pointer-ip-view"></a>Yönerge Işaretçisi (IP) görünümü
 Yönerge Işaretçisi görünümü örnekleme profili oluşturma sırasında yürütülen belirli yönergeleri görüntülemenize olanak sağlar. Daha fazla bilgi için bkz. [yönerge işaretçileri (IP) görünümü](../profiling/instruction-pointers-ips-view.md).

### <a name="allocation-view"></a>Ayırma görünümü
 **Performans oturumu** özellikleri Iletişim kutusunun **genel** sayfasında **.NET nesne ayırmayı topla** seçilmişse, ayırma görünümü kullanılabilir. [Performans oturumuna genel bakış](../profiling/performance-session-overview.md)konusuna bakın. Ayırma görünümü, uygulama veya bileşen tarafından ayrılan .NET nesnelerini listeler. Bir nesne satırı genişletildiğinde, bir çağrı ağacı görüntülenir. Çağrı ağacı, nesnesinin oluşturulmasına neden olan yürütme yollarını gösterir. Ayrıca, çağrı ağacındaki her bir işlev için kapsamlı ve dışlamalı ayırma sayısı hakkında bilgiler de görüntülenir. Ayırma görünümü Ayrıca en fazla nesne sayısını tahsis eden bir işlevin yürütme yolunu genişletebilir ve vurgulayabilir. En etkin yolu göstermek için, işlevine sağ tıklayın ve ardından **etkin yolu genişlet**' e tıklayın. Daha fazla bilgi için bkz. [.net bellek ayırma ve ömür verileri](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) ve [ayırma görünümü](../profiling/dotnet-memory-allocations-view.md)toplama.

### <a name="objects-lifetime-view"></a>Nesne ömrü görünümü
 **Performans oturumu** özellikleri Iletişim kutusunun **genel** sayfasında **.NET nesne ayırma bilgilerini topla** ve **Ayrıca .NET nesne yaşam süresi bilgilerini topla** seçilirse, nesne ömrü görünümü kullanılabilir.

 Nesne ömrü görünümü her bir türün toplam örnek sayısını ve her bir çöp toplama oluşturmada toplanan nesne sayısını görüntüler. Daha fazla bilgi için bkz. [nesne ömrü görünümü](../profiling/object-lifetime-view.md).

## <a name="customizable-filter-control"></a>Özelleştirilebilir filtre denetimi
 Özelleştirilebilir filtre denetimi aşağıdaki seçeneklere sahiptir:

- **Içeri aktarma filtresi** -önceden kaydedilmiş bir özel sorgu alır.

- **Dışarı aktarma filtresi** -özel sorguyu belirtilen konuma kaydeder.

- **Sorguyu Yürüt** -sorguyu özel sorgu denetiminde gösterildiği gibi çalıştırır.

- **Sorguyu durdur** -çalıştıran bir sorgunun yürütülmesini durdurur. Hiçbir sorgu çalışmıyorsa bu düğme kullanılamaz.

- **Sorguyu göster** -özel sorgu denetimini gösterir/gizler.

- **Çözümlenme** -raporu, geçerli analiziyle birlikte. vsps dosyası olarak kaydeder.

- **Dışarı aktar** -geçerli raporu ' de kaydeder. CVS-biçimli veya. Farklı görünümleri kaydetme seçenekleriyle, XML biçimli dosya.

## <a name="see-also"></a>Ayrıca bkz.
- [Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md)
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
