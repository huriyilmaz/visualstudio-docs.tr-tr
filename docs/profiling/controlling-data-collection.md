---
title: Veri toplamayı denetleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 48c7047bdd321943074221c9f09193970d42a247
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777809"
---
# <a name="control-data-collection"></a>Veri toplamayı denetleme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları, bir performans oturumu sırasında profil oluşturma verilerinin ne zaman toplandığını denetlemenizi ve profili oluşturulan işlevleri belirtmenize olanak tanır. Bu bölümde, veri toplamayı **Performans Gezgini** ve **veri toplama denetimi** pencerelerini başlatma ve durdurma ve profil oluşturma verilerinin toplandığı nesnelerinin nasıl sınırlandırılacağını açıklanmaktadır.

## <a name="common-tasks"></a>Ortak görevler

|Görev|İlgili Içerik|
|----------|---------------------|
|**Profil oluşturmayı başlatma ve durdurma:** Uygulama başlatıldığında bir uygulama profili oluşturmayı başlatabilir ya da profil oluşturucuyu zaten çalışmakta olan bir işleme ekleyebilirsiniz. Hedef uygulama çalışırken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Hedef uygulamayı kapatarak veya profil oluşturucuyu çalışan bir işlemden ayırarak bir profil oluşturma oturumunu sonlandırabilirsiniz.|-   [nasıl yapılır: performans veri toplamayı başlatma ve bitirme](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [nasıl yapılır: performans araçlarını çalıştırma Işlemlerine bağlama ve ayırma](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [nasıl yapılır: performans veri toplamayı duraklatma ve devam etme](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Toplanan verileri sınırlandırmak için izleme profili oluşturmayı yapılandırın:** İzleme yöntemini kullanan profil oluşturma çalışmalarından toplanan verileri sınırlandırmak için performans oturumu yapılandırma özelliklerini kullanabilirsiniz. Belirli .dll dosyalarını, ad alanlarını, sınıfları ve işlevleri dahil edebilir veya hariç tutabilirsiniz. Ayrıca, belirttiğiniz bir boyut eşiğini karşılamayan işlevleri çıkarabilirsiniz.|-   [nasıl yapılır: belirli dll 'lerle Izleme sınırlandırma](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [nasıl yapılır: belirli işlevlerle Izleme sınırlandırma](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [nasıl yapılır: izleme 'den kısa Işlevler hariç tutma veya dahil](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md) etme|

## <a name="related-sections"></a>İlgili bölümler
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
