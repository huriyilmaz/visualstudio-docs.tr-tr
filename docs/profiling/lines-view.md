---
title: Satırlar Görünümü | Microsoft Docs
description: Çizgiler görünümünün yalnızca örnekleme yöntemi kullanılarak toplanan profil oluşturma verileri için nasıl kullanılabilir olduğunu öğrenin.
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
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 645bd910ec6213f9aef006f7e95e1f3fe7833250
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141811"
---
# <a name="lines-view"></a>Satırlar Görünümü
Satırlar görünümü yalnızca örnekleme yöntemi kullanılarak toplanan profil oluşturma verileri için kullanılabilir. Görünüm, ölçümler kullanılarak toplanan veriler için kullanılamaz.

 Örnekleme profili verileri için Satırlar görünümü, örnek toplanmışken doğrudan yürütülen bir işlevde deyimini tanımlar. .NET bellek verileri için Satırlar görünümü bellek ayıran deyimleri tanımlar.

 Kaynak dosyada bir deyim, bir kaynak dosyada bir satırdan daha fazlasını yayma ve tek bir satır birden fazla deyim içerebilir.

 Deyimi aşağıdakiler tarafından tanımlanır:

- İşlev deyimini içeren kaynak dosya.

- deyimini içeren işlev.

- Deyimin başlat olduğu kaynak satır.

- Deyimin başlat olduğu kaynak satırda yer alan karakter.

- Deyimin bitiş yaptığı kaynak satır.

- Deyimin bitiş yaptığı kaynak satırda yer alan karakter.

## <a name="see-also"></a>Ayrıca bkz.
- [Satırlar Görünümü](../profiling/lines-view-sampling-data.md)
- [Çizgi Görünümü - örnekleme](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Satırlar Görünümü](../profiling/lines-view-contention-data.md)
