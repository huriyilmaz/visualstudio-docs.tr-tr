---
title: VSPerfCLREnv | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2163ebb9b363de8ee638998dbe56fd76f5a891c8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779915"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

VSPerfCLREnv aracı, bir .NET Framework uygulamasının profilini çıkarmak için gereken ortam değişkenlerini ayarlamak için kullanılır. Aşağıdaki sözdizimini kullanır:

```cmd
VsPerfCLREnv [/option]
```

Seçtiğiniz seçenek, üç profil oluşturma türünden hangisine bağlıdır: örnekleme, enstrümantasyon veya genel. Profil oluşturma verilerine katman etkileşim verilerini eklemek için ayrı bir seçenek gereklidir. Her seçenek için sözdizimi aşağıdaki tablolarda açıklanmıştır.

> [!NOTE]
> Profil oluşturmayı bitirdiğinizde, profil oluşturma için gerekli ortam değişkenlerini silmek için **/off** veya **/globaloff** seçeneğiyle **VSPerfCLREnv** çalıştırın. Daha fazla bilgi için, burada gösterilen Çevre Ayarlarını Silmek için VSPerfCLREnv Seçenekleri'ne bakın.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>VSPerfCLREnv seçenekleri katman etkileşimi verileri dahil etmek için

> [!WARNING]
> Seviye etkileşimi profiloluşturma Visual Studio herhangi bir sürümü kullanılarak toplanabilir. Ancak, katman etkileşimprofilleme verileri yalnızca Visual Studio Enterprise'da görüntülenebilir.

Katman etkileşimi profil oluşturma, çok katmanlı uygulamalardaki ADO.NET sorguları hakkında ek bilgiler sağlar. Veriler yalnızca eşzamanlı işlev çağrıları için toplanır. Etkileşim verileri herhangi bir profil oluşturma yöntemi kullanılarak herhangi bir profil oluşturma çalışmasına eklenebilir.

**InteractionOn** ve **GlobalInteractionOn** seçenekleri katman etkileşim verilerinin toplanmasını sağlar. Etkileşim seçeneği, bir uygulamanın profilini çıkarmak için gerekli olan VSPerfCLREnv ortam değişkenini ayarladıktan sonra ayarlanmalıdır.

Aşağıdaki örnek, örnekleme yöntemini kullanan bir profil oluşturma çalışmasında katman etkileşim verilerini içerir:

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

Aşağıdaki örnek, bir Windows hizmeti için profil oluşturma çalışmasında katman etkileşim verilerini içerir:

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>Proses enstrümantasyon profilleme için VSPerfCLREnv seçenekleri

Aşağıdaki tabloda enstrümantasyon profilleme için VSPerfCLREnv seçenekleri açıklanmaktadır:

|Seçenek|Açıklama|
|------------|-----------------|
|**Traceon**|Enstrümantasyon yöntemini kullanarak profil oluşturmayı sağlar. Bellek ayırma profil oluşturma veya nesne yaşam boyu veri toplama sağlamaz.|
|**TraceGC**|Enstrümantasyon yöntemini kullanarak bellek ayırma profiloluşturmayı sağlar. Nesne yaşam boyu verilerinin toplanmasını etkinleştirmez.|
|**TraceGCLife**|Enstrümantasyon yöntemini kullanarak bellek ayırma profiloluşturma ve nesne yaşam boyu veri toplama sağlar.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>Süreç örnekleme profilleme için VSPerfCLREnv seçenekleri

Aşağıdaki tabloda profil oluşturma örneklemesi için VSPerfCLREnv seçenekleri açıklanmaktadır:

