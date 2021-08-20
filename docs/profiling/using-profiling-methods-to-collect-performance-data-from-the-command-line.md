---
title: Performans verilerini almak için komut satırı profil oluşturma yöntemlerini kullanma
description: Komut satırı Visual Studio Profil Oluşturma Araçları seçeneklerinin, profil oluşturmakta olduğunuz uygulama türü gibi faktörlere nasıl bağlı olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 71cc4ceceb2ef9b09ccc72102f0a38f5f98eeee2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156948"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Komut satırından performans verileri toplamak için profil oluşturma metotlarını kullanma
Komut Profil Oluşturma Araçları araçları ve seçenekleri seçiminiz, profil oluşturmakta olduğunuz uygulama türü, kullanmak istediğiniz profil oluşturma yöntemi ve hedef uygulamanın yerel kodda mı yoksa yerel kodda mı yazıldığı .NET Framework [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bağlıdır.

 Bu konu, komut satırı yordam konularını seçtiğiniz profil oluşturma yöntemine göre düzenletir.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Performans istatistikleri toplamak için örnekleme yöntemini kullanma
 Örnek Profil Oluşturma Araçları yöntemi, profil oluşturma çalıştırması içinde belirtilen aralıklarla performans verilerini toplar. Örnekleme verileri, CPU'ya bağlı performans sorunlarıyla ilgili içgörüler sağlar ve bir uygulamanın performansını keşfetmeye başlamanın iyi bir yolu olabilir.

 Profilleyiciyi ve uygulamayı aynı anda başlatabilirsiniz veya profilleyiciyi bir uygulamanın çalışan örneğine iliştirebilirsiniz.

|Görev|Hedef uygulama türü|
|----------|-----------------------------|
|**Uygulama başlatma**|-   [Tek başına uygulamalar](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Çalışan bir işleme ekleme**|-   [.NET Framework tek başına uygulamalar](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Yerel tek başına uygulamalar](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [ASP.NET web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Yerel hizmetler](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Ayrıntılı zamanlama verileri toplamak için ölçüm yöntemini kullanma
 Bu Profil Oluşturma Araçları yöntemi, performans bilgilerini kaydetmek için yazılım yoklamaları içeren uygulama ikililerinin kopyalarından performans verilerini toplar. Ölçüm ölçüm verisi, her bir irdeleme işlevinin başında ve sonunda ve ölçümli işlevden diğer işlevlere yapılan her çağrıda toplanır. Ölçüm yöntemi, disk kullanımı gibi işletim sistemi sorunlarıyla ilgili performans sorunlarını bulmak için kullanışlıdır.

 VInstr.exearacı ile [VInstr.exe](../profiling/vsinstr.md) oluşturabilirsiniz. Profilleyiciyi başlatıldıktan sonra, hedef uygulamayı çalıştırarak, veriler otomatik olarak, araçlı ikililerden toplanır.

 **Hedef Uygulama Türü**

- [.NET Framework tek başına bileşenleri](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Yerel tek başına bileşenler](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Web uygulamaları için ASP.NET derlenmiş](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Web uygulamaları ASP.NET olarak derlenmiş](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [.NET hizmetleri](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Yerel hizmetler](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Bellek ayırma ve nesne yaşam süresi verilerini toplamak için .NET bellek yöntemlerini kullanma
 .NET Profil Oluşturma Araçları yöntemi, bellek ayırma .NET Framework verileri ve veri kaynağında nesnelerin yaşam süresi hakkında bilgi toplama .NET Framework.

 Profilleyiciyi kullanarak hedef uygulamayı başlatabilirsiniz; profilleyiciyi bir uygulamanın çalışan örneğine iliştirebilirsiniz; ve ayrıntılı zamanlama bilgilerini bellek verileriyle birlikte toplamak için uygulamanın .NET Framework oluşturabilirsiniz.

|Görev|Hedef uygulama türü|
|----------|-----------------------------|
|**Uygulama başlatma**|-   [Tek başına .NET Framework uygulamalar](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Çalışan bir işleme ekleme**|-   [.NET Framework tek başına uygulamalar](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [ASP.NET web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Ölçüm modülleri**|-   [.NET Framework tek başına bileşenler](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Web uygulamaları için ASP.NET derlenmiş](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Web uygulamaları ASP.NET olarak derlenmiş](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [.NET hizmetleri](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Kaynak ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanma
 Eşzamanlılık Profil Oluşturma Araçları yöntemi, çok iş parçacıklı uygulamalardan kaynak ve iş parçacığı ve işlem etkinliği verilerini toplamaya olanak sağlar.

 Profiler'ı kullanarak uygulamayı başlatabilirsiniz veya profilleyiciyi bir uygulamanın çalışan örneğine iliştirebilirsiniz.

|Görev|Hedef uygulama türü|
|----------|-----------------------------|
|**Uygulama başlatma**|-   [Tek başına .NET Framework uygulama](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Tek başına yerel uygulama](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Çalışan bir işleme ekleme**|-   [.NET Framework tek başına uygulama](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Yerel tek başına uygulama](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [ASP.NET web uygulaması](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET hizmeti](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Yerel hizmet](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Profil oluşturma çalıştırması için katman etkileşim verileri ekleme
 Profil oluşturma çalıştırması için katman etkileşim verileri eklemek için komut satırı profil oluşturma araçlarıyla belirli yordamlar gerekir. Bkz. [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
