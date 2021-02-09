---
title: Satırlar Görünümü | Microsoft Docs
description: Satırlar görünümünün yalnızca örnekleme yöntemi kullanılarak toplanan profil oluşturucu verileri için nasıl kullanılabilir olduğunu öğrenin.
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f99431faaa7bfc77bd7cd9a14be03f7cc2238127
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917834"
---
# <a name="lines-view"></a>Satırlar Görünümü
Satırlar görünümü yalnızca örnekleme yöntemi kullanılarak toplanan profil oluşturucu verileri için kullanılabilir. Görünüm, izleme kullanılarak toplanan veriler için kullanılamaz.

 Örnekleme profili verileri için satırlar görünümü, örnek toplandığında doğrudan yürütülen bir işlevde ifadeyi tanımlar. .NET bellek verileri için satırlar görünümü bellek ayıran deyimleri tanımlar.

 Bir kaynak dosyasında, bir ifade kaynak dosyada bir satırı daha fazla yayılabilir ve tek bir satır birden fazla deyime dahil olabilir.

 Bir ifade aşağıdaki şekilde tanımlanır:

- Function ifadesini içeren kaynak dosya.

- İfadesini içeren işlev.

- Deyimin başladığı kaynak satır.

- Deyimin başladığı kaynak satırdaki karakter.

- Deyimin bittiği kaynak satır.

- Deyimin bittiği kaynak satırdaki karakter.

## <a name="see-also"></a>Ayrıca bkz.
- [Satırlar Görünümü](../profiling/lines-view-sampling-data.md)
- [Satırlar Görünümü-Örnekleme](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Satırlar Görünümü](../profiling/lines-view-contention-data.md)
