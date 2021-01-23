---
title: Sayaç | Microsoft Docs
description: VSPerfCmd.exe sayaç seçeneği hakkında bilgi edinin. Bir örnekleme aralığı belirtir veya izleme profili oluşturma sırasında olay aralıklarının bir ölçümüdür.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 85ed799cac54d630dfff1b285d3f2257e5eb99b5
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720702"
---
# <a name="counter"></a>Sayaç
**Sayaç** seçeneği, işlemci (donanım) performans sayaçlarından verileri toplar.

- Örnekleme profil oluşturma yöntemini kullanırken, **sayaç** on yonga performans sayacını ve örnekleme aralığı olarak kullanılacak sayaç olaylarının sayısını belirtir. Örnekleme kullanırken yalnızca bir sayaç belirtebilirsiniz.

- İzleme profili oluşturma yöntemini kullanırken, önceki ve geçerli koleksiyon olayları arasındaki aralıkta gerçekleşen sayaç olaylarının sayısı profil oluşturucu raporlarında ayrı alanlar olarak listelenir. Birden çok **sayaç** seçeneği, izleme kullanırken belirtilebilir.

  Her işlemci türünün kendi donanım performans sayacı kümesi vardır. Profil Oluşturucu, neredeyse tüm işlemciler için ortak olan genel performans sayaçları kümesini tanımlar. Bilgisayarınızdaki genel ve işlemciye özgü sayaçları listelemek için VSPerfCmd **QueryCounters** komutunu kullanın.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]
```

```cmd
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]
```

#### <a name="parameters"></a>Parametreler
 `Name` Sayacın adı. Bilgisayardaki kullanılabilir sayaçların adlarını listelemek için VSPerfCmd.exe **/QueryCounters** seçeneğini kullanın.

 `Reload` Örnekleme aralığındaki sayaç olaylarının sayısı. , İzleme yöntemiyle birlikte kullanmayın.

 `FriendlyName` Seçim `Name` Profil Oluşturucu raporlarının ve görünümlerinin sütun üstbilgilerinde yerine kullanılacak dize.

## <a name="required-options"></a>Gerekli seçenekler
 Sayaç seçeneği, yalnızca aşağıdaki seçeneklerden biriyle kullanılabilir:

 **Başlangıç:** `Trace` İzleme yöntemini kullanmak için profil oluşturucuyu başlatır.

 **Başlatma:** `AppName` Belirtilen uygulamayı ve profil oluşturucuyu başlatır. Örnekleme yöntemini kullanmak için profil oluşturucunun başlatılmış olması gerekir.

 **Ekle:** `PID` Profil oluşturucuyu başlatır ve işlem KIMLIĞI tarafından belirtilen işleme iliştirir. Örnekleme yöntemini kullanmak için profil oluşturucunun başlatılmış olması gerekir.

## <a name="example"></a>Örnek
 Örnekleme yöntemi örneği, genel Profiler sayacı Nonıtteddöngüleri her 1000 tekrarından uygulamanın nasıl örneklendiğini gösterir.

 İzleme yöntemi örneği, L2InstructionFetches sayacı olaylarını toplamak için profil oluşturucuyu nasıl başlatacağınızı gösterir. L2InstructionFetches sayaç adı işlemciye özeldir.

```cmd
; Sample Method Example
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"

;INSTRUMENTATION METHOD EXAMPLE
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
