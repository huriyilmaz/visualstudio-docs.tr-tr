---
title: Katman etkileşim verileri toplanıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a20266c870316be9b6be67e661d13eb4e6fdbaee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568053"
---
# <a name="collecting-tier-interaction-data"></a>Katman etkileşim verileri toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Katman etkileşimi profili oluşturma, ADO.NET Hizmetleri aracılığıyla veritabanlarıyla iletişim kuran çok katmanlı uygulamalar işlevlerinin yürütme zamanları hakkında ek bilgiler sağlar. Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır.  
  
 **Visual Studio sürümleri**  
  
 Katman etkileşimi profil oluşturma verileri Visual Studio Ultimate, Visual Studio Premium veya Visual Studio Professional kullanılarak toplanabilir. Ancak, katman etkileşimi profil oluşturma verileri yalnızca VS Ultimate ve VS Premium 'da görüntülenebilir.  
  
 **Windows 8 ve Windows Server 2012**  
  
 Windows 8 masaüstü uygulamaları ve Windows Server 2012 uygulamalarında katman etkileşim verilerini toplamak için, izleme yöntemini kullanmanız gerekir. Windows Mağazası uygulamaları için katman etkileşimi verilerini toplayamazsınız. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Katman etkileşim verilerini, desteklenen diğer Windows sürümündeki tüm profil oluşturma yöntemlerine dahil edebilirsiniz.  
  
 **Performans Sihirbazı**  
  
 Performans Sihirbazı 'ndaki bir hata nedeniyle, katman etkileşim verileri toplama seçeneğini Performans Gezgini bir profil oluşturma çalıştırmasına eklemeniz gerekir. Ayrıca, Performans Gezgini hedef düğümüne proje, çalıştırılabilir veya Web sitesini de eklemeniz gerekir.  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Performans oturumu özellik sayfalarını kullanarak bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek için  
  
1. Performans Gezgini, bağlam menüsünden **Özellikler** ' i seçin.  
  
2. **Katman etkileşimleri** sayfası ' nı seçin ve ardından **katman etkileşim profilini etkinleştir** onay kutusunu işaretleyin.  
  
3. Performans Gezgini ' de, **hedefler** düğümünü seçin ve ardından profil eklemek istediğiniz projeyi, yürütülebilir dosyayı veya Web sitesini belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Katman Etkileşimleri Görünümü](../profiling/tier-interactions-view.md)
