---
title: Örnekleme Kullanarak Performans İstatistiklerini Toplama | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772884"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>Örnekleme kullanarak performans istatistikleri toplama

Varsayılan olarak, Visual Studio Profil Oluşturma Araçları örnekleme yöntemi her 10.000.000 işlemci döngüsünde profil oluşturma bilgileri toplar (1 GHz bilgisayarda saniyenin yaklaşık yüzde biri). Örnekleme yöntemi işlemci kullanım sorunlarını bulmak için yararlıdır ve çoğu performans araştırmasını başlatmak için önerilen yöntemdir.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

Örnekleme yöntemini aşağıdaki yordamlardan birini kullanarak belirtebilirsiniz:

- Profil Oluşturma Sihirbazı'nın ilk sayfasında **CPU Örneklemesi'ni (önerilir)** tıklatın.
- Performans **Gezgini** araç çubuğunda, **Yöntem** listesinde **Örnekleme'yi**tıklatın.
- Performans oturumu için özellikler iletişim kutusunun **Genel** sayfasında **Örnekleme'yi**tıklatın.

## <a name="common-tasks"></a>Genel görevler

_Performans Oturumu_**Özellik Sayfaları** iletişim kutusunda ek seçenekler belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- **Performans Gezgini'nde,** performans oturumu adını sağ tıklatın ve ardından **Özellikler'i**tıklatın.

  Aşağıdaki tablodaki görevler, örnekleme yöntemini kullanarak profil yaparken _Performans Oturumu_**Özellik Sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri açıklar.

|Görev|İlgili İçerik|
|----------|---------------------|
|**Genel** sayfada ,.NET bellek ayırma ve toplam veri toplama ekleyin ve oluşturulan profil oluşturma verileri (.vsp) dosyası için adlandırma ayrıntılarını belirtin.|- [.NET Bellek Tahsisi ve Yaşam Boyu Veri Toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Nasıl kullanılır: Performans Verisi Dosya Adı Seçeneklerini Ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|**Örnekleme** sayfasında, örnekleme hızını değiştirin, örnekleme olayını işlemci saat döngülerinden başka bir işlemci performans sayacına dönüştürün veya her ikisini de değiştirin...|- [Nasıl seçilir: Örnekleme Olayları seçin](../profiling/how-to-choose-sampling-events.md)|
|**Başlat** sayfasında, kod çözümünüzde birden çok .exe projeniz varsa, başlatılan uygulamayı ve başlangıç sırasını belirtin.|- [Katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)|
|Katman **Etkileşimi** sayfasında, profil oluşturma çalışmasında toplanan verilere ADO.NET çağrı bilgileri ekleyin.|- [Katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)|
|Windows **Etkinlikleri** sayfasında, örnekleme verileriyle toplamak üzere windows (ETW) olayları için bir veya daha fazla Olay İzleme belirtin.|- [Nasıl Yapılır: Windows (ETW) Verileri için Olay İzlemesini Toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Windows **Sayaçları** sayfasında, profil oluşturma verilerine işaret olarak eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|- [Nasıl Kullanılır: Windows Sayacı Verilerini Toplama](../profiling/how-to-collect-windows-counter-data.md)|
|**Gelişmiş** sayfada, uygulama modülleriniz birden çok sürüm kullanıyorsa,.NET Framework çalışma zamanının sürümünü profiliçin belirtin. Varsayılan olarak, yüklenen ilk sürüm profillenir.|- [Nasıl yapılsın: .NET Framework Runtime'ı belirtin](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
