---
title: Katman etkileşim verileri | Microsoft Docs
description: Veritabanlarıyla iletişim kurarak hizmetlerden hizmet alan çok katmanlı uygulamalar için katman profili oluşturma ADO.NET öğrenin.
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
ms.openlocfilehash: 6729052dea38ee39213670d001d3c95de639f7f08cd744d874e502f434073146
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121302156"
---
# <a name="collect-tier-interaction-data"></a>Katman etkileşim verileri toplama

Katman etkileşimi profili oluşturma, veritabanlarıyla iletişim kuran çok katmanlı uygulamaların işlevlerinin yürütme süreleri hakkında ek bilgi sağlar ve ADO.NET sağlar. Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır.

**Visual Studio sürümleri**

Katman etkileşimi profil oluşturma verileri herhangi bir sürüm kullanılarak toplanabilir Visual Studio. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise.

**Windows 8 ve Windows Server 2012**

Masaüstü uygulamaları ve uygulama Windows 8 katman etkileşim Windows Server 2012 toplamak için ölçüm ölçüm yöntemini kullansanız gerekir. UWP uygulamaları için katman etkileşim verileri toplayabilirsiniz. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md) Katman etkileşim verilerini tüm profil oluşturma yöntemlerine diğer desteklenen sürümlerde dahil Windows.

**Performans Sihirbazı**

Performans Sihirbazı'nda bir hata nedeniyle, katman etkileşim veri toplama seçeneğini profil oluşturma çalıştırması için katmandan Performans Gezgini. Ayrıca projeyi, yürütülebilir dosyayı veya web sitesini de uygulamanın Hedef düğümüne Performans Gezgini.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Performans oturumu özellik sayfalarını kullanarak profil oluşturma çalıştırması için katman etkileşim verileri eklemek için

1. Bu Performans Gezgini bağlam **menüsünden** Özellikler'i seçin.

2. Katman **Etkileşimleri sayfasını** seçin ve ardından Katman etkileşimi **profili oluşturmayı etkinleştir onay** kutusunu işaretleyin.

3. Bu Performans Gezgini Hedefler **düğümünü** seçin ve ardından profili oluşturmak istediğiniz projeyi, yürütülebilir dosyayı veya web sitesini belirtin.

## <a name="see-also"></a>Ayrıca bkz.

[Katman etkileşimleri görünümü](../profiling/tier-interactions-view.md)
