---
title: İzleme kullanarak ayrıntılı zamanlama verileri toplama
description: Kodunuzun bir bölümüyle ilgili ayrıntılı zamanlama bilgileri için Profil Oluşturma Araçları izleme yöntemini kullanın ve g/ç işlemlerinin etkisini anlayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fc7f3596175c2259a3f1c8054f1bacd4e3be0513
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635817"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>İzleme kullanarak ayrıntılı zamanlama verileri toplama
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Profil oluşturma araçları izleme yöntemi, profil oluşturma kodunu bir modülün kopyasına çıkarır. Kod, bir profil oluşturma çalışması sırasında modüldeki işlevlerin her bir girdisini, çıkış ve işlev çağrısını kaydeder. İzleme yöntemi, kodunuzun bir bölümü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemlerinin uygulama performansı üzerinde etkisini anlamak için yararlıdır.

 Aşağıdaki yordamlardan birini kullanarak izleme yöntemini belirtebilirsiniz:

- Profil oluşturma sihirbazının ilk sayfasında, **izleme**' yi seçin.

- **Performans Gezgini** araç çubuğunda, **Yöntem** listesinde, **izleme**' yi tıklatın.

- Performans oturumunun Özellikler iletişim kutusunun **genel** sayfasında, **izleme**' yi seçin.

## <a name="common-tasks"></a>Genel görevler
 Performans oturumunun _performans oturumu_**Özellik sayfaları** iletişim kutusunda ek seçenekleri belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- **Performans Gezgini**, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

  Aşağıdaki tabloda yer alan görevler, izleme yöntemini kullanarak profil oluştururken _performans oturumu_**Özellik sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri anlatmaktadır.

|Görev|İlgili İçerik|
|----------|---------------------|
|**Genel** sayfasında, .net bellek ayırma ve ömür verileri ekleyin ve oluşturulan profil oluşturma verileri (. vsp) dosyası için adlandırma ayrıntılarını belirtin.|-   [.NET bellek ayırma ve yaşam süresi verilerini toplayın](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|**Başlatma** sayfasında, çözümünüzde birden çok .exe projeniz varsa, başlatılacak uygulamayı ve başlangıç sıralarını belirtin.|-   [Nasıl yapılır: başlatılacak ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md)|
|**Ikili dosyalar** sayfasında, modüllerin belgelenmiş kopyaları için bir konum belirtin. Varsayılan olarak, özgün ikililer bir yedekleme klasörüne taşınır.|-   [Nasıl yapılır: işaretlenmiş ikililerin konumunu değiştirme](../profiling/how-to-relocate-instrumented-binaries.md)|
|**katman etkileşimi** sayfasında, profil oluşturma çalıştırmasına ADO.NET çağrı verileri ekleyin.|-   [Katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md)|
|izleme sayfasında, profil oluşturma ek yükünü azaltmak, ASP.NET Web sayfalarında JavaScript kodu profilini oluşturmak ve izleme işleminden önce ve sonra komut isteminde çalışacak komutları belirtmek için, **izleme** sayfasından küçük işlevleri hariç tutun.|-   [Nasıl yapılır: izleme 'den kısa işlevler hariç tutma veya dahil etme](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Nasıl yapılır: Web sayfalarında JavaScript kodu profili oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Nasıl yapılır: ön ve araç sonrası komutları belirtme](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|
|**CPU sayaçları** sayfasında, profil oluşturma verilerine eklemek için bir veya daha fazla işlemci performans sayacı belirtin.|-   [Nasıl yapılır: CPU sayacı verilerini toplama](../profiling/how-to-collect-cpu-counter-data.md)|
|**Windows olayları** sayfasında, örnekleme verileriyle toplanacak bir veya daha fazla Windows (ETW) olay izleme olayı seçin.|-   [nasıl yapılır: Windows (ETW) verileri için olay izlemeyi toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|**Windows sayaçları** sayfasında, profil oluşturma verilerine işaret eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|-   [nasıl yapılır: Windows sayaç verileri toplama](../profiling/how-to-collect-windows-counter-data.md)|
|**Gelişmiş** sayfasında, belirli işlevleri dahil etme veya hariç tutma seçenekleri gibi VSInstr araçları programına geçirmek istediğiniz ek seçenekleri belirtin.|-   [Nasıl yapılır: ek izleme seçeneklerini belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Nasıl yapılır: belirli işlevlerle izleme sınırlandırma](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
