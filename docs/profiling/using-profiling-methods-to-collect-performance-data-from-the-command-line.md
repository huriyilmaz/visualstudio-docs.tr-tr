---
title: Performans verilerini almak için komut satırı profil oluşturma yöntemlerini kullanma
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74779980"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Komut satırından performans verileri toplamak için profil oluşturma metotlarını kullanma
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Komut satırı araçları ve seçenekleri profil oluşturma araçları seçiminiz, profil oluşturduğunuz uygulamanın türü, kullanmak istediğiniz profil oluşturma yöntemi ve hedef uygulamanın yerel veya .NET Framework kodunda yazılıp yazılmayacağı gibi faktörlere bağlıdır.

 Bu konu, komut satırı yordamsal konuları seçtiğiniz profil oluşturma yöntemine göre düzenler.

## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Performans istatistiklerini toplamak için örnekleme yöntemini kullanın
 Profil Oluşturma Araçları örnekleme yöntemi, bir profil oluşturma çalıştırmasında belirtilen aralıklarda performans verilerini toplar. Örnekleme verileri, CPU 'ya dayalı performans sorunlarına yönelik öngörüler sağlayabilir ve bir uygulamanın performansını keşfetmeye başlamak için iyi bir yoldur.

 Profil oluşturucuyu ve uygulamayı aynı anda başlatabilir veya profil oluşturucuyu uygulamanın çalışan bir örneğine iliştirebilirsiniz.

|Görev|Hedef uygulama türü|
|----------|-----------------------------|
|**Uygulama başlatma**|-   [Tek başına uygulamalar](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Çalışan bir işleme iliştirme**|-   [Tek başına uygulamalar .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Yerel tek başına uygulamalar](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [ASP.NET Web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET Hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Yerel hizmetler](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Ayrıntılı zamanlama verileri toplamak için izleme yöntemini kullanın
 Profil Oluşturma Araçları izleme yöntemi, performans bilgilerini kaydetmek için yazılım araştırmalarını içeren uygulama ikili dosyalarının kopyalarından performans verilerini toplar. İzleme verileri, her bir belgelenmiş işlevin başlangıcında ve sonunda ve belgelenmiş işlevden gelen diğer işlevlere yapılan her çağrıda toplanır. İzleme yöntemi, disk kullanımı gibi g/ç sorunları ile ilgili performans sorunlarını bulmak için yararlıdır.

 İşaretlenmiş ikiliyi [VInstr.exe](../profiling/vsinstr.md) aracı ile oluşturursunuz. Profil oluşturucuyu başlattıktan sonra, hedef uygulamayı çalıştırdığınızda veriler otomatik olarak belgelenmiş ikili dosyalar üzerinden toplanır.

 **Hedef uygulama türü**

- [Tek başına bileşenleri .NET Framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)

- [Yerel tek başına bileşenler](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)

- [Statik olarak derlenen ASP.NET Web uygulamaları](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)

- [Dinamik olarak derlenen ASP.NET Web uygulamaları](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)

- [.NET Hizmetleri](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

- [Yerel hizmetler](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)

## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Bellek ayırma ve nesne yaşam süresi verilerini toplamak için .NET bellek yöntemlerini kullanın
 Profil Oluşturma Araçları .NET bellek yöntemi, .NET Framework nesnelerinin yaşam süresi hakkında .NET Framework bellek ayırma verileri ve bilgileri toplamanıza olanak sağlar.

 Profil oluşturucuyu kullanarak hedef uygulamayı başlatabilirsiniz; profil oluşturucuyu uygulamanın çalışan bir örneğine ekleyebilirsiniz; ve ayrıntılı zamanlama bilgilerini .NET Framework bellek verileriyle birlikte toplamak için uygulamanın belgelenmiş sürümlerini oluşturabilirsiniz.

|Görev|Hedef uygulama türü|
|----------|-----------------------------|
|**Uygulama başlatma**|-   [Tek başına .NET Framework uygulamalar](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|
|**Çalışan bir işleme iliştirme**|-   [Tek başına uygulamalar .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [ASP.NET Web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET Hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|
|**Araç modülleri**|-   [Tek başına bileşenleri .NET Framework](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Statik olarak derlenen ASP.NET Web uygulamaları](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Dinamik olarak derlenen ASP.NET Web uygulamaları](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [.NET Hizmetleri](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|

## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Kaynak çekişmesini ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın
 Profil Oluşturma Araçları eşzamanlılık yöntemi, çok iş parçacıklı uygulamalardan kaynak çekişmesini ve iş parçacığını toplamanıza ve etkinlik verilerini işlemenize olanak sağlar.

 Profil oluşturucuyu kullanarak uygulamayı başlatabilir veya profil oluşturucuyu bir uygulamanın çalışan örneğine iliştirebilirsiniz.

|Görev|Hedef uygulama türü|
|----------|-----------------------------|
|**Uygulama başlatma**|-   [Tek başına .NET Framework uygulaması](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Tek başına yerel uygulama](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Çalışan bir işleme iliştirme**|-   [Tek başına uygulama .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Yerel tek başına uygulama](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [ASP.NET Web uygulaması](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET hizmeti](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Yerel hizmet](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Bir profil oluşturma çalıştırmasına katman etkileşim verileri ekleme
 Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
