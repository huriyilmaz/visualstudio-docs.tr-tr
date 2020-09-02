---
title: VSPerfCLREnv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: afee2c56a7f29d50f46c7cbb734bc0297223845c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64829028"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCLREnv Aracı, bir .NET Framework uygulamasının profilini oluşturma için gereken ortam değişkenlerini ayarlamak için kullanılır. Aşağıdaki sözdizimini kullanır:  
  
```  
VsPerfCLREnv [/option]  
```  
  
 Seçtiğiniz seçenek, kullandığınız üç profil oluşturma türünden hangisinin olacağına bağlıdır: örnekleme, izleme veya küresel. Profil oluşturma verilerine katman etkileşim verileri dahil etmek için ayrı bir seçenek gereklidir. Her seçeneğin sözdizimi aşağıdaki tablolarda açıklanmıştır.  
  
> [!NOTE]
> Profil oluşturmayı tamamladığınızda, profil oluşturma için gereken ortam değişkenlerini silmek için **/off** veya **/globaloff** seçeneğiyle **VSPerfCLREnv** komutunu çalıştırın. Daha fazla bilgi için burada gösterilen ortam ayarlarını silmek üzere VSPerfCLREnv seçenekleri bölümüne bakın.  
  
 **Katman etkileşimi verilerini dahil etmek için VSPerfCLREnv seçenekleri**  
  
> [!WARNING]
> Katman etkileşimi profili oluşturma,, veya kullanılarak toplanabilir [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)] . Ancak, katman etkileşimi profil oluşturma verileri yalnızca ve ' de [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] görüntülenebilir [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] .  
  
 Katman etkileşimi profili oluşturma, çok katmanlı uygulamalardaki ADO.NET sorguları hakkında ek bilgiler sağlar. Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır. Etkileşim verileri, herhangi bir profil oluşturma yöntemi kullanılarak herhangi bir profil oluşturma çalıştırmasına eklenebilir.  
  
 **InteractionOn** ve **GlobalInteractionOn** seçenekleri, katman etkileşim verileri koleksiyonunu etkinleştirir. Bir uygulamayı profil için gereken VSPerfCLREnv ortam değişkeni ayarlandıktan sonra etkileşim seçeneği ayarlanmalıdır.  
  
 Aşağıdaki örnek, örnekleme yöntemini kullanan bir profil oluşturma çalıştırmasında katman etkileşim verileri içerir:  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 Aşağıdaki örnek, bir Windows hizmeti için profil oluşturma çalıştırmasında katman etkileşim verileri içerir:  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **Işlem Izleme profili oluşturma için VSPerfCLREnv seçenekleri**  
  
 Aşağıdaki tabloda, izleme profili oluşturma için VSPerfCLREnv seçenekleri açıklanmaktadır:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**TraceOn**|İzleme yöntemini kullanarak profil oluşturmayı etkinleştirilir. Bellek ayırma profili oluşturmayı veya nesne yaşam süresi verilerini toplamayı etkinleştirmez.|  
|**TraceGC**|İzleme yöntemini kullanarak bellek ayırma profili oluşturmayı mümkün. Nesne ömrü verilerinin toplanmasını etkinleştirmez.|  
|**TraceGCLife**|Bellek ayırma profili oluşturmayı ve izleme yöntemini kullanarak nesne yaşam süresi verilerini toplamayı mümkün bir şekilde sunar.|  
  
 **Işlem örnekleme profili oluşturma için VSPerfCLREnv seçenekleri**  
  
 Aşağıdaki tabloda örnekleme profili oluşturma için VSPerfCLREnv seçenekleri açıklanmaktadır:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**SampleOn**|Örnekleme yöntemi kullanılarak profil oluşturmayı etkinleştirilir. Bellek ayırma profili oluşturmayı veya nesne yaşam süresi verilerini toplamayı etkinleştirmez.|  
|**Örnekley**|Örnekleme yöntemini kullanarak bellek ayırma profili oluşturmayı mümkün. Nesne ömrü verilerinin toplanmasını etkinleştirmez.|  
|**SampleGCLife**|Örnekleme yöntemini kullanarak bellek ayırma profili oluşturmayı mümkün. , Nesne ömrü verilerinin toplanmasını de mümkün.|  
|**SampleLineOff**|.NET satır düzeyi profil oluşturma verilerinin koleksiyonunu devre dışı bırakır.|  
  
 **Genel profil oluşturma için VSPerfCLREnv seçenekleri**  
  
 Ve Kullanıcı tarafından başlatılmakta olan işletim sistemi tarafından başlatılan Web uygulaması gibi yönetilen bir hizmeti profil oluşturmak için, VSPerfCLREnv seçeneklerinin genel profil oluşturma seçeneklerini kullanın. Aşağıdaki tablo, VSPerfCLREnv seçeneklerinin genel sürümlerini açıklamaktadır. Bu seçenekler kayıt defterindeki uygun ortam değişkenlerini ayarlar.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**GlobalTraceOn**|İzleme yöntemini kullanarak genel profil oluşturmayı mümkün. Bellek ayırma olayları veya nesne yaşam süresi verileri toplamaz.|  
|**GlobalTraceGC**|İzleme yöntemini kullanarak genel bellek ayırma profili oluşturmayı mümkün. Nesne ömrü verilerinin toplanmasını etkinleştirmez.|  
|**GlobalTraceGCLife**|İzleme yöntemini kullanarak genel bellek ayırma profili oluşturmayı mümkün. , Nesne ömrü verilerinin toplanmasını da mümkün.|  
|**GlobalSampleOn**|Örnekleme yöntemini kullanarak genel profil oluşturmayı mümkün. , Bellek ayırma olaylarının veya nesne yaşam süresi verilerinin toplanmasını etkinleştirmez.|  
|**GlobalSampleGC**|Örnekleme yöntemini kullanarak genel bellek ayırma profili oluşturmayı mümkün. Nesne ömrü verilerinin toplanmasını etkinleştirmez.|  
|**GlobalSampleGCLife**|Örnekleme yöntemini kullanarak genel bellek ayırma profili oluşturmayı mümkün. , Nesne ömrü verilerinin toplanmasını de mümkün.|  
  
 **Ortam ayarlarını silmek için VSPerfCLREnv seçenekleri**  
  
 Yönetilen uygulamanın profilini oluşturmayı tamamladığınızda, VSPerfCLREnv tarafından eklenen ortam değişkenlerini silmek için aşağıdaki seçeneklerden birini kullanın. Aşağıdaki tabloda hem standart hem de genel ortam değişkenlerinin nasıl silineceği açıklanmaktadır:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Kapalı**|Standart .NET profil oluşturma için ortam değişkenlerini siler. Profil Oluşturucu ortam değişkenlerini ayarlamak için genel olmayan VSPerfClrEnv seçenekleri kullanıldığında bu seçeneği kullanın.|  
|**GlobalOff**|Genel .NET profil oluşturma için ortam değişkenlerini siler. Uygulama, profil oluşturucu değil, işletim sistemi tarafından başlatıldığında bu seçeneği kullanın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenekler, uygulama IDE 'de Performans Gezgini kullanılarak başlatılırsa, yönetilen bir uygulamanın profilini oluşturmak için gerekli değildir. Performans Gezgini, sizin için gerekli tüm ortam ayarlarını belirler.  
  
 Profil oluşturma sırasında doğru ortam ayarlanmamışsa, analiz sırasında bir uyarı bildirilir ve yönetilen işlev adları düzgün bir şekilde çözümlenmeyecektir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut Satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)
