---
title: Verileri çözümlemek için performans kurallarını kullanma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc0c1b5245817a8946b1ccbd0fb244b3f0608c6e
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189321"
---
# <a name="use-performance-rules-to-analyze-data"></a>Performans kurallarını kullanarak verileri analiz etme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları performans uyarıları, programın yürütülmesini yavaşlatabilecek, profili oluşturulmuş bir uygulamadaki sorunları gösterir. Uyarılar Ayrıca, daha yararlı veriler toplamak için koleksiyon yöntemlerini değiştirmeniz gerekebilecek anlamına da gelebilir. Performans uyarıları, profil oluşturma oturumunda otomatik olarak oluşturulur. Visual Studio 'da bir profil oluşturma veri dosyası açıldığında uyarılar **hata listesi** penceresinde görüntülenir. **Hata listesi** penceresinden, sorunun kaynak kodunu bulabilir ve hata hakkında ayrıntılı bilgileri (örneğin, sorunun nasıl çözüleceği hakkında bilgi) görüntüleyebilirsiniz. İlgilendiğiniz uyarıları da devre dışı bırakabilirsiniz.

> [!NOTE]
> Profil Oluşturucu performans uyarıları, program yürütmenin dinamik analizi tarafından oluşturulur ve kod analizi uyarılarından bağımsızdır. Kod Analizi, kaynak kodun statik analizine dayalı olarak yönetilen kod için de performans uyarıları oluşturabilir. Daha fazla bilgi için bkz. [yönetilen kod kalitesini](../code-quality/code-analysis-for-managed-code-overview.md) ve [performans uyarılarını](../code-quality/performance-warnings.md)çözümleme.

## <a name="in-this-section"></a>Bu bölümde
- [Nasıl yapılır: Performans uyarılarını görüntüleme](../profiling/how-to-view-performance-warnings.md)

 Profil Oluşturucu performans uyarılarını görüntülemek için **hata listesi** penceresinin nasıl açılacağı hakkında bilgi sağlar.

- [Nasıl yapılır: Performans kurallarını yapılandırma](../profiling/how-to-configure-performance-rules.md)

 Ayrı performans uyarılarını açma veya kapatma hakkında bilgi sağlar.

- [Performans kuralları başvurusu](../profiling/performance-rules-reference.md)

 Profil Oluşturucu performans uyarıları hakkında ayrıntılı bilgi sağlar