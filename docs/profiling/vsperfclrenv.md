---
title: VSPerfCLREnv | Microsoft Docs
description: Bir uygulamanın profilini oluşturmak için gereken ortam değişkenlerini ayarlamak için VSPerfCLREnv aracının nasıl .NET Framework öğrenin.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ee2333e73e6fbc22e25f12da49c7e6586885215d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140563"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

VSPerfCLREnv aracı, bir uygulamanın profilini oluşturmak için gereken ortam değişkenlerini .NET Framework kullanılır. Aşağıdaki söz dizimlerini kullanır:

```cmd
VsPerfCLREnv [/option]
```

Seçtiğiniz seçenek, kullandığınız üç profil oluşturma türüne bağlıdır: örnekleme, ölçümleme veya genel. Profil oluşturma verilerine katman etkileşim verilerini eklemek için ayrı bir seçenek gereklidir. Her seçeneğin söz dizimi aşağıdaki tablolarda açıklanmıştır.

> [!NOTE]
> Profil oluşturmayı bitirdikten sonra **VSPerfCLREnv'i** **/off** veya **/globaloff** seçeneğiyle çalıştırarak profil oluşturma için gerekli ortam değişkenlerini silin. Daha fazla bilgi için burada gösterilen VSPerfCLREnv Ortam Bilgilerini Ayarlar Seçenekleri'ne bakın.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>Katman etkileşimi verilerini dahil etme için VSPerfCLREnv seçenekleri

> [!WARNING]
> Katman etkileşimi profili oluşturma, herhangi bir sürüm kullanılarak Visual Studio. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise.

Katman etkileşimi profili oluşturma, çok katmanlı ADO.NET sorgular hakkında ek bilgi sağlar. Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır. Etkileşim verileri herhangi bir profil oluşturma yöntemi kullanılarak profil oluşturma çalıştırmalarına eklenebilir.

**InteractionOn** ve **GlobalInteractionOn** seçenekleri katman etkileşim verilerini toplamaya olanak sağlar. Bir uygulamanın profilini oluşturmak için gereken VSPerfCLREnv ortam değişkeni ayardan sonra etkileşim seçeneğinin ayarlanmış olması gerekir.

Aşağıdaki örnek, örnekleme yöntemini kullanan bir profil oluşturma çalıştırması içinde katman etkileşim verilerini içerir:

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

Aşağıdaki örnek, bir hizmet için profil oluşturma çalıştırması içinde katman etkileşim Windows içerir:

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>İşlem araçları profili oluşturma için VSPerfCLREnv seçenekleri

Aşağıdaki tabloda, ölçümcük profili oluşturma için VSPerfCLREnv seçenekleri açık almaktadır:

|Seçenek|Açıklama|
|------------|-----------------|
|**Traceon**|Ölçümleme yöntemini kullanarak profil oluşturmayı sağlar. Bellek ayırma profili oluşturmayı veya nesne yaşam süresi verilerini toplamayı etkinleştirmez.|
|**TraceGC**|Ölçümleme yöntemini kullanarak bellek ayırma profili oluşturmayı sağlar. Nesne yaşam süresi verilerini toplamayı etkinleştirmez.|
|**TraceGCLife**|Ölçümleme yöntemini kullanarak bellek ayırma profili oluşturmayı ve nesne yaşam süresi verilerini toplamayı sağlar.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>İşlem örnekleme profili oluşturma için VSPerfCLREnv seçenekleri

Aşağıdaki tabloda, örnekleme profili oluşturma için VSPerfCLREnv seçenekleri açık almaktadır:

