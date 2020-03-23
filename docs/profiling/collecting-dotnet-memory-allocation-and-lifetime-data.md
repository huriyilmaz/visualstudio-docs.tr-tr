---
title: .NET Bellek Tahsisi ve Yaşam Boyu Veri Toplama | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779590"
---
# <a name="collect-net-memory-allocation-and-lifetime-data"></a>.NET bellek ayırma ve yaşam süresi verilerini toplama

Visual Studio Profil Oluşturma Araçları, .NET bellek ayırma ve nesne yaşam boyu verilerinin toplanmasını destekler ve bu da uygulamanızdaki bellekle ilgili performans sorunlarını algılamanıza yardımcı olur.

- .NET bellek ayırma ile ilgili veriler, ayrılan .NET Framework bellek nesnelerinin boyutunu ve sayısını içerir.

- Nesne yaşam boyu verileri, üç çöp toplama neslinde geri alınan .NET Framework bellek nesnelerinin boyutunu ve sayısını içerir.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

Örnekleme veya enstrümantasyon profil oluşturma yöntemini kullanarak veri toplayabilirsiniz.

- Örnekleme yöntemini kullandığınızda, profil oluşturucu başlatılan veya eklenen işlem tarafından oluşturulan tüm .NET bellek ayırmalarını ve nesnelerini izler.

- Enstrümantasyon yöntemini kullandığınızda, profil oluşturucu yalnızca .NET bellek ayırmalarını ve enstrümantasyonlu modüller tarafından oluşturulan nesneleri izler.

> [!IMPORTANT]
> Örnekleme yöntemini kullanarak .NET bellek verilerini (ayırmalar, nesne yaşam alanları veya her ikisi) toplarken, kullanıcı tarafından belirtilen tüm örnekleme olayları yoksayılır ve veri toplamak için uygun bellek ayırma olayları kullanılır.

Profil oluşturma of.NET bellek ayırmayı etkinleştiriyorsanız, Ayırma Görünümü'ne de olanak tanırsınız. .NET yaşam boyu verilerinin profilini çıkarmayı etkinleştiriyorsanız, Nesneler Ömür Boyu Görünümü'ne de olanak tanırsınız. Daha fazla bilgi için [Bkz. Tahsisler Görünüm](../profiling/dotnet-memory-allocations-view.md) ve [Nesne Yaşam Boyu Görünümü.](../profiling/object-lifetime-view.md)

Profil Oluşturma Araçları komut satırı araçlarını kullanarak .NET bellek verilerinin nasıl toplandığı hakkında bilgi için bkz. [Using Profiling Methods From the Command Line](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)

## <a name="to-collect-net-memory-data"></a>.NET bellek verilerini toplamak için

1. **Performans Gezgini'nde,** performans oturumuna sağ tıklayın ve ardından **Özellikler'i**tıklatın.

2. Performans *Oturumu* **Özellik Sayfaları** iletişim kutusunda **Genel** sekmesini tıklatın ve **.NET nesne ayırma bilgilerini topla onay** kutusunu seçin.

3. .NET nesne yaşam boyu verilerini toplamak için **Ayrıca topla .NET nesne yaşam boyu bilgi** onay kutusunu seçin.

## <a name="common-tasks"></a>Genel görevler

_Performans Oturumu_**Özellik Sayfaları** iletişim kutusunda ek seçenekler belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- **Performans Gezgini'nde,** performans oturumu adını sağ tıklatın ve ardından **Özellikler'i**tıklatın.

Aşağıdaki tablodaki görevler, .NET bellek verilerini topladığınızda _Performans Oturumu_**Özellik Sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri açıklar.

|Görev|İlgili İçerik|
|----------|---------------------|
|**Genel** sayfada, oluşturulan profil oluşturma verileri (.vsp) dosyasının adlandırma ayrıntılarını belirtin.|- [.NET bellek ayırma ve yaşam boyu verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Nasıl kullanılır: Performans verisi dosya adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|**Başlat** sayfasında, kod çözümünüzde birden çok .exe projeniz varsa başlayacak uygulamayı seçin.|- [Katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)|
|Katman **Etkileşimi** sayfasında, profil oluşturma çalışmasına arama verileri ADO.NET ekleyin.|- [Katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)|
|Windows **Etkinlikleri** sayfasında, örnekleme verileriyle toplamak üzere windows (ETW) olayları için bir veya daha fazla Olay İzleme belirtin.|- [Nasıl yapılır: Windows (ETW) verileri için Olay İzlemesini Toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Windows **Sayaçları** sayfasında, profil oluşturma verilerine işaret olarak eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|- [Nasıl kullanılır: Windows karşı veri toplama](../profiling/how-to-collect-windows-counter-data.md)|
|**Gelişmiş** sayfada, uygulama modülleriniz birden çok sürüm kullanıyorsa,.NET Framework çalışma zamanının sürümünü profiliçin belirtin. Varsayılan olarak, yüklenen ilk sürüm profillenir.|- [Nasıl yapılsın: .NET Framework çalışma süresini belirtin](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|

## <a name="instrumentation-tasks"></a>Enstrümantasyon görevleri

Aşağıdaki tablodaki görevler, Özellik **Sayfaları** iletişim kutusunda, enstrümantasyon yöntemiyle profil oluşturmaya özgü seçeneklerdir.

|Görev|İlgili İçerik|
|----------|---------------------|
|**İkili** sayfada, modüllerin enstrümante kopyaları için bir konum belirtin. Varsayılan olarak, özgün ikililer bir yedekleme klasörüne taşınır.|- [Nasıl Yapılır: Enstrümanlı İkilileri Başkabir](../profiling/how-to-relocate-instrumented-binaries.md)|
|**Instrumentation** sayfasında, profil oluşturma ek yükü azaltmak için küçük işlevleri profil oluşturmayı hariç tinleyin, ASP.NET Web sayfalarında JavaScript kodunu profilleyin ve enstrümantasyon işleminden önce ve sonra komut isteminde çalışacak komutları belirtin.|- [Nasıl yapılır: Enstrümantasyondan kısa işlevleri hariç tutma veya ekleme](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />- [Nasıl kullanılır: Web Sayfalarında Profil JavaScript Kodu](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />- [Nasıl Yapılır: Ön ve Post-Enstrüman Komutlarını Belirt](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|CPU **Sayaçları** sayfasında, profil oluşturma verilerine eklemek için bir veya daha fazla işlemci performans sayacı belirtin.|- [Nasıl Kullanılır: CPU Karşı Veri toplama](../profiling/how-to-collect-cpu-counter-data.md)|
|**Gelişmiş** sayfada, belirli işlevleri ekleme veya hariç tutma seçenekleri gibi istediğiniz ek VSInstr.exe seçeneklerini belirtin. VSInstr seçenekleri hakkında daha fazla bilgi için [VSInstr'a](../profiling/vsinstr.md) bakın|- [Nasıl yapılır: Ek enstrümantasyon seçeneklerini belirtin](../profiling/how-to-specify-additional-instrumentation-options.md)<br />- [Nasıl yapılır: Enstrümantasyonu belirli işlevler ile sınırlandırın](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını](../profiling/configuring-performance-sessions.md)
[yapılandırma: Toplama yöntemlerini](../profiling/how-to-choose-collection-methods.md)
seçin[Performans oturumu özellikleri](../profiling/performance-session-properties.md)
