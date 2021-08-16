---
title: Verileri çözümlemek için performans kurallarını kullanma | Microsoft Docs
description: Visual Studio Profil Oluşturma Araçları performans uyarılarının, programın yürütülmesini yavaşlatabilecek profili oluşturulmuş bir uygulamadaki sorunları nasıl belirteceğinizi öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2ad220b0e674510824c569523b437e2cf03cb716e6a3921e1f0ad41d6b6374ba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270152"
---
# <a name="use-performance-rules-to-analyze-data"></a>Performans kurallarını kullanarak verileri analiz etme
Profil Oluşturma Araçları performans uyarıları, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] programın yürütülmesini yavaşlatabilecek, profili oluşturulmuş bir uygulamadaki sorunları gösterir. Uyarılar Ayrıca, daha yararlı veriler toplamak için koleksiyon yöntemlerini değiştirmeniz gerekebilecek anlamına da gelebilir. Performans uyarıları, profil oluşturma oturumunda otomatik olarak oluşturulur. Visual Studio bir profil oluşturma veri dosyası açıldığında uyarılar **hata listesi** penceresinde görünür. **Hata listesi** penceresinden, sorunun kaynak kodunu bulabilir ve hata hakkında ayrıntılı bilgileri (örneğin, sorunun nasıl çözüleceği hakkında bilgi) görüntüleyebilirsiniz. İlgilendiğiniz uyarıları da devre dışı bırakabilirsiniz.

> [!NOTE]
> profil oluşturucu performans uyarıları, program yürütmenin dinamik analizi tarafından oluşturulur ve Code Analysis uyarılarından bağımsızdır. Code Analysis, kaynak kodun statik analizine dayalı olarak yönetilen kod için de performans uyarıları oluşturabilir. Daha fazla bilgi için bkz. [yönetilen kod kalitesini](../code-quality/code-analysis-for-managed-code-overview.md) ve [performans uyarılarını](/dotnet/fundamentals/code-analysis/quality-rules/performance-warnings)çözümleme.

## <a name="in-this-section"></a>Bu bölümde
- [Nasıl yapılır: Performans uyarılarını görüntüleme](../profiling/how-to-view-performance-warnings.md)

 Profil Oluşturucu performans uyarılarını görüntülemek için **hata listesi** penceresinin nasıl açılacağı hakkında bilgi sağlar.

- [Nasıl yapılır: Performans kurallarını yapılandırma](../profiling/how-to-configure-performance-rules.md)

 Ayrı performans uyarılarını açma veya kapatma hakkında bilgi sağlar.

- [Performans kuralları başvurusu](../profiling/performance-rules-reference.md)

 Profil Oluşturucu performans uyarıları hakkında ayrıntılı bilgi sağlar
