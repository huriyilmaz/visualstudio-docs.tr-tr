---
title: .NET zaman uyumsuz kodunun performansını çözümleme | Microsoft Docs
description: Zaman uyumsuz kodun performansını çözümlemek için .NET Async aracını kullanın. Listelenen her görev için zamanlama vardır. Kodu görmek için kaynak dosyasına git ' i kullanın.
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
ms.openlocfilehash: 86575cd71c41ac8ac874e9b62f8273ee46e02c57
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205495"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>.NET zaman uyumsuz kodunun performansını çözümleme

Uygulamanızda zaman uyumsuz kodun performansını çözümlemek için .NET Async aracını kullanın.

> [!NOTE]
> .NET Async Aracı, Visual Studio 2019 sürüm 16,7 veya üzeri ve **Async** ve **await** kullanan bir .NET projesi gerektirir.

## <a name="setup"></a>Kurulum

1. Visual Studio 'da performans profil oluşturucuyu açmak için **alt + f2** ' yi seçin.

1. **.Net Async** onay kutusunu seçin.

   ![.NET zaman uyumsuz aracı seçildi](../profiling/media/async-tool-selected.png ".NET zaman uyumsuz aracı seçildi")

1. Aracı çalıştırmak için **Başlat** düğmesine tıklayın.

1. Araç çalışmaya başladıktan sonra, uygulamanızda profili eklemek istediğiniz senaryoya gidin. Ardından, **toplamayı durdur** ' u seçin veya verilerinizi görmek için uygulamanızı kapatın.

1. Koleksiyon durdurulduktan sonra, profil oluşturma oturumunuz sırasında gerçekleşen etkinliklerin tablosunu görürsünüz.

   ![.NET Async aracı durdu](../profiling/media/async-tool-opened.png ".NET Async aracı durdu")

Zaman uyumsuz olaylar kronolojik olarak Etkinlikler halinde düzenlenir. Her biri başlangıç saatini, bitiş saatini ve süresini görüntüler.

Bir [göreve](/dotnet/api/system.threading.tasks) karşılık gelen her satır **ad** sütununda etiketlidir. Çözümlenemeyen herhangi bir görev adı için, etiketteki bir **görev** görüntülenir. Bunun ardından görevin gerçekleştiği yöntemin adı gelir. Bir zaman uyumsuz etkinlik koleksiyon oturumunda tamamlanmazsa, **bitiş zamanı** sütununda **tamamlanmamış** bir etiket görüntülenir.

Belirli bir görevi veya etkinliği daha fazla araştırmak için, satıra sağ tıklayın. Ardından, kodunuzun etkinlik meydana geldiğini görmek için **kaynak dosyasına git** ' i seçin.

![Kaynak dosyasına git seçiliyken .NET Async aracı seçildi](../profiling/media/async-tool-gotosource.png "Kaynak dosyasına git seçiliyken .NET Async aracı seçildi")

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturucu ayarlarını iyileştirme](../profiling/optimize-profiler-settings.md)