---
title: Sayaç | Microsoft Docs
description: Bu seçeneğin Sayaç seçeneği hakkında VSPerfCmd.exe. Örnekleme aralığını belirtir veya ölçüm profili oluşturmada olay aralıklarının ölçüsüdür.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b1d49ac97d783457634a82705033ac7a2d043d84
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039286"
---
# <a name="counter"></a>Sayaç
Sayaç **seçeneği,** işlemci (donanım) performans sayaçlarından veri toplar.

- Örnekleme profil oluşturma yöntemini kullanırken **Counter,** yonga üzerinde performans sayacını ve örnekleme aralığı olarak kullanmak üzere sayaç olay sayısını belirtir. Örnekleme kullanırken yalnızca bir sayaç belirtesiniz.

- Ölçümcük profili oluşturma yöntemini kullanırken, önceki ve geçerli koleksiyon olayları arasındaki aralıkta meydana gelen sayaç olaylarının sayısı profil oluşturma raporlarında ayrı alanlar olarak listelenir. Ölçüm **ölçümlerini** kullanırken birden çok Sayaç seçeneği belirtilebilir.

  Her işlemci türünün kendi donanım performans sayaçları kümesi vardır. Profilleyici, neredeyse tüm işlemciler için ortak olan bir dizi genel performans sayacı tanımlar. Bilgisayarınızda genel ve işlemciye özgü sayaçları listeleyebilirsiniz. VSPerfCmd **QueryCounters komutunu** kullanın.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]][Options]
```

```cmd
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]][/Counter:Name[,Reload[,FriendlyName]]][Options]
```

#### <a name="parameters"></a>Parametreler
 `Name` Sayacın adı. Bilgisayarda VSPerfCmd.exe sayaçların adlarını listeley için **VSPerfCmd.exe /QueryCounters** seçeneğini kullanın.

 `Reload` Örnekleme aralığındaki sayaç olaylarının sayısı. ölçüm ölçümleme yöntemiyle birlikte kullanmayın.

 `FriendlyName` (İsteğe bağlı) Profil oluşturma raporlarının ve `Name` görünümlerinin sütun üst bilgisinde yerine kullanmak istediğiniz dize.

## <a name="required-options"></a>Gerekli seçenekler
 Sayaç seçeneği yalnızca aşağıdaki seçeneklerden biri ile kullanılabilir:

 **Başlat:** `Trace` Profil oluşturma yöntemini kullanmak için profilleyiciyi başlatılır.

 **Başlatma:** `AppName` Belirtilen uygulamayı ve profilleyiciyi başlatır. Örnekleme yöntemini kullanmak için profil oluşturma başlatıcı başlatılmış olması gerekir.

 **Ekleme:** `PID` Profilleyiciyi başlatır ve işlem kimliği tarafından belirtilen işleme iliştirer. Örnekleme yöntemini kullanmak için profil oluşturma başlatıcı başlatılmış olması gerekir.

## <a name="example"></a>Örnek
 Örnekleme yöntemi örneğinde, NonHaltedCycles genel profil oluşturma sayacının her 1000 örneğinde bir uygulamanın nasıl örneklen olduğu gösterildi.

 Ölçüm yöntemi örneği, L2InstructionFetches sayaç olaylarını toplamak için profil oluşturmanın nasıl başlatılamadığnı gösteriyor. L2InstructionFetches sayacının adı işlemciye özeldir.

```cmd
; Sample Method Example
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"

;INSTRUMENTATION METHOD EXAMPLE
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
