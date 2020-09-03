---
title: Katman etkileşim verileri toplanıyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4f7b2a2bb5efd86d052247825a29a06c7f5ad109
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331599"
---
# <a name="collect-tier-interaction-data"></a>Katman etkileşim verileri toplama

Katman etkileşimi profili oluşturma, ADO.NET Hizmetleri aracılığıyla veritabanlarıyla iletişim kuran çok katmanlı uygulamalar işlevlerinin yürütme zamanları hakkında ek bilgiler sağlar. Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır.

**Visual Studio sürümleri**

Katman etkileşimi profil oluşturma verileri, herhangi bir Visual Studio sürümü kullanılarak toplanabilir. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise görüntülenebilir.

**Windows 8 ve Windows Server 2012**

Windows 8 masaüstü uygulamaları ve Windows Server 2012 uygulamalarında katman etkileşim verilerini toplamak için, izleme yöntemini kullanmanız gerekir. UWP uygulamaları için katman etkileşimi verilerini toplayamazsınız. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Katman etkileşim verilerini, desteklenen diğer Windows sürümündeki tüm profil oluşturma yöntemlerine dahil edebilirsiniz.

**Performans Sihirbazı**

Performans Sihirbazı 'ndaki bir hata nedeniyle, katman etkileşim verileri toplama seçeneğini Performans Gezgini bir profil oluşturma çalıştırmasına eklemeniz gerekir. Ayrıca, Performans Gezgini hedef düğümüne proje, çalıştırılabilir veya Web sitesini de eklemeniz gerekir.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Performans oturumu özellik sayfalarını kullanarak bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek için

1. Performans Gezgini, bağlam menüsünden **Özellikler** ' i seçin.

2. **Katman etkileşimleri** sayfası ' nı seçin ve ardından **katman etkileşim profilini etkinleştir** onay kutusunu işaretleyin.

3. Performans Gezgini ' de, **hedefler** düğümünü seçin ve ardından profil eklemek istediğiniz projeyi, yürütülebilir dosyayı veya Web sitesini belirtin.

## <a name="see-also"></a>Ayrıca bkz.

[Katman etkileşimleri görünümü](../profiling/tier-interactions-view.md)
