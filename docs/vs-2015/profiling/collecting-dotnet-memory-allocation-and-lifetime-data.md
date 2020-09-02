---
title: .NET bellek ayırma ve yaşam süresi verilerini toplama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68decc73e14f8748d8434e05e50d6d3b48612d40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64816121"
---
# <a name="collecting-net-memory-allocation-and-lifetime-data"></a>.NET Bellek Ayırma ve Yaşam Süresi Verilerini Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profil Oluşturma Araçları, uygulamanızda bellekle ilgili performans sorunlarını algılamanıza yardımcı olan .NET bellek ayırma ve nesne yaşam süresi verilerinin toplanmasını destekler.  
  
- .NET bellek ayırma hakkındaki veriler, ayrılan .NET Framework bellek nesnelerinin boyutunu ve sayısını içerir.  
  
- Nesne yaşam süresi verileri, üç çöp toplama nesekte geri kazanılan .NET Framework bellek nesnelerinin boyutunu ve sayısını içerir.  
  
  **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Örnekleme veya izleme profili oluşturma yöntemini kullanarak verileri toplayabilirsiniz.  
  
- Örnekleme yöntemini kullandığınızda, Profil Oluşturucu tüm .NET bellek ayırmalarını ve başlatılan veya öğesine bağlı işlem tarafından oluşturulan nesneleri izler.  
  
- İzleme yöntemini kullandığınızda, Profil Oluşturucu yalnızca bu .NET bellek ayırmalarını ve belgelenmiş modüller tarafından oluşturulan nesneleri izler.  
  
> [!IMPORTANT]
> Örnekleme yöntemini kullanarak .NET bellek verileri (ayırmalar, nesne ömürleri veya her ikisi de) toplarken, Kullanıcı tarafından belirtilen tüm örnekleme olayları yok sayılır ve uygun bellek ayırma olayları veri toplamak için kullanılır.  
  
 Profil oluşturma of.NET bellek ayırmayı etkinleştirirseniz, ayırma görünümünü de etkinleştirirsiniz. .NET ömür verilerinin profilini oluşturmayı etkinleştirirseniz, nesne ömrü görünümünü de etkinleştirirsiniz. Daha fazla bilgi için bkz. [ayırma görünümü](../profiling/dotnet-memory-allocations-view.md) ve [nesne ömrü görünümü](../profiling/object-lifetime-view.md).  
  
 Profil Oluşturma Araçları komut satırı araçlarını kullanarak .NET bellek verilerinin nasıl toplanacağı hakkında daha fazla bilgi için, bkz. [komut satırından profil oluşturma yöntemlerini kullanarak](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)bellek ayırmayı ve nesne yaşam süresi verilerini toplamak Için .net bellek yöntemlerini kullanma.  
  
### <a name="to-collect-net-memory-data"></a>.NET bellek verileri toplamak için  
  
1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
2. _Performans oturumu_**Özellik sayfaları** iletişim kutusunda, **genel** sekmesine tıklayın ve **.NET nesne ayırma bilgilerini topla** onay kutusunu seçin.  
  
3. .NET nesne yaşam süresi verilerini toplamak için **.NET nesne yaşam süresi bilgilerini de topla** onay kutusunu seçin.  
  
## <a name="common-tasks"></a>Ortak Görevler  
 Performans oturumunun _performans oturumu_**Özellik sayfaları** iletişim kutusunda ek seçenekleri belirtebilirsiniz. Bu iletişim kutusunu açmak için:  
  
- **Performans Gezgini**, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
  Aşağıdaki tabloda yer alan görevler, .NET bellek verilerini toplarken _performans oturumu_**Özellik sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri anlatmaktadır.  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Genel** sayfasında, oluşturulan profil oluşturma verileri (. vsp) dosyasının adlandırma ayrıntılarını belirtin.|-   [.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Kod çözümünüzde birden çok. exe projeniz varsa, **Başlat sayfasında başlatılacak** uygulamayı seçin.|-   [Katman etkileşimi verilerini toplama](../profiling/collecting-tier-interaction-data.md)|  
|**Katman etkileşimi** sayfasında, profil oluşturma çalıştırmasına ADO.NET çağrı verileri ekleyin.|-   [Katman etkileşimi verilerini toplama](../profiling/collecting-tier-interaction-data.md)|  
|**Windows olayları** sayfasında, örnekleme verileriyle toplanacak bir veya daha fazla Windows Için olay Izleme (ETW) olayları belirtin.|-   [Nasıl yapılır: Windows için olay Izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|**Windows sayaçları** sayfasında, profil oluşturma verilerine işaret eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|-   [Nasıl yapılır: Windows sayaç verileri toplama](../profiling/how-to-collect-windows-counter-data.md)|  
|**Gelişmiş** sayfasında, uygulama modülleriniz birden çok sürüm kullanıyorsa, profil için .NET Framework çalışma zamanının sürümünü belirtin. Varsayılan olarak, yüklenen ilk sürüm profili oluşturulur.|-   [Nasıl yapılır: .NET Framework çalışma zamanını belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|  
  
## <a name="instrumentation-tasks"></a>İzleme görevleri  
 Aşağıdaki tabloda yer alan görevler, izleme yöntemiyle profil oluşturmaya özgü **Özellik sayfaları** iletişim kutusunda bulunan seçeneklerdir.  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Ikili dosyalar** sayfasında, modüllerin belgelenmiş kopyaları için bir konum belirtin. Varsayılan olarak, özgün ikililer bir yedekleme klasörüne taşınır.|-   [Nasıl yapılır: Işaretlenmiş Ikililerin konumunu değiştirme](../profiling/how-to-relocate-instrumented-binaries.md)|  
|**İzleme** sayfasında, profil oluşturma ek yükünü azaltmak, ASP.NET Web sayfalarındaki JavaScript kodu profilini oluşturmak ve izleme işleminden önce ve sonra bir komut isteminde çalışacak komutları belirtmek için, yönetim sayfası ' ndan küçük işlevleri hariç tutun.|-   [Nasıl yapılır: Izleme 'den kısa Işlevler hariç tutma veya dahil etme](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Nasıl yapılır: Web sayfalarında JavaScript kodu profili oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Nasıl yapılır: ön ve araç sonrası komutları belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|**CPU sayaçları** sayfasında, profil oluşturma verilerine eklemek için bir veya daha fazla işlemci performans sayacı belirtin.|-   [Nasıl yapılır: CPU sayacı verilerini toplama](../profiling/how-to-collect-cpu-counter-data.md)|  
|**Gelişmiş** sayfasında, belirli işlevleri ekleme veya hariç tutma seçenekleri gibi istediğiniz ek VSInstr.exe seçeneklerini belirtin. VSInstr seçenekleri hakkında daha fazla bilgi için bkz. [vsinstr](../profiling/vsinstr.md)|-   [Nasıl yapılır: ek Izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Nasıl yapılır: belirli Işlevlerle Izleme sınırlandırma](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Nasıl yapılır: koleksiyon yöntemleri seçme](../profiling/how-to-choose-collection-methods.md)   
 [Performans oturumu özellikleri](../profiling/performance-session-properties.md)
