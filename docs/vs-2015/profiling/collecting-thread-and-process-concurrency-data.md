---
title: Iş parçacığı toplama ve eşzamanlılık verilerini Işleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf8a9de5f2a7e520a745fab81197016d6e1bd15d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568198"
---
# <a name="collecting-thread-and-process-concurrency-data"></a>İş Parçacığı ve İşlem Eşzamanlılık Verileri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Profil oluşturma araçları eşzamanlılık profili oluşturma yöntemi, profili oluşturulmuş uygulamadaki bir işlevin bir kaynağa erişim beklemesini sağlayan her eşitleme olayı hakkında bilgi içeren kaynak çekişmesini sağlar.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Eşzamanlılık profili oluşturma yöntemini aşağıdaki yordamlardan birini kullanarak belirtebilirsiniz:  
  
- Profil oluşturma sihirbazının ilk sayfasında **eşzamanlılık** ' e tıklayın.  
  
- Performans oturumunun Özellikler iletişim kutusunun **genel** sayfasında **eşzamanlılık**' e tıklayın.  
  
- **Performans Gezgini** araç çubuğunda, **Yöntem** listesinden **eşzamanlılık**' e tıklayın.  
  
## <a name="common-tasks"></a>Ortak Görevler  
 Performans oturumunun _performans oturumu_**Özellik sayfaları** iletişim kutusunda ek seçenekleri belirtebilirsiniz. Bu iletişim kutusunu açmak için:  
  
- **Performans Gezgini**, performans oturumu adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
  Aşağıdaki tabloda yer alan görevler, eşzamanlılık yöntemini kullanarak profil oluştururken _performans oturumu_**Özellik sayfaları** iletişim kutusunda belirtebileceğiniz seçenekleri anlatmaktadır.  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Genel** sayfasında, oluşturulan profil oluşturma verileri (. vsp) dosyasının adlandırma ayrıntılarını belirtin.|-   [Nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Kod çözümünüzde birden çok. exe projeniz varsa, **Başlat sayfasında başlatılacak** uygulamayı belirtin.|-   [Nasıl yapılır: başlatılacak Ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md)|  
|**Katman etkileşimi** sayfasında, profil oluşturma çalıştırmasına ADO.NET çağrı verileri ekleyin.|-   [Katman etkileşimi verilerini toplama](../profiling/collecting-tier-interaction-data.md)|  
|**Windows sayaçları** sayfasında, profil oluşturma verilerine işaret eklemek için bir veya daha fazla işletim sistemi performans sayacı belirtin.|-   [Nasıl yapılır: Windows sayaç verileri toplama](../profiling/how-to-collect-windows-counter-data.md)|  
|**Gelişmiş** sayfasında, uygulama modülleriniz birden çok sürüm kullanıyorsa, profil yapılacak .NET Framework çalışma zamanı sürümünü belirtin. Varsayılan olarak, yüklenen ilk sürüm profili oluşturulur.|-   [Nasıl yapılır: .NET Framework çalışma zamanını belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
