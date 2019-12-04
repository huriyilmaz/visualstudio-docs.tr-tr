---
title: İşaretle | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4bf89469c4137052247b5a1fdfee7f8dc694fbcc
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74774000"
---
# <a name="mark"></a>İşaret
*VSPerfCmd. exe* **işaret** seçeneği, belirtilen bilgileri profil oluşturma veri dosyasına ekler. Mark, ayrı bir VSPerfReport raporunda veya profiler Kullanıcı arabiriminin Işaret raporu görünümünde listelenebilir. **İşaret** , rapor ve görüntüleme filtrelerinde başlangıç ve bitiş noktalarını belirtmek için kullanılabilir.

 **Mark** seçeneği, komut satırında belirtilen tek seçenek olmalıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Parametreler
 Profil Oluşturucu görünümlerinde ve raporlarında Işaret KIMLIĞI olarak listelenen kullanıcı tanımlı bir tamsayı `MarkID`. `MarkID` benzersiz olması gerekmez.

 `MarkName` (Isteğe bağlı) profil oluşturucu görünümlerinde ve raporlarında Işaret adı olarak listelenen kullanıcı tanımlı bir dize. `MarkName` belirtilmemişse, işaret listesinin Işaret adı alanı boştur. Boşluk veya eğik çizgi ("/") içeren dizeleri tırnak işaretleri içine alın.

## <a name="example"></a>Örnek
 Bu örnek, KIMLIĞI 123 ve işaret adı "TestMark" olan bir işaret ekler.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
