---
title: Katman etkileşim verilerini toplama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: e01259fdd23e60a1408addc10a6af3a12479c9f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772824"
---
# <a name="collect-tier-interaction-data"></a>Katman etkileşim verileri toplama

Katman etkileşimi profil oluşturma, veritabanlarıyla ADO.NET hizmetler aracılığıyla iletişim sağlayan çok katmanlı uygulamaların işlevlerinin yürütme süreleri hakkında ek bilgiler sağlar. Veriler yalnızca eşzamanlı işlev çağrıları için toplanır.

**Visual Studio sürümleri**

Katman etkileşimprofilleme verileri Visual Studio'nun herhangi bir sürümü kullanılarak toplanabilir. Ancak, katman etkileşimprofilleme verileri yalnızca Visual Studio Enterprise'da görüntülenebilir.

**Windows 8 ve Windows Server 2012**

Windows 8 masaüstü uygulamalarında ve Windows Server 2012 uygulamalarında katman etkileşim verileri toplamak için enstrümantasyon yöntemini kullanmanız gerekir. UWP uygulamaları için katman etkileşim verileri toplayamazsınız. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın. Windows'un desteklenen diğer sürümündeki tüm profil oluşturma yöntemlerine katman etkileşim verilerini ekleyebilirsiniz.

**Performans Sihirbazı**

Performans Sihirbazı'ndaki bir hata nedeniyle, Performans Gezgini'nden gelen profil oluşturma çalışmasına katman etkileşim veri toplama seçeneğini eklemeniz gerekir. Ayrıca, projeyi, çalıştırılabilir veya web sitesini Performans Gezgini'nin Hedef düğümüne eklemeniz gerekir.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Performans oturumu özelliği sayfalarını kullanarak çalıştırılarak bir profil oluşturmaya katman etkileşim verileri eklemek için

1. Performans Gezgini'nde bağlam menüsünden **Özellikler'i** seçin.

2. **Katman Etkileşimleri** sayfasını seçin ve ardından **Katman etkileşimini etkinleştir onay** kutusunu işaretleyin.

3. Performans Gezgini'nde **Hedef** düğümünü seçin ve ardından profilini çıkarmak istediğiniz projeyi, çalıştırılabilir ivediliği veya web sitesini belirtin.

## <a name="see-also"></a>Ayrıca bkz.

[Katman etkileşimleri görünümü](../profiling/tier-interactions-view.md)
