---
title: Veri Toplamayı Denetleme | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777809"
---
# <a name="control-data-collection"></a>Veri toplamayı denetleme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Profil Oluşturma Araçları, bir performans oturumu sırasında profil oluşturma verilerinin ne zaman toplandığını denetlemenize ve profilli işlevleri belirtmenize olanak tanır. Bu **bölümde, Performans Gezgini** ve **Veri Toplama Denetimi** pencerelerinden veri toplamanın nasıl başlatılabildiğini ve durdurulabildiğini ve profil oluşturma verilerinin toplandığı nesnelerin nasıl sınırlandırılabildiğini açıklar.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil oluşturmayı başlatın ve durdurun:** Uygulama başladığında bir uygulamanın profilini çıkarmaya başlayabilir veya profil oluşturucuyu zaten çalışmakta olan bir işleme ekleyebilirsiniz. Hedef uygulama çalışırken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Hedef uygulamayı kapatarak veya profil oluşturucuyu çalışan bir işlemden ayırarak bir profil oluşturma oturumunu sonlandırabilirsiniz. |-   [Nasıl kullanılır: Performans veri toplamayı başlatın ve sonla](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Nasıl yapilir: Performans araçlarını çalıştırma işlemlerine ekleme ve ayırma](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Nasıl kullanılır: Performans veri toplamayı duraklatma ve devam ettirme](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Toplanan verileri sınırlamak için enstrümantasyon profiloluşturmasını yapılandırın:** Enstrümantasyon yöntemini kullanan profil oluşturma çalıştırmalarında toplanan verileri sınırlamak için performans oturumu yapılandırma özelliklerini kullanabilirsiniz. Belirli .dll dosyalarını, ad alanlarını, sınıfları ve işlevleri dahil edebilir veya hariç tutabilirsiniz. Ayrıca, belirttiğiniz bir boyut eşiğini karşılamayan işlevleri çıkarabilirsiniz.|-   [Nasıl yapılır: Enstrümantasyonu belirli DL'lerle sınırlandırın](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Nasıl yapılır: Enstrümantasyonu belirli işlevler ile sınırlandırın](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Nasıl yapılır: Enstrümantasyondan kısa işlevleri hariç tutma veya ekleme](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|

## <a name="related-sections"></a>İlgili bölümler
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
