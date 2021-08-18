---
title: .NET zaman uyumsuz kodunun performansını çözümleme | Microsoft Docs
description: zaman uyumsuz kodun performansını analiz etmek için .NET Async aracını kullanın. Listelenen her görev için zamanlama vardır. Kodu görmek için kaynak dosyasına git ' i kullanın.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: f6d688706fbc26013badea2beb06a534bbf5932245879dfbaede609a325434d8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427319"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>.NET zaman uyumsuz kodunun performansını çözümleme

uygulamanızdaki zaman uyumsuz kodun performansını çözümlemek için .NET Async aracını kullanın.

> [!NOTE]
> .NET Async aracı, Visual Studio 2019 sürüm 16,7 veya üzeri ve **zaman uyumsuz** ve **await** kullanan bir .net projesi gerektirir.

## <a name="setup"></a>Kurulum

1. Visual Studio ' de performans profil oluşturucuyu açmak için **alt + f2** ' yi seçin.

1. **.NET Async** onay kutusunu seçin.

   ![.NET Async araç seçildi](../profiling/media/async-tool-selected.png ".NET Async araç seçildi")

1. Aracı çalıştırmak için **Başlat** düğmesine tıklayın.

1. Araç çalışmaya başladıktan sonra, uygulamanızda profili eklemek istediğiniz senaryoya gidin. Ardından, **toplamayı durdur** ' u seçin veya verilerinizi görmek için uygulamanızı kapatın.

1. Koleksiyon durdurulduktan sonra, profil oluşturma oturumunuz sırasında gerçekleşen etkinliklerin tablosunu görürsünüz.

   ![.NET Async araç durdu](../profiling/media/async-tool-opened.png ".NET Async araç durdu")

Zaman uyumsuz olaylar kronolojik olarak Etkinlikler halinde düzenlenir. Her biri başlangıç saatini, bitiş saatini ve süresini görüntüler.

Bir [göreve](/dotnet/api/system.threading.tasks) karşılık gelen her satır **ad** sütununda etiketlidir. Çözümlenemeyen herhangi bir görev adı için, etiketteki bir **görev** görüntülenir. Bunun ardından görevin gerçekleştiği yöntemin adı gelir. Bir zaman uyumsuz etkinlik koleksiyon oturumunda tamamlanmazsa, **bitiş zamanı** sütununda **tamamlanmamış** bir etiket görüntülenir.

Belirli bir görevi veya etkinliği daha fazla araştırmak için, satıra sağ tıklayın. Ardından, kodunuzun etkinlik meydana geldiğini görmek için **kaynak dosyasına git** ' i seçin.

![kaynak dosyasına git seçiliyken .NET Async araç](../profiling/media/async-tool-gotosource.png "kaynak dosyasına git seçiliyken .NET Async araç")

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturucu ayarlarını iyileştirme](../profiling/optimize-profiler-settings.md)