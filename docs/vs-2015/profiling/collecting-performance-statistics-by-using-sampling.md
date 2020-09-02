---
title: Örnekleme kullanarak performans Istatistiklerini toplama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b84674eafde85528e04157ab213913e57d27e60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831116"
---
# <a name="collecting-performance-statistics-by-using-sampling"></a>Örnekleme Kullanarak Performans İstatistikleri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varsayılan olarak, [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] profil oluşturma araçları örnekleme yöntemi, profil oluşturma bilgilerini her 10.000.000 işlemci döngüsünde (yaklaşık olarak 1 GHz bilgisayar üzerinde her biri bir saniyede) toplar. Örnekleme yöntemi, işlemci kullanımı sorunlarını bulmak için yararlıdır ve performans araştırmaları 'nın en iyi şekilde başlatılması için önerilen yöntemdir.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Aşağıdaki yordamlardan birini kullanarak örnekleme yöntemini belirtebilirsiniz:  
  
- Profil oluşturma sihirbazının ilk sayfasında **CPU örnekleme (önerilen)** seçeneğine tıklayın.  
  
- **Performans Gezgini** araç çubuğunda, **Yöntem** listesinde **örnekleme**' ye tıklayın.  
  
- Performans oturumunun Özellikler iletişim kutusunun **genel** sayfasında **örnekleme**' ye tıklayın.  
  
## <a name="common-tasks"></a>Ortak Görevler  
 Performans oturumunun _performans oturumu_**Özellik sayfaları** iletişim kutusunda ek seçenekleri belirtebilirsiniz. Bu iletişim kutusunu açmak için:  
  
- **Performans Gezgini**, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
  Aşağıdaki tabloda yer alan görevler, örnekleme yöntemini kullanarak profil oluştururken _performans oturumu_**Özellik sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri anlatmaktadır.  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Genel** sayfasında, .net bellek ayırma ve yaşam süresi veri toplamayı ekleyin ve oluşturulan profil oluşturma verileri (. vsp) dosyası için adlandırma ayrıntılarını belirtin.|-   [.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Örnekleme** sayfasında, örnekleme oranını değiştirin, örnekleme olayını işlemci saati döngülerinden başka bir işlemci performans sayacından değiştirin veya her ikisini de değiştirin.|-   [Nasıl yapılır: örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md)|  
|**Başlatma** sayfasında, kod çözümünüzde birden fazla. exe projeniz varsa, başlatılacak uygulamayı ve başlangıç sırasını belirtin.|-   [Katman etkileşimi verilerini toplama](../profiling/collecting-tier-interaction-data.md)|  
|**Katman etkileşimi** sayfasında, profil oluşturma çalıştırmasında toplanan verilere ADO.NET çağrı bilgilerini ekleyin.|-   [Katman etkileşimi verilerini toplama](../profiling/collecting-tier-interaction-data.md)|  
|**Windows olayları** sayfasında, örnekleme verileriyle toplanacak bir veya daha fazla Windows Için olay Izleme (ETW) olayları belirtin.|-   [Nasıl yapılır: Windows için olay Izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|**Windows sayaçları** sayfasında, profil oluşturma verilerine işaret eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|-   [Nasıl yapılır: Windows sayaç verileri toplama](../profiling/how-to-collect-windows-counter-data.md)|  
|**Gelişmiş** sayfasında, uygulama modülleriniz birden çok sürüm kullanıyorsa, profil için .NET Framework çalışma zamanının sürümünü belirtin. Varsayılan olarak, yüklenen ilk sürüm profili oluşturulur.|-   [Nasıl yapılır: .NET Framework çalışma zamanını belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
