---
title: İş Parçacığı ve Süreç EşzamanlıLık Verilerini Toplama | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779525"
---
# <a name="collect-thread-and-process-concurrency-data"></a>İş parçacığı ve işlem eşzamanlılık verileri toplama

Visual Studio Profil Oluşturma Araçları eşzamanlılık oluşturma yöntemi, profilli uygulamada bir işlevin kaynağa erişimi beklemesine neden olan her eşitleme olayı hakkında bilgi içeren kaynak çekişme verileri toplamanızı sağlar.

Aşağıdaki yordamlardan birini kullanarak eşzamanlılık profil oluşturma yöntemini belirtebilirsiniz:

- Profil Oluşturma Sihirbazı'nın ilk sayfasında **Eşzamanlılık**
- Performans oturumu için özellikler iletişim kutusunun **Genel** sayfasında **Eşzamanlılık'ı**tıklatın.
- Performans **Gezgini** araç çubuğunda, **Yöntem** listesinde **Eşzamanlılık'ı**tıklatın.

## <a name="common-tasks"></a>Genel görevler

_Performans Oturumu_**Özellik Sayfaları** iletişim kutusunda ek seçenekler belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- **Performans Gezgini'nde,** performans oturumu adını sağ tıklatın ve ardından **Özellikler'i**tıklatın.

Aşağıdaki tablodaki görevler, eşzamanlılık yöntemini kullanarak profil yaparken _Performans Oturumu_**Özellik Sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri açıklar.

|Görev|İlgili İçerik|
|----------|---------------------|
|**Genel** sayfada, oluşturulan profil oluşturma verileri (.vsp) dosyasının adlandırma ayrıntılarını belirtin.|- [Nasıl kullanılır: Performans verisi dosya adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|**Başlat** sayfasında, kod çözümünüzde birden çok .exe projeniz varsa başlayacak uygulamayı belirtin.|- [Nasıl yapılır: Başlamak için ikiliyi belirtin](../profiling/how-to-specify-the-binary-to-start.md)|
|Katman **Etkileşimi** sayfasında, profil oluşturma çalışmasına arama verileri ADO.NET ekleyin.|- [Katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)|
|Windows **Sayaçları** sayfasında, profil oluşturma verilerine işaret olarak eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|- [Nasıl kullanılır: Windows karşı veri toplama](../profiling/how-to-collect-windows-counter-data.md)|
|**Gelişmiş** sayfada, uygulama modülleriniz birden çok sürüm kullanıyorsa ,.NET Framework çalışma zamanının profilini belirleyin. Varsayılan olarak, yüklenen ilk sürüm profillenir.|- [Nasıl yapılsın: .NET Framework çalışma süresini belirtin](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
