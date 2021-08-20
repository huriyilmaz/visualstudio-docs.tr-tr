---
title: İş parçacığı toplama & eşzamanlılık verilerini işleme
description: Bir işlevin kaynak erişimini beklemesine neden olan her eşitleme olayı hakkında veri toplamak için Profil Oluşturma Araçları eşzamanlılık profili oluşturma yöntemini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cdcefa6559aea6ed59bb2097e2a2285eabc4b07a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142331"
---
# <a name="collect-thread-and-process-concurrency-data"></a>İş parçacığı ve işlem eşzamanlılık verileri toplama

Visual Studio Profil Oluşturma Araçları eşzamanlılık profili oluşturma yöntemi, profili oluşturulmuş uygulamadaki bir işlevin bir kaynağa erişim beklemesini sağlayan her eşitleme olayı hakkında bilgi içeren kaynak çekişmesini sağlar.

Eşzamanlılık profili oluşturma yöntemini aşağıdaki yordamlardan birini kullanarak belirtebilirsiniz:

- Profil oluşturma sihirbazının ilk sayfasında **eşzamanlılık** ' e tıklayın.
- Performans oturumunun Özellikler iletişim kutusunun **genel** sayfasında **eşzamanlılık**' e tıklayın.
- **Performans Gezgini** araç çubuğunda, **Yöntem** listesinden **eşzamanlılık**' e tıklayın.

## <a name="common-tasks"></a>Genel görevler

Performans oturumunun _performans oturumu_**Özellik sayfaları** iletişim kutusunda ek seçenekleri belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- **Performans Gezgini**, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

Aşağıdaki tabloda yer alan görevler, eşzamanlılık yöntemini kullanarak profil oluştururken _performans oturumu_**Özellik sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri anlatmaktadır.

|Görev|İlgili İçerik|
|----------|---------------------|
|**Genel** sayfasında, oluşturulan profil oluşturma verileri (. vsp) dosyasının adlandırma ayrıntılarını belirtin.|- [Nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|Kod çözümünüzde birden çok .exe projeniz varsa, **Başlat sayfasında başlatılacak** uygulamayı belirtin.|- [Nasıl yapılır: başlatılacak ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md)|
|**katman etkileşimi** sayfasında, profil oluşturma çalıştırmasına ADO.NET çağrı verileri ekleyin.|- [Katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md)|
|**Windows sayaçları** sayfasında, profil oluşturma verilerine işaret eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|- [nasıl yapılır: Windows sayaç verileri toplama](../profiling/how-to-collect-windows-counter-data.md)|
|**gelişmiş** sayfasında, uygulama modülleriniz birden çok sürüm kullanıyorsa, profil yapılacak .NET Framework çalışma zamanı sürümünü belirtin. Varsayılan olarak, yüklenen ilk sürüm profili oluşturulur.|- [nasıl yapılır: .NET Framework çalışma zamanını belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
