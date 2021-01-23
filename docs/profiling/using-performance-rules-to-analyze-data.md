---
title: Verileri çözümlemek için performans kurallarını kullanma | Microsoft Docs
description: Visual Studio 'nun performans uyarılarının, program yürütmeyi yavaşlatabilecek profili oluşturulmuş bir uygulamada sorunları nasıl belirteceğinizi öğrenin Profil Oluşturma Araçları.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9a896e128f949897b64fd6a273784f39543a9663
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721144"
---
# <a name="use-performance-rules-to-analyze-data"></a>Performans kurallarını kullanarak verileri analiz etme
Profil Oluşturma Araçları performans uyarıları, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] programın yürütülmesini yavaşlatabilecek, profili oluşturulmuş bir uygulamadaki sorunları gösterir. Uyarılar Ayrıca, daha yararlı veriler toplamak için koleksiyon yöntemlerini değiştirmeniz gerekebilecek anlamına da gelebilir. Performans uyarıları, profil oluşturma oturumunda otomatik olarak oluşturulur. Visual Studio 'da bir profil oluşturma veri dosyası açıldığında uyarılar **hata listesi** penceresinde görüntülenir. **Hata listesi** penceresinden, sorunun kaynak kodunu bulabilir ve hata hakkında ayrıntılı bilgileri (örneğin, sorunun nasıl çözüleceği hakkında bilgi) görüntüleyebilirsiniz. İlgilendiğiniz uyarıları da devre dışı bırakabilirsiniz.

> [!NOTE]
> Profil Oluşturucu performans uyarıları, program yürütmenin dinamik analizi tarafından oluşturulur ve kod analizi uyarılarından bağımsızdır. Kod Analizi, kaynak kodun statik analizine dayalı olarak yönetilen kod için de performans uyarıları oluşturabilir. Daha fazla bilgi için bkz. [yönetilen kod kalitesini](../code-quality/code-analysis-for-managed-code-overview.md) ve [performans uyarılarını](/dotnet/fundamentals/code-analysis/quality-rules/performance-warnings)çözümleme.

## <a name="in-this-section"></a>Bu bölümde
- [Nasıl yapılır: Performans uyarılarını görüntüleme](../profiling/how-to-view-performance-warnings.md)

 Profil Oluşturucu performans uyarılarını görüntülemek için **hata listesi** penceresinin nasıl açılacağı hakkında bilgi sağlar.

- [Nasıl yapılır: Performans kurallarını yapılandırma](../profiling/how-to-configure-performance-rules.md)

 Ayrı performans uyarılarını açma veya kapatma hakkında bilgi sağlar.

- [Performans kuralları başvurusu](../profiling/performance-rules-reference.md)

 Profil Oluşturucu performans uyarıları hakkında ayrıntılı bilgi sağlar
