---
title: Izleme kullanarak ayrıntılı zamanlama verileri toplama | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779629"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>İzleme kullanarak ayrıntılı zamanlama verileri toplama
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları izleme yöntemi, profil oluşturma kodunu bir modülün kopyasına çıkarır. Kod, bir profil oluşturma çalışması sırasında modüldeki işlevlerin her bir girdisini, çıkış ve işlev çağrısını kaydeder. İzleme yöntemi, kodunuzun bir bölümü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemlerinin uygulama performansı üzerinde etkisini anlamak için yararlıdır.

 Aşağıdaki yordamlardan birini kullanarak izleme yöntemini belirtebilirsiniz:

- Profil oluşturma sihirbazının ilk sayfasında, **izleme**' yi seçin.

- **Performans Gezgini** araç çubuğunda, **Yöntem** listesinde, **izleme**' yi tıklatın.

- Performans oturumunun Özellikler iletişim kutusunun **genel** sayfasında, **izleme**' yi seçin.

## <a name="common-tasks"></a>Ortak görevler
 Performans oturumunun _performans oturumu_**Özellik sayfaları** iletişim kutusunda ek seçenekleri belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- **Performans Gezgini**, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

  Aşağıdaki tabloda yer alan görevler, izleme yöntemini kullanarak profil oluştururken _performans oturumu_**Özellik sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri anlatmaktadır.

|Görev|İlgili Içerik|
|----------|---------------------|
|**Genel** sayfasında, .net bellek ayırma ve ömür verileri ekleyin ve oluşturulan profil oluşturma verileri (. vsp) dosyası için adlandırma ayrıntılarını belirtin.|[.net bellek ayırma ve ömür verileri toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) -   <br />-   [nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|**Başlatma** sayfasında, çözümünüzde birden çok. exe projeniz varsa, başlatılacak uygulamayı ve başlangıç sıralarını belirtin.|-   [nasıl yapılır: başlatılacak Ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md)|
|**Ikili dosyalar** sayfasında, modüllerin belgelenmiş kopyaları için bir konum belirtin. Varsayılan olarak, özgün ikililer bir yedekleme klasörüne taşınır.|-   [nasıl yapılır: işaretlenmiş Ikililerin konumunu](../profiling/how-to-relocate-instrumented-binaries.md) değiştirme|
|**Katman etkileşimi** sayfasında, profil oluşturma çalıştırmasına ADO.NET çağrı verileri ekleyin.|[katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md) -   |
|**İzleme** sayfasında, profil oluşturma ek yükünü azaltmak, ASP.NET Web sayfalarındaki JavaScript kodu profilini oluşturmak ve izleme işleminden önce ve sonra bir komut isteminde çalışacak komutları belirtmek için, yönetim sayfası ' ndan küçük işlevleri hariç tutun.|-   [nasıl yapılır: izleme 'den kısa Işlevler hariç tutma veya dahil](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md) etme<br />-   [nasıl yapılır: Web sayfalarında JavaScript kodunun profilini](../profiling/how-to-profile-javascript-code-in-web-pages.md) oluşturma<br />-   [nasıl yapılır: ön ve son izleme komutları belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|**CPU sayaçları** sayfasında, profil oluşturma verilerine eklemek için bir veya daha fazla işlemci performans sayacı belirtin.|-   [nasıl yapılır: CPU sayacı verilerini toplama](../profiling/how-to-collect-cpu-counter-data.md)|
|**Windows olayları** sayfasında, örnekleme verileriyle toplanacak bir veya daha fazla Windows Için olay Izleme (ETW) olayları seçin.|-   [nasıl yapılır: Windows için olay izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|**Windows sayaçları** sayfasında, profil oluşturma verilerine işaret eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|-   [nasıl yapılır: Windows sayaç verilerini toplama](../profiling/how-to-collect-windows-counter-data.md)|
|**Gelişmiş** sayfasında, belirli işlevleri dahil etme veya hariç tutma seçenekleri gibi VSInstr araçları programına geçirmek istediğiniz ek seçenekleri belirtin.|-   [nasıl yapılır: ek izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [nasıl yapılır: belirli işlevlerle Izleme sınırlandırma](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [vsinstr](../profiling/vsinstr.md)|
