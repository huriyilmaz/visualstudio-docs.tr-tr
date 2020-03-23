---
title: Performans Oturum Özellikleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b3bafa976c8e57f468a3f3f59a3b6b19308fd1b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772208"
---
# <a name="performance-session-properties"></a>Performans oturumu özellikleri

**Performans Oturumu,** uygulamanın nasıl profilinin açıkolduğunu belirleyen ayarları yapılandırmanızı sağlar. Ayrıca profil oluşturma oturumu için oluşturulan raporları da saklar.

**Performans Sihirbazı'nı** çalıştırarak veya el ile oturum oluşturarak bir **Performans Oturumu** oluşturursunuz. **Performans Oturumu,** **Performans Oturumu** oluşturulduktan sonra **Performans Gezgini'nde** görüntülenir.

Performans **Oturumu** özelliklerini görüntülemek **için, Performans Gezgini'nde**oturum adını seçin, sağ tıklatın ve ardından **Özellikler'i**seçin.

Performans oturumunda aşağıdaki özellik sayfaları vardır:

## <a name="general"></a>Genel

Bu ayarlar profil oluşturma yöntemini seçmenize, .NET nesne toplama ve ömür boyu veri eklemenize ve varsayılan rapor konumunu ve adlandırma kurallarını belirtmenize olanak tanır.

Daha fazla bilgi için bkz.

[Nasıl yapılır: Toplama yöntemlerini seçin](../profiling/how-to-choose-collection-methods.md)

[.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

- [Nasıl yapılır: Performans veri dosyası adlandırma seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)

## <a name="launch"></a>Başlat

Bu ayarlar, ikililer listesinden seçim yapmanızı ve ikililerin başlangıç sırasını belirtmenizi sağlar.

Daha fazla bilgi için [bkz: Başlamak için ikiliyi belirtin](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="sampling"></a>Örnekleme

Bu ayarlar, örnekleme profil oluşturma yöntemi olarak kullanıldığında örnek olay ve örnekleme aralığını seçmenize olanak tanır. Örnek olay, belirtilen aralıkta profil oluşturma verileri toplamak için kullanılır. Örneğin, örnek olay saat döngüleri ve örnekleme aralığı 10.000.000 olarak ayarlanırsa, profil oluşturma verileri her 10 milyon saat döngüsünden sonra toplanır. Aşağıdaki dört tür örnek olay mevcuttur:

- Saat Döngüleri - CPU bağlama sorunları için
- Sayfa Hataları - bellekle ilgili sorunlar için
- Sistem Aramaları - G/Ç ile ilgili sorunlar için
- Performans Sayaçları - düşük seviyeli performans sorunları için
- Kullanılabilir performans sayaçlarına göre ek örnek olaylar belirtilebilir

Daha fazla bilgi için [bkz: Örnekleme olaylarını seçin](../profiling/how-to-choose-sampling-events.md)

## <a name="binary"></a>İkili
Bu ayarlar, enstrümantasyonlu ikiliyi başka bir konuma taşımak isteyip istemediğinizi belirtmenize olanak tanır. Örneğin, *My.DLL'nin* profilini çıkarıyorsanız ve enstrümantize ikiliyi başka bir yere taşımamayı seçiyorsanız, *My.DLL'nin* *My.Orig.DLL* adlı yedek bir kopyası oluşturulur. Daha sonra, *My.DLL* veri toplamak için problar ekleyerek değiştirilir. Enstrümantasyonlu ikilinin yerini değiştirmeye karar verirseniz, orijinal ikilinin adı değiştirilmez ve enstrümantasyon sırasında kullanılmak üzere belirtilen konuma kopyalanır.

Daha fazla bilgi için [bkz: Başlamak için ikiliyi belirtin](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="tier-interactions"></a>Katman etkileşimleri

Daha fazla bilgi için bkz. [katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)

## <a name="instrumentation"></a>İzleme

Bu ayarlar, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web sayfalarında JScript kodu için performans verileri toplamanızı ve enstrümantasyon işleminden önce veya sonra gerçekleşmesini istediğiniz Ön **enstrüman** ve **Post-instrument** olaylarını belirtmenize olanak tanır.

Daha fazla bilgi için bkz.

[Nasıl kullanılır: Web sayfalarında Profil JavaScript kodu](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[Nasıl yapılır: Enstrüman öncesi ve sonrası komutları belirtin](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>CPU sayaçları

Bu ayarlar, enstrümantasyon profil oluşturma yöntemini kullanırken CPU performans sayaçları hakkında veri toplamanızı sağlar. Taşınabilir Performans sayaçları, CPU tasarımı veya üreticisi ne olursa olsun kullanılabilir. Platform Etkinlikleri, CPU tasarımına ve üreticisine özgüdür. On-chip performans sayaçları hakkında daha fazla bilgi için, belirli işlemci belgelerine bakın.

Daha fazla bilgi için [bkz: CPU karşı veritoplama](../profiling/how-to-collect-cpu-counter-data.md)

## <a name="windows-events"></a>Windows olayları

Profil oluşturma sırasında, olay izleme sağlayıcılarından veri toplayabilirsiniz. *VSPerfReport.exe* komut satırı aracı `/calltrace` seçeneğini kullanarak verileri görüntüleyebilirsiniz. Windows için Olay İzleme (ETW) hakkında daha fazla bilgi için, [Olay İzleme Hakkında'ya](/windows/win32/etw/about-event-tracing)bakın.

Daha fazla bilgi için bkz.

[Nasıl yapılır: Windows (ETW) verileri için olay izleme toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md).

## <a name="windows-counters"></a>Windows sayaçları

Bu seçenek, Windows Performance Monitor sayaçlarından veri toplamanızı sağlar. Bu verileri toplamak **için, Windows Performans Sayaçlarını Topla**etiketli onay kutusunu seçin. Toplama aralığı **Toplama Aralığı** kutusunda ayarlanabilir. **Sayaç Kategorisi** ve **Örneği** de kullanılabilir. Bazı varsayılan Windows Performance Monitor sayaçları kullanılabilir.

 Daha fazla bilgi için [bkz: Windows karşı veritoplama.](../profiling/how-to-collect-windows-counter-data.md)

## <a name="advanced"></a>Gelişmiş

Bu ayarlar, [VSInstr](../profiling/vsinstr.md) komut satırı profil oluşturma aracının bir veya daha fazla seçeneğini belirterek enstrümantasyon işlemine seçenekler eklemenizi sağlar. Uygulama birden fazla sürüm kullanırken profil için Ortak Çalışma Zamanı sürümünü de belirtebilirsiniz.

Daha fazla bilgi için bkz.

[Nasıl yapılır: .NET Framework çalışma zamanını belirtin](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[Nasıl yapılır: Ek izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>Ayrıca bkz.

[Genel BakışPerformans](../profiling/overviews-performance-tools.md)
[oturumlarını](../profiling/configuring-performance-sessions.md)
yapılandırma Kontrol veri[toplama](../profiling/controlling-data-collection.md)
