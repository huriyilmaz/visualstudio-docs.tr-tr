---
title: Iş parçacığı toplama ve eşzamanlılık verilerini Işleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e8fda0300aad4a331366fac0a9ebd1b559cecc9d
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779525"
---
# <a name="collect-thread-and-process-concurrency-data"></a>İş parçacığı ve işlem eşzamanlılık verileri toplama

Visual Studio Profil Oluşturma Araçları eşzamanlılık profili oluşturma yöntemi, profili oluşturulmuş uygulamadaki bir işlevin bir kaynağa erişim beklemesini sağlayan her eşitleme olayı hakkında bilgi içeren kaynak çekişmesini sağlar.

Eşzamanlılık profili oluşturma yöntemini aşağıdaki yordamlardan birini kullanarak belirtebilirsiniz:

- Profil oluşturma sihirbazının ilk sayfasında **eşzamanlılık** ' e tıklayın.
- Performans oturumunun Özellikler iletişim kutusunun **genel** sayfasında **eşzamanlılık**' e tıklayın.
- **Performans Gezgini** araç çubuğunda, **Yöntem** listesinden **eşzamanlılık**' e tıklayın.

## <a name="common-tasks"></a>Ortak görevler

Performans oturumunun _performans oturumu_**Özellik sayfaları** iletişim kutusunda ek seçenekleri belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- **Performans Gezgini**, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

Aşağıdaki tabloda yer alan görevler, eşzamanlılık yöntemini kullanarak profil oluştururken _performans oturumu_**Özellik sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri anlatmaktadır.

|Görev|İlgili Içerik|
|----------|---------------------|
|**Genel** sayfasında, oluşturulan profil oluşturma verileri (. vsp) dosyasının adlandırma ayrıntılarını belirtin.|- [nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|Kod çözümünüzde birden çok. exe projeniz varsa, **Başlat sayfasında başlatılacak** uygulamayı belirtin.|- [nasıl yapılır: başlatılacak Ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md)|
|**Katman etkileşimi** sayfasında, profil oluşturma çalıştırmasına ADO.NET çağrı verileri ekleyin.|[katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md) - |
|**Windows sayaçları** sayfasında, profil oluşturma verilerine işaret eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|- [nasıl yapılır: Windows sayaç verilerini toplama](../profiling/how-to-collect-windows-counter-data.md)|
|**Gelişmiş** sayfasında, uygulama modülleriniz birden çok sürüm kullanıyorsa, profil yapılacak .NET Framework çalışma zamanı sürümünü belirtin. Varsayılan olarak, yüklenen ilk sürüm profili oluşturulur.|- [nasıl yapılır: .NET Framework çalışma zamanını belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
