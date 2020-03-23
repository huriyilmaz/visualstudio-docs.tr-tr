---
title: Sayaç | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e2f1684257ed39560fa0ea049d3296a6e45cdd7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779486"
---
# <a name="counter"></a>Sayaç
**Sayaç** seçeneği işlemci (donanım) performans sayaçlarından veri toplar.

- Örnekleme profil oluşturma yöntemini kullanırken, **Counter** çip üzerinde performans sayacını ve örnekleme aralığı olarak kullanılacak sayaç olaylarının sayısını belirtir. Örnekleme kullanırken yalnızca bir sayaç belirtebilirsiniz.

- Enstrümantasyon profil oluşturma yöntemini kullanırken, önceki ve geçerli toplama olayları arasındaki aralıkta oluşan sayaç olaylarının sayısı profil oluşturucu raporlarında ayrı alanlar olarak listelenir. Enstrümantasyon kullanırken birden çok **Sayaç** seçeneği belirtilebilir.

  Her işlemci türünün kendi donanım performans sayaçları kümesi vardır. Profil oluşturucu, hemen hemen tüm işlemciler için ortak olan genel performans sayaçları kümesini tanımlar. Bilgisayarınızdaki genel ve işlemciye özgü sayaçları listelemek için VSPerfCmd **QueryCounters** komutunu kullanın.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]
```

```cmd
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]
```

#### <a name="parameters"></a>Parametreler
 `Name`Tezgâhın adı. Bilgisayardaki kullanılabilir sayaçların adlarını listelemek için VSPerfCmd.exe **/QueryCounters** seçeneğini kullanın.

 `Reload`Örnekleme aralığındaki sayaç olaylarının sayısı. Enstrümantasyon yöntemiile kullanmayın.

 `FriendlyName`(İsteğe bağlı) Profil oluşturucu raporlarının `Name` ve görünümlerinin sütun üstbilgilerinin yerine kullanılacak dize.

## <a name="required-options"></a>Gerekli seçenekler
 Sayaç seçeneği yalnızca aşağıdaki seçeneklerden biriyle kullanılabilir:

 **Başlangıç:** `Trace` Enstrümantasyon yöntemini kullanmak için profiloluşturucuyu başlatır.

 **Başlatma:** `AppName` Belirtilen uygulamayı ve profiloluşturucuyu başlatır. Örnekleme yöntemini kullanmak için profil oluşturucu nun başlatılması gerekir.

 **Ekle:** `PID` Profiloluşturciyi başlatır ve işlem kimliğiyle belirtilen işleme bağlar. Örnekleme yöntemini kullanmak için profil oluşturucu nun başlatılması gerekir.

## <a name="example"></a>Örnek
 Örnekleme yöntemi örneği, genel profil oluşturucu NonHaltedCycles'ın her 1000 olayında bir uygulamanın nasıl örneklenilen olduğunu gösterir.

 Enstrümantasyon yöntemi örneği, l2InstructionFetches sayaç olaylarını toplamak için profilleyicinin nasıl başharfe atınır olduğunu gösterir. L2InstructionFetches sayaç adı işlemciye özgüdür.

```cmd
; Sample Method Example
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"

;INSTRUMENTATION METHOD EXAMPLE
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
