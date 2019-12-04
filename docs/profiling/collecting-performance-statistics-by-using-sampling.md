---
title: Örnekleme kullanarak performans Istatistiklerini toplama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cbe03f52b31664c59cb7e59d448db7c6b96b6487
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772884"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>Örnekleme kullanarak performans istatistikleri toplama

Varsayılan olarak, Visual Studio Profil Oluşturma Araçları örnekleme yöntemi, profil oluşturma bilgilerini her 10.000.000 işlemci döngüsünde (yaklaşık 1 GHz bilgisayar üzerinde bir saniyenin her biri) toplar. Örnekleme yöntemi, işlemci kullanımı sorunlarını bulmak için yararlıdır ve performans araştırmaları 'nın en iyi şekilde başlatılması için önerilen yöntemdir.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

Aşağıdaki yordamlardan birini kullanarak örnekleme yöntemini belirtebilirsiniz:

- Profil oluşturma sihirbazının ilk sayfasında **CPU örnekleme (önerilen)** seçeneğine tıklayın.
- **Performans Gezgini** araç çubuğunda, **Yöntem** listesinde **örnekleme**' ye tıklayın.
- Performans oturumunun Özellikler iletişim kutusunun **genel** sayfasında **örnekleme**' ye tıklayın.

## <a name="common-tasks"></a>Ortak görevler

Performans oturumunun _performans oturumu_**Özellik sayfaları** iletişim kutusunda ek seçenekleri belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- **Performans Gezgini**, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

  Aşağıdaki tabloda yer alan görevler, örnekleme yöntemini kullanarak profil oluştururken _performans oturumu_**Özellik sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri anlatmaktadır.

|Görev|İlgili Içerik|
|----------|---------------------|
|**Genel** sayfasında, .net bellek ayırma ve yaşam süresi veri toplamayı ekleyin ve oluşturulan profil oluşturma verileri (. vsp) dosyası için adlandırma ayrıntılarını belirtin.|[.net bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) - <br />- [nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|**Örnekleme** sayfasında, örnekleme oranını değiştirin, örnekleme olayını işlemci saati döngülerinden başka bir işlemci performans sayacından değiştirin veya her ikisini de değiştirin.|- [nasıl yapılır: örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md)|
|**Başlatma** sayfasında, kod çözümünüzde birden fazla. exe projeniz varsa, başlatılacak uygulamayı ve başlangıç sırasını belirtin.|[katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md) - |
|**Katman etkileşimi** sayfasında, profil oluşturma çalıştırmasında toplanan verilere ADO.NET çağrı bilgilerini ekleyin.|[katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md) - |
|**Windows olayları** sayfasında, örnekleme verileriyle toplanacak bir veya daha fazla Windows Için olay Izleme (ETW) olayları belirtin.|- [nasıl yapılır: Windows Için olay izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|**Windows sayaçları** sayfasında, profil oluşturma verilerine işaret eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|- [nasıl yapılır: Windows sayaç verilerini toplama](../profiling/how-to-collect-windows-counter-data.md)|
|**Gelişmiş** sayfasında, uygulama modülleriniz birden çok sürüm kullanıyorsa, profil için .NET Framework çalışma zamanının sürümünü belirtin. Varsayılan olarak, yüklenen ilk sürüm profili oluşturulur.|- [nasıl yapılır: .NET Framework çalışma zamanını belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
