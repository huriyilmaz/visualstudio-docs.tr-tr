---
title: Performans Oturumu Özellikleri | Microsoft Docs
description: Performans Oturumu'nın, uygulamanın profilini belirleyen ayarları yapılandırmayı nasıl olanaklı olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0fb9846958700e89ea4bc7cf12815ccf6335e39c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726813"
---
# <a name="performance-session-properties"></a>Performans oturumu özellikleri

Performans **Oturumu,** uygulamanın profilini belirleyen ayarları yapılandırmaya olanak sağlar. Profil oluşturma oturumu için oluşturulan raporları da depolar.

Performans **Sihirbazı'nı çalıştırarak** veya el **ile oturum** oluşturarak bir Performans Oturumu oluşturabilirsiniz. Performans **Oturumu** oluşturulduktan **sonra Performans Gezgini** **oturumda** görüntülenir.

Performans Oturumu **özelliklerini görüntülemek** için, oturum adını Performans Gezgini **tıklayın** ve ardından Özellikler'i **seçin.**

Performans oturumu aşağıdaki özellik sayfalarına sahip:

## <a name="general"></a>Genel

Bu ayarlar profil oluşturma yöntemini seçmenize, .NET nesne koleksiyonu ve yaşam süresi verileri eklemenize ve varsayılan rapor konumu ile adlandırma kuralları belirtmenize olanak sağlar.

Daha fazla bilgi için bkz.

[Nasıl yapılacaklar: Koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md)

[.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

- [Nasıl yapılır: Performans veri dosyası adlandırma seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)

## <a name="launch"></a>Başlat

Bu ayarlar, ikili dosyalar listesinden seçim yapabilirsiniz ve ikililerin başlangıç sırası belirtebilirsiniz.

Daha fazla bilgi için, [bkz. How to: Specify the binary to start](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="sampling"></a>Örnekleme

Bu ayarlar, örnekleme profil oluşturma yöntemi olarak kullanılırken örnek olay ve örnekleme aralığını seçmenize olanak sağlar. Belirtilen aralıkta profil oluşturma verilerini toplamak için örnek bir olay kullanılır. Örneğin, örnek olay saat döngüleri ise ve örnekleme aralığı 10.000.000 olarak ayarlanırsa, profil oluşturma verileri her 10 milyon saat döngüsünde toplanır. Aşağıdaki dört örnek olay türü kullanılabilir:

- Saat Döngüleri - CPU'ya bağlı sorunlar için
- Sayfa Hataları - bellekle ilgili sorunlar için
- Sistem Çağrıları - I/O ile ilgili sorunlar için
- Performans Sayaçları - alt düzey performans sorunları için
- Kullanılabilir performans sayaçlarına göre ek örnek olaylar belirtilebilir

Daha fazla bilgi için [bkz. Nasıl? Örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md)

## <a name="binary"></a>İkili
Bu ayarlar, araçlı ikili dosyanın başka bir konuma taşınmak isteyip istemediklerini belirtmenize olanak sağlar. Örneğin,My.DLLprofiliMy.DLL ikili dosyayı yeniden taşınmazsanız,My.DLLadlı bir *My.Orig.DLL*  oluşturulur. Daha sonra *My.DLL* veri toplamak için yoklamalar eksildiğinde değişiklik değiştirilebilir. Araçlı ikili dosyayı yeniden kullanmaya karar verdiy olursanız, özgün ikili dosya yeniden adlandırılamaz ve ölçümleme sırasında kullanmak üzere belirtilen konuma kopyalanır.

Daha fazla bilgi için, [bkz. How to: Specify the binary to start](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="tier-interactions"></a>Katman etkileşimleri

Daha fazla bilgi için [bkz. Katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md)

## <a name="instrumentation"></a>İzleme

Bu ayarlar, Web sayfalarındaki JScript için performans verileri toplamanız ve ölçümleme işlemi öncesinde veya sonrasında gerçekleşmesini istediğiniz Ön ölçüm ve Son ölçüm olaylarını [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] belirtmenize olanak  sağlar. 

Daha fazla bilgi için bkz.

[Nasıl kullanılır: Web sayfalarında JavaScript kodunun profilini oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[Nasıl kullanılır: Ön ve son ölçüm komutları belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>CPU sayaçları

Bu ayarlar, ölçüm ölçüm profil oluşturma yöntemini kullanırken CPU performans sayaçları hakkında veri toplamaya olanak sağlar. Taşınabilir Performans sayaçları CPU tasarımına veya üreticisine bakılmaksızın kullanılabilir. Platform Olayları, CPU tasarımına ve üreticisine özeldir. Yonga üzerinde performans sayaçları hakkında daha fazla bilgi için ilgili işlemci belgelerine bakın.

Daha fazla bilgi için [bkz. Nasıl kullanılır: CPU sayacı verilerini toplama](../profiling/how-to-collect-cpu-counter-data.md)

## <a name="windows-events"></a>Windows olayları

Profil oluşturma sırasında olay izleme sağlayıcılarından veri toplayabilirsiniz. Komut satırı aracı seçeneğini kullanarak *VSPerfReport.exe* `/calltrace` görüntüebilirsiniz. Windows için Olay İzleme (ETW) hakkında daha fazla bilgi için [bkz. Olay İzleme Hakkında.](/windows/win32/etw/about-event-tracing)

Daha fazla bilgi için bkz.

[Nasıl Windows (ETW) verileri için olay izleme toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md).

## <a name="windows-counters"></a>Windows sayaçları

Bu seçenek, farklı sayaçlardan veri Windows Performans İzleyicisi sağlar. Bu verileri toplamak için Performans Sayaçlarını Topla **etiketli Windows kutusunu seçin.** Koleksiyon aralığı, Koleksiyon Aralığı **kutusunda ayarlanabilir.** **Sayaç Kategorisi** ve **Örneği** de kullanılabilir. Bazı varsayılan Windows Performans İzleyicisi sayaçları kullanılabilir.

 Daha fazla bilgi için [bkz. Nasıl Windows verileri toplama.](../profiling/how-to-collect-windows-counter-data.md)

## <a name="advanced"></a>Gelişmiş

Bu ayarlar, [VSInstr](../profiling/vsinstr.md) komut satırı profil oluşturma aracının bir veya daha fazla seçeneği belirterek ölçümleme sürecine seçenekler eklemenize olanak sağlar. Uygulama birden fazla sürüm kullanırken profili oluşturmak için Common Runtime sürümünü de belirtebilirsiniz.

Daha fazla bilgi için bkz.

[Nasıl yapılır: .NET Framework çalışma zamanını belirtin](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[Nasıl yapılır: Ek izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>Ayrıca bkz.

[Genel Bakışlar](../profiling/overviews-performance-tools.md) 
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)
