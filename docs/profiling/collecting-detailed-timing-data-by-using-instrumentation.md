---
title: Enstrümantasyon Kullanarak Ayrıntılı Zamanlama Verilerini Toplama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bfd22edc9bd672a8d82c94a705b523ce7d836169
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779629"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>İzleme kullanarak ayrıntılı zamanlama verileri toplama
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları enstrümantasyon yöntemi, bir modülün kopyasına profil oluşturma kodu enjekte eder. Kod, profil oluşturma çalışması sırasında modüldeki işlevlerin her giriş, çıkış ve işlev çağrısını kaydeder. Enstrümantasyon yöntemi, kodunuzun bir bölümü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıktı işlemlerinin uygulama performansı üzerindeki etkisini anlamak için yararlıdır.

 Aşağıdaki yordamlardan birini kullanarak enstrümantasyon yöntemini belirtebilirsiniz:

- Profil Oluşturma Sihirbazı'nın ilk sayfasında **Enstrümantasyon'u**seçin.

- Performans **Gezgini** araç çubuğunda, **Yöntem** listesinde **Enstrümantasyon'u**tıklatın.

- Performans oturumu için özellikler iletişim kutusunun **Genel** sayfasında **Enstrümantasyon'u**seçin.

## <a name="common-tasks"></a>Genel görevler
 _Performans Oturumu_**Özellik Sayfaları** iletişim kutusunda ek seçenekler belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- **Performans Gezgini'nde,** performans oturumu adını sağ tıklatın ve ardından **Özellikler'i**tıklatın.

  Aşağıdaki tablodaki görevler, enstrümantasyon yöntemini kullanarak profil yaparken _Performans Oturumu_**Özellik Sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri açıklar.

|Görev|İlgili İçerik|
|----------|---------------------|
|**Genel** sayfada ,.NET bellek ayırma ve yaşam boyu verilerini ekleyin ve oluşturulan profil oluşturma verileri (.vsp) dosyasıiçin adlandırma ayrıntılarını belirtin.|-   [.NET bellek ayırma ve yaşam boyu verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Nasıl kullanılır: Performans verisi dosya adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|**Başlat** sayfasında, çözümünüzde birden fazla .exe projesi varsa.başlayacak uygulamayı ve başlangıç sırasını belirtin.|-   [Nasıl yapılır: Başlamak için ikiliyi belirtin](../profiling/how-to-specify-the-binary-to-start.md)|
|**İkili** sayfada, modüllerin enstrümante kopyaları için bir konum belirtin. Varsayılan olarak, özgün ikililer bir yedekleme klasörüne taşınır.|-   [Nasıl yapılır: Enstrümanlı ikilileri taşıma](../profiling/how-to-relocate-instrumented-binaries.md)|
|Katman **Etkileşimi** sayfasında, profil oluşturma çalışmasına arama verileri ADO.NET ekleyin.|-   [Katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)|
|**Instrumentation** sayfasında, profil oluşturma ek yükü azaltmak için küçük işlevleri profil oluşturmayı hariç tinleyin, ASP.NET Web sayfalarında JavaScript kodunu profilleyin ve enstrümantasyon işleminden önce ve sonra komut isteminde çalışacak komutları belirtin.|-   [Nasıl yapılır: Enstrümantasyondan kısa işlevleri hariç tutma veya ekleme](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Nasıl kullanılır: Web sayfalarında Profil JavaScript kodu](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Nasıl yapılır: Enstrüman öncesi ve sonrası komutları belirtin](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|CPU **Sayaçları** sayfasında, profil oluşturma verilerine eklemek için bir veya daha fazla işlemci performans sayacı belirtin.|-   [Nasıl kullanılır: CPU karşı veri toplamak](../profiling/how-to-collect-cpu-counter-data.md)|
|Windows **Etkinlikleri** sayfasında, örnekleme verileriyle toplamak üzere Windows (ETW) olayları için bir veya daha fazla Olay İzleme'yi seçin.|-   [Nasıl yapılır: Windows (ETW) verileri için olay izleme toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Windows **Sayaçları** sayfasında, profil oluşturma verilerine işaret olarak eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|-   [Nasıl kullanılır: Windows karşı veri toplama](../profiling/how-to-collect-windows-counter-data.md)|
|**Gelişmiş** sayfada, belirli işlevleri ekleme veya hariç tutma seçenekleri gibi VSInstr enstrümantasyon programına geçmek istediğiniz ek seçenekleri belirtin.|-   [Nasıl yapılır: Ek enstrümantasyon seçeneklerini belirtin](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Nasıl yapılır: Enstrümantasyonu belirli işlevler ile sınırlandırın](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Vsınstr](../profiling/vsinstr.md)|
