---
title: Veri toplamayı denetleme | Microsoft Docs
description: Profil Oluşturma Araçları veri toplamayı başlatma ve durdurma ve profil oluşturma verilerinin toplandığı nesneleri sınırlama hakkında bilgi edinin. Bu makale genel bakıştır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1ca23b5477cee37154f1334328745a5d2b066b39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910743"
---
# <a name="control-data-collection"></a>Veri toplamayı denetleme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları, bir performans oturumu sırasında profil oluşturma verilerinin ne zaman toplandığını denetlemenize ve profili oluşturulan işlevleri belirtmenize olanak tanır. Bu bölümde, veri toplamayı **Performans Gezgini** ve **veri toplama denetimi** pencerelerini başlatma ve durdurma ve profil oluşturma verilerinin toplandığı nesnelerinin nasıl sınırlandırılacağını açıklanmaktadır.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil oluşturmayı başlatma ve durdurma:** Uygulama başlatıldığında bir uygulama profili oluşturmayı başlatabilir ya da profil oluşturucuyu zaten çalışmakta olan bir işleme ekleyebilirsiniz. Hedef uygulama çalışırken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Hedef uygulamayı kapatarak veya profil oluşturucuyu çalışan bir işlemden ayırarak bir profil oluşturma oturumunu sonlandırabilirsiniz. |-   [Nasıl yapılır: performans veri toplamayı başlatma ve bitirme](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Nasıl yapılır: performans araçlarını çalıştırma işlemlerine bağlama ve ayırma](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Nasıl yapılır: performans veri toplamayı duraklatma ve devam etme](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Toplanan verileri sınırlandırmak için izleme profili oluşturmayı yapılandırın:** İzleme yöntemini kullanan profil oluşturma çalışmalarından toplanan verileri sınırlandırmak için performans oturumu yapılandırma özelliklerini kullanabilirsiniz. Belirli .dll dosyalarını, ad alanlarını, sınıfları ve işlevleri dahil edebilir veya hariç tutabilirsiniz. Ayrıca, belirttiğiniz bir boyut eşiğini karşılamayan işlevleri çıkarabilirsiniz.|-   [Nasıl yapılır: belirli dll 'Lerle izleme sınırlandırma](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Nasıl yapılır: belirli işlevlerle izleme sınırlandırma](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Nasıl yapılır: izleme 'den kısa işlevler hariç tutma veya dahil etme](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|

## <a name="related-sections"></a>İlgili bölümler
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
