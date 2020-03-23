---
title: Performans verileri elde etmek için komut satırı profil oluşturma yöntemlerini kullanma
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b30aa723ea3014aec2bd05d4bd204b9427b3c218
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779980"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Komut satırından performans verileri toplamak için profil oluşturma metotlarını kullanma
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları komut satırı araçları ve seçenekleri seçiminiz, profil oluşturma yaptığınız uygulama türü, kullanmak istediğiniz profil oluşturma yöntemi ve hedef uygulamanın yerel veya .NET Framework kodunda yazıp yazılmadığı gibi etkenlere bağlıdır.

 Bu konu, komut satırı yordam konularını seçtiğiniz profil oluşturma yöntemine göre düzenler.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Performans istatistiklerini toplamak için örnekleme yöntemini kullanın
 Profil Oluşturma Araçları örnekleme yöntemi, profil oluşturma çalışmasında belirli aralıklarla performans verileri toplar. Örnekleme verileri, CPU'ya bağlı performans sorunları hakkında öngörüler sağlayabilir ve bir uygulamanın performansını keşfetmeye başlamak için iyi bir yol olabilir.

 Profil oluşturucuyu ve uygulamayı aynı anda başlatabilir veya profil oluşturucuyu çalışan bir uygulama örneğine ekleyebilirsiniz.

|Görev|Hedef uygulama türü|
|----------|-----------------------------|
|**Bir uygulama başlatma**|-   [Tek başına uygulamalar](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Çalışan bir işleme ekleme**|-   [.NET Framework tek başına uygulamalar](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Yerel tek başına uygulamalar](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [ASP.NET web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Yerel hizmetler](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Ayrıntılı zamanlama verileri toplamak için enstrümantasyon yöntemini kullanın
 Profil Oluşturma Araçları enstrümantasyon yöntemi, performans bilgilerini kaydetmek için yazılım sondaları içeren uygulama ikililerinin kopyalarından performans verileri toplar. Enstrümantasyon verileri, her enstrümantasyon işlevinin başında ve sonunda ve enstrümantasyon işlevinden diğer işlevlere yapılan her çağrıda toplanır. Enstrümantasyon yöntemi, disk kullanımı gibi G/Ç sorunlarıyla ilgili performans sorunlarını keşfetmek için yararlıdır.

 [VInstr.exe](../profiling/vsinstr.md) aracı ile enstrümante ikili oluşturun. Profil oluşturucuyu başlattıktan sonra, hedef uygulamayı çalıştırdığınızda veriler otomatik olarak araçlı ikililerden toplanır.

 **Hedef Uygulama Türü**

- [.NET Framework tek başına bileşenler](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Yerel bağımsız bileşenler](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Web uygulamaları ASP.NET statik olarak derlenmiş](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Web uygulamaları ASP.NET dinamik olarak derlenmiş](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [.NET hizmetleri](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Yerel hizmetler](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Bellek ayırma ve nesne yaşam boyu verilerini toplamak için .NET bellek yöntemlerini kullanın
 Profil Oluşturma Araçları .NET bellek yöntemi, .NET Framework bellek ayırma verilerini ve .NET Framework'deki nesnelerin yaşam süresi hakkında bilgi toplamanızı sağlar.

 Profil oluşturucuyu kullanarak hedef uygulamayı başlatabilirsiniz; profil oluşturucuyu çalışan bir uygulama örneğine ekleyebilirsiniz; ve .NET Framework bellek verileriyle birlikte ayrıntılı zamanlama bilgileri toplamak için uygulamanın enstrümante sürümlerini oluşturabilirsiniz.

|Görev|Hedef uygulama türü|
|----------|-----------------------------|
|**Bir uygulama başlatma**|-   [Tek başına .NET Framework uygulamaları](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Çalışan bir işleme ekleme**|-   [.NET Framework tek başına uygulamalar](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [ASP.NET web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Enstrüman modülleri**|-   [.NET Framework tek başına bileşenler](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Web uygulamaları ASP.NET statik olarak derlenmiş](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Web uygulamaları ASP.NET dinamik olarak derlenmiş](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [.NET hizmetleri](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Kaynak çekişmesi ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın
 Profil Oluşturma Araçları eşzamanlılık yöntemi, çok iş parçacıklı uygulamalardan kaynak çekişmesi ve iş parçacığı ve iş parçacığı verileri toplamanızı sağlar.

 Profiler'ı kullanarak uygulamayı başlatabilir veya profil oluşturucuyu çalışan bir uygulama örneğine ekleyebilirsiniz.

|Görev|Hedef uygulama türü|
|----------|-----------------------------|
|**Bir uygulama başlatma**|-   [Tek başına .NET Framework uygulaması](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Tek başına yerel uygulama](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Çalışan bir işleme ekleme**|-   [.NET Framework tek başına uygulama](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Yerel tek başına uygulama](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [ASP.NET web uygulaması](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET servisi](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Yerel hizmet](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Profil oluşturma çalışmasına katman etkileşim verileri ekleme
 Profil oluşturma çalışmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşim verilerini topla](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
