---
title: Satır Görünümü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 25dbb0beb600f7f043ae006e09ac48b9b64d613b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773987"
---
# <a name="lines-view"></a>Satırlar Görünümü
Satırlar görünümü yalnızca örnekleme yöntemi kullanılarak toplanan profil oluşturucu verileri için kullanılabilir. Görünüm, enstrümantasyon kullanılarak toplanan veriler için kullanılamaz.

 Profil verilerini örneklemek için, Satırlar görünümü, örnek toplandığında doğrudan çalıştırılan bir işlevdeki deyimi tanımlar. .NET bellek verileri için, Satırlar görünümü bellek ayıran ifadeleri tanımlar.

 Kaynak dosyada, bir deyim kaynak dosyadaki bir satırdan daha fazla satıra yayılabilir ve tek bir satır birden fazla deyim içerebilir.

 Bir deyim aşağıdaki ler tarafından tanımlanır:

- İşlev deyimini içeren kaynak dosya.

- İfadeyi içeren işlev.

- İfadenin başladığı kaynak satırı.

- İfadenin başladığı kaynak satırdaki karakter.

- İfadenin sona erdiği kaynak satırı.

- İfadenin sona erdiği kaynak satırdaki karakter.

## <a name="see-also"></a>Ayrıca bkz.
- [Satırlar Görünümü](../profiling/lines-view-sampling-data.md)
- [Satır Görünümü - örnekleme](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Satırlar Görünümü](../profiling/lines-view-contention-data.md)
