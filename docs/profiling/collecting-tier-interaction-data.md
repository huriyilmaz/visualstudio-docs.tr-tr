---
title: Katman etkileşim verileri toplanıyor | Microsoft Docs
description: ADO.NET hizmetleri aracılığıyla veritabanlarıyla iletişim kuran çok katmanlı uygulamalar için katman profili oluşturma bilgilerini nasıl toplayacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 63729ef75c858d423ad48da73634ede544086b71
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136371"
---
# <a name="collect-tier-interaction-data"></a>Katman etkileşim verileri toplama

katman etkileşimi profili oluşturma, ADO.NET hizmetleri aracılığıyla veritabanlarıyla iletişim kuran çok katmanlı uygulamalar işlevlerinin yürütme zamanları hakkında ek bilgiler sağlar. Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır.

**Visual Studio sürümleri**

Katman etkileşimi profil oluşturma verileri, herhangi bir Visual Studio sürümü kullanılarak toplanabilir. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise görüntülenebilir.

**Windows 8 ve Windows Server 2012**

Windows 8 masaüstü uygulamaları ve Windows Server 2012 uygulamalar üzerinde katman etkileşim verileri toplamak için, izleme yöntemini kullanmanız gerekir. UWP uygulamaları için katman etkileşimi verilerini toplayamazsınız. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Katman etkileşim verilerini, desteklenen diğer Windows sürümüne tüm profil oluşturma yöntemlerine dahil edebilirsiniz.

**Performans Sihirbazı**

Performans Sihirbazı 'ndaki bir hata nedeniyle, katman etkileşim verileri toplama seçeneğini Performans Gezgini bir profil oluşturma çalıştırmasına eklemeniz gerekir. Ayrıca, Performans Gezgini hedef düğümüne proje, çalıştırılabilir veya Web sitesini de eklemeniz gerekir.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Performans oturumu özellik sayfalarını kullanarak bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek için

1. Performans Gezgini, bağlam menüsünden **Özellikler** ' i seçin.

2. **Katman etkileşimleri** sayfası ' nı seçin ve ardından **katman etkileşim profilini etkinleştir** onay kutusunu işaretleyin.

3. Performans Gezgini ' de, **hedefler** düğümünü seçin ve ardından profil eklemek istediğiniz projeyi, yürütülebilir dosyayı veya Web sitesini belirtin.

## <a name="see-also"></a>Ayrıca bkz.

[Katman etkileşimleri görünümü](../profiling/tier-interactions-view.md)
