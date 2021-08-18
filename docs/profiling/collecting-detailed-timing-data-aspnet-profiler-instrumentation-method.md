---
title: Ölçüm ölçümlerini kullanarak ASP.NET verileri toplama
description: Web uygulamasına ilişkin ayrıntılı performans verilerini toplamak için VSPerfCmd'ASP.NET öğrenin. İşlevselliğe tam Profil Oluşturma Araçları sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 78bcf3fcb7ae2512a3ab92474f68cc80e238a765
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107933"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Komut satırdan profil oluşturma ASP.NET kullanarak bir web uygulaması için ayrıntılı zamanlama verileri toplama
Bu bölümde, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] **VSPerfCmd** komut satırı aracını ve ölçüm aracını kullanarak bir Web uygulaması için ayrıntılı performans verileri toplamaya ilişkin yordamlar ve seçenekler açıklanır.

> [!NOTE]
> **VSPerfCmd** aracı, profil oluşturmayı duraklatma ve devam Profil Oluşturma Araçları, işlemci ve performans sayaçlarından ek veri toplama da dahil olmak üzere Windows tam erişim sağlar. Bu işleve ihtiyacınız yoksa  **VSPerfASPNETCmd** komut satırı aracını da kullanabilirsiniz. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracına kıyasla hiçbir ortam değişkeni ayarlanmaz ve bilgisayarın yeniden başlatılması gerekmez. Daha fazla bilgi için [bkz. VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)ile hızlı web sitesi profili oluşturma.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Statik olarak derlenmiş ikili dosyalar profili oluşturma**|-   [Nasıl kullanılır: Statik olarak derlenmiş bir uygulama ASP.NET ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Dinamik olarak derlenmiş ikili dosyalar profili oluşturma**|-   [Nasıl ASP.NET: Dinamik olarak derlenmiş ASP.NET zamanlama verilerini toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-aspnet-web-applications"></a>Web ASP.NET profil oluşturma

|Görev|İlgili İçerik|
|----------|---------------------|
|**Örnekleme yöntemini kullanarak profil oluşturma**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Bellek ayırma ve atık toplama profili oluşturma**|-   [Bellek verilerini toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Profil kaynak etkinliği ve iş parçacığı etkinliği**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Ölçümleme yöntemini kullanarak profil oluşturma

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamaların profilini oluşturma**|-   [Ölçüm ölçümlerini kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profil hizmetleri**|-   [Ölçüm ölçümlerini kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Ölçüm izleme veri görünümlerini ve raporlarını analiz etme
- [Ölçüm izleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
