---
title: Örnekleme kullanarak perf istatistikleri toplama
description: İşlemci kullanım Profil Oluşturma Araçları bulmak için Profil Oluşturma Araçları örnekleme yöntemini kullanın. Bu, çoğu performans araştırmalarını başlatmaya ilişkin önerilen yöntemdir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f016fb7498ec30bab30e58af4d3023be3986ab4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076821"
---
# <a name="collect-performance-statistics-by-using-sampling"></a>Örnekleme kullanarak performans istatistikleri toplama

Visual Studio Profil Oluşturma Araçları örnekleme yöntemi varsayılan olarak 10.000.000 işlemci döngüsünde (1 GHz bilgisayarda saniyenin yaklaşık yüzde biri) profil oluşturma bilgilerini toplar. Örnekleme yöntemi, işlemci kullanım sorunlarını bulmak için yararlıdır ve performans araştırmalarını başlatmaya ilişkin önerilen yöntemdir.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

Örnekleme yöntemini aşağıdaki yordamlardan birini kullanarak belirtebilirsiniz:

- Profil Oluşturma Sihirbazı'nın ilk sayfasında CPU Örnekleme **(önerilen) öğesini tıklatın.**
- Performans Gezgini **araç** çubuğunda, Yöntem **listesinde Örnekleme'ye** **tıklayın.**
- Performans **oturumunun** özellikler iletişim kutusunun Genel sayfasında Örnekleme'ye **tıklayın.**

## <a name="common-tasks"></a>Genel görevler

Performans oturumunun Performans Oturumu _Özellik Sayfaları_**iletişim kutusunda** ek seçenekler belirtebilirsiniz. Bu iletişim kutusunu açmak için:

- Bu **Performans Gezgini,** performans oturumu adına sağ tıklayın ve ardından Özellikler'e **tıklayın.**

  Aşağıdaki tabloda yer alan görevler, örnekleme yöntemini kullanarak profil oluşturma sırasında Performans Oturumu **Özellik** Sayfaları iletişim kutusunda belirtebilirsiniz seçenekleri açıklar.

|Görev|İlgili İçerik|
|----------|---------------------|
|Genel sayfasında **.NET** bellek ayırma ve yaşam süresi veri toplama'ya ek olarak oluşturulan profil oluşturma verileri (.vsp) dosyası için adlandırma ayrıntılarını belirtin.|- [.NET Bellek Ayırma ve Yaşam Süresi Verilerini Toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />- [Nasıl yapabilirsiniz: Performans Veri Dosyası Adı Seçeneklerini Ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|
|Örnekleme sayfasında **örnekleme** oranını, örnekleme olaylarını işlemci saat döngülerinden başka bir işlemci performans sayacına veya her ikisini de değiştirebilirsiniz.|- [Nasıl: Örnekleme Olaylarını Seçme](../profiling/how-to-choose-sampling-events.md)|
|Başlat **sayfasında,** kod çözümde birden çok projeniz varsa başlatacak uygulamayı ve .exe sıralamayı belirtin.|- [Katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)|
|Katman **Etkileşimi sayfasında** profil oluşturma ADO.NET verilerine çağrı bilgileri ekleyin.|- [Katman etkileşim verilerini toplama](../profiling/collecting-tier-interaction-data.md)|
|Windows **Olayları sayfasında,** örnekleme verileriyle topilebilecek Windows (ETW) olayları için bir veya daha fazla Olay İzleme belirtin.|- [Nasıl kullanılır: Windows (ETW) Verileri için Olay İzleme Toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|
|Profil **Windows profil** oluşturma verilerine işaret olarak eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|- [Nasıl kullanılır: Windows Sayaç Verileri Toplama](../profiling/how-to-collect-windows-counter-data.md)|
|Gelişmiş **sayfasında,** uygulama modülleriniz birden çok sürüm kullanıyorsa .NET Framework çalışma zamanının sürümünü belirtin. Varsayılan olarak, yüklenen ilk sürümün profili kullanılır.|- [Nasıl kullanılır: .NET Framework Çalışma Zamanı Belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