|Seçenek|Açıklama|
|------------|-----------------|
|**SampleOn**|Örnekleme yöntemini kullanarak profil oluşturmayı sağlar. Bellek ayırma profili oluşturmayı veya nesne yaşam süresi verilerini toplamayı etkinleştirmez.|
|**SampleGC**|Örnekleme yöntemini kullanarak bellek ayırma profili oluşturmayı sağlar. Nesne yaşam süresi verilerini toplamayı etkinleştirmez.|
|**SampleGCLife**|Örnekleme yöntemini kullanarak bellek ayırma profili oluşturmayı sağlar. Ayrıca nesne yaşam süresi verilerini toplamayı da sağlar.|
|**SampleLineOff**|.NET satır düzeyi profil oluşturma verilerini toplamayı devre dışı bırakma.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Genel profil oluşturma için VSPerfCLREnv seçenekleri

kullanıcı tarafından değil işletim sistemi tarafından ASP.NET web uygulaması gibi yönetilen bir hizmetin profilini oluşturmak için VSPerfCLREnv seçeneklerinin genel profil oluşturma seçeneklerini kullanın. Aşağıdaki tabloda VSPerfCLREnv seçeneklerinin genel sürümleri açık almaktadır. Bu seçenekler kayıt defterindeki uygun ortam değişkenlerini ayarlar.

|Seçenek|Açıklama|
|------------|-----------------|
|**GlobalTraceOn**|Ölçümleme yöntemini kullanarak genel profil oluşturmayı sağlar. Bellek ayırma olaylarını veya nesne yaşam süresi verilerini toplamaz.|
|**GlobalTraceGC**|Ölçümleme yöntemini kullanarak genel bellek ayırma profili oluşturmayı sağlar. Nesne yaşam süresi verilerini toplamayı etkinleştirmez.|
|**GlobalTraceGCLife**|Ölçümleme yöntemini kullanarak genel bellek ayırma profili oluşturmayı sağlar. Ayrıca nesne ömrü verilerini toplamayı da sağlar.|
|**GlobalSampleOn**|Örnekleme yöntemini kullanarak genel profil oluşturmayı sağlar. Bellek ayırma olaylarını veya nesne yaşam süresi verilerini toplamayı etkinleştirmez.|
|**GlobalSampleGC**|Örnekleme yöntemini kullanarak genel bellek ayırma profili oluşturmayı sağlar. Nesne yaşam süresi verilerini toplamayı etkinleştirmez.|
|**GlobalSampleGCLife**|Örnekleme yöntemini kullanarak genel bellek ayırma profili oluşturmayı sağlar. Ayrıca nesne yaşam süresi verilerini toplamayı da sağlar.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>Ortam ayarlarını silmek için VSPerfCLREnv seçenekleri

 Yönetilen uygulamanın profilini oluşturmayı bitirdikten sonra, VSPerfCLREnv tarafından eklenen ortam değişkenlerini silmek için aşağıdaki seçeneklerden birini kullanın. Aşağıdaki tabloda hem standart hem de genel ortam değişkenlerinin nasıl silinecekleri açıkmektedir:

|Seçenek|Açıklama|
|------------|-----------------|
|**Kapalı**|Standart .NET profili oluşturma için ortam değişkenlerini siler. Profil oluşturma ortam değişkenlerini ayarlamak için genel olmayan VSPerfClrEnv seçenekleri kullanılırken bu seçeneği kullanın.|
|**GlobalOff**|Genel .NET profili oluşturma için ortam değişkenlerini siler. Uygulama, profil oluşturma sistemi tarafından değil işletim sistemi tarafından başlatken bu seçeneği kullanın.|

## <a name="remarks"></a>Açıklamalar

Bu seçenekler, uygulama IDE'de uygulamanın profili kullanılarak Performans Gezgini için gerekli değildir. Bu Performans Gezgini gerekli tüm ortam ayarlarını sizin için ayarlar.

Profil oluşturma sırasında doğru ortam ayarlanmamışsa analiz sırasında bir uyarı rapor eder ve yönetilen işlev adları düzgün çözümlenmeyebilir.

## <a name="see-also"></a>Ayrıca bkz.

[Komut satırı profili](../profiling/using-the-profiling-tools-from-the-command-line.md)
