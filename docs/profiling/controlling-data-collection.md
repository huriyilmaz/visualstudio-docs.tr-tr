---
title: Veri Toplama verilerini | Microsoft Docs
description: Veri toplamayı başlatmayı Profil Oluşturma Araçları durdurmayı ve profil oluşturma verilerini topladığı nesneleri sınırlamayı öğrenin. Bu makale genel bir bakış sağlar.
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
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bb967ea2e8c3b22428217f05b49a9cb917d16abb80ea6d41cf3e8c0bea10cde3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333489"
---
# <a name="control-data-collection"></a>Veri toplamayı denetleme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları profil oluşturmanın bir performans oturumu sırasında ne zaman toplanacaklarını denetlemeyi ve profili yapılan işlevleri belirtmenizi sağlar. Bu bölümde veri toplamayı Performans Gezgini ve  Veri Toplama Denetimi  pencerelerinden başlatmayı ve durdurmayı ve profil oluşturma verilerini topladığı nesneleri sınırlamayı açıklar.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil oluşturmayı başlatma ve durdurma:** Uygulama başlatıldığında bir uygulamanın profilini oluşturmaya başlayabilir veya profil işleyiciyi zaten çalışan bir işleme iliştirebilirsiniz. Hedef uygulama çalışırken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Hedef uygulamayı kapatarak veya profil oluşturucuyu çalışan bir işlemden ayırarak bir profil oluşturma oturumunu sonlandırabilirsiniz. |-   [Nasıl kullanılır: Başlangıç ve bitiş performans verileri toplama](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Nasıl olur: Performans araçlarını çalışan işlemlere ekleme ve ayırma](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Nasıl kullanılır: Performans verileri toplamayı duraklatma ve sürdürme](../profiling/how-to-pause-and-resume-performance-data-collection.md)|
|**Toplanan verileri sınırlamak için ölçüm ölçümleme profili oluşturmayı yapılandırma:** Ölçümleme yöntemini kullanan profil oluşturma çalıştırmalarında toplanan verileri sınırlamak için performans oturumu yapılandırma özelliklerini kullanabilirsiniz. Belirli .dll dosyalarını, ad alanlarını, sınıfları ve işlevleri dahil edebilir veya hariç tutabilirsiniz. Ayrıca, belirttiğiniz bir boyut eşiğini karşılamayan işlevleri çıkarabilirsiniz.|-   [Nasıllı: Araçları belirli URL'ler ile sınırlama](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Nasıl kullanılır: Araçları belirli işlevlerle sınırlama](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Nasıl kullanılır: Kısa işlevleri ölçümden hariç tutmak veya dahil etmek](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|

## <a name="related-sections"></a>İlgili bölümler
- [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
