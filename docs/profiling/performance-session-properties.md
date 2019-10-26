---
title: Performans oturumu özellikleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c8a5058d52684ec08e13641953c789c244f2fa9
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72910141"
---
# <a name="performance-session-properties"></a>Performans oturumu özellikleri

Bir **performans oturumu** , uygulamanın profili oluşturma şeklini belirleyecek ayarları yapılandırmanıza olanak sağlar. Profil oluşturma oturumu için oluşturulan raporları da depolar.

Performans **sihirbazını** çalıştırarak veya el ile bir oturum oluşturarak bir **performans oturumu** oluşturursunuz. Performans **oturumu** , performans **oturumu** oluşturulduktan sonra **Performans Gezgini** görüntülenir.

**Performans oturumu** özelliklerini görüntülemek için **Performans Gezgini**oturum adını seçin, sağ tıklayın ve ardından **Özellikler**' i seçin.

Performans oturumu aşağıdaki özellik sayfalarına sahiptir:

## <a name="general"></a>Genel

Bu ayarlar, .NET nesne koleksiyonu ve ömür verileri eklemek ve varsayılan rapor konumunu ve adlandırma kurallarını belirtmek için profil oluşturma yöntemini seçmenizi sağlar.

Daha fazla bilgi için bkz.:

[Nasıl yapılır: Toplama metotlarını seçme](../profiling/how-to-choose-collection-methods.md)

[.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

- [Nasıl yapılır: Performans veri dosyası adlandırma seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)

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
Bu ayarlar, izlenen ikiliyi başka bir konuma değiştirmek isteyip istemediğinizi belirtmenize olanak tanır. Örneğin, *My. DLL dosyasını* profillendirilir ve izlenen ikilinin yerini değiştirmek istemiyorsanız, My. *DLL* ' nin yedek kopyası *My. orig. dll* adlı bir yedekleme oluşturulur. Daha sonra, *My. dll* verileri toplamak için yoklamalar eklenerek değiştirilir. İzlenen ikilinin yeniden konumlandırmaya karar verirseniz, orijinal ikili yeniden adlandırılmaz ve izlenen ikili, izleme sırasında kullanılmak üzere belirtilen konuma kopyalanır.

Daha fazla bilgi için bkz. [nasıl yapılır: başlatılacak Ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="tier-interactions"></a>Katman etkileşimleri

Daha fazla bilgi için bkz. [Katman etkileşimi verilerini toplama](../profiling/collecting-tier-interaction-data.md)

## <a name="instrumentation"></a>İzleme

Bu ayarlar, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web sayfalarında JScript kodu için performans verileri toplamanıza olanak sağlar ve izleme işleminden önce veya sonra gerçekleşmesini istediğiniz herhangi bir **araç öncesi** ve **sonrası** olay belirtebilirsiniz.

Daha fazla bilgi için bkz.:

[Nasıl yapılır: Web sayfalarında JavaScript kodu profili oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[Nasıl yapılır: Ön ve son izleme komutları belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>CPU sayaçları

Bu ayarlar, izleme profili oluşturma yöntemini kullanırken CPU performans sayaçları hakkında veri toplamanıza olanak tanır. Taşınabilir performans sayaçları, CPU tasarımı veya üreticisi ne olursa olsun kullanılabilir. Platform olayları, CPU tasarımına ve üreticisine özeldir. Yonga hakkında performans sayaçları hakkında daha fazla bilgi için bkz. belirli işlemci belgeleri.

Daha fazla bilgi için bkz [. nasıl yapılır: CPU sayacı verilerini toplama](../profiling/how-to-collect-cpu-counter-data.md)

## <a name="windows-events"></a>Windows olayları

Profil oluşturma sırasında, olay izleme sağlayıcılarından veri toplayabilirsiniz. *VSPerfReport. exe* komut satırı aracı `/calltrace` seçeneğini kullanarak verileri görüntüleyebilirsiniz. Windows için olay Izleme (ETW) hakkında daha fazla bilgi için bkz. [olay Izleme hakkında](/windows/win32/etw/about-event-tracing).

Daha fazla bilgi için bkz.:

[Nasıl yapılır: Windows için olay izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md).

## <a name="windows-counters"></a>Windows sayaçları

Bu seçenek, Windows performans Izleyicisi sayaçlarından veri toplamanıza olanak sağlar. Bu verileri toplamak için **Windows performans sayaçlarını topla**etiketli onay kutusunu seçin. Koleksiyon aralığı, **koleksiyon aralığı** kutusunda ayarlanabilir. **Sayaç kategorisi** ve **örneği** de kullanılabilir olabilir. Bazı varsayılan Windows performans Izleyicisi sayaçları kullanılabilir.

 Daha fazla bilgi için bkz. [nasıl yapılır: Windows sayaç verilerini toplama](../profiling/how-to-collect-windows-counter-data.md).

## <a name="advanced"></a>Gelişmiş

Bu ayarlar, [vsinstr](../profiling/vsinstr.md) komut satırı profil oluşturma Aracı ' nın bir veya daha fazla seçeneğini belirterek, izleme işlemine seçenekler eklemenize olanak tanır. Ayrıca, uygulama birden fazla sürüm kullanırken profil için ortak çalışma zamanının sürümünü belirtebilirsiniz.

Daha fazla bilgi için bkz.:

[Nasıl yapılır: .NET Framework çalışma zamanını belirtin](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[Nasıl yapılır: Ek izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>Ayrıca bkz.

[Genel bakış](../profiling/overviews-performance-tools.md)
[performans oturumlarını](../profiling/configuring-performance-sessions.md)
[Denetim verileri toplamayı](../profiling/controlling-data-collection.md) yapılandırma