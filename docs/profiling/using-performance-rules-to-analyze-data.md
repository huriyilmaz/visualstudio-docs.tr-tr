---
title: Performans Kurallarını Kullanarak Veri Analizi | Microsoft Docs
description: Uygulamanın performans uyarılarının, Visual Studio Profil Oluşturma Araçları program yürütmeyi yavaşlatan, profili belirtilmiş bir uygulamada sorunları nasıl göster olduğunu öğrenin.
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
ms.openlocfilehash: 1366d4e73499c1ff3cd7e6424197b5ebb7005b99
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725669"
---
# <a name="use-performance-rules-to-analyze-data"></a>Performans kurallarını kullanarak verileri analiz etme
Uygulamanın performans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları, program yürütmeyi yavaşlatan profili belirtilmiş bir uygulamada sorunları gösteriyor. Uyarılar, daha kullanışlı veriler toplamak için toplama yöntemlerini değiştirmenin gerekyebilirsiniz olduğunu da gösteriyor olabilir. Profil oluşturma oturumunda performans uyarıları otomatik olarak oluşturulur. Profil oluşturma veri **dosyası bir** profil oluşturma dosyası açılırken Hata Listesi penceresinde uyarılar Visual Studio. Hata **Listesi penceresinde** sorunun kaynak kodunu bulup hatayla ilgili ayrıntılı bilgileri (örneğin, sorunun nasıl çözüleceklerini) görüntüebilirsiniz. İlgilenmiyorsanız uyarıları da devre dışı olduğu gibi devre dışı dır.

> [!NOTE]
> Profil oluşturma performansı uyarıları, program yürütmenin dinamik analizi tarafından oluşturulur ve bu uyarılardan Code Analysis bağımsızdır. Code Analysis, kaynak kodun statik analizine bağlı olarak yönetilen kod için performans uyarıları da üretebilir. Daha fazla bilgi için [bkz. Yönetilen kod kalitesini ve Performans](../code-quality/code-analysis-for-managed-code-overview.md) [uyarılarını analiz etme.](/dotnet/fundamentals/code-analysis/quality-rules/performance-warnings)

## <a name="in-this-section"></a>Bu bölümde
- [Nasıl yapılır: Performans uyarılarını görüntüleme](../profiling/how-to-view-performance-warnings.md)

 Profil oluşturma performansı uyarılarını görüntülemek **için Hata Listesi** penceresinin açılması hakkında bilgi sağlar.

- [Nasıl yapılır: Performans kurallarını yapılandırma](../profiling/how-to-configure-performance-rules.md)

 Tek tek performans uyarılarını açma veya kapatma hakkında bilgi sağlar.

- [Performans kuralları başvurusu](../profiling/performance-rules-reference.md)

 Profil oluşturma performansı uyarıları hakkında ayrıntılı bilgi sağlar