|Seçenek|Açıklama|
|------------|-----------------|
|**SampleOn**|Örnekleme yöntemini kullanarak profil oluşturmayı sağlar. Bellek ayırma profil oluşturma veya nesne yaşam boyu veri toplama sağlamaz.|
|**SampleGC**|Örnekleme yöntemini kullanarak bellek ayırma profiloluşturmayı sağlar. Nesne yaşam boyu verilerinin toplanmasını etkinleştirmez.|
|**SampleGCLife**|Örnekleme yöntemini kullanarak bellek ayırma profiloluşturmayı sağlar. Ayrıca nesne yaşam boyu veri toplama sağlar.|
|**ÖrnekLineOff**|.NET satır düzeyinde profil oluşturma verilerinin toplanmasını devre dışı alır.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>Küresel profilleme için VSPerfCLREnv seçenekleri

Kullanıcı tarafından başlatılmak yerine işletim sistemi tarafından başlatılan ve ASP.NET web uygulaması gibi yönetilen bir hizmetin profilini çıkarmak için VSPerfCLREnv seçeneklerinin küresel profil oluşturma seçeneklerini kullanın. Aşağıdaki tabloda VSPerfCLREnv seçeneklerinin genel sürümleri açıklanmaktadır. Bu seçenekler kayıt defterinde uygun ortam değişkenlerini ayarlar.

|Seçenek|Açıklama|
|------------|-----------------|
|**GlobalTraceOn**|Enstrümantasyon yöntemini kullanarak genel profil oluşturmayı sağlar. Bellek ayırma olayları veya nesne yaşam boyu verileri toplamaz.|
|**GlobalTraceGC**|Enstrümantasyon yöntemini kullanarak genel bellek ayırma profiloluşturmayı sağlar. Nesne yaşam boyu verilerinin toplanmasını etkinleştirmez.|
|**GlobalTraceGCLife**|Enstrümantasyon yöntemini kullanarak genel bellek ayırma profiloluşturmayı sağlar. Ayrıca nesne yaşam boyu verilerinin toplanmasını sağlar.|
|**GlobalSampleon**|Örnekleme yöntemini kullanarak genel profil oluşturmayı sağlar. Bellek ayırma olaylarının veya nesne yaşam boyu verilerin indenin toplanmasını sağlamaz.|
|**GlobalSampleGC**|Örnekleme yöntemini kullanarak genel bellek ayırma profiloluşturmayı sağlar. Nesne yaşam boyu verilerinin toplanmasını etkinleştirmez.|
|**GlobalSampleGCLife**|Örnekleme yöntemini kullanarak genel bellek ayırma profiloluşturmayı sağlar. Ayrıca nesne yaşam boyu veri toplama sağlar.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>VSPerfCLREnv seçenekleri çevre ayarlarını silmek için

 Yönetilen uygulamanın profilini çıkarmayı bitirdiğinizde, VSPerfCLREnv tarafından eklenen ortam değişkenlerini silmek için aşağıdaki seçeneklerden birini kullanın. Aşağıdaki tabloda hem standart hem de genel ortam değişkenlerinin nasıl silinir:

|Seçenek|Açıklama|
|------------|-----------------|
|**Kapalı**|Standart .NET profil oluşturma için ortam değişkenlerini siler. Profil oluşturucu ortam değişkenlerini ayarlamak için global olmayan VSPerfClrEnv seçenekleri kullanıldığında bu seçeneği kullanın.|
|**GlobalOff**|Global .NET profil oluşturma için ortam değişkenlerini siler. Uygulama profil oluşturucu tarafından değil, işletim sistemi tarafından başlatıldığında bu seçeneği kullanın.|

## <a name="remarks"></a>Açıklamalar

Uygulama IDE'deki Performans Gezgini kullanılarak başlatılırsa, yönetilen bir uygulamanın profilini çıkarmak için bu seçenekler gerekmez. Performans Gezgini sizin için gerekli tüm ortam ayarlarını ayarlar.

Profil oluşturma sırasında doğru ortam ayarlanmazsa, çözümleme sırasında bir uyarı bildirilir ve yönetilen işlev adları düzgün şekilde çözülmez.

## <a name="see-also"></a>Ayrıca bkz.

[Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
