---
title: Performans oturumu özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
ms.assetid: c3a86913-172b-488f-a31a-cea01a71b2ea
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: af214f6a29e12dcdf2fe8bd2de75e05283894922
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74290108"
---
# <a name="performance-session-properties"></a>Performans Oturum Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir **performans oturumu** , uygulamanın profili oluşturma şeklini belirleyecek ayarları yapılandırmanıza olanak sağlar. Profil oluşturma oturumu için oluşturulan raporları da depolar.  
  
 **Requirements**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Performans **sihirbazını** çalıştırarak veya el ile bir oturum oluşturarak bir **performans oturumu** oluşturursunuz. Performans **oturumu** , performans **oturumu** oluşturulduktan sonra **Performans Gezgini** görüntülenir.  
  
  **Performans oturumu** özelliklerini görüntülemek için **Performans Gezgini**oturum adını seçin, sağ tıklayın ve ardından **Özellikler**' i seçin.  
  
  Performans oturumu aşağıdaki özellik sayfalarına sahiptir:  
  
## <a name="general"></a>Genel  
 Bu ayarlar, .NET nesne koleksiyonu ve ömür verileri eklemek ve varsayılan rapor konumunu ve adlandırma kurallarını belirtmek için profil oluşturma yöntemini seçmenizi sağlar.  
  
 Daha fazla bilgi için bkz.:  
  
 [Nasıl Yapılır: Toplama Metotlarını Seçme](../profiling/how-to-choose-collection-methods.md)  
  
 [.NET Bellek Ayırma ve Yaşam Süresi Verilerini Toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [Nasıl Yapılır: Performans Veri Dosyası Adlandırma Seçeneklerini Ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)  
  
## <a name="launch"></a>Başlat  
 Bu ayarlar, ikili bir listeden seçim yapmanız ve ikili dosyaların başlangıç sırasını belirtmenizi sağlar.  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: başlatılacak Ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="sampling"></a>Aşağıdakine  
 Bu ayarlar, örnekleme profil oluşturma yöntemi olarak kullanıldığında örnek olay ve örnekleme aralığını seçmenizi sağlar. Belirtilen aralıkta profil oluşturma verilerini toplamak için örnek bir olay kullanılır. Örneğin, örnek olay saat döngüleri ise ve örnekleme aralığı 10.000.000 olarak ayarlanırsa, profil oluşturma verileri her 10.000.000 saat döngüden sonra toplanır. Aşağıdaki dört örnek olay türü mevcuttur:  
  
- Saat döngüleri-CPU ile bağlantılı sorunlar için  
  
- Sayfa hataları-bellekle ilgili sorunlar için  
  
- Sistem çağrıları-g/ç ile ilgili sorunlar için  
  
- Performans sayaçları-düşük düzeyde performans sorunları için  
  
- Ek örnek olaylar, kullanılabilir performans sayaçlarına göre belirtilebilir  
  
  Daha fazla bilgi için bkz [. nasıl yapılır: örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md)  
  
## <a name="binary"></a>İkili  
 Bu ayarlar, izlenen ikiliyi başka bir konuma değiştirmek isteyip istemediğinizi belirtmenize olanak tanır. Örneğin, My. DLL dosyasını profillendirilir ve izlenen ikilinin yerini değiştirmek istemiyorsanız, My. DLL ' nin yedek kopyası My. orig. DLL adlı bir yedekleme oluşturulur. Daha sonra, My. DLL verileri toplamak için yoklamalar eklenerek değiştirilir. İzlenen ikilinin yeniden konumlandırmaya karar verirseniz, orijinal ikili yeniden adlandırılmaz ve izlenen ikili, izleme sırasında kullanılmak üzere belirtilen konuma kopyalanır.  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: başlatılacak Ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="tier-interactions"></a>Katman etkileşimleri  
 Daha fazla bilgi için bkz. [Katman etkileşimi verilerini toplama](../profiling/collecting-tier-interaction-data.md)  
  
## <a name="instrumentation"></a>İzleme  
 Bu ayarlar, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web sayfalarında JScript kodu için performans verileri toplamanıza olanak sağlar ve izleme işleminden önce veya sonra gerçekleşmesini istediğiniz herhangi bir **araç öncesi** ve **sonrası** olay belirtebilirsiniz.  
  
 Daha fazla bilgi için bkz.:  
  
 [Nasıl Yapılır: Web Sayfalarında JavaScript Kodunun Profilini Oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)  
  
 [Nasıl Yapılır: Ön ve Son İzleme Komutları Belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)  
  
## <a name="cpu-counters"></a>CPU sayaçları  
 Bu ayarlar, izleme profili oluşturma yöntemini kullanırken CPU performans sayaçları hakkında veri toplamanıza olanak tanır. Taşınabilir performans sayaçları, CPU tasarımı veya üreticisi ne olursa olsun kullanılabilir. Platform olayları, CPU tasarımına ve üreticisine özeldir. Yonga hakkında performans sayaçları hakkında daha fazla bilgi için bkz. belirli işlemci belgeleri.  
  
 Daha fazla bilgi için bkz [. nasıl yapılır: CPU sayacı verilerini toplama](../profiling/how-to-collect-cpu-counter-data.md)  
  
## <a name="windows-events"></a>Windows Olayları  
 Profil oluşturma sırasında, olay izleme sağlayıcılarından veri toplayabilirsiniz. VSPerfReport. exe komut satırı aracı `/calltrace` seçeneğini kullanarak verileri görüntüleyebilirsiniz. Windows için olay Izleme (ETW) hakkında daha fazla bilgi için bkz. [olay Izleme hakkında](https://go.microsoft.com/fwlink/?linkid=90752).  
  
 Daha fazla bilgi için bkz.:  
  
 [Nasıl Yapılır: Windows İçin Olay İzleme (ETW) Verileri Toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)  
  
 [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="windows-counters"></a>Windows sayaçları  
 Bu seçenek, Windows performans Izleyicisi sayaçlarından veri toplamanıza olanak sağlar. Bu verileri toplamak için **Windows performans sayaçlarını topla**etiketli onay kutusunu seçin. Koleksiyon aralığı, **koleksiyon aralığı** kutusunda ayarlanabilir. **Sayaç kategorisi** ve **örneği** de kullanılabilir olabilir. Bazı varsayılan Windows performans Izleyicisi sayaçları kullanılabilir.  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: Windows sayaç verilerini toplama](../profiling/how-to-collect-windows-counter-data.md).  
  
## <a name="advanced"></a>Gelişmiş  
 Bu ayarlar, [vsinstr](../profiling/vsinstr.md) komut satırı profil oluşturma Aracı ' nın bir veya daha fazla seçeneğini belirterek, izleme işlemine seçenekler eklemenize olanak tanır. Ayrıca, uygulama birden fazla sürüm kullanırken profil için ortak çalışma zamanının sürümünü belirtebilirsiniz.  
  
 Daha fazla bilgi için bkz.:  
  
 [Nasıl Yapılır: .NET Framework Çalışma Zamanını Belirtin](../profiling/how-to-specify-the-dotnet-framework-runtime.md)  
  
 [Nasıl Yapılır: Ek İzleme Seçeneklerini Belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel bakış](../profiling/overviews-performance-tools.md)   
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Veri Koleksiyonunu Denetleme](../profiling/controlling-data-collection.md)
