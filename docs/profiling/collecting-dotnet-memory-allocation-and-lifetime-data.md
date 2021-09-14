---
title: Yaşam süresi verileri için .NET & ayırmayı toplama
description: .NET uygulamanıza bellekle ilgili performans sorunlarını algılamaya yardımcı olmak için Profil Oluşturma Araçları ayırma ve nesne yaşam süresi verilerini toplamak üzere .NET uygulamasını kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 2335db6165d5dd973c454723bda9eeee97475ba8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635793"
---
# <a name="collect-net-framework-memory-allocation-and-lifetime-data"></a>Bellek .NET Framework yaşam süresi verilerini toplama

Visual Studio Profil Oluşturma Araçları bellek ayırma ve .NET Framework ömrü verilerini toplamayı destekler ve bu da uygulamanıza bellekle ilgili performans sorunlarını algılamanıza yardımcı olur.

- .NET bellek ayırma hakkında veriler, ayrılan bellek nesnelerinin .NET Framework sayısını içerir.

- Nesne yaşam süresi verileri, üç atık toplama .NET Framework geri alan bellek nesnelerinin boyutunu ve sayısını içerir.

> [!NOTE]
> Bu platformlarda Windows 8 Windows Server 2012 profil oluşturma Visual Studio önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

Örnekleme veya ölçüm profil oluşturma yöntemini kullanarak veri toplayabilirsiniz.

- Örnekleme yöntemini kullanarak profil oluşturan, başlatan veya bağlanan işlem tarafından oluşturulan tüm .NET bellek ayırmalarını ve nesnelerini izler.

- Ölçümleme yöntemini kullanırken, profilleyici yalnızca izli modüller tarafından oluşturulan .NET bellek ayırmalarını ve nesnelerini izler.

> [!IMPORTANT]
> Örnekleme yöntemini kullanarak .NET bellek verilerini (ayırmalar, nesne yaşamları veya her ikisi) toplarken, kullanıcı tarafından belirtilen tüm örnekleme olayları yoksayılır ve verileri toplamak için uygun bellek ayırma olayları kullanılır.

Profil oluşturmayı bellek ayırma of.NET etkinleştirerek Ayırma Görünümü'lerini de etkinleştirirsiniz. .NET yaşam süresi verilerini profil oluşturmayı etkinleştirirsanız, Nesneler Yaşam Süresi Görünümü'ne de olanak sağlar. Daha fazla bilgi için [bkz. Ayırmalar Görünümü](../profiling/dotnet-memory-allocations-view.md) ve [Nesne Ömrü Görünümü.](../profiling/object-lifetime-view.md)

Profil Oluşturma Araçları komut satırı araçlarını kullanarak .NET bellek verilerini toplama hakkında bilgi için, bkz. Komut Satırı'dan Profil Oluşturma Yöntemlerini Kullanarak Bellek Ayırma ve Nesne Ömrü Verilerini Toplamak için .NET Bellek Yöntemlerini [Kullanma.](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)

## <a name="to-collect-net-memory-data"></a>.NET bellek verilerini toplamak için

1. Bu **Performans Gezgini,** performans oturumuna sağ tıklayın ve ardından Özellikler'e **tıklayın.**

2. Performans Oturumu *Özellik* **Sayfaları iletişim** kutusunda Genel sekmesine tıklayın ve **.NET** nesne ayırma bilgilerini topla onay kutusunu seçin. 

3. .NET nesne ömrü verilerini toplamak için **.NET** nesne yaşam süresi bilgilerini de topla onay kutusunu işaretleyin.

## <a name="common-tasks"></a>Genel görevler

Performans oturumunun Performans Oturumu _Özellik Sayfaları_**iletişim kutusunda** ek seçenekler belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- Bu **Performans Gezgini,** performans oturumu adına sağ tıklayın ve ardından Özellikler'e **tıklayın.**

Aşağıdaki tabloda yer alan görevler, .NET bellek verilerini toplayan Performans Oturumu **Özellik** Sayfaları iletişim kutusunda belirtebilirsiniz seçenekleri açıklar.

|Görev|İlgili İçerik|
|----------|---------------------|
|Genel **sayfasında,** oluşturulan profil oluşturma verileri (.vsp) dosyası için adlandırma ayrıntılarını belirtin.|- [.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Nasıl kullanılır: Performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|Başlat **sayfasında,** kod çözümde birden çok projeniz varsa .exe uygulamayı seçin.|- [Katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)|
|Katman **Etkileşimi sayfasında,** profil oluşturma ADO.NET veri çağırmayı seçin.|- [Katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)|
|Windows **Olayları sayfasında,** örnekleme verileriyle topilebilecek Windows (ETW) olayları için bir veya daha fazla Olay İzleme belirtin.|- [Nasıl kullanılır: Veri kaynağı (ETW) Windows Olay İzleme toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Profil **Windows profil** oluşturma verilerine işaret olarak eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|- [Nasıl Windows: Windows toplama](../profiling/how-to-collect-windows-counter-data.md)|
|Gelişmiş **sayfasında,** uygulama modülleriniz birden çok sürüm kullanıyorsa .NET Framework çalışma zamanının sürümünü belirtin. Varsayılan olarak, yüklenen ilk sürümün profili kullanılır.|- [Nasıl kullanılır: Çalışma .NET Framework belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|

## <a name="instrumentation-tasks"></a>Ölçüm araçları görevleri

Aşağıdaki tabloda yer alan görevler, Özellik Sayfaları **iletişim** kutusundaki ölçümleme yöntemiyle profil oluşturmaya özgü seçeneklerdir.

|Görev|İlgili İçerik|
|----------|---------------------|
|Ikili **Dosyalar sayfasında,** modüllerin irdeli kopyaları için bir konum belirtin. Varsayılan olarak, özgün ikili dosyalar bir yedekleme klasörüne taşınır.|- [Nasıl olur: Araçlı IkiliLeri Yeniden Konumlandır](../profiling/how-to-relocate-instrumented-binaries.md)|
|Ölçümler **sayfasında,** profil oluşturma yükünü azaltmak için küçük işlevleri profil oluşturmanın dışında tutmak, ASP.NET Web sayfalarında JavaScript kodunun profilini oluşturmak ve ölçümleme işlemi öncesinde ve sonrasında komut isteminde çalıştırılacak komutları belirtin.|- [Nasıl kullanılır: Kısa işlevleri ölçümden hariç tutmak veya dahil etmek](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />- [Nasıl kullanılır: Web Sayfalarında JavaScript Kodunun Profilini Oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />- [Nasıl kullanılır: Ön ve Son Ölçüm Komutlarını Belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|CPU **Sayaçları sayfasında,** profil oluşturma verilerine eklemek için bir veya daha fazla işlemci performans sayacı belirtin.|- [Nasıl kullanılır: CPU Sayacı Verileri Toplama](../profiling/how-to-collect-cpu-counter-data.md)|
|Gelişmiş **sayfasında,** belirli işlevleri dahil VSInstr.exe dışlama seçenekleri gibi istediğiniz tüm ek güvenlik ayarları seçeneklerini belirtin. VSInstr seçenekleri hakkında daha fazla bilgi için bkz. [VSInstr](../profiling/vsinstr.md)|- [Nasıl yapabilirsiniz: Ek ölçümler belirtme seçenekleri](../profiling/how-to-specify-additional-instrumentation-options.md)<br />- [Nasıl kullanılır: Araçları belirli işlevlerle sınırlama](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Nasıl yapılacaklar: Koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md) 
 [Performans oturumu özellikleri](../profiling/performance-session-properties.md)
