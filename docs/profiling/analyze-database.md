---
title: .NET Core projeleri için veritabanı kullanımını analiz etme | Microsoft Docs
description: Uygulamanızın veritabanı sorgularını kaydetmek için veritabanı aracını kullanın, ardından performansı artırmanın yollarını bulmak için bunları çözümleyin.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- database, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 758fad160bad89b5e8a4305bf4757302b05732e1
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122981092"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>Veritabanı aracını kullanarak veritabanı performansını çözümleme

Tanılama oturumu sırasında uygulamanızın yaptığı veritabanı sorgularını kaydetmek için veritabanı aracını kullanın. Daha sonra, uygulamanızın performansını iyileştirecek yerleri bulmak üzere ayrı sorgular hakkındaki bilgileri çözümleyebilirsiniz.

> [!NOTE]
> veritabanı aracı, [ADO.NET](/dotnet/framework/data/adonet/ado-net-overview) veya [Entity Framework Core](/ef/core/)kullanarak Windows Visual Studio 2019 sürüm 16,3 veya üzeri ve bir .net Core projesi gerektirir.

## <a name="setup"></a>Kurulum

1. Visual Studio ' de performans profil oluşturucuyu açmak için **alt + f2** ' yi seçin.

1. **Veritabanı** onay kutusunu seçin.

   ![Veritabanı aracı seçildi](./media/db-launch.png "Veritabanı aracı seçildi")

   > [!NOTE]
   > Araç seçilebilir olarak yoksa, bazı araçların tek başına çalıştırılması gerektiğinden, diğer her aracın onay kutusunu temizleyin. Araçları birlikte çalıştırma hakkında daha fazla bilgi için bkz. [komut satırından profil oluşturma araçlarını kullanma](../profiling/using-the-profiling-tools-from-the-command-line.md).
   >
   > Araç hala kullanılamıyorsa, projenizin önceki gereksinimleri karşıladığından emin olun. En doğru verileri yakalamak için projenizin yayın modunda olduğundan emin olun.

1. Aracı çalıştırmak için **Başlat** düğmesini seçin.

1. Araç çalışmaya başladıktan sonra, uygulamanızda profili eklemek istediğiniz senaryoya gidin. Ardından, **toplamayı durdur** ' u seçin veya verilerinizi görmek için uygulamanızı kapatın.

1. Koleksiyon durdurulduktan sonra, profil oluşturma oturumunuz sırasında çalıştırılan sorguların bir tablosunu görürsünüz.

   ![Veritabanı aracı durdu](./media/db-after.png "Veritabanı aracı durdu")

Sorgular kronolojik olarak düzenlenir, ancak bunları sütunlardan herhangi birine göre de sıralayabilirsiniz. Sütun başlıklarına sağ tıklayarak daha fazla sütun gösterebilirsiniz. **Süre** sütununun belirlenmesi en uzun olan sorguları en kısasına göre sıralar.

Araştırmak istediğiniz bir sorgu bulduktan sonra sorguya sağ tıklayın. Sonra bu sorgudan sorumlu kodu görmek için **kaynak dosyasına git** ' i seçin.

![Kaynak dosyasına git seçili](./media/db-gotosource.png "Kaynak dosyasına git seçili")

Grafik üzerinde bir zaman aralığı seçerseniz, sorgu tablosu yalnızca o zaman aralığında gerçekleşen sorguları gösterir. Bu davranış, özellikle de [CPU kullanımı aracını](./cpu-usage.md?view=vs-2019&preserve-view=true)çalıştırdığınızda yararlı olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturucu ayarlarını iyileştirme](../profiling/optimize-profiler-settings.md)