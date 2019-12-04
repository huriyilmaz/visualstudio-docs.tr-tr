---
title: .NET bellek ayırma ve yaşam süresi verilerini toplama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 6a8c5d431b7be54c4c5bc1a1c37619deb67de751
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779590"
---
# <a name="collect-net-memory-allocation-and-lifetime-data"></a>.NET bellek ayırma ve yaşam süresi verilerini toplama

Visual Studio Profil Oluşturma Araçları, uygulamanızdaki bellekle ilgili performans sorunlarını algılamanıza yardımcı olan .NET bellek ayırma ve nesne yaşam süresi verilerinin toplanmasını destekler.

- .NET bellek ayırma hakkındaki veriler, ayrılan .NET Framework bellek nesnelerinin boyutunu ve sayısını içerir.

- Nesne yaşam süresi verileri, üç çöp toplama nesekte geri kazanılan .NET Framework bellek nesnelerinin boyutunu ve sayısını içerir.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Örnekleme veya izleme profili oluşturma yöntemini kullanarak verileri toplayabilirsiniz.

- Örnekleme yöntemini kullandığınızda, Profil Oluşturucu tüm .NET bellek ayırmalarını ve başlatılan veya öğesine bağlı işlem tarafından oluşturulan nesneleri izler.

- İzleme yöntemini kullandığınızda, Profil Oluşturucu yalnızca bu .NET bellek ayırmalarını ve belgelenmiş modüller tarafından oluşturulan nesneleri izler.

> [!IMPORTANT]
> Örnekleme yöntemini kullanarak .NET bellek verileri (ayırmalar, nesne ömürleri veya her ikisi de) toplarken, Kullanıcı tarafından belirtilen tüm örnekleme olayları yok sayılır ve uygun bellek ayırma olayları veri toplamak için kullanılır.

Profil oluşturma of.NET bellek ayırmayı etkinleştirirseniz, ayırma görünümünü de etkinleştirirsiniz. .NET ömür verilerinin profilini oluşturmayı etkinleştirirseniz, nesne ömrü görünümünü de etkinleştirirsiniz. Daha fazla bilgi için bkz. [ayırma görünümü](../profiling/dotnet-memory-allocations-view.md) ve [nesne ömrü görünümü](../profiling/object-lifetime-view.md).

Profil Oluşturma Araçları komut satırı araçlarını kullanarak .NET bellek verilerinin nasıl toplanacağı hakkında daha fazla bilgi için, bkz. [komut satırından profil oluşturma yöntemlerini kullanarak](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)bellek ayırmayı ve nesne yaşam süresi verilerini toplamak Için .net bellek yöntemlerini kullanma.

## <a name="to-collect-net-memory-data"></a>.NET bellek verileri toplamak için

1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. *Performans oturumu* **Özellik sayfaları** iletişim kutusunda, **genel** sekmesine tıklayın ve **.NET nesne ayırma bilgilerini topla** onay kutusunu seçin.

3. .NET nesne yaşam süresi verilerini toplamak için **.NET nesne yaşam süresi bilgilerini de topla** onay kutusunu seçin.

## <a name="common-tasks"></a>Ortak görevler

Performans oturumunun _performans oturumu_**Özellik sayfaları** iletişim kutusunda ek seçenekleri belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- **Performans Gezgini**, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

Aşağıdaki tabloda yer alan görevler, .NET bellek verilerini toplarken _performans oturumu_**Özellik sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri anlatmaktadır.

|Görev|İlgili Içerik|
|----------|---------------------|
|**Genel** sayfasında, oluşturulan profil oluşturma verileri (. vsp) dosyasının adlandırma ayrıntılarını belirtin.|[.net bellek ayırma ve ömür verileri toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) - <br />- [nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|Kod çözümünüzde birden çok. exe projeniz varsa, **Başlat sayfasında başlatılacak** uygulamayı seçin.|[katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md) - |
|**Katman etkileşimi** sayfasında, profil oluşturma çalıştırmasına ADO.NET çağrı verileri ekleyin.|[katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md) - |
|**Windows olayları** sayfasında, örnekleme verileriyle toplanacak bir veya daha fazla Windows Için olay Izleme (ETW) olayları belirtin.|- [nasıl yapılır: Windows Için olay izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|**Windows sayaçları** sayfasında, profil oluşturma verilerine işaret eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|- [nasıl yapılır: Windows sayaç verilerini toplama](../profiling/how-to-collect-windows-counter-data.md)|
|**Gelişmiş** sayfasında, uygulama modülleriniz birden çok sürüm kullanıyorsa, profil için .NET Framework çalışma zamanının sürümünü belirtin. Varsayılan olarak, yüklenen ilk sürüm profili oluşturulur.|- [nasıl yapılır: .NET Framework çalışma zamanını belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|

## <a name="instrumentation-tasks"></a>İzleme görevleri

Aşağıdaki tabloda yer alan görevler, izleme yöntemiyle profil oluşturmaya özgü **Özellik sayfaları** iletişim kutusunda bulunan seçeneklerdir.

|Görev|İlgili Içerik|
|----------|---------------------|
|**Ikili dosyalar** sayfasında, modüllerin belgelenmiş kopyaları için bir konum belirtin. Varsayılan olarak, özgün ikililer bir yedekleme klasörüne taşınır.|- [nasıl yapılır: Işaretlenmiş Ikililerin konumunu](../profiling/how-to-relocate-instrumented-binaries.md) değiştirme|
|**İzleme** sayfasında, profil oluşturma ek yükünü azaltmak, ASP.NET Web sayfalarındaki JavaScript kodu profilini oluşturmak ve izleme işleminden önce ve sonra bir komut isteminde çalışacak komutları belirtmek için, yönetim sayfası ' ndan küçük işlevleri hariç tutun.|- [nasıl yapılır: izleme 'den kısa Işlevler hariç tutma veya dahil](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md) etme<br />- [nasıl yapılır: Web sayfalarında JavaScript kodunun profilini](../profiling/how-to-profile-javascript-code-in-web-pages.md) oluşturma<br />- [nasıl yapılır: ön ve son Izleme komutları belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|**CPU sayaçları** sayfasında, profil oluşturma verilerine eklemek için bir veya daha fazla işlemci performans sayacı belirtin.|- [nasıl yapılır: CPU sayacı verilerini toplama](../profiling/how-to-collect-cpu-counter-data.md)|
|**Gelişmiş** sayfasında, belirli işlevleri ekleme veya hariç tutma seçenekleri gibi Istediğiniz ek VSInstr. exe seçeneklerini belirtin. VSInstr seçenekleri hakkında daha fazla bilgi için bkz. [vsinstr](../profiling/vsinstr.md)|- [nasıl yapılır: ek izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)<br />- [nasıl yapılır: belirli işlevlerle Izleme sınırlandırma](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
[nasıl yapılır: koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md)
[performans oturumu özellikleri](../profiling/performance-session-properties.md)
